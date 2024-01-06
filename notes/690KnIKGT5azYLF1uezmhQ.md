
# Day 29 - 準備好要上線了嗎？(七)

雖然本次架設的挑戰已經完成了，但既然都用到 Traefik 就讓我們繼續往後學下去吧（汗

因為之後 App 將交由 Traefik 的架構去處理，之後的流量將從原本的一台機器接到流量在透過 Traefik 分配變成 到 Traefik 的機器，再導引至 app 的機器

今天開始設定 Swarm 前有其他前置作業

## DNS
重新設定兩台機器，預計會放一台 Manager(Traefik)，跟一台 Worker(App)
現在只需要將 Manager 的 IP 放入 DNS 導入即可，剩下的會交由 Traefik

## EC2
這邊則是多加開一台機器做 Worker
同時為了之後的 Swarm 設定，先將內網打通，將 `InboundRules` 加入一條給 `SecurityGroup`（內含兩台機器）

## Swarm
開好兩台機器後，在機器內做 Swarm 的初始化，將一台機器設為 Manager ，一台設定為 Work
步驟很簡單，詳細在[官方文件](https://dockerswarm.rocks/)很清楚
確認兩台機器進入管理的狀態後就能開始設定 YAML 了

## Compose YAML
之前是將 Traefik & App 的服務都寫在一起，這邊就要分開之後給不同機器部署
原則上就是前面的檔案做分離，按照[文件](https://dockerswarm.rocks/traefik/)除了 YAML 增補一些設定之外，在部署前還有一些 Docker node 的設定都是參照文件
雖然他說二十分鐘就可以弄，但感覺有點唬 XD ，前提還是要對整個 Network 熟悉才能順利完成 

下面因為前幾天已經把設定搞得差不多了，所以改動很小
### Traefik
```
services:
  traefik:
    ...
    deploy:
      placement:
        constraints:
          - node.labels.traefik-public.traefik-public-certificates == true
      labels:
        ...
    volumes:
      ...
    command:
      ...
      - --providers.docker.swarmmode
```


### docker-compose
```
  app:
    ...
    deploy:
      placement:
        constraints:
          - node.role == manager
```

## Deploy
這邊也簡單，因為之前 Action 也寫好了，所以只是把 `compose up` 換成 `stack deploy`

小地方改的就是因為 Action 目前寫法是靠 Push 觸發，所以 Traefik / App 分成兩個分支處理
```
# .github/workflows/deploy_traefik.yml

on:
  push:
    branches: [ "traefik" ]
 
   ...
  deploy:
    name: Traefik compose
    runs-on: ubuntu-latest
    needs: check

    steps:
      - name: Stack deploy
        uses: appleboy/ssh-action@master
        with:
          host: ${{ vars.TRAEFIK_HOST_DNS }}
          username: ${{ vars.EC2_USER_NAME }}
          key: ${{ secrets.EC2_SSH_KEY }}
          script: >-
            cd ~/${{ vars.REPO_NAME }};
            GODADDY_API_KEY=${{ secrets.GODADDY_API_KEY }}
            GODADDY_API_SECRET=${{ secrets.GODADDY_API_SECRET }}
            docker stack deploy -c traefik.yml traefik
```

```
# .github/workflows/deploy_app.yml

on:
  push:
    branches: [ "main" ]

jobs:
  ...

  deploy:
    name: App compose 
    runs-on: ubuntu-latest
    needs: check

    steps:
      - name: Build image
        uses: appleboy/ssh-action@master
        with:
          host: ${{ vars.TRAEFIK_HOST_DNS }}
          username: ${{ vars.EC2_USER_NAME }}
          key: ${{ secrets.EC2_SSH_KEY }}
          script: |
            cd ~/${{ vars.REPO_NAME }}
            docker-compose build --build-arg RAILS_MASTER_KEY=${{ secrets.RAILS_MASTER_KEY }}

      - name: Compose up
        uses: appleboy/ssh-action@master
        with:
          host: ${{ vars.TRAEFIK_HOST_DNS }}
          username: ${{ vars.EC2_USER_NAME }}
          key: ${{ secrets.EC2_SSH_KEY }}
          script: >-
            cd ~/${{ vars.REPO_NAME }};
            RAILS_MASTER_KEY=${{ secrets.RAILS_MASTER_KEY }}
            MPG_HASH_KEY=${{ secrets.MPG_HASH_KEY }}
            MPG_HASH_IV=${{ secrets.MPG_HASH_IV }}
            docker stack deploy -c docker-compose.yml ironman2023

```

兩個都分都推一遍，就能個自動部署囉！ 終於要完賽啦！

----
目前網址修正：
`https://ironman2023.dantecheng.me/`

~~看到 Error 畫面是正常的，過程中 Compile 被我玩壞， SSL 則是不小心被我刪掉 總之還在處理 XD~~
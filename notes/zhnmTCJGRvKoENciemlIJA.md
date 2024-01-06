# Day 26 - 準備好要上線了嗎？(四)

## Traefik
昨天設定完 compose 後已經可以在本機連到容器內

而今天的目標就是使用 `Traefik` 來做 `reverse-proxy`，並手動部署到機器內

因為讓情境簡單化，都會先暫時跳過 SSL 憑證

首先 在 compose yml 內部加入 traefik image

```
# docker-compose.yml

  traefik:
    image: traefik:v2.10
    restart: always
    container_name: reverse-proxy
```

因為原本服務(app / database / redis) 有自己的 `net`，這裡視為一個內網，我們並不希望外部能直接接觸到這層，所以會包一層網路並有一個入口供外部流量進入

而 traefik 就是那個入口，所以加一層網路 `traefik-public` 給 app 與 traefik 溝通，如此外部就不能直接觸碰到 database / redis

```
# docker-compose.yml

  app:
    networks:
      - net
      - traefik-public

  traefik:
    image: traefik:v2.10
    restart: always
    container_name: reverse-proxy
    networks:
      - traefik-public
```

開 80 port 給內外部流量對應， 8080 的部分則是 `traefik` 的 dashboard，可以查看設定與狀態

```
# docker-compose.yml

  traefik:
    ...
    networks:
      - traefik-public
    ports:
      - "80:80"
      - "8080:8080"
```

開完 `traefik` 的 port 後，內部 app 需要去接外面的流量
所以要指定 
1. 啟用 `traefik` 
2. network `traefik-public`
3. 流量的 host name, 這裡預計用 `ironman2023.traefik.dantecheng.me`

```
# docker-compose.yml

  app:
    labels:
      - traefik.enable=true
      - traefik.docker.network=traefik-public
      - traefik.http.routers.app.rule=Host(`ironman2023.traefik.dantecheng.me`)
```

還有一些基本設定，這部分就不贅述，[文件](https://doc.traefik.io/traefik/getting-started/quick-start/)有說明

```
traefik:
    ...
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
    command:
      - --providers.docker
```

到這裡算是做完 compose 的設定檔，可以預期在機器內開始跑的時候會按設定檔運作

## EC2
做完設定檔接下來就是在 EC2 內部手動部署實驗看看是否網路暢通

先做 EC2 的建立，基本上都照著介面填入即可

這裡只特別做了一把新的 key 供後面 SSH 連線進入，也可以不用 key 透過 Web 連線進入實體

都建完後，用剛剛的 Key 來設定本機的 SSH

```
# ~/.ssh/config

Host <name>
  HostName <ip>
  Port 22
  IdentitiesOnly yes
  IdentityFile </path/key_name.pem>
  User ec2-user
~
```

如此這般就能輸入 `ssh <name>` 連入機器

進入機器後要手動在 EC2 內拉下前面實作的內容，此時因為還沒做好自動設定，先從簡使用 HTTPS 來拉專案

這一步會需要先去 GitHub 的 [AccessToken](https://github.com/settings/tokens?type=beta)去開一個 token 供暫時性的使用，因為前兩年 GitHub 已經移除個人密碼來拉專案

在實體內拉完專案之後，因為內部還沒有 `docker` 與 `docker compose`，所以先進行安裝

安裝完之後原則上只要啟動容器即可

```
docker compose up -d
```

但還沒完！ 這樣也無法進入流量進入，還需要設定 EC2 `Security Groups` の `InboundRules`

剛剛建機器的時候我只開了 22 port 給 SSH 使用，這裡需要再開 80 port

如此一來，整個網路就串通了！ 可喜可賀！


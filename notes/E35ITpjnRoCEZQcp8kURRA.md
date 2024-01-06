# Day 27 - 準備好要上線了嗎？(五

## GitHub Action
前一步已經完成了 HTTP 連線進入網站，目前就還剩下 `Swarm`, `SSL`, 以及 `Runner` 的設定

考量到方便性，這邊先完成 `Runner` 的基本設定，因為一開始都是在用 `GitHub` ，理所當然的使用 `Actions` 來完成後續的自動化部署

基於篇幅就只做很土炮的方式自動部署，只需要先有人代替我在推 Branch 後將程式丟到 EC2 上執行即可 XD
因為這邊也是自己短時間摸索出一個最簡單的方式，所以如果有任何想法歡迎不吝指教
後面的篇章也還會慢慢改進

### 觸發條件
先設定只要有東西推到 `main` 上就自動執行

```
# .github/workflows/deploy.yml

name: "Deploy"

on:
  push:
    branches: [ "main" ]
```


### 重新拉取專案
`HOST_DNS` 是這次 EC2 的 host name
`EC2_USER_NAME` 則是 EC2 User 通常都是 `ec2-user`
`EC2_SSH_KEY` 就是設定進入實體要用的那個 pem

```yaml
# .github/workflows/deploy.yml

name: "Deploy"
...
jobs:
  reset:
    name: Deploy to EC2 on master branch push
    runs-on: ubuntu-latest
    
    steps:
      - name: Deploy
          uses: appleboy/ssh-action@master
          with:
          host: ${{ vars.HOST_DNS }}
          username: ${{ vars.EC2_USER_NAME }}
          key: ${{ secrets.EC2_SSH_KEY }}
```

script 幫我執行原本手動的事情
因為暫時不想寫判斷，所以就一率移除後重新 clone XD

```yaml
# .github/workflows/deploy.yml

name: "Deploy"
...
jobs:
  deploy:
    ...
    steps:
      - name: Deploy
        ...
        script: |
          sudo rm -f -r ~/${{ vars.REPO_NAME }}/
          git clone https://${{ vars.REPO_USER_NAME }}:${{ secrets.REPO_KEY}}@github.com/Dantecheng41/ironman2023.git
```

### 啟動容器
這裡也是把原本的 `docker compose up` 自動化 

```yaml
# .github/workflows/deploy.yml

name: "Deploy"
...
jobs:
  reset:
    ...
    
  start:
        name: Up Docker compose
    runs-on: ubuntu-latest
    steps:
       - name: compose up
       ...
       - script: |
         cd ~/ironman2023
         docker compose down
         docker compose up --build -d
```


這樣設定完之後，往後推上 `GitHub` 就會自動處理囉


![https://ithelp.ithome.com.tw/upload/images/20231012/20142040n1EwUihnlJ.png](https://ithelp.ithome.com.tw/upload/images/20231012/20142040n1EwUihnlJ.png)

預計明天來處理 `SSL` ！
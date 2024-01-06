---
title: "後臺與DEMO網站"
tags: hackpad
---

# 後臺與DEMO網站

> [點此觀看原始內容](https://g0v.hackpad.tw/H4AHFXkL7Pc)


後臺
[http://ec2-54-92-66-45.ap-northeast-1.compute.amazonaws.com:3000/](http://ec2-54-92-66-45.ap-northeast-1.compute.amazonaws.com:3000/)
設置環境變數
export MONGO_URL=mongodb://localhost:27017/app4am
export ROOT_URL=[http://ec2-54-92-66-45.ap-northeast-1.compute.amazonaws.com:3000/](http://ec2-54-92-66-45.ap-northeast-1.compute.amazonaws.com:3000/)
export PORT=3000
啟動指令
forever start /home/ec2-user/mrbigmouth/server/backend/main.js
(forever指令位於 /usr/local/bin/forever內)

前臺Demo網站
[http://ec2-54-92-66-45.ap-northeast-1.compute.amazonaws.com:9090/](http://ec2-54-92-66-45.ap-northeast-1.compute.amazonaws.com:9090/)
設置環境變數
export MONGO_URL=mongodb://localhost:27017/app4am
export ROOT_URL=[http://ec2-54-92-66-45.ap-northeast-1.compute.amazonaws.com:](http://ec2-54-92-66-45.ap-northeast-1.compute.amazonaws.com:9090/)[9](http://ec2-54-92-66-45.ap-northeast-1.compute.amazonaws.com:9090/)[09](http://ec2-54-92-66-45.ap-northeast-1.compute.amazonaws.com:9090/)[0/](http://ec2-54-92-66-45.ap-northeast-1.compute.amazonaws.com:9090/)
export PORT=9090
啟動指令
forever start /home/ec2-user/mrbigmouth/server/web/main.js
(forever指令位於 /usr/local/bin/forever內)



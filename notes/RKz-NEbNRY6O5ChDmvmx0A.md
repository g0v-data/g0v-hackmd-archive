---
title: "g0v Cloud"
tags: hackpad
---

# g0v Cloud

> [點此觀看原始內容](https://g0v.hackpad.tw/IL5LKFS9yHp)


## 前言

我是 Ronny ，我在三年前開發了一個 heroku clone ，主因是我覺得 heroku 的 PaaS 界面使用起來很方便，只要在網頁上點一下就可以新增一個專案並得到一個 git url ，然後把程式碼用 git 推上去網頁就建置好了，省去很多 web server 設定的麻煩，但是 Heroku 價錢太貴了，因此我決定自幹一個 Heroku 出來，之後新聞小幫手、求職小幫手、台灣公司資料等我有幾十個專案都跑在上面，現在 open source 在 [https://github.com/ronnywang/hisoku](https://github.com/ronnywang/hisoku) (hisoku 這名字是想跟 heroku 相對，heroku 是 her ，hisoku 是 his XD) ，目前有實作若超過一小時無人瀏覽的網站會將資源釋出，等到有人看到再自動跑起來，因此可以用更少的機器資源跑起更多的服務，希望能先提供給 g0v project   試試看來這邊跑跑看，省去自己的機器錢，也希望有機會可以。

我是 ipa，這三年多來共同主辦大松n次，看到很多專案主自付主機費用，覺得應該可以聯合募款共同維護。2016年中舉辦大松的[「揪松團」工作小組](https://trello.com/b/f8gWnjeC/g0v-jothon-organizer)（clkao, tkirby, etblue, ttcat, isabel) 開始思考是否能募款來共同維護 g0v 專案的主機，在[第零次 community hangout](https://hackmd.io/IwQwbAxgnADApjAtADgKypIgLAM2cRAIzlS20OTFSgCZgATDZIA=) 上提出此想法，poga 先認領，之後第肆次基礎鬆中 Ronny 跳坑。之後希望揪松團順利募款，由 Ronny 長期維護 g0v Cloud。


## 功能

- 支援 PHP (5.6.24), NodeJS(0.10.29), Python(2.7.9), ruby(2.1.5)
- 支援 npm (package.json), pip(requirements.txt), gem (Gemfile) 自動安裝套件
- 可自動建立 MySQL, PostgreSQL, ElasticSearch db 使用
- 可以用 env 設定各種 api key 或是設定，以便程式碼內不用放這些資訊
- 以 git push 做 deployment
- 每一個專案是運作在 docker 內，因此專案間是無法互相碰到別的專案
- 可以用 custom domain ，也支援 letsencrpt 可幫專案加上  SSL
- 可以跑 cron (1min, 1hour, 1day) ，也可以跑 worker
- database 未開放外部可連，但是可以透過 ssh tunnel 連入方便遠端將初始資料倒入或 migration

## 目前已運作網站

- [https://company.g0v.ronny.tw/](https://company.g0v.ronny.tw/) 台灣公司資料
- [https://newshelper.g0v.ronny.tw/](https://newshelper.g0v.ronny.tw/) 新聞小幫手
- [https://jobhelper.g0v.ronny.tw/](https://jobhelper.g0v.ronny.tw/) 求職小幫手
- [http://report.nat.g0v.tw/](http://report.nat.g0v.tw/) 公務人員出國指南
- [http://portal.g0v.ronny.tw/](http://portal.g0v.ronny.tw/) 關貿進出口資料

## 申請方式

因為過去都是 Ronny 自己的專案在運作，不確定其他人專案會不會遇到什麼問題，因此目前未開放註冊，如有需要可以透過 slack 或是 ronnywang@gmail.com 信箱與 ronnywang 聯絡，只要你的專案是 open data 或是 civic tech project ，並且有 open source code ，這邊都歡迎加入。

## 討論區

歡迎大家自由發問討論!
> 雖然有 open source ，不過現在文件很不足 XD 會慢慢再補齊的
> [name=Ronny W]

> [Donald Zhan](https://g0v.hackpad.tw/ep/profile/sUiBIOVIzQO)  [天龍特公地](http://taipei-pop.herokuapp.com/) 可以參考？
> [name=che l]



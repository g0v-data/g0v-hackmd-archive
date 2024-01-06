---
title: "地誌"
tags: hackpad
---

# 地誌

> [點此觀看原始內容](https://g0v.hackpad.tw/gXClCsJc6Fg)

帝雉？

構想來自[g0v/twangry#94](https://github.com/g0v/twangry/issues/94)

### BOT地圖？

[Pomin Wu](https://g0v.hackpad.tw/ep/profile/oGf5HRRuJSf) 提供的流程：
1.  找到BOT地號 [http://ppp.pcc.gov.tw/PPP.Website/Case/AnnounceView.aspx](http://ppp.pcc.gov.tw/PPP.Website/Case/AnnounceView.aspx)
    1.  寫 crawler [https://github.com/pm5/twbot-data](https://github.com/pm5/twbot-data)
2.  國土測繪圖資網路地圖服務可以查到地號對應的經緯度 [http://maps.nlsc.gov.tw/](http://maps.nlsc.gov.tw/)
    1.  例如: 基地範圍及基本規範：本園區範圍為金沙鎮鵲山段403-48及403-53地號 [http://goo.gl/ZJLN4s](http://goo.gl/ZJLN4s)
3.  地號可以找小幫手轉換成地理圖資
4.  小幫手可以把地理圖資 show在 Google Map上, like this [http://github.ronny.tw/ronnywang/sandbox/blob/master/20131221/map.json#25.06560076568261,121.29926467437745,15](http://github.ronny.tw/ronnywang/sandbox/blob/master/20131221/map.json#25.06560076568261,121.29926467437745,15)
5.  可以加入海市蜃樓(蚊子館)的資料: soidid at gmail.com
> 已下載. 會轉成txt來parse地址
> [name=stardog]

6.  把附件parse出來轉成txt來parse地號/地址

### 相關規劃


- taililee提供的[想法](https://github.com/g0v/twangry/issues/94#issuecomment-29684641)
- starsdog提供的[Sample](https://github.com/g0v/twangry/issues/94#issuecomment-29719097)
- 我是想把歷年的 BOT 案都弄出來。目前打算先把促參司的資料爬下來。
- 進去以後, 要秀哪些info呢:
```
得標公司, 公司負責人, 建設類別,企劃內容,工程進度, 得標金額, 相關爭議(可能要從別的source來)
招標單位, 專案負責人, 評審委員名單 (真正有弊案都是官商勾結阿!)
```
- 想要可以呈現不同的group method except map, for example
```
group by 得標公司 (也許都被某家公司給攏斷了)
group by type (公共建設類別: 觀光,交通建設...)
group by 民間參與方式(原來不止BOT耶....超多的還有DB, DBM, DBMF)
reference: http://www.taiwanbot.com/bot.html
group by 得標金額

```
### 相關專案

[苗栗互動圖表大作戰](http://hack.g0v.tw/osm-leopard-cat-project/http%253A%252F%252Flittleb.tc%252Fmiaoli-carnivores%252F)
> 目前 OpenStreetMap 社群的努力，已經將苗栗臺13線外環道路線畫上去了，以及後龍殯葬園區位置標定
> [name=Supaplex]


### 參考資料：

幫手小幫手！
ronnywang: [http://ronnywang.pixnet.net/blog/post/39285865](http://ronnywang.pixnet.net/blog/post/39285865)



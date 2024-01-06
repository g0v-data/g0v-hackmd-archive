---
title: CoTeach 教案共享平臺 1091103 會議紀錄
tags: edu, CoTeach
---

# CoTeach 教案共享平臺 1091103 會議紀錄
:::warning
slack channel：[#edu-coteach](https://app.slack.com/client/T02G2SXKM/C01D21G7F0E)
[專案簡介](https://github.com/coteach/web/wiki)
[提案簡報](https://docs.google.com/presentation/d/1eQKuXvn96uC7v50fkLaEmdWHgsyIB9b9Ue81HXsaLDk)
[過往會議記錄](https://beta.hackfoldr.org/coteach )
:::

:::info
形式：online
參與者：Ada、Ivy、孟庭、嘉豪、緯修、震龍
記錄：孟庭、Ada
會議時間：20:00 - 21:12
:::

## 討論事項
1. 確認孟庭的約訪文案及註冊 CoTeach 聯繫 email
2. Ada 列了 mockup 1.0 and 2.0
3. firebase 是否可用？ => 用登入的部分就好，嘉豪看過，覺得後端部份不太適合
4. v1.0 實作順序討論調整過，有空開工可以順著往下做，v2.0可以等v1.0收集數據和有訪談結果後再討論設計細節
5. v1.0 先繼續用angular擴寫， 2.0 再考慮是否換react


### 約訪文案討論
```
【教案協作平臺徵求受訪教師】
CoTeach 教案共享平臺是一個誕生於公民科技社群 g0v 的開源專案。CoTeach 初步整合現有線上公開教案，設計教案搜尋引擎，下一階段想加入線上協作教案的功能，讓跨地區、跨領域的老師能在CoTeach共同備課，從教師端彌平教育資源的不均等。
專案還在初期階段，希望能訪談瞭解現場教師的需求。
 
**徵求對象：**
有撰寫教案需求的體制內外中小學教師一名（有共同備課經驗者佳）
訪談時間：平日晚上或週末，約一小時
訪談地點：市區捷運站附近公共空間，以面談為主，若受訪教師能接受線上訪談亦可

專案還在初期階段，專案團隊很需要教育現場老師的經驗。對專案有興趣的老師們都歡迎留言或填表單給予任何建議，後續還會有相關訪談機會，謝謝！

相關資料： 
【g0v hackath41n 提案影片】或簡報
https://www.youtube.com/watch?v=59abr70Ksnw&t
【CoTeach 網站】
https://coteach.app
【g0v 公民科技社群零時小學校專案】
https://sch001.g0v.tw
 g0v slack channel： #edu-coteach
 ```
 老師背景資料蒐集：
 > 教學年段、科目、備課習慣
 > 使用網路素材備課的頻率？網路素材來源？（比如：ＸＸ教學網站、YouTube
 > 有沒有加入什麼教師線上社群？交流方式？

### 開發順序：暫由編輯器 改至 留言區討論、建立社群
類似愛料理的模式
協作暫緩，老師各自上來分享自己的教案，教案下方開闢留言區供老師討論小事項，若有大事項想討論則畫起來另開 issue。

### 後端使用語言討論
嘉豪：預計想要用 AWS + Golang
Ada：如果用 node.js，後端卡關時前端也較好協助，想請教其他專案前後端語言選擇的考量
Ivy：大松時有共識了，大家都不會 Go 也都有意願學，所以想採用 Go

### mockup v1.0
[v1.0](https://docs.google.com/presentation/d/1LQXcBJy5DO-DtS7p6OEFVMeZvfHG9ILm8MescqxwNWE/edit#slide=id.p) by Ada
嘉豪希望可以採用 Material Design 設計，Ivy 說有一套 [Material UI](https://material-ui.com/zh/) 可拿來開發

Ada 對 v1.0 的想像是一個聚合器，先把現有的功能展示出來，訪談過後再加入 v2.0 

目前繼續採用angular直到1.0上線且營運到一定程度，到2.0再評估是否要換framework

#### 社群資源頁面
孟庭蒐集一些教師社群（FB 社團、Telegram 群組、Line 群組）
>FB group
[教育創新與另類教育討論](https://www.facebook.com/groups/educationinnovation/)
[瑩光教育讀書會](https://www.facebook.com/groups/551317922040666/)
[均一教育後援會](https://www.facebook.com/groups/junyiacademy/)
[公民教學社群](https://www.facebook.com/groups/264913330343248/)
[學思達教學社群](https://www.facebook.com/groups/780188175346334/)：這個社團的置頂公告有很多教師線上交流社群的連結



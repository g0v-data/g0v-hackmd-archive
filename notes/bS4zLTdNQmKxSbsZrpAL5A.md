---
title: "急難救助公民行動網路App"
tags: g0v idea pool,hackpad
---

# 急難救助公民行動網路App

> [點此觀看原始內容](https://g0v.hackpad.tw/jgLrXNuSB33)

### 專案介紹

> 利用 App 讓每一個行動裝置都成為網路收發裝置,
> [name=Yichang W]

> 串接成一個巨型移動網路，讓壅塞的網路傳輸變的有秩序
> [name=Yichang W]

> ※ 這不是短期可實現的東西, 我只是把想法丟出來 ... (逃)
> [name=許正昇]

> 看一下[這](https://g0v.hackpad.tw/X86-U2Dd3HcSqG8)個會不會讓你的專案變完整
> [name=許正昇]



## 要解決的問題

### 專案說明

搭車時常常碰到網路擁塞,  我都會想在人群中要怎麼可以讓網路順利運轉,
有天下班, 繞去立法院外圍呆了30min,下班後人很多, 3G理所當然的阻斷了,
當時主持不斷喊話請外圍的朋友將3G關閉, 讓裡面的訊息可以順利傳遞
> 我覺得搞不好是電信商在動手腳
> [name=許正昇]

後來回家又開始了幻想, 在人群目標一致, 配合度高的時候,
讓所有人一同串起網路, 應該不是問題

理論上用上各項網路技術, 應該可以實現？ (我只認識皮毛不是研究網路的, 需要網路專家)
雛型大概就是用 Ad hoc 串接所有的手機
透過 SDN 來定義路徑傳遞封包 (Controller 透過手機協同運算, 或是NB負責)
只讓外圍的 node 負責與周遭3G或實體網路AP做傳訊避免擁塞
另外 Qos 讓管理團/直播, 有高優先權讓訊息可對外發送
最後是廣播功能, 在對外網路被阻斷的情況下, 可以把訊息傳遞到每個人手上
進一步擴展互動廣播, 如在現場發起不記名投票, 調查之類
最終還是要考慮安全防護機制, 避免從中竊取/偽造資訊、阻斷攻擊

Google 一下, 好像有幾篇像是
"Software-defined networking in ad hoc networks of smartphones"
之類的論文, 可以研究看看, 需要強者及網路專家

如果目標是抗爭, 需要防護被阻斷的問題
那長期目標就要以急難救助網路前進
最方便, 最容易使用的就是手機APP
每個手機都是個節點, 把網路串連起來

最近有實現的企業新聞是 NEC
[http://www.ithome.com.tw/node/84112](http://www.ithome.com.tw/node/84112)
(但只到擴散訊息至所有手機)

以上取自留言：
[https://www.facebook.com/groups/g0v.general/permalink/608518202557923/?stream_ref=3](https://www.facebook.com/groups/g0v.general/permalink/608518202557923/?stream_ref=3)

### 現有類似專案

[X86型車載路由器(可以參考)](https://g0v.hackpad.tw/X86-U2Dd3HcSqG8)

[https://www.youtube.com/watch?v=7r7VwU-NK1A](https://www.youtube.com/watch?v=7r7VwU-NK1A)
這個可以在救災使用了
[bored1980](https://www.youtube.com/user/bored1980) 這位 崁入式玩家應用的成果

[https://www.youtube.com/watch?v=FoWQycTXXOs](https://www.youtube.com/watch?v=FoWQycTXXOs)
這2篇是他網站的開發過程敘述
[http://www.suzukiswift.info/my-car-has-internet-access/](http://www.suzukiswift.info/my-car-has-internet-access/)
[http://www.suzukiswift.info/creating-my-box-of-tricks/](http://www.suzukiswift.info/creating-my-box-of-tricks/)

參考看看 Raspberry Pi 的應用 此為 崁入式系統 開放碼 平台
### [Raspberry Pi台灣樹莓派](http://www.raspberrypi.com.tw/)

[http://www.raspberrypi.com.tw/](http://www.raspberrypi.com.tw/purchase/)[purchase/](http://www.raspberrypi.com.tw/purchase/)
一般簡易的單機板 可至這購買 約3000元
較高級的套件需國外購買 但最主要最困難的是 軔體攥寫
[http://www.openfoundry.org/tw/foss-news/9145--raspberry-pi-kickstarter](http://www.openfoundry.org/tw/foss-news/9145--raspberry-pi-kickstarter)
網拍有也人在賣喔

### 授權方式

由主持人決策

### 專案目前狀態

（**_構想 / 規劃_** / 雛形 / 實作）


## 目標與功能（要如何解決）

### 預定 App 顯性功能

- App 網路開關
- App 設定
    - 強制
        - 允許控制 Wifi
        - 允許控制數據連線 (3G/4G)
    - 使用者選擇
        - [x] 允許 App 透過我手機連接外部通訊 (3G/4G)
        - [x] 確認！我是吃到飽網路 (**確認啟用上一條功能**)
    - 重新產生自我金鑰 (非對稱 for 訊息簽章 & 端點傳輸加密)
- Ad hoc 群組
    - 管理組 (Creator Default)
    - 群眾組 (User Default)
    - Other Group (由管理組建立)
- QoS
    - 群組優先權管理
- 群組廣播
    - 文字
    - 圖片
    - 影片
    - 即時串流影片
    - 互動訊息
- 統計資訊
    - 群組人數
    - 網路流量
        - 整體通訊流量
        - 節點流量

### 預定功能外圍裝置

- Ad hoc AP : 連接實體網路之 AP
- Ad hoc bridge : 實體串連兩個相距較遠的 Ad hoc 群組

### 預定使用者

- 持智慧型手機的現場群眾

## 徵求主持人

- [ ] NeedsManager：需要主持人
> 只是來挖坑的...
> [name=Yichang W]


## 徵求協作者

分工與成員
- [x] NeedsDesigner：需要介面設計
- [x] NeedsTech:：需要技術支援（程式、架站 etc)
- [x] NeedsProcess：需要幫忙設計作業流程
- [x] NeedsMoney: 需要金錢支援

## 實作細節（非技術背景可跳填）

### 協作工具

github repo：
hackfoldr 工作資料夾網址：
google drive 共用資料夾網址：

### 進度與 to-do



## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）

[g0v 急難救助行動網路_Yi草稿20140419.pdf](https://www.dropbox.com/s/l0pt7icdclu7s65/g0v%20%E6%80%A5%E9%9B%A3%E6%95%91%E5%8A%A9%E8%A1%8C%E5%8B%95%E7%B6%B2%E8%B7%AF_Yi%E8%8D%89%E7%A8%BF20140419.pdf)





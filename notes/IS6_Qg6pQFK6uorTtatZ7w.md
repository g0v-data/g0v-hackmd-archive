---
tags: cofacts, meeting note
---

20200401 會議紀錄
=====
Bil, Orz, Yang
> 
> 線上：https://tico.chat/powercall?room=cofactshack&type=timeFirst
> 上次開會紀錄：https://g0v.hackmd.io/@mrorz/HkqrDEOLI
>

## 小聚怎麼辦

- 過去討論：https://g0v.hackmd.io/eqkFjUjYTYetmvmr6d2AZQ#418-%E7%B7%A8%E8%BC%AF%E5%B0%8F%E8%81%9A
- Slack 討論：https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP/2020-03#ts-1585216585.014600

需討論：
案1: 照常
案2: 延期

bil
線上辦
不延期
基礎松也是線上
台北沒有地方借，NPO hub 不外借
小樹屋無法控制洗手
廁所跟工作場所分開

可以開直播

orz
所以基礎松怎麼做

bil
用 ronny 的網站

orz
可以觀摩基礎松
jitsi 可以放夠多人，可以直接連

bil 
powercall 會不知道誰是誰

orz
jitsi 會 crosstalk 沒辦法像是實體
可以在旁邊講話而不會影響到其他人

bil
可以直播
直播參與門檻比 jitsi 低

orz
小聚小聚有個重要的互動是舉手  然後我們走過去回答

bil
可能用私訊或 slido 解決

orz
但這樣無法看他螢幕

mozilla hub 可以解決螢幕分享與 crosstalk 的問題

bil
但效能很糟糕
開會效率很差
不能用同一台打字記重點

文武
他 bug 很多  會遇到很多瀏覽器的問題
對新手很難

orz
可能只能跟 ronny 許願了

1. 麥克風功能：有麥克風的人或區域 = 全域，其他都是周圍的人能聽到

2. 螢幕分享給附近的人看


什麼時候宣傳？

bil
直播的形式的話，前一天晚上也可以

超過三天的話反而沒有人記得

基礎松也是 3 天前宣傳

:::success
先看基礎松怎麼進行
4/5 1pm

【g0v 第拾陸次基礎建設松 行前通知】

Hi all ,

4/5（日）下午 14:00 是 g0v 第拾陸次基礎建設松，本次是全線上會議，將使用揪松團成員 Ronny 開發的「線上揪松」平台，因此需要先於網頁中登入 g0v Slack，並請先加入主頻道參與討論！

本次討論的議題如下，請還沒有報名的朋友在本次活動共筆裡的報名區加上你的暱稱及 Slack ID，歡迎一起來討論社群的基礎建設。
:round_pushpin: 「線上揪松 Jothon Online」平台更新
:round_pushpin: g0v.tw 官網改版
:round_pushpin: CoC 修改程序
:round_pushpin: g0v slack app 申請機制

線上視訊會議，要請參與者找到背景聲音安靜、網路順暢的環境，以提升會議參與的品質。

4/5 一起翻新社群的基礎建設～

【g0v 第拾陸次基礎建設松】
:date: 時間 Date & Time：2020/04/05 （日）14:00-18:00 GMT+8
:closed_book: 活動共筆（報名登記處）：https://g0v.hackmd.io/@jothon/g0v-infras-16
:zap: 線上視訊會議大廳：https://intro.g0v.ronny.tw/meet/show/g0v-infrath16n
↑ 需先登入 g0v slack，活動開始請先加入主頻道

#不是愚人節
#不能出去玩就線上相見吧
:::

## rumors-line-bot memory issue

[#166 Fix issue, limit number of image processing function didn't work](https://github.com/cofacts/rumors-line-bot/pull/166)


文武
multiple instance 目前想到兩個解法
1. dyno 起來的時候不 reset to 0，每個 instance 自己在多個變數紀錄現在有幾個 image 是自己處理的，在 process.on('SIGINT') 扣掉
2. 一樣 dyno 起來的時候 reset to 0，如果 desc 會小於 0 就不 -1 => 有機會在剛 scale up 的時候 processing_number > max_image_number，不過等reset to 0 之前還在處理的 process 處理完就會變正常了

> 2 比較好寫
> 

[3/27 update (還沒deploy)]
看最近七天 memory quota exceeded 只發生一次，推測應該是這禮拜比較少圖片傳進 line bot

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_868cb50e2afcf5f37a3df7ac419f8cd5)

:::info
撈個 analytics data 來看看
:::

[3/31 update]
Daily and hourly input message type
https://datastudio.google.com/reporting/3a7f93c2-2b87-4852-83fe-76599eba88ad

文武：
每個小時傳圖的數量沒有差很多
爆量的時間，圖片總數沒有特別多
會爆掉可能是因為傳了要 ＯＣＲ很久的圖

orz
關於 multiple instance 的 2 這樣好像就不 atomic

文武：
對所以有點麻煩

:::success
開個票紀錄
:::


- - -

### 3/30 Request timeout 大爆發

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_50ac96a5aaee78f39f3d3d5f73b23540)

- 發生時間: 3/30 18:00 JST (台灣時間 17:00 ~ 18:00; UTC 9:00 ~ 10:00)
- Request timeout 定義：[1秒](https://developers.line.biz/en/enterprise/business-connect/error-notification/)


LINE developer console 的 Chatbot error:
- https://docs.google.com/spreadsheets/d/1nHjbnL7B92UvEjqz1fmU080MpsjsGWyLlsx3LXGlUMg/edit?ts=5e842b70#gid=0


## 開發
GitHub activities
https://datastudio.google.com/u/0/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/WSQFB

### LINE bot 互動修改

上週討論：https://g0v.hackmd.io/6f12uznTQjCDRAKRyPOSxw?both#LINE-bot-%E4%BA%92%E5%8B%95%E4%BF%AE%E6%94%B9



## rich menu 選項

- 教學
- [專案簡介](https://beta.hackfoldr.org/cofacts)
- [FB 討論區](https://www.facebook.com/groups/cofacts)
- (未來) 我問過的訊息
- (未來) 設定
- (不定期) 小聚報名

:::warning
mrorz 還沒做
:::

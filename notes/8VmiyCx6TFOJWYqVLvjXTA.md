---
tags: cofacts, meeting note
---

20190529 會議記錄
====
orz,文武
(老闆出門後) lucien
線上參與： ttcat, bil
> 上次開會紀錄：https://g0v.hackmd.io/s/Hyzu2ebaV
> 

## Dev items

### Trendline in article page
https://github.com/cofacts/rumors-site/pull/161

- Add "30-day trend" in data studio.

:::warning
- Add total search count number as well?
- 換成顯圖？https://support.google.com/datastudio/answer/9044629?hl=en&ref_topic=7442437
- Cover up with URL to full-page report?
:::

datastudio:
https://datastudio.google.com/u/0/reporting/1t6Qx0P_3lsQilD1PPNf0jIfXsJ1Id7uC/page/q0iq

顯圖：
https://datastudio.google.com/u/0/reporting/1t6Qx0P_3lsQilD1PPNf0jIfXsJ1Id7uC/page/q0iq/thumbnail

Doesn't work with config
https://datastudio.google.com/embed/reporting/1t6Qx0P_3lsQilD1PPNf0jIfXsJ1Id7uC/page/q0iq/thumbnail?config=%7B%22df1%22:%22include%25EE%2580%25800%25EE%2580%2580IN%25EE%2580%2580atn1ubqar4g8%22%7D yeilds full thumbnail

:::success
加了 total search count
決定蓋一個 div，連結導向 full report
放棄圖內互動
:::

### Asking article source
Now on staging LINE bot
https://github.com/cofacts/rumors-line-bot/pull/135

:::warning
降低發文門檻？ 
要等 API 嗎？ ( https://github.com/cofacts/rumors-api/issues/127 )
:::

orz
送出文章等於多一步，那是不是相對應要把理由最小字數的限制拿掉

bil
好唷

orz
HC 有沒有把使用者選擇存到 google analytics 呀

文武
我記得有
https://github.com/cofacts/rumors-line-bot/pull/135/files#diff-f8051c184f469280912e9748671986e6R26

orz
要不要加上 article id
但這個 state 很可能還沒有 article id 可以用，要送出後才有

但這裡用 data.selectedArticleText 應該不對，
因為他是選不到文章才會進這 state，使用者不可能會有 `data.selectedArticleText`

:::success
orz
把字數限制拿掉之後發 PR
進 staging 大家玩玩看

GA issue:
https://github.com/cofacts/rumors-line-bot/issues/138
:::

### Remove fbclid
https://github.com/cofacts/rumors-api/pull/128

:::warning
要修 unit test，初步研判是 URL `.toString` 會自己拿掉 trailing hash 導致 URL cache miss。
:::

## 6/22 小聚

主題: 夏至

- 時間：6/22 (六)
- [ ] kktix 
- [x] Lucien 貼紙
- 散佈
    - [ ] Facebook fanpage
    - [ ] Facebook group
    - [ ] LINE bot 貼文
    - [ ] LINE bot richmenu
- [ ] 場地：青平台:只剩下小的會議室8-10人或 與開放空間 餐桌區、沙發區，可以容納15-20人(都可以掛投影片、投影機) - bil
    - [ ] 茶水
    - [ ] 麥克風
    - [ ] 食物
    - [ ] 訂夏至啤酒 by 啤酒頭釀造 一瓶 120元 330mL

bil
青平台：人太多不方便，週五再說
文案下週處理

主題：夏至
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9be17af56f5e81be6a11db191d91d9fd)

orz
沒有啤酒怎麼辦

bil
頂多5支，沒有要一人一支，沒有要酗酒
而且也有人不喝酒

lucien
不喝酒的怎麼辦 要照顧他們吧

bil 喝茶啊ㄏㄏ

lucien
小聚有什麼 slogan 嗎

bil
人不照天理
天不照甲子
都幾月了還這麼熱

orz
還是
轉傳不照天理 天不照甲子
之類的

lucien
畫個煙火好了

orz
但日本好像只有立春立夏
https://www.goodlucktripjapan.com/zh/article/item/11321/

bil
煙火是八月

orz
還是「轉傳不照天理 天不照甲子」
然後畫北極熊與融冰

bil
熊熊 畫北極熊 好嗎

ttcat
六月不是端午節嗎

orz
端午好像是六月初

文武
6/7

夏至有個吃麵的習俗
https://baike.baidu.com/item/%E5%A4%8F%E8%87%B3%E9%9D%A2/5812790
http://new.ctv.com.tw/Article/%E5%A4%8F%E8%87%B3%E5%85%A8%E5%8F%B0%E7%86%B1%E5%91%BC%E5%91%BC-%E6%B6%88%E6%9A%91%E6%B0%A3%E7%BF%92%E4%BF%97-%E5%90%83%E6%B6%BC%E9%BA%B5-%E4%B8%AD%E8%A6%96%E6%96%B0%E8%81%9E-20170621


:::success
KKTIX 文案 bil 下週處理
Lucien 小聚 banner
:::

## 搬主機

目標：get rid of the "request timeout" emails

- [x] 設定 elasticsearch GCP repo (`/_snapshot/gcp`)
- [x] 用 docker-compose 把服務跑起來
- [ ] nginx + https setup
- [ ] cofacts.org domain 指向新主機
- [ ] 與 g0v domain 管理者敲定 migration 時間
- [ ] perf monitor
- [ ] Cron job: https://github.com/cofacts/rumors-line-bot/issues/136

:::danger
GGM 沒來所以沒進度
:::

## 貼紙
> GGM
> 

:::danger
已通知
:::

## LOGO
> Lucien & Lou

Lucien:
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_022e15136f2428f381fbacd04c6b36a3)
中間那個「真」是字
中間有類似對話筐

文武
Lou 的 CO 也是類似對話筐
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_87e46d759250cb9628d79a21d5b77464)


Lucien:
群眾可能會記不住

bil
我們要中文一個
英文一個嗎
像 airbnb

還有就是 LINE 帳號的官方大頭貼也會有圖像
名義不一定是 logo，但會有一個專門瞄準使用者的
預想就是中文

orz
「真」不是圖像主視覺？

Lucien
「真」是字
另外有圖像

orz
有沒有辦法跟 Lou 協作？

Lucien
可以討論圖像
或是做英文版 這樣就會有中文與英文

orz
中文英文分工嗎

:::success
Lucien 在 g0v slack 再與 Lou 討論與溝通
:::

## 十傑

投影片：https://docs.google.com/presentation/d/1AJdY2G9ihNG6uMuyHduqPSX5F31T_xc73I_MJwugHA4/edit#slide=id.p

90min 15/60/15

ｏｒｚ
雖然只有 8 人但心得、提問都滿多的

文武：
有點看人，他們有興趣才會一直問

@Lucien Lee

1. 沒有請他們加 FB group，也能順利進行。
2. spreadsheet 準備 10 個分頁絕對夠。
3. 兩個兩個一組感覺效果不錯
    - 聊得來的人，一起做事情感覺比較熱絡
    - 聊不來的人，也會分工各自做各自的 XD
4. 投影片會先印出來在本子上發給學員。
5. 問題：學員會抓不到該回應的重點
    - ex: 羅智強臉書
    - ex: 5G 與交響樂影片
    - 或許帶著看「編輯奇幻旅程」的案例，一起練習抓回應點？
6. 投影片可以變成小聚與宣講（如媒體素養贏）的 SOP~
7. 打開 cofacts.g0v.tw/instant

:::success
Lucien 請把 bio 交給對方
(cofacts page)
:::

## RightsCon

### Landmark session
[Landmark: Voter Beware! - Microtargeting in Political Elections and Campaigns](https://rightscon2019.sched.com/event/Pvib/landmark-voter-beware-microtargeting-in-political-elections-and-campaigns)

明晚會 concall 討論

1. Closed messaging platform 看到比較多的型態：假貼圖、假粉專抽獎吸引人，然後整團賣給八大行業。賣渠道，沒有 targeting；但如果付費，就能用 demography 來分眾
2. 講觀察到的 vote page 可能會被用來 micro-targeting

### Lightning talk session: 找不到 囧

Slide: https://docs.google.com/presentation/d/1sPCR188wI6BPiE9BgF0__-P7yeL8GEfeLzMOIeRrtGc/edit

選前30天最有興趣的文章

### iYouth

50p

bil
pofeng 說不管有沒有申請到，都要跟社群分享申請的過程

:::info
orz: 研讀 iYouth 結案報告需要的東西
確保我們 RightCon 過程期間要蒐集到所有結案報告會用到的東西
- 照片
- 機票單據
- 住宿單據
- Anything else
:::

## GEC
沒有消息。

:::info
MrOrz 整理：
- assumption 跟 observation 都要盡量有研究或實證
- methodology 要曾有相應的實作
:::


## 活動

- 6/4-6 Google深度事實查核培訓營
- 7/3-10 FNF HK
- 6/5 Facebook （跟 google 請假）
- 7/23 (二) 15:00 - 17:00 媒體素養營

:::success
比鄰已經向前三者表達出席意願；
出席 Facebook 會與 google 請假
:::

### 媒體素養營
> 7/23 (二) 15:00-17:00
> 30min 媒觀講查核的方法和項目
> 90min Cofacts

50 高中生小隊員
預計分成 6 組，每一組會安排隊輔，隊輔會有訓練

orz
應該只要 1~2 人

bil
可能可以

orz
可以 reuse 十傑用的投影片

:::success
比鄰回信
歡迎大家報名
Lucien 在日本
:::

### FNF

bil
是個基金會，更像新創產業的 hub
補助機票但要註冊很貴
3-day workshop + 3-day 創業大會
因為補助機票住宿所以要寫心得報告

## 公益基金會

full timer 做教育訓練

## 編輯鬧版

https://cofacts.g0v.tw/article/1fj7zlv1mgfbs

lucien
可以把同一個人的聚集在一起
限制一個人同時最多只能有幾篇

orz
好像也可以把相同字的回應聚集在一起

lucien
我們對付 cheater 的做法是
讓他以為他的東西還在，但實際上別人看不到

之前（任職的公司）被俄羅斯帳號攻擊過
這種內容只差一兩個字，又同一個人，可以篩得出來

orz
我覺得人工標也可以

lucien
我們可以有裁量權嗎

我覺得我們對假帳號強勢點應該沒關係，因為他們不會出來講話

但我們(公司)有個 cheater 跑到我們 google play 留負評 XDD

orz
要不要丟到群組裡面一起討論
我猜那個人應該也不會在群組裡面

lucien
可以呀

:::success

:::


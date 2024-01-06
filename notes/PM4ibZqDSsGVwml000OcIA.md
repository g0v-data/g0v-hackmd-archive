---
tags: cofacts, meeting note
--- 

20190717 會議紀錄
====
orz,bil,文武,ggm
>
> 上次開會紀錄：https://g0v.hackmd.io/s/By-LxAGWS
> 

## Solve
https://g0v.hackmd.io/Fhh7iovtSVSaMvfSGyAIvw

## 8/13(二) 電視台訪談

(Cofacts 粉專私訊)

:::success
bil 確認時間，若可以的話就會去
:::

## 大松準備

- 誰會來：orz, bil, 文武
- GGM 遠端參與，修 token 問題
- 要徵什麼人：
    - Javascript 工程師
        - LINE bot: https://github.com/cofacts/rumors-line-bot/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22
        - Site: https://github.com/cofacts/rumors-site/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22
    - 找編輯
- 投影片：複製上次的https://docs.google.com/presentation/d/1A1hLnyDIMXObY--gIp1ElHhVQGl_lKHMxL2habMWV2g/edit#slide=id.p by bil
- BBC Click

## 合作：共同查核

:::warning
誰來執行
怎麼執行
如何選題

合約
:::

:::info
> 於本服務上遞交或揭露之訊息如涉下列敏感事項將無法查證，且可能受到相關限制。如政治，公投，選舉，腥羶色，個人隱私及名譽傷害，交友，侵權直播，藥品販售，金融交易，或個人主觀意見或評論等。請用戶務必知悉且應對傳送訊息之內容負完全責任。
:::

（玩了一下 silent launch 的 bot）

orz
他們上線之後我們要做什麼嗎

bil
之前有澄清我們是平台，所以很難上來回

ggm
合約上沒有說我們有義務

不過 API 方面，可以說 cofacts API 開放大家接取，那希望 LINE 這個也可以開放來接。

可以說希望什麼時候提供 API，但什麼時候接取，就不押時限

orz
感覺趨勢科技防詐達人也會想要這樣的 API
那要有寫入的 API 嗎

ggm
至少要有讀的 API

:::success
ggm 回信
:::

## 合作：專板專帳號

符合自律條款「提供民眾簡便識別不實訊息之管道」

bil:
可以有一個放文章的地方

orz
要用經營 FB group 的方式嗎
這樣 ptt 文章會很容易轉錄進來

bil
可以隱版嗎
希望做一個專屬工作區

orz
感覺預期的可能不是想要這樣做
但可以跟他們問問看

bil
依照他們之前簽的自律合約，應該是只要能夠對「媒體識讀」幫助就好，應該這樣也行。


:::success
我們目前沒有管版的資源，因此來問 ptt 是否可以作為工作區
:::


## TFD 問答
> Subject: Questions From TFD

https://hackmd.io/@mrorz/Hyw4eSh-B

:::success
大家可以先寫
orz 7月底開始寫
:::

## 活動

### 7/26 FB / IG 工作坊
> Subject: [g0v 揪松團] 分享工作坊資訊：7/26 Facebook 及 Instagram 工具應用工作坊

https://fbtrainingforngo.splashthat.com/

:::success
Bil 想要去
:::

### 9/13 OFF in 華山

> FNC 正在轉寄周知ing

https://hrf.org/events_posts/2019-oslo-freedom-forum-in-taiwan/

:::success
ggm (可能要返鄉) or MrOrz、bil


7/22 之前要給基本資料
- 1-2 sentences about your organization (English and Mandarin): 
  This will be in the event program book. 
- Information about your work, whether that be photos, videos, visual assets
- Design style guide if your organization has one
- Goal: 
  - What do you wish to accomplish through participation in our exhibition space?
- Call to action: 
  - What do you want attendees to do after visiting your space?
- High res logo: In .ai or .svg or .eps format
- Social Media: 
  - Website
  - Instagram
  - Facebook
  - LINE
:::

## Google News Lab APAC
看起來沒有了。

## 主機轉移

目標主機（ cofacts.org ）已經備齊。

先轉移 Linode 上的服務（API, DB, Site, URL resolver. resource intensive），chatbot 之後再說

- [ ] 公告下線時間（12hr）
    - [ ] LINE bot 公告
    - [ ] LINE bot 自動回應
    - [ ] FB page 公告，轉到 FB group
- [ ] 下線
    - [ ] 更換 cofacts-api.g0v.tw 與 cofacts.g0v.tw 網域到新的 IP
    - [ ] 舊機器 API server 關閉、確認服務無法存取
    - [ ] 關閉舊機器 DB 自動備份
    - [ ] 新機器 API 關閉
    - [ ] 轉移 SSL cert
    - [ ] 執行 database 備份
    - [ ] 在新機器下載備份
    - [ ] 開啟新機器 API
    - [ ] 測試 Cofacts 網站運作
    - [ ] 開啟新機器 DB 自動備份
- [ ] 上線

:::success
1. 演練一次備份的部分
3. 敲定時間，與 g0v 方確認可否執行
4. Run it! (7/31)
:::
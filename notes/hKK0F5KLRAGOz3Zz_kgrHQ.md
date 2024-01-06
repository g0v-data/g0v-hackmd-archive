---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210310 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz, nonumpa
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API

[DIFF](https://github.com/cofacts/rumors-api/compare/bb6778705fdc41c61284601359f8ecdfb5f0a479...a78340aa4dbb914c106d0e455efaf565d804cbea)
- #248 Contribution API on `GetUser`

#### :globe_with_meridians: Site

[2021/03/04 release](https://github.com/cofacts/rumors-site/releases/tag/release%2F20210304)
- #398 impact report translation & animation
- #395 edit avatar
- #402 contribution

### :rocket: Staging

#### :electric_plug: API

- [#249 post PR cleanups for contributions API](https://github.com/cofacts/rumors-api/pull/249)

##### ENV change

`GA_WEB_TIMEZONE`, `GA_LINE_TIMEZONE` are combined into `TIMEZONE`.

#### :globe_with_meridians: Site

- #404 Shuffle openpeeps & fix warning 
- #405 Tutorial translation
- #406 #407 #411 Impact report implementation: sponsor URL & ecosystem section
- #409 Enable Google analytics on impact report page
- #410 Security fix on `elliptic` package

##### 未竟事項
landing page 不會有 open peep - 開票 https://github.com/cofacts/rumors-site/issues/417

## 2021 三月計畫

- [ ] 3/start 寄送 impact report
- [x] 3/5 簡訊設計影片完成
    - [x] 上傳 Youtube
        - title
            - 華：
            - 英：
            - 日：
        - description
            - 華：
            - 英：
            - 日：
    - [x] 放進 impact report
- [ ] 4 月初：deploy API header 讓第三方接取
- [ ] 4 月初：公開 profile page 
    - [x] 在[社團徵求意見](https://www.facebook.com/groups/cofacts/permalink/2946837205548089)
- [ ] apply 日文翻譯 --> ja.cofacts.org / ja.cofacts.tw
- [x] [Canonical URL setup](https://github.com/cofacts/rumors-deploy/pull/15) merge 了還沒 deploy
    - old.cofacts.org 應該要排除 index
- [ ] [Google sign-in](https://github.com/cofacts/rumors-api/issues/234)
- [ ] [LINE bot 送出流程改版](https://github.com/cofacts/rumors-line-bot/issues/214)
    - 目標：更簡單地送出流程、LIFF 不要 send message to chatroom (為 share dialog 做準備)

### Group chatbot analytics

https://github.com/cofacts/rumors-line-bot/issues/245

https://datastudio.google.com/u/0/reporting/10419a96-67c9-4225-9feb-b5e673df4cac/page/lijmB (Only visible for people in the meeting)

- 案例：https://cofacts.org/article/knfmpkrm72q1
    - 很長，GA 截到的文字，比對率 80%
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_151e886c32b10f4ecf184a002601d610.png)
    - 沒有中的那幾次，是 elasticsearch 這裡就沒有列為候選，所以與 similarity threshold=0.9 無關 [name=nonumpa]
        - 因為真正的版本在 3/5 才送進來
        - 在 3/5 之前會 match 到資料庫裡現有的其他文章，但那些都很不像（繁體 v.s 簡體）
- "Hi cofactors" 有兩次
- 純網址 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b5153c935feb77ce159579768d45e4f8.png)
    - 但我們不可以只 match 網址。先例：https://www.facebook.com/groups/2034059996670763/permalink/2260959403980820/
- 要不要在 match 的時候，Cofacts 在群組裡面表示「Cofacts 想到了些什麼，但不方便在這裡說」然後有個「私下問」的按鈕，按下去會用 URL scheme 啟動 Cofacts 詢問流程 [name=mrorz]
    - 無論是 category 不對或相似度不夠高都可以這樣處理 [nam=mrorz]
    - 可以 [name=bil]
    - 可以放著 [name=nonumpa]


### Tutorial 翻譯

https://github.com/cofacts/rumors-site/pull/405#discussion_r588840165

:::success
改 tutorial 裡的字，與現有 UI 對齊 [name=bil]

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b1b453c716cae541532a21d503083ed4.png)

"Latest Checked" --> "Replies"
"No validated responses yet" --> "No useful reply yet" 
"popularly reported" --> "Asked many times"
"hot topics" --> "Replied many times"
:::


### Impact report

- 寄送對象 [name=bil]
    - 名單已經整理好了
    - 等簡訊設計影片
    - 日文（for 日本人）等日文版好
- Report 開發進度
    - [x] 1st fold, intro, participate, video, donation, features, footer
    - [ ] ecosystem + 香檳塔 - ongoing
        - [x] 實作
        - [ ] 翻譯
    - [ ] 新詩、媒體報導、演講經歷
    - [ ] 得獎紀錄 timeline
    - [ ] 影響、特色、理念 etc
    - [ ] 不實訊息案例

### 台灣吧影片

#### Hosting
- 放在非 youtube 的地方，才不會需要看廣告 or 受到未來 youtube 的限制 [name=bil]
- LBRY [name=nonumpa]
- 可能放 GCS ㄅ https://cloud.google.com/customers/vimeo

:::info
開票研究
要在收到成品後兩年內（2023/1/15）放好

Research: https://www.reddit.com/r/googlecloud/comments/fflfww/best_way_to_stream_videos_from_cloud_storage_like/
:::

#### Embed

- 放在 about 最上面 https://dev.cofacts.org/about
- 放在 landing page 「你可以這麼做」下面

#### 英文字幕
含 description、title

需要另外翻譯
credit 放翻譯者

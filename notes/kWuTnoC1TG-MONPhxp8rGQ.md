---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20201111 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：hsiao, bil, mrorz, nonumpa, zoe, lucien
:::

## Cofacts Next 追蹤

- 需要 FB 教學：see [20201104](https://g0v.hackmd.io/Sl_84QO8TQ6WKKI0bT4pYw?both#Cofacts-Next-%E8%BF%BD%E8%B9%A4)

## User ID Migration

Deploy https://github.com/cofacts/rumors-api/pull/227 的時候需要暫時停機來執行 migration。

執行完畢之後：

- 過去所有 LINE 使用者的操作都會有：
    - 假名
    - avatar (但 UI 還不會顯示，因為放在不同 GraphQL 欄位)
    - rumors-api 內相對應的 user id
- Cofacts website user 的所有功能不應有所改變

整體需要約一個小時，要事前公告下線維護時間。

部分沒有 user 的 airtable 時期 reply，原本作者會標記為 someone:
https://cofacts.org/reply/5481538314048-answer

會變成直率的蘇澳愛琳:
https://dev.cofacts.org/reply/5481538314048-answer

- 某些 reply request 的 appId 是 `BOT_LEGACY` 但 userId 為空
	- Airtable 時期沒有紀錄 user id
- 這個 reply 沒有 userId、appId 為 null
- 這個 reply 的第一個 article-reply 有 userId, appId 為 BOT_LEGACY
	- 大概是 3 年前的 migration script 的問題
- 有一些 article reply 的 appId 是 BOT_LEGACY 但 userId 是 website user
	- 這是某次手動的變更，把舊的 article reply 歸給一個編輯
	- 當時保留 appId 是 BOT_LEGACY
	- 但現在大多數這類 article reply 為 DELETED
	:::success
	不用與 Lin 合併
	:::
- article category 有 appId 是 `DEVELOPMENT_BACKEND` 
	- AI bot 目前因為沒有議定 server-to-server secret 所以會被填入 DEVELOPMENT_BACKEND
	- 之後這類 article category 還是都會被歸類在同一個 user，真的要顯示的時候再改顯示名字（legacy Cofacts bot?） 就好
	:::success
	先 leave as-is
	:::

:::warning
2020/11/11 在 FB 與 Slack 公告，預計 2020/11/13 01:00 ~ 02:00 執行

> ⚡ Cofacts 系統維護公告 ⚡
>
> Cofacts 將於 2020/11/13 凌晨 01:00 - 02:00 進行維護，
> 屆時 Cofacts 真的假的「LINE bot」與「網站」都將暫時無法連線唷。
>
> 如果很好奇的話，這裡有維護的詳細內容：https://g0v.hackmd.io/kWuTnoC1TG-MONPhxp8rGQ?both#User-ID-Migration
:::

### Data migration steps
- [x] Get latest API image (Image ID: `75eb267411dc`)
- [x] Shutdown nginx to stop all incoming requests
- [x] Perform DB backup
    ```bash
    SNAPHSOT_NAME=
    DB_URL=
    
    # Perform
    curl -XPUT $DB_URL:9200/_snapshot/gcs/$SNAPSHOT_NAME -H 'Content-Type: application/json' -d '{"indices": "*,-urls*"}'
    
    # See progress
    curl $DB_URL:9200/_snapshot/gcs/$SNAPSHOT_NAME
    ```
- [x] Deploy API
    - [x] Comment out rollbar server token temporarily
- [x] Run src/scripts/migrations/createBackendUsers.js
    ```bash
    docker-compose exec api node build/scripts/migrations/createBackendUsers.js
    ```
- [x] Restart API with Rollbar server token back on
- [x] Switch nginx back on


## 2020 Q4 ~ 2021 Q1 進度確認

- Landing page info
    > 紀錄 Slack 對話
    - 翻譯：https://docs.google.com/spreadsheets/d/1Y2ag7xK5Hd-tdkfR1mde43a0EPw_SWXH-Pe2GQrdWU4/edit#gid=0
    - 算我一個按鈕，[中文](https://beta.hackfoldr.org/1yXwRJwFNFHNJibKENnLCAV5xB8jnUvEwY_oUq-KcETU/https%253A%252F%252Fhackmd.io%252Fs%252FSyMRyrfEl) | [英文](https://hackmd.io/@mrorz/SklM4dV9m/https%3A%2F%2Fg0v.hackmd.io%2Fz7PY2mQeSMyWBoZpaVhAPg?type=book)
    > figma已經更新圖片囉～另外登入選單的部分，我想一想覺得會登入的人，應該就不會想再看landing page了，所以現在改成點選登入後登入並連到個人頁，如果使用者再跳回landing page的話只要把登入的地方換成頭像即可，再點頭像也不會有選單，而是直接連到個人頁，感謝～ [name=nick]
    > 目前還沒有個人頁 (還在做 ><)
    > 可以先連到 /hoax-for-you 唷 [name=mrorz]
- Tutorial design
	> Lucien~~
- FB bot 是否繼續維護
    - 送出訊息流程: 拔掉 or 改 webview
- Dialogflow intents 設計
    - Disable ML
        > ML Classification Threshold (intentDetectionConfidence) 調到 0.4 感覺~~還行~~ [name=nonumpa]
        > intentDetectionConfidence isn't reliable
        > 我是台灣人嗎 0.4042442
        > 我是日本人嗎 0.38319492

        - 這個訊息會 Match Welcome intent (0.48)
        > ⬆️ 綜合以上，回應者認為它含有不實訊息。
        > 💁 以上資訊由好心人提供。請斟酌出處與理由思考判斷。
        > ⁉️ 如果你對這則訊息有不同看法，歡迎到下面這裡寫入新的回應：
https://cofacts.hacktabl.org/article/2sn80q5l5mzi0
    - Training phrases
        - 參考資料(limited access)： https://datastudio.google.com/u/0/reporting/64c3b474-a306-40f5-86b9-2e894d028da6/page/lijmB
        - 問題類：請問(xxx)、(xxx)什麼(xxx)、資料庫...
        - 無意義類：謝謝、好的、了解、OK、測試、天氣、你好、`國家`、`人名`...
    

## 第 22 次小聚

- [x] 主題：訊息真的很多來闢謠吧
- [x] https://www.dropbox.com/sh/ks93mvamb068fks/AAB-bCMhHEJWokmqbuxnbNUma?dl=0&fbclid=IwAR3UKV9NlnFBK0P06SdxGpy-wlAXzerU83KsCz1ujXiG1Cs-kSzs1TS_RcE
- [x] 時間：11/29 (日) 14:00-17:00 (借13:30-17:30)
- [x] KKTIX https://cofacts.kktix.cc/events/cofacteditor22
- [ ] 準備貼紙
- 場地：NPO Hub 4 樓廚房 （台北市中正區重慶南路三段 2 號 4 樓）
    - Keyholder: Ronny
    - [x] 場地單
    - [ ] 食物
    - [ ] 延長線 (場地有)
    - [ ] wifi
        - [ ] Nighthawk M1 + 4G sim
        - [ ] ASUS RT-N12 Wireless N300 (2x 5dbi高增益天線)
- [ ] 誰會來呢？ bil, mrorz
- [ ] 誰不會來
- [x] 志超做圖
- [x] LINE 文案：複製上一次的
新款貼紙出沒中！！！就在本年度台北最後一次的編輯小聚。
地點：NPO Hub 4 樓廚房 （台北市中正區重慶南路三段 2 號 4 樓）
時間：11/29 (日) 14:00-17:00
:::info
週末帶川普款貼紙
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: LINE bot

https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20201105


### :rocket: Staging

#### :electric_plug: API

##### Refactors
- #227 index user if not existed and log last active time for user accessing apis via backend apps

會改變到 insert article, reply, reply request 等地方，因此需要全面測試。

#### :robot_face: LINE bot
- #234 Fix tutorial image order and handle the case RUMORS_LINE_BOT_URL undefined

:::info
這個是小變更，看一看 tutorial 是否有改變就好；但還是要幫 API 變更，測試會送出東西的部分。
:::

##### Testing checklist

https://lin.ee/1QUzEX4nI

與「送出」有關的測試項目：

- [x] 應可送出「全新訊息」
    - [x] 問訊息來源時選擇「我自己打的」或「LINE 外面看到的」，應該會被擋下。
    - [x] 提供正確訊息來源後跳到理由頁面，關掉理由視窗，訊息應該還是有被送出。
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [x] 可以修改理由送出。查看 article page 看理由是否有被送出。
    - [x] 「分享到 Facebook」、「分享到 LINE」可以正常運作

- [x] 送出「沒回應」的舊訊息，應可送出新理由
    - [x] 跳出來源視窗後關閉，文章的「N 人回報」應該仍然要 + 1（除非測試者已經針對該篇送過 reply request）。
    - [x] 提供正確訊息來源後跳到理由頁面，關掉理由視窗，可以看到「提供更多資訊」按鈕，按下去可以再打開「理由」視窗
    - [x] 可從聊天視窗內打開理由視窗，繼續填寫理由送出。查看 article page 看理由是否有被送出。
    - [x] 可以修改理由送出。查看 article page 看理由是否有被送出。

- [x] 送出「有回應」的舊訊息，應自動回傳回應
    - [x] 應列出訊息所有的回應
    - [x] 選擇回應之後可以幫回應 upvote
    - [x] 可以再次選擇 downvote
    - [x] 選完回應之後，還可以捲回去選其他回應

- [x] Rich menu 測試
    - [x] 「教學」應該可以叫出教學流程
        
#### :globe_with_meridians: Site

:::info
本週無變更，但還是要幫 API 變更，測試會送出東西的部分。
:::

##### Testing checklist

http://dev.cofacts.org/

登入自有帳號後檢測：
- [x] Replies search page
  - [x] can upvote / downvote replies
- [x] Replies list
  - [x] 可選擇 Replied by me
  - [x] can upvote / downvote replies
- [x] Article detail
  - [x] Can submit, upvote, downvote reply request
  - [x] Can submit, remove own reply
  - [x] Can upvote, downvote other's article reply
  - [x] Can add, remove, upvote, downvote category
- [x] Can logout
- [x] Can register new account
	- [x] via github




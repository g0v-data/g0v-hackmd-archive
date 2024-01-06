---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20210929 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, nonumpa, mrorz
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :globe_with_meridians: Site
##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [x] Report page looks good - https://dev.cofacts.tw/impact , https://dev-en.cofacts.tw/impact

登入自有帳號後檢測：
- [x] Article detail
  - [x] Can submit, remove own reply
  - [x] Cannot submit with empty reply text, or when reply contains only whitespace.

##### ⛔️ Release Blockers

##### 未竟項目

### :eye: Under review
- https://github.com/cofacts/rumors-site/pull/451
- https://github.com/cofacts/rumors-site/pull/448


## 清除空 reply

- FB 上已經公告一週：https://www.facebook.com/groups/cofacts/posts/3087699461461862/
- rumors-site 阻擋空回應：https://github.com/cofacts/rumors-site/pull/451

`reply.text` 是 analyzed text field 非 keyword，無法直接 term: "" (因為 query 裡面[沒東西可以 analyze](https://stackoverflow.com/a/25562877))
https://github.com/elastic/elasticsearch/issues/7515#issuecomment-158668403


```bash
curl -X POST localhost:9200/replies/doc/_search?pretty=true -d '{"query": {"bool": {"must_not": [{"wildcard": {"text": "*"}}]}}, "size": 100}' -H 'Content-Type: application/json'
```

API 結果
https://docs.google.com/spreadsheets/d/1X2myO4xyFLjBTT6UEJcPTiEy1-Z9dTn8HGUTka9WPYg/edit#gid=2080968331

刪除公告 PR：https://github.com/cofacts/takedowns/pull/19/files?short_path=9a29ca4#diff-9a29ca42102e58b5bbad8aa3adc17bf8c146b340969ed1d4164abb52a4b91229

- 未來要在網站端刪除只有 . 或 emoji 的 reply 嗎？[name=nonumpa]
    - 目前想不到怎麼刪。現階段先讓 chatbot 不要出問題，所以在網站阻斷 + 清除現有空 reply。[name=mrorz]

## 小聚檢討

- 推播點擊率會震盪 [name=mrorz]
- jitsi 各種聽得到聽不到 [name=mrorz]
    - 後來參與者用手機可以 [name=bil]
    - 最後 30min 一直被強制下線，顯示為斷線，問是否要重新進入聊天室 [name=bil]
- 沒有給麥克風或相機權限就會進不去 [name=nonumpa]
    - 好像有改版
    - 有人留言有提醒大家允許權限
    - 權限沒開會看不到：chrome->右上角三點選取設定->網站設定->麥克風/攝影機 允許jitsi連結 [name=參與者提醒]
- 重新整理之後權限會不見，google chrome 就會進不去。看得到大家但沒狀態 icon(投影中、麥克風、攝影機)，但沒聲音而且投影看不到。
- slido 回應模式 
    - SOP 要增加加 moderator 權限一事
    - 不要 archive 回答過的問題
    - wall 無法顯示 reply，可能要改投影 participant view
- 文件一開始是「僅供檢視」 [name=4000]
    - 開文件的是我，我可以先開編輯權限再 transfer ownership [name=mrorz]

## LIFF 的 consent window

重現 Cofacts LIFF 的 consent 步驟
1. 照著「如何檢查並刪除自己已有授權的App」做 https://getdr.com/%E9%BB%9E%E9%96%8Bliff-line-me%E7%9A%84%E9%80%A3%E7%B5%90%EF%BC%8C%E5%87%BA%E7%8F%BE%E8%A6%81%E6%B1%82%E8%AA%8D%E8%AD%89%E8%A8%B1%E5%8F%AF%EF%BC%9F%E5%AD%98%E5%8F%96%E6%AC%8A%E9%99%90%EF%BC%9F/
2. 進入 cofacts chatbot，開啟任意 LIFF (如設定)

LIFF「傳送訊息到聊天室」惡作劇：
- https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP/2021-09#ts-1632211572.0618
- Cofacts 拿掉「傳送訊息到聊天室」過往討論：https://www.facebook.com/groups/cofacts/posts/2672723192959493/
- 拿掉「傳送訊息到聊天室」要做的事情：https://g0v.hackmd.io/iTCmUFHeQLSILSXi2dBTjw#%E6%B6%88%E9%99%A4%E3%80%8C%E9%80%81%E8%A8%8A%E6%81%AF%E8%87%B3%E8%81%8A%E5%A4%A9%E5%AE%A4%E3%80%8D%E6%AC%8A%E9%99%90%E8%AB%8B%E6%B1%82

「用戶識別資訊」與「個人檔案」
- https://github.com/cofacts/rumors-line-bot/issues/293
- 另一個作法：先呈現一部份的頁面，讓使用者看一部分的內容之後，點按繼續時再出現 consent screen

----

- 可以先寫一個惡作劇機器人的文章 [name=bil]
- https://cofacts.tw/reply/qsJCDHwBucwAqrba8r6X

## Google Trusted Media Summit 2021 APAC

> “When a meeting, or part thereof, is held under the Chatham House Rule, participants are free to use the information received, but neither the identity nor the affiliation of the speaker(s), nor that of any other participant, may be revealed.” 
>
> Unauthorized sharing (through any form or media), copying, reproduction, distribution, and/or recording without written consent is strictly prohibited.
> 

> 以下資料均為來自 booth 或公開網站的資訊，紀錄新知道的資訊；不會有演講中的截圖與 citation / quotes。
> 

III: 查克佬 https://chrome.google.com/webstore/detail/%E6%9F%A5%E5%85%8B%E4%BD%AC-check-it-out/jnjjhepfpafbhhndhchciimcfkmmfpci?hl=zh-TW https://www.youtube.com/watch?v=fzcElazz-x0

感覺可以推給實證醫學就台灣：
https://firstcheck.in/

新加坡 crowdsourced fact-checking community：https://verifact.sg/
- FB https://www.facebook.com/VeriFactSG
- 介紹文：https://medium.com/@wyess/media-literacy-crowdsourced-fact-checking-896b804667b6 由 Better.sg NGO 發起
- Multiple answer per question https://verifact.sg/question/UXVlc3Rpb25Ob2RlOjU=

首爾大學 - 多家 newsroom 的查核平台
https://factcheck.snu.ac.kr/

當今大馬專題報導 - https://pages.malaysiakini.com/hk-misinfo/zh/

亞洲 Fact checking landscape (2021 Sep) https://newsinasia.jninstitute.org/chapter/faster-facts-the-rapid-expansion-of-fact-checking/


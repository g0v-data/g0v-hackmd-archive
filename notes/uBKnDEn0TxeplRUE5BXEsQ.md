---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20230118 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis：bil, mrorz, nonumpa
- 線上出席：4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :electric_plug: API

https://github.com/cofacts/rumors-api/pull/294

#### :robot_face: rumors-line-bot

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 應可送出「全新圖片影片訊息」

##### ⛔️ Release Blockers
##### 未竟項目

## 小聚檢討

[小松果](https://g0v.hackmd.io/-LFjxaAZTO6FwGJAR5G42A)

- 即使只回一篇，當天回的品質不太夠 [name=bil]
  - 課程刪減：評價只花 5~10mimn
  - comment 件數也不多
  - 想要先寫回應在講 comment [name=bil]
    - comment 的教學有很多溯源技巧，跟回應技巧合併的話會拉很長 [name=mrorz]
- 個人意見的 3 個樣板例子：明確指出前兩個不好的地方，指出第三種（個人意見）比較好
- 要求品質的話，可能要給即時回饋 [name=nonumpa]
  - 可以提說寫不出來不要硬寫 [name=nonumpa]
- https://www.facebook.com/WSOTK/posts/4314465108778736/ [name=cai]
- 時間長一點呢 [name=mrorz]
  - 不寫的還是不會寫 [name=bil]
- 從簡單的來做：如詐騙分類 [name=bil]
  - 可以找舊的純網址還沒清的 [name=cai]
  - 需要「0人回過」filter
    - 「等你來答」通常比較難 [name=bil]
    - 只有一個人回報的訊息，回得不好也還好，所以更適合練習
- 沒有人寫逐字稿 [name=bil]
- 自我介紹應該保留，因為是實體聚會的價值 [name=bil]

## 色情 mitigation

https://g0v.hackmd.io/vfsdHNS2R0-XhYyy2Lphbw#%E8%89%B2%E6%83%85-mitigation
- 照抄？
  - 換成超連結引用
- 改完發 PR？
- 技術：本次 `replaceMedia` script 可以更換圖片 / 影片等
  - media type 需相同
  - 更新 hash 與 article，刪除舊 file

## Dev

- [Crowdsource transcript](https://github.com/orgs/cofacts/projects/11) update [name=nonumpa]
- Community builder
- GA4: 改成 BigQuery [name=mrorz]
    - FB 發問：https://www.facebook.com/johnsonliang/posts/pfbid023yJtMNdCgvQWREUXYYWnEEQHAEFAzYXCoXroRUhEz8aLxC2EFKNQEdEQYSkPK2Rzl
    - 網站、LIFF:
      - 先上 Google tag manager
      - 在 GTM 同時埋現在的 UA 與新的 GA4 一起收資料
    - BigQuery pricing?
- Anti-seo spam [name=mrorz]


## Discord
- Previous: https://g0v.hackmd.io/Kne1R4BZTKeBbC3np6MOaw
- Channels
  - Slack 連動：`#general` <> g0v `#cofacts`
  - Github 連動：`程式開發`
  - IFTTT 連動：`#hoax-for-you`
    - 要考慮 [snailbot](https://snailbot.net/en/automatic-feed) 嗎？
- 規則審查
  - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4d527b4ddca6553eb02a5caaf6afc1b8.png)
- 永久邀請連結：https://discord.gg/mmZS9sZuau
- Forum channel
  - 像 Reddit?
  - 先不用

## 印刷品校稿

### 傳單
過去校稿：
- https://g0v.hackmd.io/6c3CpKXhQwOtFX8kf31ePA#%E5%82%B3%E5%96%AE%E6%A0%A1%E7%A8%BF
- https://g0v.hackmd.io/QPTHTIGEQpGgyYrDxNOMCQ#%E5%82%B3%E5%96%AE

預覽檔 https://drive.google.com/file/d/1UNq6Hl6VTrT5LEWpGPRVoopTQj3ZUwda/view?usp=share_link


### 海報

- https://drive.google.com/file/d/1yxOn-V7UOI0ifw709gA_2cP_CoYIA1ej/view?usp=share_link


文案：


右上：民主議題
美國發動222場戰爭搶劫黃金運回美國，烏克蘭想加入美國北約30幾國邪惡集團部署飛彈 
俄羅斯要單挑30幾個國家，中國及俄羅斯人民生命財產沒有保障



美秀姨：蝦米！緊分享--->春嬌姨：假的！要查證

左側框框：
每年查證ＯＯＯＯＯＯ次訊息
  - 每日查證逾 30 萬次 （查 / 搜尋 / 諮詢）

累積約ＯＯＯＯＯ筆資料
  - 超過 10 萬筆資料

超過ＯＯＯＯ次媒體採訪報導
  - 獲 NHK、PBS、路透社、英國衛報、半島電視台、The Atlantic 採訪報導

獲ＯＯＯＯＯ公家單位推薦
  - 機器人 QR code


秀蘭：我們這一家


右下：
在分享之前，你可以先傳給Cofacts 真的假的
Cofacts 真的假的 是能幫你自動查證不實訊息的聊天機器人。
圖片、影片、文字訊息、聲音檔，我們隨時為您服務！



一鍵分享，快速查證：--->了解更多
（跟傳單相同）
捐款連結
捐款給 Cofacts
資助活動講座、系統開發維護



平台開放-->有新回應時通知
意見交鋒-->多元意見
開源授權-->開放資料
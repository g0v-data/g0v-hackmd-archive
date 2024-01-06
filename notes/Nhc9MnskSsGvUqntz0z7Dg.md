---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20210804 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz, nonumpa, 4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## 商標申請

- 個人 or 團體 --> 先個人
- 建議先不要用 OCF，先用個人就好
- https://ossf.denny.one/tw/legal-column-list/8654-looking-at-well-know-marks-from-controversies-in-open-source-project-naming.html
- https://fossmarks.org/post/6commercializing/
- https://lab.ocf.tw/2020/07/22/googlelogo/

:::success
Johnson 用 https://aiplux.com/ 逕行申請～
:::

## iOS12 登入問題

https://github.com/cofacts/rumors-api/issues/259

登入問題歷程：

1. Samesite 導致 localhost 無法登入 --> 開啟 secure & samesite
2. iOS 與部分瀏覽器會關閉 3rd party cookie https://github.com/cofacts/rumors-api/issues/250 --> 改用 cofacts.tw & api.cofacts.tw
3. iOS 12 有 bug 導致 OAuth login redirect 完全不會送 cookie --> Solutions:
    1. 只針對 iOS 12 不設定 samesite none (user agent detection rule: https://www.chromium.org/updates/same-site/incompatible-clients )
    2. 針對所有瀏覽器不開放 same-site cookie
        - cofacts.org, cofacts.g0v.tw 登入都會停止運作，必須使用 cofacts.tw
        - 不過其實關閉 3rd party cookie 的瀏覽器，本來就無法用 cofacts.org 與 cofacts.g0v.tw
        - 301 redirect cofacts.org & cofacts.g0v.tw to cofacts.tw?
            - 無法針對不同網域做不同事情（例如如果未來放廣告，cofacts.g0v.tw 就不能放）
            - 網域所有權問題

:::success
只針對 iOS 12 不設定 samesite none
impact 比較小
:::


## 泰國 Cofact chatbot 支援圖片影片

https://github.com/cofacts/rumors-line-bot/issues/7#issuecomment-890709756

- 超酷。可以做嗎？[name=bil]
    - 會造成編輯困擾嗎？[name=mrorz]
    - 現在已經夠困擾了。增加圖片影片，造成的邊際困擾很小。[name=bil]
- Melody 說「我們不支援圖片喔」但這會擋掉 OCR 可以查。應該鼓勵使用者做 OCR 、手打文字、或請他把周邊的字傳給他。否則「我們不支援圖片喔」會讓使用者不再傳任何圖片進去。[name=bil]
    - 不過實際上使用者還是看到什麼就繼續傳，不是每個使用者都會看字 XD [name=bil]
- 現在 google drive 恐怖圖片不多，但有些裸體的照片，還有身分證
    - 希望可以兩則以上再顯示，或後台控制 [name=bil]
    - 我覺得可以在呈現上預設模糊，滑鼠移上去或點擊之後才變清楚，至少不會在 UI 第一眼就直接看到刺激性的或隱私的東西 [name=mrorz]
- 可能要改成詢問之後才上傳 [name=nonumpa]
    - 泰國 Cofact 看起來是一率上傳，但有經過文章送出流程的，才會呈現在資料庫 [name=mrorz]

:::success
1. 使用 google drive 作為圖床 + 用圖檔名稱搜尋的資料庫
2. 可能不要用 magic string 而是在 article 上增加欄位來做
    - 但用 magic string 做確實 effort 最小⋯⋯
3. ListArticles filter by hash or file id
:::

## 讀者回應

:::info
TFC 活動讀者
:::

[傳送門](https://g0v.hackmd.io/o3-A1j6XTzWl27tK_MomZQ?both)

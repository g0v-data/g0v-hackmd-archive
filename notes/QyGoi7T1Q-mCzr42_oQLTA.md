---
tags: cofacts, meeting note
---

20190130 會議記錄
======

> 前次會議記錄：https://g0v.hackmd.io/s/B1uUy3VQ4
> 

:::info
大人[不在家](https://www.facebook.com/278182895881552/posts/780710082295495/)
本次開會變小松 (?)
:::

## 小聚

散佈：
- [x] Facebook group
- [x] Facebook fanpage
- [x] LINE bot 貼文
- [x] LINE bot richmenu

## Cofacts TODO

- Editor 也可以送出 reply request https://github.com/cofacts/rumors-site/issues/13
- API: 計算下面數字，以用來計算等級。
    https://github.com/cofacts/rumors-api/issues/124

    - 「把一則訊息與回應連在一起」的數量（articleReply Count）-- 已有
    - 「有人（包含自己）把你的回應跟別的文章連在一起」 -- 可能要把 reply arthor 記在 articleReply 裡才算得出來
    - 上述 article reply 的有用程度加總：每個正的有用程度 * 2 點 for 回應者 & 連線者 -- 同上
    - 可以 cache 算完的結果，用 cron job 更新即可
- rumors-site Profile 頁面
    - 自己的回應的列表（可搜尋關鍵字）
    - 自己連接的回應列表
    - 自己撰寫的回應被其他人引用在哪些文章（這個不好做）
    - 最多人覺得有用（最近 n 天，n 可調）
    - 最多人覺得沒用（最近 n 天，n 可調）
- Rich menu 附範例: TBD
- rumors-site FOUC: TBD
- 調查 + 引導對話去其他 LINE@ https://github.com/cofacts/rumors-line-bot/issues/121


## 我愛家我解惑 TODO

- 討論網站架構
- 把 [Hackmd](https://g0v.hackmd.io/c/B1iHBvVPQ) 的資料輸入到 [網站](http://answerfamily.org)。

### 網站架構



1. 展示社會疑惑與「愛家語言」，使觀者明白社會對同志的不友善，真實存在，不容否認。

2. 簡便的查詢理性回覆的方法：我們把理性論述自動化，減少大家搜尋論述的時間，就能讓大家花更多時間在感性的溝通上面。

簡而言之，就是讓平權支持者人人都能撿到槍。

#### 用語
- article: 愛家論述，愛家論述存檔
- paragraph: 論述段落
- articlesource: 愛家論述出處
- reply: 平權解惑


#### 首頁內容
- 搜尋框貼上訊息內容 -> 搜尋
- 搜尋框貼上網址 -> 解析內容搜尋
- 看對話 -> article頁面閱讀訊息與回應

#### 搜尋頁面
- searched article
- searched paragraph
- 把論述存進公開資料庫

#### article submission
- 編輯論述內容
- 增改出處

#### article 頁面(論述存檔)
- 列出 article source 愛家論述出處、允許大家新增
- article 內的超連結，可以連到以其為 article source 的頁面
    - 例：有民視新聞 youtube 連結的性平謠言，點擊 youtube 連結之後，會連到內容出自該 youtube 的逐字稿 article。
    - 多層次的回應：reply 在 article 頁面只針對該頁面的 paragraph；超連結內容，應該另開一份 article 處理
- 列出 paragraph
  - 登入後可新增回應，或連結現有回應

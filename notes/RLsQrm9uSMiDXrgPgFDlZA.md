---
tags: cofacts, meeting note
---

20181212 會議記錄
====

> 前次會議記錄：https://g0v.hackmd.io/s/ry8jMZBJ4
> 

## Dev items

### Chatbot issue: Puppeteer 斷線
https://github.com/cofacts/url-resolver/issues/9

### LIFF
> 等待 LINE 技術端回覆。
> 

Orz:
其實在 user consent window 有可能按取消
https://github.com/line/line-platform-feedback/issues/106

目前無法追蹤使用者是否按取消，按了大概也是 403


GGM:
403 背後的意義應該是沒有給我們權限

MrOrz:
所以到頭來我們還是得要 handle 403 然後請使用者解除連動。

如果一個使用者一直沒有允許我們的 user consent，那就會無法送出理由，他永遠只能查詢，不能送出。

他連 reply request 也不能送。


:::success
GGM: 問別的 API expert 怎麼解
Orz: 把英文版問題貼去 https://github.com/line/line-platform-feedback/issues 看有沒有人回
:::

## 以下重排順序

GGM
簡單的先做
但明年才有空

:::success
Orz: 先做可以回頭按按鈕功能。
:::


### LINE bot 加入群組功能
https://github.com/cofacts/rumors-line-bot/issues/13

GGM
覺得這要好一段時間，要改機制
因為一進群組就會一直收到每個人講的話，每一筆都要去搜尋

Orz
那超過 50 字才 query 呢

GGM
還有要叫他閉嘴的功能

Orz
還有一個問題是，一個群組只能有一個 bot
如果加了趨勢的防詐達人 bot 就不能用我們

GGM
趨勢的防詐達人應該是全搜，他們機器應該沒什麼問題


### 讓 LINE 使用者可以回頭按按鈕，讀其他則文章或回應
issue: https://github.com/cofacts/rumors-line-bot/issues/49

### Bug: 覺得有用 / 沒用的分數最多只有 10
> MrOrz

issue: https://github.com/cofacts/rumors-api/issues/77

### 顯示覺得 article reply 沒用的理由；使用者在網站上按 Ｘ 時也詢問理由
> MrOrz

issue: https://github.com/cofacts/rumors-site/issues/97


## 我愛家我解惑

### DB
https://answerfamily.org

1. 展示社會疑惑與「愛家語言」
使觀者明白社會對同志的不友善，真實存在，不容否認。

2. 簡便的查詢理性回覆的方法
我們把理性論述自動化，減少大家搜尋論述的時間，就能讓大家花更多時間在感性的溝通上面。

需要填填填

### 逐字稿工具

現有工具：
- youtube download: https://github.com/rg3/youtube-dl
- video to subtitle: https://github.com/agermanidis/autosub

使用者自備 API Key。

CLI 工具
1. youtube downloader
2. 上傳到 [google ml speech](https://cloud.google.com/speech-to-text/docs/quickstart-gcloud) [CLI](https://cloud.google.com/sdk/gcloud/reference/ml/speech/recognize-long-running) 得 transcript 與 [time code](https://cloud.google.com/speech-to-text/docs/async-time-offsets)
3. 寫成 srt 字幕檔


## bloomberg
需要填填填
下週二前回完
https://docs.google.com/document/d/14hWF9-bkg-d6GnoCIqcHMe8x6IHDHI7oCV2GYEfoK3c/edit#




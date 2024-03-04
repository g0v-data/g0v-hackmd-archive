---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240304 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site

https://github.com/cofacts/rumors-site/releases/tag/release%2F20240304
- marcussfu++

## CCPRIP
### [Op] Transcript spam
> nonumpa
> https://g0v.hackmd.io/vKCvrqSQTlm7GEx9MAXGaw?view#op-Transcript-spam-處理


### [Comm] article group 收尾
> nonumpa

### [Comm] Thumbnails for video and audio
> https://github.com/cofacts/rumors-api/issues/326
> [name=mrorz]

- 上次測的問題：忘記升級 media manager package，升級後可以傳送
    - 不會等轉檔完才回 LINE，還不錯
- 但仍然有問題：佔用 CPU
    - 其實轉檔沒有必要在主 API server 處理
    - 可以考慮改在 cloud run 做，或
- Alternatives
    1. Cloudflare Stream
    2. Google Transcoding API

### [Op] Google 非營利
- 回信後尚無回音

## User organization / badge


## 小聚籌備


## 協會

About 頁面英文修改
> Source: https://g0v.hackmd.io/6tCmrXsyS3WEGgC_bMcd9w#-Site

ChatGPT 建議：https://chat.openai.com/c/50d6faed-c65a-4092-9741-0e4b621b2896
> Cofacts originated as an open-source project in 2016. In 2023, the core members of Cofacts established an NGO named Cofacts Association in Taiwan to sustain the Cofacts community.

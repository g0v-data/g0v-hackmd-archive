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
    1. [Cloudflare Stream](https://developers.cloudflare.com/stream/)
        - 儲存費用每月付 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7f2a3f0cbc63b4d3c7200e0893262431.png)
            - 假設每個影片 1min，Cofacts 已經有 9214 video / audio --> 9000 min，$50/mo 的範圍
            - 播放費用另計，但如果只有查核協作者可以播放的話就會很省
        - 目前看起來，關於 thumbnail：
            - thumbnail 好像不算錢，只有靜止的跟 gif（限 15s 內、fps 限制 1~15）
            - thumbnail 是 request 來才會即時生成，如果是 gif 的話可能要生數秒鐘，產出十幾 MB 的 gif 送到瀏覽器
            - thumbnail 可以指定開始播放的時間，但無法調整播放速度
        - 另外關於影片檔案：
            - 檔案可以做 signedUrl，所以可以在 rumors-api 產出 signed URL 吐在 attachmentUrl 裡頭，也可以在裡面放 thumbnail URL
            - 可以生成指定長度的 clip 限制播放時長
        - 要用的話，一般的做法：
            - 訊息列表 thumbnail: 用 cloudflare 的 gif thumbnail
            - 未登入造訪訊息內頁 preview: 用 cloudflare 的 iframe stream player 播放 30s clip
            - 登入後的使用者可以拿到 original，用 cloudflare 的 iframe stream player 播放原長度影片
        - 更省的做法：
            - 訊息列表 thumbnail: 用 cloudflare 的靜止 thumbnail（jpg，較小）
            - 未登入造訪訊息內頁 preview: 用 cloudflare 的 gif thumbnail 15s （不用錢，但應該要生一陣子）
            - 登入後的使用者可以拿到 original，用 cloudflare 的 iframe stream player 播放原長度影片
        - 附加好處
            - 可以透過 cloudflare retrieve video detail API 拿到影片時長
            - 因為有 on-the-fly 的 thumbnail URL 可以用，因此未來如果接了 google video intelligence API 偵測 shot changes，甚至可以做到列出影片分段截圖的功能，對查核影片會超級方便——點擊截圖跳到那個分段、對截圖右鍵來用瀏覽器內建功能以圖找圖等等。
    2. Google Transcoding API
        - 指定要轉的解析度、轉完放哪裡。轉換[算便宜](https://cloud.google.com/transcoder/pricing) (0.015/min for SD thumbnail)，儲存就是 GCS
        - 直接有 sprite sheet! https://cloud.google.com/transcoder/docs/how-to/generate-spritesheet#generate_image_periodically
            - Google lens 可以只選一幀出來 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_05dc6db86196cb855046859d5e151d3d.png)
        - 跟 bucket、cloud function 串在一起： https://cloud.google.com/use-cases/video-on-demand?hl=en#features
        - 輸出檔案：
            - Thumbnail 放 360p 影片, 前 20s、15fps 在 [client side `<video>`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement/defaultPlaybackRate) 加速到 2x
            - Preview 放 sprite，每隔幾秒一格
        - 形式
            - media manager 上傳原始檔案之後，GCS bucket file change 觸發 cloud function 
            - cloud function 呼叫 transcoding API (batch mode)
            - 檔案回存到同一個 GCS bucket file 資料夾底下，未來 rumors-api 與 media manager 可以讀得到該 variant
        - 缺點
            - 沒有辦法拿影片長度之類的 metadata，但這可以另外呼叫 ffprobe 搞定

### [Op] Google 非營利
- 回信後尚無回音

## User organization


## 小聚籌備

- [ ] 日期：3/24 (日)
- [ ] 食物：
- [ ] 場地：新北青職基地 1F
- [ ] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Slido 暖身
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：
  - 推播日：
  - 目標：雙北、桃園？
      - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_aff7fe2b732675b4b90f1e90a56fd071.png)
    - 14 萬人收到、2萬分之一報名率 --> 開 30~40 人、預期 20 人到場？
- [ ] KKTIX:
- [ ] 誰會來呢：
- [ ] 記得帶：貼紙、環保杯
- [ ] LINE 文案
- [ ] VOOM 發文


## 協會

About 頁面英文修改
> Source: https://g0v.hackmd.io/6tCmrXsyS3WEGgC_bMcd9w#-Site

ChatGPT 建議：https://chat.openai.com/c/50d6faed-c65a-4092-9741-0e4b621b2896
> Cofacts originated as an open-source project in 2016. In 2023, the core members of Cofacts established an NGO named Cofacts Association in Taiwan to sustain the Cofacts community.

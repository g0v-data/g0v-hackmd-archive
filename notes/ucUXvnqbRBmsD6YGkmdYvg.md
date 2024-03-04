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

contributor 在 snapshot update 時更新
- 可能會有兩個人的 contribution 會記成同一個時間 [name=nonumpa]
  - 像 google doc 所以 ok [name=mrorz]

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
- 目前沒登入就無法看影片 [name=nonumpa]
  - 上傳色情影片，沒登入就看不到，預覽圖下 google 抓到的機率更大 [name=nonumpa]
  - 可能就是要上 video intelligence API [name=mrorz]
    - 模糊化處理，登入才能檢視？

:::success
- 朝 2 進行
- 寫 design doc
:::

### [Op] Google 非營利
- 回信後尚無回音

## User organization and CoC

> https://hackmd.io/ktxqGDX4S4iuBd1MoZqDmQ?view#Cofacts-Editor-Organization-%E6%A9%9F%E5%88%B6

- Organization qualification: 不另外要求 qualification
    - 但可以想一想，自己無法接受什麼樣的組織來申請 organization?
- 更嚴格要求 CoC？
    - For all contributors：反騷擾原則
        - https://www.facebook.com/legacy/notes/2046634208901731/
        - 參考 https://hackmd.io/1U4u6d81QCqgtYriyC5kOA?view#II-COSCUP-CoC-%E4%BF%AE%E8%A8%82%E5%88%86%E4%BA%AB---%E9%9D%A2%E5%B0%8D-MeToo-%E7%A4%BE%E7%BE%A4%E8%A9%B2%E5%A6%82%E4%BD%95%E5%9B%A0%E6%87%89
    - 因為比較顯眼，所以要求要比一般協作者多：
        - 要提供錯誤回報更正機制
        - 違反 CoC 的話嚴重可能撤銷 organization，全部變回一般查核協作者的樣子
- Progression: CoC draft --> 社群討論是否有意見 --> 公告 apply 到網站內容、小聚 etc
  - 之後實作 organization、處理都有依歸 [name=mrorz]
  - 4 月底 [name=bil]
    - 產出內容避免國籍、性別、種族、年齡歧視
    - 參考 OCF 
    - 處置: 內容 --> 修改文字、移除部分段落 or 全篇移除

:::success
Bil draft CoC
:::

## 小聚籌備

- [ ] 日期：3/24 (日)
- [ ] 食物：要自己清，垃圾桶不能丟
- [ ] 場地：新北青職基地 1F
    - 一定要 20 人以上，最多坐 60
    - 6 個桌子、20 張椅子、麥克風、投影幕、筆電
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
  - 推播日：3/18 (一)推播
  - 推播日之前：新北志工優先報名
  - 目標：雙北、桃園？
      - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_aff7fe2b732675b4b90f1e90a56fd071.png)
    - 14 萬人收到、萬分之2報名率 --> 開 30~40 人、預期 20 人到場？
    - Ref: [past click through rates](https://docs.google.com/spreadsheets/d/1XjEQZ9esNKfkGd8XYd1p3E8DTgB0f5QPDl5ghf-JxE0/edit#gid=0)
- [ ] KKTIX:
- [ ] 誰會來呢：bil, mrorz, nonumpa
- [ ] 記得帶：貼紙、環保杯
- [ ] LINE 文案
- [ ] VOOM 發文


## 協會

About 頁面英文修改
> Source: https://g0v.hackmd.io/6tCmrXsyS3WEGgC_bMcd9w#-Site

ChatGPT 建議：https://chat.openai.com/c/50d6faed-c65a-4092-9741-0e4b621b2896
> Cofacts originated as an open-source project in 2016. In 2023, the core members of Cofacts established an NGO named Cofacts Association in Taiwan to sustain the Cofacts community.

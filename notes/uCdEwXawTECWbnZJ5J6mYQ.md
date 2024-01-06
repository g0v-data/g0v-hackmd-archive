---
tags: cofacts, meeting note
---
20191120 會議記錄
=====
> 上次開會紀錄：https://g0v.hackmd.io/m5yFYM3PT7SKeVrBqjdixA
> 
Orz/Lucien(無飲料)/(Remote:Bil,lora,rock)
## 下次小聚

- [x] 主題：
    - 世界愛滋病日 slogan:
        - 愛滋慢性病、謠言要人命。
- [x] 時間：12/1 14:00-17:00 
- [x] KKTIX(bil上班寫)
https://cofacts.kktix.cc/events/cofacteditor17?preview_token=fee6a0dfb71fcb379c6721ab931b6dbf
- [x] 攜帶貼紙
- [x] 場地：青平台已確認
    - [ ] 茶水
    - [x] 麥克風+插座+網路
    - [x] 投影機
    - [x] 延長線
    - [ ] 食物
    - [x] 垃圾
    - [ ] Talk
    - [x] wifi
        - [x] Nighthawk M1 + 4G sim
        - [x] ASUS RT-N12 Wireless N300 (2x 5dbi高增益天線)
- [x] 誰會來呢？ bil, mrorz, 文武, lucien
- [x] LINE 文案


> 「Cofacts 編輯小聚」就在 12/1 囉！
>
> 過去這一年，大家應該多多少少都有看過愛滋病相關的轉傳訊息。今年世界愛滋日，我們邀請大家一起來闢謠！
>
> 機器人為什麼可以精準地陪你查證 LINE 的謠言，都是因為每兩個月有一群義工無私的付出——也就是讀到這行無私的你。
>
> 一起加入把手上的燈提高一點就能照亮更多朋友的行列。參加小聚活動，一起把不實訊息的澄清送進資料庫，你的回應就會出現在「Cofacts 真的假的」、「美玉姨」、與「趨勢科技防詐達人」唷！
>
> 不管你是從一開始就支持「Cofacts 真的假的」的好朋友，或者是聽到「美玉姨」才認識的好朋友，都歡迎一起來替 LINE 上的轉傳訊息，撰寫回應。沒有現場的大家一筆一筆回應，機器人就很難動啊，所以真的萬事拜託了，缺你不可。
>
> （當天要查很多資料，記得要帶電腦 來唷！！！)

> 時間：2019/12/1(日) 2pm ~ 5pm
 地點： 台北市中正區中華路一段77號6樓之1 (最近的捷運站是西門捷運站)
 線上報名： https://cofacts.kktix.cc/events/cofacteditor17
 
- [ ] 行前通知
- [ ] 開場使用材料更新：https://docs.google.com/presentation/d/1QCAPtwkxreQ4EUtIWsOgR4c8h4tkRs22Qvv7jBFNrfI/edit#slide=id.g1ffc87ef17_0_23

## 11/16 新聞與言論自由論壇－假新聞的起源、目的與產出結構

Slides: https://docs.google.com/presentation/d/12rH1_bh2bfOGdRpJ4p5TObND5Z5P3e37V5WQgYLEp3Y/edit

群眾發問：

## Facebook bot

Testing Facebook w/ rumor & chatbot: https://www.facebook.com/Demo-of-Cofacts-messenger-bot-100628288070779/?modal=admin_todo_tour

準備上線文案

Cofacts 1-page flyer: https://docs.google.com/document/d/1w8c4GXVfm3zt9WRB_GTFPLZ4JIOL7wxODmwiIb6Dq3Y/edit

HC: I think we can put "Beta" or "Alpha" instead of "Experimental"

## Rumors-site 升級 next9
1. [x] Article list --> PR to dev
2. [x] Article page （見 API 更新）
3. [x] Reply list
4. [x] reply page
5. [x] docker build
6. [x] landing page
7. [x] 上 staging
8. [ ] 上 production
9. [ ] google analytics (w/ gtag)
10. [ ] All i18n (including levels...)
11. [ ] RSS feed

## OCR

> 文武

HC: 我之前有嘗試過 tesseract 之類的但效果很差 (不過也沒有 normalize input 就是了)，不知道是不是還是要自己 train

文武：基本的功能做好了，剩下heroku buildpack 還在弄，網路上找到的 buildpack binary 都有點舊，打算自己重 build 一個。 

不用自己 train，雖然效果差，不過辨識得出一點文字剩下的交給 elasticsearch 感覺還行。
原本還去找了 image text detection 想把 input 弄乾淨點，減少雜訊，不過大部分都是做英文，中文效果完全不行..

## 交大理工大學部
subject: [KKTIX] 您的組織 Cofacts 收到了一封聯絡信件

> 有一班45人，95%都是交大理工大學部
> 兩小時的課程
> 週三上午十點到十二點

:::info
已經提供十傑材料，對方仍然在評估
:::

## LINE 開發者大會

LINE 訊息查證其實有用 BERT 做 IR

https://speakerdeck.com/line_devday2019/how-machine-learning-helps-line-fact-checker-now-and-future

## Google news intiative APAC

bil: 開始安排 visit，寄信詢問關於 session 的事情

## OpenUp Summit

11/30 tour

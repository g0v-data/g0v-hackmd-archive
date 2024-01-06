---
tags: cofacts, meeting note
---
文武、mrorz、Korr (沒飲料)
billion (線上)

20191113 會議記錄
=====
> 上次開會紀錄：https://g0v.hackmd.io/@mrorz/Sks220yiS
> 

## 下次小聚

- [x] 主題：
    - 世界愛滋病日 slogan
        - 愛滋不可怕，謠言才可怕。
        - 愛滋慢性病、謠言要人命。
        - 健保開銷第一名其實是腎臟病不是愛滋病。
        - 女同性戀是幾乎不可能得愛滋病的。 
    - 感恩節（11/28）
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
- [ ] 開場使用材料更新：https://docs.google.com/presentation/d/1QCAPtwkxreQ4EUtIWsOgR4c8h4tkRs22Qvv7jBFNrfI/edit#slide=id.g1ffc87ef17_0_23

## MCOT ([Sure and share](http://www.mcotglobal.com/content/57fcb61c2f01f3c06fff56fd)) 來訪

MCOT 也想要做 bot，但是是 for MCOT 內部蒐集謠言的優先順序用
網站：http://sure-web-app.herokuapp.com/ 已經有 full-text search
有 data collection bot 做 undercover journalism
不過他們不碰政治，只做健康與可以被 fact check 的謠言。

2020/2 會有黑客松想邀請我們，辦在週末

:::success
Orz 貼 Design choice 的 talk 給他參考
https://docs.google.com/presentation/d/1I5hnd1pHE1nTY8uzoMokhJINJbG4V3I7Mr5_G5NPo3o/edit#slide=id.g5f9be56449_1_1
:::

## 11/16 新聞與言論自由論壇－假新聞的起源、目的與產出結構

Slides: https://docs.google.com/presentation/d/12rH1_bh2bfOGdRpJ4p5TObND5Z5P3e37V5WQgYLEp3Y/edit

## cofact.org (OpenDream) 約時間討論社群
subject: Greetings from Cofacts - Connecting with FNF Thailand

Cofacts 建議 opendream 找到 TA 做 marketing，例如厭惡家庭群組裡謠言的年輕人

:::success
會在 Discord follow-up
:::

## 12/6 ~ 11 - Google Trusted Media Summit APAC
收到信了，有登記
:::success
- 可以去的人都拿到了 Google 的 invitation
- 不確定是否會有 recording (沒回)
:::

## Facebook bot

> Last discussion: https://g0v.hackmd.io/@GuJ5fZ3uR-O09mlTi1w2UQ/rJUCYp2SB#Facebook-chatbot

> Github issue: https://github.com/cofacts/rumors-fb-bot/issues/4

:::info
TODO
- Production deployment - HC 這兩天會更新 token，放 heroku free dyno
- 等 Facebook 回應 app review 相關事項，轉手到其他人那邊了
- testing app
:::

Testing Facebook w/ rumor & chatbot: https://www.facebook.com/Demo-of-Cofacts-messenger-bot-100628288070779/?modal=admin_todo_tour
Testing App: https://www.facebook.com/Testing-App-292042981551899/

## LINE bot

今日更新部分 wording: https://github.com/cofacts/rumors-line-bot/compare/6899a402...0e161a54
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f5fcd3f40fb13a82846fbc25acebdfa5)


LINE 英文 Demo： http://nav.cx/mcCjvow
LINE 英文版： http://nav.cx/sM4NFfu

Cofacts 1-page flyer: https://docs.google.com/document/d/1w8c4GXVfm3zt9WRB_GTFPLZ4JIOL7wxODmwiIb6Dq3Y/edit


## Rumors-site 升級 next9
1. [x] Article list --> PR to dev
2. [x] Article page （見 API 更新）
3. [x] Reply list
4. [x] reply page
5. [x] docker build
6. [x] landing page
7. [x] 上 staging
8. [ ] 上 production
9. [ ] All i18n (including levels...)
10. [ ] RSS feed

## 其他信件

### contact from Nick Monaco

(Updates)

## OCR

文武：nodejs --> call tesseract binary
tesseract.js 太慢（1:30）

- 無法處理直向 (趨勢 bot 也不行)
- 會有雜訊，連空白的圖都能辨識出字
- google 的好很多

文武:UX 還沒討論
現在「我幫你找ＸＸ」那句都是雜訊 
但給他 list 讓他選應該也是有用的

orz
要把它獨立出來嗎 之後如果有 media center 也可以接

文武
要做完整會需要花時間，但如果只是要 OCR 可以很快

orz
好那先在 line bot 內 OCR 就好

不過 heroku 要跑 tesseract binary 可能會需要自訂 custom build pack 唷
或許可以考慮 google API

orz
如果搜尋不到的話  使用者會把他送進資料庫嗎

文武
不會有這個選項

:::success
請 GGM 提供 Google cloud vision 的 key
:::

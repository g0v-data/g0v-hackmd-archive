---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210317 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz, hsiao, lucien, ggm
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API

[DIFF](https://github.com/cofacts/rumors-api/compare/a78340aa4dbb914c106d0e455efaf565d804cbea...b887a4fb3ae968e0b1e248cc32099f80ad812353) Contribution code cleanup

#### :globe_with_meridians: Site
- [0311 release](https://github.com/cofacts/rumors-site/releases/tag/release%2F20210311)
    - openpeeps shuffle
    - tutorial english translation
    - impact report: sponsor URL, ecosystem, Google analytics
- [0313 release](https://github.com/cofacts/rumors-site/releases/tag/release%2F20210313)
    - 上架簡訊設計影片

####  :construction_worker: rumors-deploy
- cofacts.tw as canonical URL
- Google search console

#### :robot_face: rumors-line-bot

[0314 hotfix](https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20210314) Fix http://cofacts.org redirect isue

### :rocket: Staging

#### :globe_with_meridians: Site
- Ecosystem modal translation https://github.com/cofacts/rumors-site/pull/416/files


## 2021 三月計畫

- [x] 3/start 寄送 impact report
    - Sent 50
    - opened 18 times ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a6731b93f8923e6e101e53f2875704ea.png)
- [x] 3/5 簡訊設計影片完成
- [ ] 4 月初：deploy API header 讓第三方接取
- [ ] 4 月初：公開 profile page 
    - [x] 在[社團徵求意見](https://www.facebook.com/groups/cofacts/permalink/2946837205548089)
- [ ] apply 日文翻譯 --> ja.cofacts.org / ja.cofacts.tw
- [x] [Canonical URL setup](https://github.com/cofacts/rumors-deploy/pull/15) merge 了還沒 deploy
    - old.cofacts.org 應該要排除 index
- [ ] Slug unicode support https://github.com/cofacts/rumors-site/issues/399
- [ ] [Google sign-in](https://github.com/cofacts/rumors-api/issues/234)
- [ ] [LINE bot 送出流程改版](https://github.com/cofacts/rumors-line-bot/issues/214)
    - 目標：更簡單地送出流程、LIFF 不要 send message to chatroom (為 share dialog 做準備)

## 新 analytics page

### Group chat analytics 
https://datastudio.google.com/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/Fuy6B

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_792c4b12ef979567668be41ea5b28636.png)


### Revamped tutorial rich menu analytics
https://datastudio.google.com/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/DtzfB

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_62030f61a57faf7317e5d0704cbd83c6.png)


## 3/20 大松

Review good-first issue


## 4/10 小聚 @ AIC

### 第 24 次小聚
- [ ] 主題：Cofacts 真的假的第 24 次闢謠者工廠編輯小聚 @ 松山文創園區
    - 松菸 古蹟
- [x] 時間：4/10
	- **活動時間：14:00 - 17:00**
	- 門外有廁所
	- 門口防疫表單
	- 場地借用 13:00 - 18:00
- [ ] KKTIX
- [ ] 準備貼紙
- [ ] 問酒精、體溫誰負責 [name=bil]
- 場地：「松菸創作者工廠」內右手邊的「AIC 美國創新中心」110台北市信義區光復南路133號2樓 
    - 使用這裡：![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cf683a2f30e447882319bf282c82a53e.png)
    - [ ] ~~食物~~
    - [ ] 延長線 (場地有)
    - [x] wifi 場地有
- [ ] 誰會來呢？bil, mrorz, hsiao
- [ ] 誰不會來：ggm 汽車路跑
- [ ] 做圖：
    - [ ] 問是否可以用手的圖 [name=bil]
    - [ ] 左邊放字右邊放圖 [name=mrorz]
- [ ] LINE 文案：
    - 四月再想

##### 新 rundown

- 14:00 - 14:20 開場
    - 先放影片 5min
        - 血多、台灣吧、圖文不符、闢謠編輯現身
    - 場地介紹、Slido 破冰、Cofacts 機器人系統簡介
- 14:20 - 14:40：介紹 mission 1 - 按讚
    - 介紹「幫回應按讚」的用途，以及怎麼做；什麼樣的回應可以按「有用」、哪些可以跳過、哪些真的母湯要按「沒用」，如何就事論事的給 feedback
- 14:40 - 15:00：按讚時間
    - 讓大家從 Slido 打開 spreadsheet 1，直接點進自己號碼的那個 sheet
    - 然後幫每一篇按有用或沒用
- 15:00 - 15:30 休息、自我介紹、交流
    - 閒聊「看到覺得最好的回應、覺得哪裡好」
- 15:30 - 15:50：介紹 mission 2 - 寫新回應
    - 如何找全文、拆解回應、附出處
- 15:50 - 16:30：挑回應來回
    - 大家從 Slido 打開 spreadsheet 2，直接點進自己號碼牌的那個 sheet
    - 先挑選「一篇」覺得最有興趣的回
    - 回完之後如果行有餘力，再挑一篇
    - 如果都覺得不想回，去「等你來答」挑，不要硬回 XDDD
- 16:30 - 17:00：閒聊時間
    - 讓大家講感想
    - 介紹 RSS、文章列表、filter 功能
    - 最後拍合照

## 字太小 issue
來信

## MOU

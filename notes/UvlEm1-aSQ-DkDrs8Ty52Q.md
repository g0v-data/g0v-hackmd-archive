---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20210324 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz, lucien, ggm
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site

[0324 release](https://github.com/cofacts/rumors-site/releases/tag/release%2F20210324)

- Ecosystem modal translation https://github.com/cofacts/rumors-site/pull/416/files

### :rocket: Staging

#### :electric_plug: API

- iOS login fix [rumors-api#251](https://github.com/cofacts/rumors-api/pull/251), [rumors-deploy#18](https://github.com/cofacts/rumors-deploy/pull/18)

#### :globe_with_meridians: Site

- Absolute date for UI [#419](https://github.com/cofacts/rumors-site/pull/419) [#420](https://github.com/cofacts/rumors-site/pull/420)
    - kerrickstaley++
- Wrap long text in detail page [#418](https://github.com/cofacts/rumors-site/pull/418)
    - playpool513++


##### Testing checklist

http://dev.cofacts.org/

- [x] iOS 測試
    - [x] dev.cofacts.tw 登入＆登出
    - [x] dev-en.cofacts.tw 登入＆登出
    - [x] dev.cofacts.org 登入
        - [x] 登入後會被導向到 dev.cofacts.tw 且有登入成功
    - [x] dev-en.cofacts.org 登入
        - [x] 登入後會被導向到 dev.cofacts.tw 且有登入成功
- [x] 送新的東西進資料庫
    - 看 timestamp 是否正確


## Devs

- [x] 修復 iOS 登入
- [ ] Slug unicode support https://github.com/cofacts/rumors-site/issues/399
- [ ] 4 月初：deploy API header 讓第三方接取
- [ ] 4 月初：公開 profile page 
    - [x] 在[社團徵求意見](https://www.facebook.com/groups/cofacts/permalink/2946837205548089)
- [ ] apply 日文翻譯 --> ja.cofacts.org / ja.cofacts.tw
- [ ] [Google sign-in](https://github.com/cofacts/rumors-api/issues/234)
- [ ] [LINE bot 送出流程改版](https://github.com/cofacts/rumors-line-bot/issues/214)
    - 目標：更簡單地送出流程、LIFF 不要 send message to chatroom (為 share dialog 做準備)

## 4/10 小聚 @ AIC

- [x] 主題：Cofacts 真的假的第 24 次闢謠者工廠編輯小聚 @ 松山文創園區
    - 松菸 古蹟
- [x] 時間：4/10
	- **活動時間：14:00 - 17:00**
	- 門外有廁所
	- 門口防疫表單
	- 場地借用 13:00 - 18:00
- [x] KKTIX  https://cofacts.kktix.cc/events/cofacteditor24
- [x] 準備貼紙
- [ ] 問酒精、體溫誰負責 [name=bil]
- 場地：「松菸創作者工廠」內右手邊的「AIC 美國創新中心」110台北市信義區光復南路133號2樓 
    - 使用這裡：![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cf683a2f30e447882319bf282c82a53e.png)
    - [ ] ~~食物~~
    - [x] 延長線 (場地有)
    - [x] wifi 場地有
- [x] 誰會來呢？bil, mrorz, hsiao
- [x] 誰不會來：ggm 汽車路跑
- [x] 做圖：
    - [x] 問是否可以用手的圖 [name=bil]
    - [x] 左邊放字右邊放圖 [name=mrorz]
- [x] LINE 文案：
    - 四月再想

春光明媚的四月，來新的地方參加 Cofacts 真的假的編輯小聚!
這次在松菸文創園區內的二樓，AIC 美國創新中心

## 組織討論

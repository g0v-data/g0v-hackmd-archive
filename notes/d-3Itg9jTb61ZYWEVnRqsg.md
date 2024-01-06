---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20230524 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz, nonumpa, cai, O
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API

- [ROC year](https://github.com/cofacts/rumors-api/releases/tag/release%2F20230520)

#### :robot_face: rumors-line-bot

- [Sending analytics to BQ](https://github.com/cofacts/rumors-line-bot/releases/tag/release/20230520), [schema](https://github.com/cofacts/rumors-db/releases/tag/release/20230520)

## CCPRIP

### [Comm] Transcript
> https://g0v.hackmd.io/@cofacts/rd/%2FOhGIQzoxR5eF6audQuS_FQ
> nonumpa

#### PRs
- [collab-server](https://github.com/cofacts/collab-server/pull/1)
- [deploy](https://github.com/cofacts/rumors-deploy/pull/24)

#### Packaging
研究了一下，資料夾結構可能要改成下面的樣子，才能簡化 build 步驟
```
node_modules
apps
  |- server
  |- ...
packages
  |- hocuspocus-extension-elasticsearch
  |- ...
```
下禮拜想先看可不可以先上一版 site，Packaging 晚點再改

#### Auth

- Proxy by rumors-api? [name=mrorz]

### [Op] 分身帳號處理

https://g0v.hackmd.io/ndNDmEkiSHyTRMOEIy2q2Q （Cofacts workspace owner only）

### [Op] 回報可疑帳號
5月 23日與 24 日收到 40 則來自同一來源
關於張紹德，醫學博士、李健明醫師、李正華,擅長雕塑紫砂佛像、張真源、張信鴻、黃泓博教授、陳澤銘教授、陳志傑教授的訊息。
混合律師、教授、醫師等專業領域，並且分篇加上投資理財的資訊。
Mary Guzmán
Abdel Belkhodja 
macaulay stowe 
Harry Hunter
أم عبد الغفور 
Abida Islam
fergus carroll 
donald tyler 

## GA4
> https://g0v.hackmd.io/@cofacts/rd/%2FcJFFXVzgT4OFT6bBLtulGg

Universal analytics <> BQ

BQ deployed in 5/20
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f09617ea62df9f9d5d7016bee05943d1.png)

Google analytics
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_051ae2140de9b1bc5aa9157f8763f272.png)

- Everyday BQ is less than GA (after LIFF is subtracted from GA)
- Every category (other than `Cronjob` category) has less events

## 小聚 rundown

- [x] 地點：
  - 2023/5/27 2pm - 5pm
  - 台南新芽 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_467d6f751c9c90edbde9615261ce0983.png)
三張大桌子，坐15人以內舒適，有延長線跟飲水機和廁所，開門即會場。當天會有新芽工作人員陪伴
- [ ] 食物？統編？
    - Maybe 双生綠豆沙？
- [x] 場地費：轉帳新芽
- [x] 時間：
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
- [x] 投放目標：台南、高雄、嘉義 57,000 人
- [x] KKTIX:https://cofacts.kktix.cc/events/cofactseditor37
- [x] 誰會來呢：bil, mrorz, nonumpa
- [ ] bil要記得帶的：杯子、貼紙、粉粉文宣
    - 需使用實體車票
- [x] LINE 文案: 
「台南市被列入全台10大疫情危險縣市？」假的！！中央流行疫情指揮中心並沒有列出10大疫情危險縣市。
活動不該只辦在台北，Cofacts 真的假的要到台南舉辦志工培訓活動啦！！5月27日(六)14:00-17:00 歡迎沒有經驗的你，用一個下午的時間當鍵盤志工，一起對抗假新聞！請自備水杯、筆記型電腦與充電線唷！
台南新芽地址：台南市中西區成功路29號4樓(賀聲助聽器樓上，一樓有電梯）


----

- 週三會議
    - [x] 週四 8 pm schedule
    - [x] 換 rich menu
- 週五早上
    - [x] KKTIX 行前通知：提醒時間、使用電腦而非手機
    > Hello 你好，
	>
	> 明天就是 5 月 27 日的志工培訓囉！
	>
	> 志工培訓需要大量查詢資料，請自備筆電 💻 與充電器 🔌 並帶著愉快的心情來參加。帶順手的平板也可以的！如果願意協助聽打影片字幕，請自備耳機唷🎧  ！
	>
	> 🕒 時間：05/27（日）14:00
	> 📍 地點：台南市中西區成功路29號4樓(賀聲助聽器樓上，一樓有電梯）
	> 
	> 費用全免，會很準時開始。
	> 
	> Cofacts 真的假的 查核協作 VIP 臉書社團在這裡 👉 https://www.facebook.com/groups/cofacts
	> Cofacts 真的假的 查核協作 Discord 在這裡 👉  https://cofacts.tw/discord
	> 說你會來查核小聚優先加入 ＝Ｄ
	> 
	> 感謝你的閱讀。
	>
	> 那麼明天見囉😊
	>
	> 比鄰敬上
    - [x] 開場使用材料更新：https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit [name=mrorz]
	- [x] 準備 Slido `#cofacts37`
		- [x] 放投影片網址
    - [x] 幫 Netgear 充電
- 當日準備 / 攜帶
    - [ ] 樓下用的標語
    - [ ] 貼紙 - bil
    - [ ] 黏土 - orz
    - [ ] 延長線 x 1 - mrorz
    - [ ] 延長線 x 2 - nonumpa
    - [x] 編輯小聚的牌子 - orz
    - [x] Wifi 機 - mrorz
        - [x] Netgear 本體
            - [x] usb type-c 充電線與插座 （已充飽電，無需插座）
            - [x] 電池
            - [x] 4G 天線
        - [x] Asus RT-N12
            - [x] 電源線
            - [x] 5dBi 天線
            - [x] RJ45 線
- 13:15 - 場佈
  - [x] 簽到
  - [x] 排桌子椅子
  - [ ] 麥克風
  - [ ] 延長線佈置
  - [ ] 門口黏引導牌
  - [x] Slido - 白板寫 slido room number `#cofacts37`
  - [ ] WIFI
      - [ ] 佈機x2
      - [ ] 連結 netgear 與 asus WAN port
      - [ ] 白紙寫 SSID Cofacts meetup(_5G) + wifi password 貼牆上
      - [ ] 192.168.2.1 進入 netgear admin 看 asus 的 IP
      - [ ] 開好兩台 router admin 監測連網狀態
      - [ ] (optional) netgear 換成 5GHz only?
  - [ ] 投影的電腦用 google chrome 開好
    - [x] Google Chrome tab: [投影片](https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit)
    - [x] Google Chrome tab: [Bignum](https://cofacts.github.io/community-builder/#/bignum/setup)
    - [x] Google Chrome tab: [KKTIX](https://cofacts.kktix.cc/events/cofactseditor34)
    - [x] Google Chrome tab: [Slido admin](https://admin.sli.do/event/65b2eE1rKAQotivuL8aUvz/polls)
    - [x] Google Chrome tab: [Slido](https://wall.sli.do/event/65b2eE1rKAQotivuL8aUvz?section=b23363ca-0f78-4ec0-96c1-3ee4e35c2ebb)
    - [x] Google Chrome tab: [開場影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNVuJ9S-In4k93trnO_D2s6R)
    - [x] BGM
    - [ ] Analytics
- 14:00 - 14:20 開場
    - 放[長影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs) 8min
    - 場地、Slido、Cofacts 機器人系統簡介
- 14:20 - 14:40：引導註冊網站、介紹評價現有回應
- 14:40 - 14:50：實作評價
    - 讓大家從網站找訊息按讚
    - 提醒 15:00 結束時會問大家有沒有想要分享的心得
- 14:50 - 15:10 介紹補充資訊
- 15:10 - 15:40 實作補充資訊、自我介紹、休息
    - 閒聊「看到覺得最好的回應、覺得哪裡好」
- 15:40 - 16:10：介紹撰寫新回應
- 16:10 - 16:40：實作撰寫新回應
    - 大家從網站挑選「一篇」覺得最有興趣的回
- 16:40 - 17:00 介紹 RSS、社群、合照

## 國際交流

- Korea
- 信
- Trusted media summit apac


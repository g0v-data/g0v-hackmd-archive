---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20241021 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, conrad, nonumpa, mrorz, T
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: rumors-line-bot

- https://github.com/cofacts/rumors-line-bot/releases/tag/release/20241020


### :rocket: Staging

#### :robot_face: rumors-line-bot

- https://github.com/cofacts/rumors-line-bot/pull/398
- https://github.com/cofacts/rumors-line-bot/pull/399

:::info
9/23 發生什麼事：https://g0v.hackmd.io/yV0cJFs4R4iQ--83MR7HEQ?view#Analysis
 
- `searchMedia` 預設 sort by score
- 第 0 個 edge 不一定是 exact match，因此會把錯的 article 框進 cooccurrence
- Fix: 修改 `searchMedia` 使其會先按照 `mediaSimilarity` 排序。
    - 副作用：圖片搜尋、影片搜尋等的順序都會受影響。
:::

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] A 回報一組圖文
    - [x] 確認 consent wording 符合預期
- [ ] A 在網站上回覆其中一個 article
- [x] B 把同一組圖文 + 一個多的文字，回報成新的 cooccurrence
- [x] 觀察現有 article 的 reply request count

##### ⛔️ Release Blockers

N/A

##### 未竟項目

N/A

### :eye: Under review

## DoS patterns

> Alex++
> ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0e5aa37f62bf8c7d01ae301a4afdf029.png)
> 
> IP from taiwan ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_440ba18b5f27f7a278d009a0ffff563c.png)

>
> GraphQL query of the IP:
> ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c4d925998185667fdd5cca96c804b47a.png)
> 
> Attack range: starts from 2024/10/2
> ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ff07932e3bc74f41ea8a55293bc2f77f.png)

- 直接對 API 的攻擊，只能用未來[發 API key](https://g0v.hackmd.io/51wwLHgvSUqtBDaP-yAVnA#Alternative-Implement-using-Cloudflare-Zero-Trust) 來擋 [name=mrorz]


## 小聚 rundown

> 人數不如預期

- 推播 funnel 跟以往差不多 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1696f459b6705a683cd006ad00fe24e6.png)
    - 台中也是 4~5 人 [name=bil]
    - 人數少比較像是 workshop，多是演講
- 推播基隆桃園宜蘭？
    - 宜蘭太遠 [name=bil]
    - 再推一次比較好，但覺得不需要 [name=bil]
    - 貼 FB [name=mrorz]
- 2 月大松 --> 1 月小聚，12 月就不會有小聚，休息一下

---

- 週六早上
    - [x] KKTIX 行前通知：提醒時間、使用電腦而非手機
    > Hello 你好，
	>
	> 本週日就是 10 月 27 日的志工培訓囉！
	>
	> 志工培訓需要大量查詢資料，請自備筆電 💻 與充電器 🔌 並帶著愉快的心情來參加。帶順手的平板也可以的！如果願意協助編修影片逐字稿，請自備耳機唷🎧！
	>
	> 🕒 時間：10/27（日）14:00
	> 📍 地點：NPO HUB Taipei 二樓 / 100台北市中正區重慶南路三段2號2樓
	> 
	> 費用全免，會很準時開始。若不克前往，記得取消報名 :)
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
    - [ ] 開場使用材料更新：https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit [name=mrorz]
	- [ ] 準備 Slido `#cofacts`
		- [ ] 放投影片網址
    - [ ] 幫 Netgear 充電
- 當日準備 / 攜帶
    - [x] 空白志工證明，印成獎狀
    - [x] 樓下用的標語 - orz
    - [x] 貼紙 - orz, bil
    - [x] 黏土 - orz
    - [ ] 手板 - bil
    - [ ] 一次性杯子 - bil
    - [x] 延長線 - bil / mrorz
        - ~~跟 jothon 借 3 條 [name=bil]++~~ 人不多，就不用
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
- 13:30 - 場佈
  - [ ] 簽到（問飲料）
  - [ ] 排桌子椅子
      - 桌子 3x3、平行於長邊
      - 一個桌子放 4 人，9x4=36 椅子
      - Reference: https://g0v.hackmd.io/9yeDnDJqQTe7CklA7pwuEA
  - [ ] 麥克風
  - [ ] 延長線佈置
  - [ ] 門口黏引導牌
  - [ ] WIFI
      - [ ] 佈機x2
      - [ ] 連結 netgear 與 asus WAN port
      - [ ] 白紙寫 SSID Cofacts meetup(_5G) + wifi password 貼牆上
      - [ ] 192.168.2.1 進入 netgear admin 看 asus 的 IP
      - [ ] 開好兩台 router admin 監測連網狀態
      - [ ] (optional) netgear 換成 5GHz only?
  - [ ] 投影的電腦用 google chrome 開好
    - [ ] Google Chrome tab: [投影片](https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit)
    - [ ] Google Chrome tab: [Bignum](https://cofacts.github.io/community-builder/#/bignum/setup)
    - [ ] Google Chrome tab: [KKTIX](https://cofacts.kktix.cc/events/cofactseditor42)
    - [ ] Google Chrome tab: [Slido admin](https://admin.sli.do/event/rFQZd27cVvgEMyJAgv4BqT/questions)
    - [ ] Google Chrome tab: [Slido](https://wall.sli.do/event/rFQZd27cVvgEMyJAgv4BqT?section=215e56d0-a002-4b7e-9bf0-c58acbacc9bf)
    - [ ] Google Chrome tab: [開場影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs)
    - [ ] BGM
    - [ ] Analytics
- 14:00 - 14:20 開場
    - 放[長影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs) 8min
    - 場地、Slido、Cofacts 機器人系統簡介
- 14:20 - 14:40：引導註冊網站、介紹評價現有回應
- 14:40 - 14:50：實作評價
    - 讓大家從網站找訊息按讚
- 14:50 - 15:10 介紹補充資訊
- 15:10 - 15:40 實作補充資訊、自我介紹、休息
    - 閒聊「看到覺得最好的回應、覺得哪裡好」
- 15:40 - 16:10：介紹撰寫新回應
- 16:10 - 16:40：實作撰寫新回應
    - 大家從網站挑選「一篇」覺得最有興趣的回
- 16:40 - 17:00 介紹 RSS、社群、合照


---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20221116 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline


### :rocket: Staging


#### :globe_with_meridians: Site

- [Fix iOS video fullscreen problem #516](https://github.com/cofacts/rumors-site/pull/516)

##### Testing checklist
http://dev.cofacts.tw/

登入自有帳號後檢測：
- [x] iOS 在影片列表不會再跳出全螢幕影片

##### ⛔️ Release Blockers

##### 未竟項目

## [Follow-up] 違規檢舉
> 上週：https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2FnNjUnOgRTqOa2dDcqF67KA
還沒發文 QQ

本週紀錄：https://cofacts.tw/article/pjagx6j66egg 與相似可疑訊息
均為同一使用者
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a532665c8e017a383009265f959bc5b3.png)

:::spoiler
```graphql
query GetArticle {
  GetArticle(id: "pjagx6j66egg") {
    text
    createdAt
    user {id}
    relatedArticles {
      edges {
        node {
          text
          createdAt
          user {id}
        }
      }
    }
  }
}
```
:::

:::success
實作此：
https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2FG8JKqoW6T-SpCa704awGsw

- Block LINE user
- Reply with 詐騙集團回應
:::


## [Follow-up] 重複影片的解法？

> 上週分析：https://g0v.hackmd.io/nNjUnOgRTqOa2dDcqF67KA?both#%E9%87%8D%E8%A4%87%E5%9C%96-log

- 沒想法，放  context [name=nonumpa]
- 開 ticket: https://github.com/cofacts/rumors-line-bot/issues/322

## CCPRIP - Google cloud

https://g0v.hackmd.io/BRsJOevWSbyUMBSZEVVWrA?view#Proposal


## [Follow-up] open data CC BY-SA compliance

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_19204a0a944bc7295c52384576eddcaf.png)

https://g0v.hackmd.io/CfWAEl5xTUG8jSlwBVdN-w?view

## 小聚 rundown

- [x] 時間:
    - 11/20 (日) 13:30-17:30 
- [x] 場地：NPO HUB 2F key holder :Ronny
    - 台北市中正區重慶南路三段 2 號 2 樓  
- [ ] 食物？統編？
- [x] 時間：2022/11/20
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [x] 投放目標：雙北 + 基隆
- [x] KKTIX：https://cofacts.kktix.cc/events/cofactseditor33
- [x] 誰會來呢：bil, mrorz, nonumpa
- [x] 無法來：
- [x] LINE 文案 
選舉前依然假新聞四處亂竄，對於厭煩吵架與對立的你，如果用一個下午的時間，參與本次志工活動，將可以對社會創造偉大的貢獻！
Cofacts 真的假的 在11月20日本週日下午 2 點- 5點  ，徵求新的查核協作志工，活動完全免費，邀請你的到訪與參與！用鍵盤與智慧，為周圍的朋友與大家帶來和諧的力量。
(記得帶筆記型電腦與充電線唷！)
時間：11月20日(日) 下午 2 點- 5點
地點：台北市中正區重慶南路三段 2 號 2 樓
最近的捷運站是中正紀念堂站2號出口 

:::success
- 已在報名表單增加受訪意願勾勾
- 喬拍攝鏡位 https://www.npohub.taipei/%E7%A9%BA%E9%96%93%E7%A7%9F%E5%80%9F
:::

--- 

- 週三會議
    - [x] 週四 8 pm schedule
    > 查核機器人所回應的查證資訊，都是善良的志工一筆一筆新增的。
    >
    > (PC) 在這裡邀請您，即使只是對查證資訊好奇，不限年齡、無論經驗，都能參與本次的查核工作坊。只需要攜帶筆記型電腦，花一個下午的時間，就能習得查核技巧幫助其他的朋友喔！
    >
    > 10月20日（日）14:00-17:00 鍵盤志工活動，完全免費，歡迎從未參加過的您，幫助不擅長查證訊息的親戚朋友。
    > 
    > 🔰 這是免費的實體志工聚會，超級歡迎沒有參加過的新手，會在活動中提供查核技巧教學。
    > 
    > 座位有限，請記得報名 👇
    > https://cofacts.kktix.cc/events/cofactseditor33
    > 
    > 📍 地點：台北市中正區重慶南路三段 2 號 2 樓

    > 🚇 最近的捷運站是中正紀念堂站2號出口 

    >
    - 目標：新北市
    - [x] 換 rich menu
- 週六早上
    - [x] KKTIX 行前通知：提醒時間、使用電腦而非手機
    > Hello 你好，
	>
	> 明天就是 11 月 20 日的志工培訓囉！
	>
	> 志工培訓需要大量查詢資料，請自備筆電 💻 與充電器 🔌 並帶著愉快的心情來參加。帶順手的平板也可以的！
	> 
	> 😷 疫情期間，參與培訓須佩戴口罩。場地備有飲水機，請攜帶自己的杯子或水瓶取用唷 🚰 ！
	>
	> 時間：11/20（日）14:00
	> 地點：台北市中正區重慶南路三段 2 號 2 樓

    > 🚇 最近的捷運站是中正紀念堂站2號出口 

	> 
	> 費用全免，會很準時開始。
	> 
	> Cofacts 真的假的 查核協作 VIP 臉書社團在這裡 👉 https://www.facebook.com/groups/cofacts
	> 說你會來查核小聚優先加入 ＝Ｄ
	> 
    > 🤒 最後，如果這幾天成為了密切接觸者、不幸確診、或是自覺有染疫風險而希望減少接觸，請記得要取消報名唷！小聚每兩個月就有一次，還是歡迎參與未來的活動。 
	>
	> 感謝你的閱讀。
	>
	> 那麼明天見囉😊
	>
	> 比鄰敬上
    - [x] 開場使用材料更新：https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit [name=mrorz]
	- [x] 準備 Slido `#cofacts33`
		- [x] 放投影片網址
    - [ ] 幫 Netgear 充電
- 當日準備 / 攜帶
    - [x] 樓下用的標語
    - [ ] 貼紙 - bil
    - [x] 黏土 - orz
    - [x] 延長線 x 1 - mrorz
    - [ ] 延長線 x 2 - nonumpa
    - [x] 編輯小聚的牌子 - orz
    - [x] Wifi 機 - mrorz
        - [ ] Netgear 本體
            - [ ] usb type-c 充電線與插座 （已充飽電，無需插座）
            - [ ] 電池
            - [ ] 4G 天線
        - [ ] Asus RT-N12
            - [ ] 電源線
            - [ ] 5dBi 天線
            - [ ] RJ45 線
- 13:00 - 場佈
  - [ ] 簽到、噴酒精、量體溫
  - [ ] 排桌子椅子
  - [ ] 麥克風
  - [ ] 延長線佈置
  - [ ] 門口黏引導牌
  - [ ] Slido - 白紙寫 slido room number `#cofacts32`
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
    - [x] Google Chrome tab: [KKTIX](https://cofacts.kktix.cc/events/cofactseditor33)
    - [x] Google Chrome tab: [Slido admin](https://admin.sli.do/event/mEj5ZYPTP7ATYzytXjZWa3/polls)
    - [x] Google Chrome tab: [Slido](https://app.sli.do/event/mEj5ZYPTP7ATYzytXjZWa3)
    - [x] Google Chrome tab: [開場影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNVuJ9S-In4k93trnO_D2s6R)
    - [x] BGM
    - [ ] Analytics
- 14:00 - 14:20 開場
    - 放[影片](https://www.youtube.com/playlist?list=PLz8KCDL90tNWn16J2xBzl53imUiDbNOzs) 8min
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

---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240422 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO Hub 出席：mrorz, bil
- 線上出席：Jonathan, nonumpa, T
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: rumors-line-bot

LIFF page "mgpAwardee", cofacts.tw/mgpAwardee
- https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20240417 Form
- https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20240418 User ID check

### :eye: Under review

## CCPRIP

### [Op] Transcript spam
> https://github.com/cofacts/rumors-api/pull/335

- 改完了，修 test [name=nonumpa]
- 修 OCR 的版本更新的字，只要 match 部分的文字 [name=nonumpa]
- 繼續 review [name=mrorz]

### [Op] 垃圾訊息反制
> https://g0v.hackmd.io/uefTz4yURImgtem--itaMw?both#Op-%E5%9E%83%E5%9C%BE%E8%A8%8A%E6%81%AF%E5%8F%8D%E5%88%B6

Design doc: https://g0v.hackmd.io/um7DyY_ESbu2LL78kLw3pg?both

:::success
mrorz 進行第一階段
:::

## 送出訊息 wording

> 上週謠言惑眾獎後續作業
> https://g0v.hackmd.io/uefTz4yURImgtem--itaMw#%E5%BE%8C%E7%BA%8C%E4%BD%9C%E6%A5%AD
> 
> 有一件事情想與 MyGoPen 的夥伴們討論。
> 目前似乎已經發生不少 Cofacts 使用者走錯，跑去打擾 MyGoPen 的情形，抱歉造成困擾 :pray:
> 我們上次開會的時候討論到，會有走過去的情形，可能是因為 Cofacts chatbot 在「傳送的訊息資料庫裡找不到、且是手動輸入的」的時候，會提示使用者到yGoPen 真人查證來查詢，如附圖所示。
> 不知道這個流程有沒有對 MyGoPen 這裡造成困擾，是否需要進行調整呢？
> [name=mrorz]
> 
> 是不至於造成困擾，民眾常常搞不清楚 :joy:
> 只是最近的案例都是希望我們幫忙下架cofacts 上的貼文，因為包含了個資，這部分可以的話看看cofacts 那邊有沒有什麼機制？
> 比如說再詢問是否要公開詢問的時候，可能要更白話一些，畢竟每個民眾的資訊程度不同。或是否提供使用者自己刪除的機制在網頁上，詢問的貼文來自於誰應該是有紀錄，如果在網頁上有個要求刪除的按鈕然後串接line 登入，可以取得是否與原詢問人相同，相同就可以刪除。如果有其他考量，也可以做成如果該詢問已經有人回應過了就可以聯絡cofacts 後續處理討論是否刪除。有這樣的機制應該就可以減少跑來我們這邊要求刪文的人也可以減少你們還要後續處理的問題。個人建議參考參考
> [name=robin@mgp]
> 
> 送出前的這段真的要改
> 1. 「在 Cofacts 真的假的資料庫公開這則訊息」 使用者不一定知道是網站
> 2. 試著最後加一句注意個人資訊的警語？
> ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_283b20329c0b8d1b12bb21f26cc78015.png =x200)
> [name=cai]
> 
> 目前的 wording 來源似乎是在 2020 年討論的結果
> 討論：
> - 兩個方案 https://g0v.hackmd.io/r3NK7xssSwCNPFxthlw7tA?view#chatbot-%E4%B8%8D%E5%95%8F%E4%BE%86%E6%BA%90
> - 方案檢討 https://g0v.hackmd.io/rEtx-47bRHeW2aM05DINDQ#chatbot-%E4%B8%8D%E5%95%8F%E4%BE%86%E6%BA%90
>
> Issue: https://github.com/cofacts/rumors-line-bot/issues/214
> 最終文案定版：https://g0v.hackmd.io/@cofacts/meetings/%2Feo8NM1VGQ7qxaamBZXRPtA
>
> 最一開始討論時 wording 好像是「我願意公開⋯⋯」
> 但因為有 concern 說「公開訊息會讓人有個資或訊息被偷看的感覺」所以修改成現在的現在的樣子
> 我個人是認為原本的「我願意公開此訊息」是個比較明確的 consent，比較不會有送出了之後還來後悔的狀況
> 我也有點忘記當時的考量點是什麼，記錄到的討論結果有點模糊
> [name=mrorz]


- 不應該讓刪文輕鬆成立，怕大家來問完之後就刪除，不符合公益 [name=bil]
- 會不會有可能送進來的人不是個資透露的本人 [name=T]
  - 目前沒發生過，但有可能。所以就算實作了本人下架功能，其實還是沒辦法 cover 這個，需要靠現有的申訴機制處理 [name=orz]
- 送出流程：想要拿掉 --> 不在資料庫 --> 是自己打的 --> 求助真人查證 [name=mrorz]
  - 在最後這裡，MyGoPen 旁邊新增聯絡 Cofacts 的選項，使用者就不會選 MyGoPen [name=T]
  - 「提出申訴」並非「真人查證」，導向到 Cofacts 處理 [name=T]
  - 「申訴」不錯，避免使用者寄信來查假訊息
- 可以用另一個信箱嗎 [name=bil]
  - 表單也是可以 [name=mrorz]
  - 要提供 URL、真實姓名、聯絡 email、電話
  - 申訴請求：個資遮蔽 / 其他 etc

:::success
想一下 wording
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3c6af7c882548e8f2529f3181076e410.png)
:::

### Proposal（單一訊息）

> `util.ts`

目前資料庫裡沒有您傳的訊息。
Currently we don’t have this message in our database.

如果您覺得：
If you think:

1. 它很可能是謠言
   It is most likely a rumor
2. 您願意公開此訊息
   You are willing to make the message public

請按「🆕 送進資料庫查核」在 Cofacts 網站公開它，讓好心人能查證與回覆。您可以幫助到未來同樣收到這份訊息的人。
Press “🆕 Report to database” to make this message public on Cofacts website and have volunteers fact-check it. This way you can help the people who receive the same message in the future.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_554a45b05b976a2c102031d003a4f1c2.png)

:::spoiler JSON

```javascript=
{
  "type": "bubble",
  "body": {
    "type": "box",
    "layout": "vertical",
    "contents": [
      {
        "type": "text",
        "text": "目前資料庫裡沒有您傳的訊息。",
        "wrap": true
      },
      {
        "type": "text",
        "text": "若您覺得：",
        "margin": "md",
        "wrap": true
      },
      {
        "type": "box",
        "layout": "horizontal",
        "contents": [
          {
            "type": "text",
            "text": "🤔",
            "flex": 0,
            "margin": "none"
          },
          {
            "type": "text",
            "text": "它很可能是謠言",
            "wrap": true,
            "flex": 1,
            "margin": "md",
            "contents": [
              {
                "type": "span",
                "text": "它很可能是"
              },
              {
                "type": "span",
                "text": "謠言",
                "decoration": "none",
                "color": "#ffb600",
                "weight": "bold"
              }
            ]
          }
        ],
        "margin": "md"
      },
      {
        "type": "box",
        "layout": "horizontal",
        "contents": [
          {
            "type": "text",
            "text": "🌐",
            "flex": 0,
            "margin": "none"
          },
          {
            "type": "text",
            "text": "它很可能是謠言",
            "wrap": true,
            "flex": 1,
            "margin": "md",
            "contents": [
              {
                "type": "span",
                "text": "您願意"
              },
              {
                "type": "span",
                "text": "公開",
                "decoration": "none",
                "color": "#ffb600",
                "weight": "bold"
              },
              {
                "type": "span",
                "text": "這則訊息"
              }
            ]
          }
        ],
        "margin": "md"
      },
      {
        "type": "text",
        "text": "請按「🆕 送進資料庫查核」在 Cofacts 網站公開它，讓好心人能查證與回覆。您可以幫助到未來同樣收到這份訊息的人。",
        "wrap": true,
        "contents": [
          {
            "type": "span",
            "text": "請按「"
          },
          {
            "type": "span",
            "text": "🆕 送進資料庫查核",
            "color": "#ffb600",
            "weight": "bold"
          },
          {
            "type": "span",
            "text": "」在 Cofacts 網站公開它，讓好心人能查證與回覆。您可以幫助到未來同樣收到這份訊息的人。"
          }
        ],
        "margin": "md"
      }
    ]
  },
  "footer": {
    "type": "box",
    "layout": "vertical",
    "spacing": "sm",
    "contents": [
      {
        "type": "button",
        "style": "primary",
        "height": "sm",
        "action": {
          "type": "uri",
          "label": "🆕 送進資料庫查核",
          "uri": "https://linecorp.com"
        },
        "color": "#ffb600"
      },
      {
        "type": "button",
        "style": "primary",
        "height": "sm",
        "action": {
          "type": "uri",
          "label": "我不想回報訊息",
          "uri": "https://linecorp.com"
        },
        "color": "#333333"
      },
      {
        "type": "box",
        "layout": "vertical",
        "contents": [],
        "margin": "sm"
      }
    ],
    "flex": 0
  }
}
```
:::

:::success
送出 wording：開票＋good first issue
:::


### Proposal（多則訊息）
> In `askingCooccurrence`

您傳的 N 則訊息，目前都不在 Cofacts 資料庫裡。

若您覺得：
1. 它們很可能是謠言
2. 您願意公開這些訊息

請按「🆕 送進資料庫查核」在 Cofacts 網站公開它，讓好心人能查證與回覆。您可以幫助到未來同樣收到這些訊息的人。

## g0v summit

社群軌 - AI 時代的資訊挑戰
5/4 10:40 @ R0
> 再不熟悉科技領域的人都可以使用生成式ＡＩ體驗各種資料累積下的預測與衝擊，更有許多人預測生成式ＡＩ將帶來更多的假資訊，而群眾的認知面臨更多的挑戰。在資訊環境中，公民科技社群Cofacts要與來自泰國的Cofact公民科技查核組織還有台灣資訊環境研究中心一起來討論假訊息的各種挑戰與如何透過協作與連結守護我們的資訊環境。

同時間在 R2：
Anti-Misinformation Factchecking Chatbot: A Prototype for Malaysia
5/4 10:40 @ R2
> https://summit.g0v.tw/2024/agenda/#2024-038
Khairil Zhafri
> An interactive workshop to introduce, gather feedback, and solicit ideas on a prototype for a cross-platform an anti-misinformation chatbot targeted at Malaysian internet users. In this session, we will go through the implementation of multimedia integrations with WhatsApp and other instant messaging systems as well as an overview of available open standards for factchecking. 
> 
:::success
不行的話 MrOrz 去聽 R2 的
:::

## 小聚籌備

5/25 (六) or 26(日）, bil 27 飛馬來西亞


- [ ] 日期：
- [ ] 食物：
- [ ] 場地：新北青職基地
    - 有一個 G-force 把 1F 整週都借掉了；6/1, 2 的一樓也已經被借走
    - NPO Hub 的 5 月 quota 已經沒有了
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
- [ ] 投放目標：
  - 推播日：
  - 推播日之前：新北志工優先報名
  - 目標：雙北、桃園？
- [ ] KKTIX:https://cofacts.kktix.cc/events/cofactseditor41
- [ ] 誰會來呢：bil, mrorz, nonumpa
- [ ] 記得帶：貼紙、環保杯
- [ ] LINE 文案
- [ ] VOOM 發文

## 下次開會

5/2 (四)，有實體，要跟 NPO hub 講 --> done


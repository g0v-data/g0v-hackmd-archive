---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20210915 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：mrorz, bil, nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: rumors-line-bot

https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20210909

Article LIFF go live!

使用量：https://datastudio.google.com/u/0/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/p_44cex908mc

## Takedowns

- https://cofacts.tw/user?id=M_TJ13sBqH8xU4AwssJ3 --> spammer list https://github.com/cofacts/takedowns/pull/18/files#diff-394a7f57024e526a2efc4bd43d993bf2124c024571491de04a08c474119bf0ae :heavy_check_mark: 
- Empty replies --> FB group

:::success
1. 貼文問 FB group :heavy_check_mark:
2. 撈資料庫找出現存的 empty replies
:::

## Facebook & Privacy

https://github.com/cofacts/rumors-site/pull/447

- 回信問 FB PR 是否要改
- 解釋 Cofacts 不能刪資料

:::warning
求 approve :heavy_check_mark:
:::

## Needs research: This paper's approach

https://www.wired.com/story/could-wisdom-of-crowds-help-fix-social-media-trust-problem/

產出：類似之前對 [twitter birdwatch](https://g0v.hackmd.io/oK1F5q4eRV2IhGM-8ULTdQ) 的筆記

:::warning
求幫讀
:::

## 26th 小聚籌備

[前次小聚檢討](https://g0v.hackmd.io/ie1Ymj_3SlmHp0jAIy6mJw#%E5%B0%8F%E8%81%9A%E6%AA%A2%E8%A8%8E)

- [ ] 主題：26th 柚子、優酪乳與香蕉編輯小聚
    - 中秋節前後
    - 經典謠言
- [ ] 時間：9/25
	- **活動時間：14:00 - 16:00**
	- 時間分配
        - 2:00 - 2:20 開場
        - 2:20 - 3:00 進行評價 (20則)
        - 3:00 - 3:20 介紹工具
        - 3:20 - 4:00 進行回應（1則）
- [ ] Jitsi 50 人
- [ ] 投放目標： All - 北北基桃 約 10 萬人
- [ ] 事前產生 spreadsheet 50 人分工
- [ ] KKTIX：
- [ ] 誰會來呢：mrorz, bil, nonumpa, Lucien
- [ ] 做圖：Lucien
    - bil 有很多柚子可以當素材
- [ ] LINE 文案

柚子不能跟優酪乳一起吃？真的假的啊？？？
假的假的，每到中秋節，這則謠言就會捲土重來。
謠言不死，隔年再來。

2021年 9 月 25 日(六)下午 2 點到 4 點，線上查核編輯小聚，邀請從來沒有參加過查核志工活動的你，在家裡看著電腦，就能輕鬆成為鍵盤志工，幫助其他遇到假訊息的朋友與家人。
線上志工聚會，免費，超級歡迎沒有參加過的新手，提供線上查核技巧教學。



雖然柚子跟優酪乳或是香蕉一起吃不會中毒，.......
（但如果正在服藥，就真的不建議同時吃柚子或是葡萄柚喔！）


## Linode scheduled maintenance

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4651c01495a9410b52c2152bac8d37c4.png)

2021/9/17 1:15AM ~ 3:15AM

:::success
MrOrz 寫公告貼 FB group & slack :heavy_check_mark:
:::


### Network & nginx logs

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fb803ce02dd9161a1a42da66f6d1bfe3.png)

nginx logs: 不知道為啥是空的⋯⋯
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2e707d569bd1922bf99010323983b1a3.png)

想趁凌晨把 nginx logs 改接到 aws cloudwatch logs 上。

rumors-line-bot production log: 4 個月 2.11GB

:::info
MrOrz 今天凌晨改 nginx log 上 cloudwatch :heavy_check_mark: 
:::

## Dev items 排序

- Share from LIFF & Share card 增加 LIFF coverage & spread [name=mrorz]
- LIFF TODO items
- 消除「送訊息至聊天室」權限請求
- LIFF 要求 LINE bot 使用者協作
- Feedback 選項樣板 / 罐頭按鈕
- 網站回應介面加強引導
- 實作存進 GCS [name=nonumpa]

### Share card：Sharable entry of LIFF

原始提案: https://g0v.hackmd.io/0RX4MsjRRJmBqJSKVilWMA#LIFF-share-dialog-proposal

放進聊天視窗，點了之後打開 LIFF

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3b42a0211272da2ddf7e4a207e53a63c.png =x500)


:::spoiler Flex message
https://developers.line.biz/flex-simulator/

```json
{
  "type": "bubble",
  "size": "giga",
  "header": {
    "type": "box",
    "layout": "vertical",
    "contents": [
      {
        "type": "text",
        "text": "對於下面這個訊息：",
        "size": "xs",
        "color": "#999999"
      },
      {
        "type": "text",
        "text": "這是最新的高雄狀況，電視新聞都被封鎖不報導，這是由醫師公會前線的醫師提醒的，高雄地區需注意的，高雄已是新冠確診全國第一名，出外一定要儆醒，要帶口罩喔！",
        "maxLines": 2,
        "color": "#999999",
        "wrap": true
      }
    ],
    "paddingAll": "lg",
    "spacing": "sm"
  },
  "body": {
    "type": "box",
    "layout": "vertical",
    "contents": [
      {
        "type": "text",
        "weight": "bold",
        "size": "xl",
        "text": "有人附上一則資料佐證，指出它",
        "contents": [
          {
            "type": "span",
            "text": "有人附上一則資料佐證，指出它"
          },
          {
            "type": "span",
            "text": "含有錯誤訊息",
            "color": "#fb5959"
          },
          {
            "type": "span",
            "text": "唷！"
          }
        ],
        "wrap": true
      },
      {
        "type": "text",
        "text": "1.截至2021年1月6日為止，高雄本土確診病例數為0，本土加境外移入病例為112例，並非是全國最高。\n2.高雄市醫生公會、高雄縣醫師公會皆表示，傳言指稱「高雄已是新冠確診全國第一名」、「電視新聞封鎖」並不正確，且醫師公會並未發出類似訊息。",
        "wrap": true,
        "maxLines": 5
      }
    ],
    "spacing": "lg"
  },
  "footer": {
    "type": "box",
    "layout": "vertical",
    "spacing": "sm",
    "contents": [
      {
        "type": "button",
        "style": "primary",
        "height": "md",
        "action": {
          "type": "uri",
          "label": "看詳細",
          "uri": "https://liff.line.me/1563196602-X6mLdDkW?p=article&articleId=19yffzgl9w0xu"
        },
        "color": "#ffb600",
        "margin": "none"
      }
    ],
    "flex": 0
  },
  "action": {
    "type": "uri",
    "label": "action",
    "uri": "https://liff.line.me/1563196602-X6mLdDkW?p=article&articleId=19yffzgl9w0xu"
  }
}
```
:::

#### 產生 Share card 

- LIFF 分享按鈕 --> [Share target picker](https://engineering.linecorp.com/zh-hant/blog/liff-share-target-picker/) --> 在目標聊天室產生 share card ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d03c2cd8412326ff29390fe041416064.png =x200)
- LINE bot 分享回應
 --> Share target picker --> 在目標聊天室產生 share card ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1d72229f48faaa8a4702678daeb91900.png =x200)
- LINE bot 在 LINE 問人 --> Share target picker --> 在目標聊天室產生 share card ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2ef5e80f95e89515e3f7228d2063af78.png =x200)


### LIFF TODO items

1. [ ] 實作 article page 的 reply request form + 使用在目前的按鈕上
2. [ ] 實作 article page 的 reply request list
3. [ ] 載入使用者自己的 feedback
4. [ ] 列出其他人的 feedback
5. [ ] 實作 article page 的 related article

### 消除「送訊息至聊天室」權限請求

- 實作 article page 的 reply request form + 使用在目前的按鈕上
- 改寫文章送出流程
    - Issue: https://github.com/cofacts/rumors-line-bot/issues/214
    - [Q2 Dev 整理](https://g0v.hackmd.io/BBeVH2VxRNOCq5QB_HC6EQ#Devs---Q2)
- 改寫送出回應 feedback 流程
    - 在 LIFF 內送出回應 + 感謝文案
    - 若為好評，在 LIFF 內鼓勵使用者分享（share target picker --> share card）
- 「看過的訊息」改點開 article LIFF（延伸：見下「LIFF 強化 LINE bot 使用者貢獻」）

### LIFF 要求 LINE bot 使用者協作

參考 birdwatch 首頁：
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9555d0e54222bdfe4be0b50cd47987de.png)
- Needs your help：協助對回應評分
    - 列出有回應過、還沒評價的熱門訊息與回應，求評價
    - 若不確定，可以按「跳過」按鈕跳過該則（新功能需另外實作）
- Rated：自己評價過的回應們（從 `ListArticleReplyFeedbacks` 撈）
- Viewed messages：看過的訊息

### Feedback 選項樣板 / 罐頭按鈕

參考 Twitter Birdwatch: https://twitter.com/birdwatch/status/1410288711921766401
相關討論：https://github.com/cofacts/rumors-line-bot/issues/213#issuecomment-903213995

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1435edf5dcb6e400529135133f54b8e3.png)


提供按鈕按下去之後自動填寫，但也可自行加字。

為何這個回應有幫助
- 所引用的資料佐證品質很好
- 用字遣詞易懂
- 有針對訊息內文回應
- 提供了重要脈絡

為何這個回應沒有幫助
- 沒有資料佐證、或資料佐證不可信
- 參考資料無法作為回應文字的佐證
- 資訊有誤
- 有錯字或用語模稜兩可
- 沒有回應到重點
- 煽動性言詞

### 網站回應介面加強引導

https://g0v.hackmd.io/6mTYVWhLSTWfDcyaxYLaXA#%E5%B8%B8%E8%A6%8B%E9%8C%AF%E8%AA%A4%E5%9B%9E%E6%87%89%E6%A8%A3%E6%85%8B

### 其他想法

- chatbot 裡「看其他回應」現在導向到網站，應該導向到 LIFF 才能評分 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8151071fc01364486a3d87e5640fc2a5.png =x300)
- LIFF 動畫
- Reply request 提供選項樣板 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_944f36384f5b249b30213db75dd7c019.png)
- 補強 tutorial page links, 加入 link of reply hash
- 偵測第一次參與編輯的人，跳出跳窗導向到 tutorial
- 支援圖片、影片、聲音 https://g0v.hackmd.io/aJqHn8f5QGuBDLSMH_EinA



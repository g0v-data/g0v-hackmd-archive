---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220525 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, nonumpa, MrOrz
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :globe_with_meridians: Site
##### Testing checklist
http://dev.cofacts.tw/

[上次的未竟項目](https://g0v.hackmd.io/_HXxDu6OQPaK08WFwOshtg#%E6%9C%AA%E7%AB%9F%E9%A0%85%E7%9B%AE)
- [x] mobile 上 article list / hoax-for-you 爆版
    用最簡單的修法即可：圖片窄一點
- [x] reply detail 的 article list item 不會顯示圖 XD
- [x] profile page 的查核回應列表也不會顯示圖 XD
- [x] 編輯介面下搜尋回應、使用現有回應的文章圖


##### ⛔️ Release Blockers

##### 未竟項目

- mobile 的寫回應的「原始文章」![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_01890b0648a49b9738f3e9089d70202b.png)


## Media support
> https://github.com/orgs/cofacts/projects/9

- https://github.com/cofacts/media-manager/pull/1
- File upload & query
- integration

## Trend and Contribution

> https://github.com/orgs/cofacts/projects/10

## Moderation discussion

https://www.facebook.com/groups/cofacts/posts/3280462345518905/

- 案例一（虛擬貨幣呼朋引伴）
- 案例一的延伸（Trust Global）
- 案例二（柯黑開分身）

:::success
執行案例一、案例一的延伸所提案的處置（block 共 8 人）

放置案例二（無具體處置方案）
:::

## 文字配圖/配影片問題 (article group)

> 昨天發現
> 原來這段文字搭配的影片有變
> 我第一時間在 FB 撈到的那個影片，看來跟在 LINE 上面傳的影片不同⋯⋯
> https://cofacts.tw/article/oc60en946cxl
> 加上之前這個 case
> https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1652189202.958809
> 似乎除了紀錄檔案之外，
> 還是要設計之前提到的 article group
> 請使用者把檔案前後搭配的文字一起轉傳進來讓我們紀錄
> [name=mrorz]


- [Co-occurrence model](https://g0v.hackmd.io/aJqHn8f5QGuBDLSMH_EinA#Surrounding-text-cooccurrence-model)
  - 作為編輯，會想要針對個別訊息回就好，還是針對「組合」做回應？
- LINE bot 如何搜集 co-occurrence
  - 訊息進來都等 5 秒，搜集同一人來的訊息一次回應
    - 若同一人有多則訊息傳進來，問「請問這 3 則訊息，在 LINE 裡是互相搭配在一起傳的嗎？」
      - 「是，這些都是對方是一口氣傳的」
        - 做成 article group 紀錄 occurrence
        - 列出個別 article 與資料庫中的相似度，讓使用者選擇一個 article，下同單篇訊息流程
        - Q: 「公開到資料庫」的流程:question:
        - Q: 如果一口氣傳的幾則訊息裡，有些有在資料庫、有些沒有，那沒有在資料庫的那些要怎麼送進資料庫:question:
      - 「否，是分開的訊息」
        - 「請再試一次，這次一次只要傳一則訊息唷。」
  - 單傳圖、影片或檔案時，詢問：「請問傳這張圖的人，有搭配其他的文字傳送嗎」
    - 「有」
      - 「網傳訊息常常有「影片本身沒問題、但搭配文字是錯的」的狀況。請再試一次，這次請把對方傳的圖片與所搭配的文字，一口氣傳給我唷！」
    - 「沒有，對方就只傳這張圖」
      - （走單一訊息查詢與送出流程）
  - 單傳文字 --> 與現在相同



## Google 停用帳號與文件

### Google drive

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_91fdda346397b3fe1eaec03784ac4950.png)

檔案：https://docs.google.com/presentation/d/1_HnjSssdLACRQqC4Zy7FrpMzHJ3xlBrqAvC5bMat4aw/edit

### Gmail account

擁有搜集的 LINE 轉傳圖片的 Google 帳號在 5/24 遭到停權

完全無法登入：
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9d955db8addb5e6eb1e1bd4fe9d9913b.png)

了解詳情點下去：https://support.google.com/accounts/answer/40695?visit_id=637890738718719347-142478532&p=disabled_le3_signin1&rd=1#why

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1125c5d22a445506929bcc6bf4704859.png)

要求重新審查的結果：
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a6c0aa36e081cbfcf2c118dd15fd0c5e.png)

傳圖片之後 log 會有 `Error: GaxiosError: invalid_grant`


---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250512 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO Hub: bil, mrorz
- 線上出席：nonumpa, Tim, EJ
- Gather Town: https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

Takedown:
- https://github.com/cofacts/takedowns/pull/203 
- More on this later

## Badge

> EJ

- API Enhancement:
    - Revoke badge for the user : DELETE /badge/award
        ```
        { 
            "userId": "ZLcNiZIBDfH0hhhZCB-7",
            "badgeId": "BYiaQZQBpiYdBld_UVwg"
        }
        ```
        
- UI/UX Enhancement: 
    - user profile page UX enhance (change cursor on the badge name).
    - add badge rewarded metadata section in the pop up, and only visible to the user.


## CCPRIP

### [Op] Automatic takedown

> Nonumpa

- mrorz@g0v-tw (2025-05-09): 討論到 spam 偵測存在 false negative 的情況，需要三篇文章一起看才能判斷是否為廣告。提供了 Langfuse 的 trace 連結供參考。
  - https://langfuse.cofacts.tw/project/cm3n1h0xu000mfdgamwhs63t2/traces/8df1a8c8-61f2-4522-b440-befb32508f91?timestamp=2025-05-09T01:49:46.510Z&display=details
  - https://langfuse.cofacts.tw/project/cm3n1h0xu000mfdgamwhs63t2/traces/e5524d4d-1af7-4cf4-8138-e0425601fadb?timestamp=2025-05-09T01:49:46.514Z&display=details
  - https://langfuse.cofacts.tw/project/cm3n1h0xu000mfdgamwhs63t2/traces/92d2d251-cb66-4799-ac46-74c863a8bc56?timestamp=2025-05-09T01:49:46.514Z&display=details
- False positives
  - MrOrz (2025-05-09): New comment on pull request #229, #228, #227, #224 (FP on spam user takedowns)
  - nonumpa (2025-05-08): Pull request closed: #223, #222 (Takedown spam user)
  - MrOrz (2025-05-08): New comment on pull request #220, #219, #218 (False positive on spam user takedowns)
  - nonumpa (2025-05-07): Pull request closed: #217, #215, #216, #214 (Takedown spam user)
  - nonumpa (2025-05-06): New comment on pull request #208 (False positive, grab Xiaohongshu ID)
- nonumpa (2025-05-10): Pull request closed: #226 feat: disable article detection since there are too many false positives [https://github.com/cofacts/takedowns/pull/226]
- nonumpa (2025-05-06): Pull request opened: #210 fix: codeowners exclude root files, test and .github folders [https://github.com/cofacts/takedowns/pull/210]
- nonumpa (2025-05-05): Pull request closed: #192 Implement Article & Reply Request detection [https://github.com/cofacts/takedowns/issues/192]

---

- 找到一些訊息符合原本設想的 spam，但訊息應該要結合送出頻率才能判斷是否是 spam
  - 真實使用者也會傳 spam [name=nonumpa]
  - 但有些人會隔一年傳那一類的
    - 也無法排除是正常使用者 [name=mrorz]
- 感覺要把訊息放在一起看，偵測機制會變麻煩 [name=mrorz]
  - Reply request & reply 要判斷頻率嗎 [name=nonumpa]
  - 現在停的好像只有 article，主要會誤判的大多是 article [name=mrorz]
  - 之前有遇到使用者誤用，在 reply 與 reply request 貼 spam，但只有一次[name=nonumpa]
  - 那所有偵測都判斷發文頻率，實作也比較乾淨 [name=mrorz]
- 在 cofacts/takedown 開票追蹤：take frequency into account when detecting spam 


### [Comm] Cofacts.ai

New initialtive - https://g0v.hackmd.io/mU8qi721RZeAQ9PDfj7XRA?view#Cofactsai

- Tim: 跟 UI 設計、核心功能有哪些需要更新
- 完整功能查到一個段落之後，可以用個按鈕送到 cofacts.tw
- 現在 deep research 太長 [name=bil]
- 可以預覽 + 再縮短，system prompt 可以設計 [name=mrorz]
- 可能要限制字數 [name=Tim]
- 開放的時候會有個 cofacts.tw 會外連到 cofacts.ai。如果做成客服視窗那種會不會比較能對應到 cofacts 原本的內容 [name=Tim]
  - 我自己發現我在查核的時候，幾乎不會回到 cofacts.tw 看，會很專心在對話視窗 [name=mrorz]
  - 可以把類似訊息、現有回應等都載入 agent
- 是否要揭露是 cofacts.ai 寫的 [name=Tim]
  - 我目前 tend to 不要顯示，因為我希望使用者付全責，等於是使用者認可這裡的每一個字都是自己嘴巴講出來這樣 [name=mrorz]

---

- 不太喜歡式窗型，對話需要比較多空間 [name=bil]
- 因為人都要看過。cofacts.ai 提供靈感。看過文字的人對文字負責。[name=bil]
  - 至於要不要顯示這是 cofacts.ai 鑄造出來的，可寫可不寫。[name=bil]

---


### [Op] API access management

https://g0v.hackmd.io/@cofacts/rd/%2F51wwLHgvSUqtBDaP-yAVnA

- 發現沒被 cloudflare 管理的流量，會一直觸發 graphql IntrospectionQuery 不過他們是每天固定在打，應該不是這次壞掉的主因 [name=nonumpa]
  - cofacts-api.g0v.tw 等 g0v domain 沒辦法被 Cloudflare 管理，因為那是 g0v 的
- Review Rollout plan
- 做到 step 2?
  - OK

## Langfuse Clickhouse follow-up

- Langfuse trace 列表會一直噴 error [name=mrorz]
    - server log: ServerErrorHandler: Poco::Exception. Code: 1000, e.code() = 0, No thread available, Stack trace
    - `max_connections` 從 16 --> 64 有改善


## Open165
- 還沒畫圖 [name=mrorz]


### Google Cloud 來信要求升級 Gemini
- 我們用 gemini-1.5-pro-002 可以到 9/24
- Gemini 最近版本出很勤，覺得可以再等
![](https://g0v.hackmd.io/_uploads/rkxPw8koggg.png)


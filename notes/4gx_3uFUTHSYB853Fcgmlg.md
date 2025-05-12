---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250512 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO Hub:
- 線上出席：
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

### [Comm] Cofacts.ai

New initialtive - https://g0v.hackmd.io/mU8qi721RZeAQ9PDfj7XRA?view#Cofactsai


### [Op] API access management

https://g0v.hackmd.io/@cofacts/rd/%2F51wwLHgvSUqtBDaP-yAVnA

- Review Rollout plan
- 做到 step 2?

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


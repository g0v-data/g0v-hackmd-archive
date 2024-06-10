---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240610 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, mrorz, nonumpa
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## CCPRIP

### [Infra] 檢視防火牆規則

#### 目前規則

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e7dfdb10577001b860d88b8f062ccb7b.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_51c64f6b85e3c37c23d04c80a3bd0f37.png)


#### Security events

僅有一次 DDoS
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_be075d7b30ff19b71dfbafcf0252afce.png)

- Baseline: 2024/6/10 早上的 sample, 每小時 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a0c654fcc2b5f36367f9cc66356cabce.png)
  - 400K/5hr, 80K requests per hour
- 6/10 13:40-13:55 DDoS https://drive.google.com/file/d/1zj1MrNvPqfxo-YNwFZINftXa7v2-q6n9/view?usp=drive_link
  - Security events: DDoS 4.03M ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7accd5cb97cd229de87af3f19ebe9004.png)
  - 目標：cofacts.tw/article/J4KgxI8B3RbBUEe2bmFt 等三個投資詐騙
  - 被什麼擋下
    - HTTP requests from known botnet (signature #1): 4M
    - Visiting certain page: 0.1M
    - Challenge foreign non-bot access: 0.029M

#### SEO 影響

尚無
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d90b68beb757ea5ebe32d538f8feef87.png)

### [Comm] Community builder 濾掉詐騙

- https://cofacts.github.io/community-builder/#/editorworks 很多詐騙
- ListReplies 的 reply 上沒有 status，只有 articleReply 上有 status [name=mrorz]
- 但可以讓 blocked user 或 reply 的外觀跟其他不一樣 [name=mrorz]

## Hackmd 會議紀錄查找 / dify 研究

- 目前：google custom search, 只有發佈到網路的內容
- https://github.com/cofacts/hackmd-sync
  - bun: 方便寫 typescript script
  - 有些 hackmd 載不下來，error handling
  - dify 內建 knowledge 需要其他調校
    - 限 20 個檔案
  - https://udify.app/chat/jx7VIMgk9Q7QdzJU

## 傳播學會
http://www.tcataiwan.org/newdetail.asp?WN_ID=1764

> 一個攤位將提供「1張長桌、2-3張椅子、1面海報架」供貴單位使用，同時現場可以有募款或銷售商品之行為。
> 建議貴單位可以在8:00-8:30分左右到場準備，在17:00左右結束。主要的人潮會在休息時間、中午、當日結束離場時

- 只去週六、週日
- 印製傳單
- 週六、週日
- 活動到週一但不會去

## 六月開會

- 6/17, 6/24 都是線上會議


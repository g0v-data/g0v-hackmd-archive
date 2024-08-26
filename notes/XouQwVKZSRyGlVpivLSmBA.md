---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240826 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO Hub: bil, 正儒, mrorz
- 線上出席：4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::


## Release
### To be reviewed

rumors-api GraphiQL 
https://github.com/cofacts/rumors-api/pull/343

:::success
PR review, merge and release
:::

## 活動

- 開源季
  - 9/14 (六) 12:00 ~ 22:00 @ Pipe Live Music
  - 可跟揪松併攤
- 9/29 (日) 大松 in 新店

## Open165

### 設計

tofus 全襯線/明體設計
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0f7b9e06b307e7a20fddeb892d473c1a.png =x400)
https://github.com/cofacts/open165/pull/23

> 其實我會想要把某些字，例如說「是詐騙」之類的重點字，用[螢光筆的方式](https://max.hn/thoughts/how-to-create-a-highlighter-marker-effect-in-css)呈現
配上襯線，會很有筆記感
>
> 然後螢光筆、襯線的筆記感
> 會讓我覺得，要不要整個網站改叫做「Open 165 防詐筆記」
> 可能會比現在冷冰冰的防詐資訊站好
> [name=mrorz]

> 好哇
> 我可以幫忙想一下視覺
> 感覺也很適合 cofact 黃？
> [name=tofus]

> 不過可能要注意 Cofacts 黃
> 和白色與黑色的對比都略顯不足，不知道怎麼辦
> [name=mrorz]

> 我可以幫忙找新的色盤，不過因為我發現在別人的檔案裡我不能用專業版的功能（比方說串 library 之類的 qq
> [name=tofus]

> 防詐筆記
> 很適合再加一兩句 溫馨副標 
> [name=chewei]
> 

:::success
專案改名 Open165 防詐筆記
:::

---

### Update DB
> https://github.com/cofacts/open165/pull/24

- 連 `curl` 都會被擋，大概是內政部有擋 IP
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_13c74e370acb70e42ec4b28e18ca3432.png)
- 正在嘗試從 Cloud Run 在台灣開 job 跑，但比較難測試

## CCPRIP

Chatbot long request handling https://github.com/cofacts/rumors-line-bot/issues/395
Blocks LLM-based transcript

---

Pick up 垃圾訊息反制 schema change
https://g0v.hackmd.io/@cofacts/meetings/%2F8arYsE5dQuu6Io82CVVSZg

## 檢舉處理

> https://cofacts.tw/article/13cpj45zy2qq3 
> 這是在學習如何用網站不會被加黑名單嗎 :laughing:
> [name=cai]

:::success
在 slack cai 的原串下討論
看 userid, 註冊用帳號等資訊
:::

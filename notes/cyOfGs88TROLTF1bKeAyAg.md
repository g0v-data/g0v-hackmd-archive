---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240408 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: rumors-line-bot

- https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20240406

### :rocket: Staging

#### :globe_with_meridians: Site

https://github.com/cofacts/rumors-site/pull/567

##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [ ] Links to MyGoPen and votes work

### :eye: Under review

## CCPRIP
### [Op] Transcript spam
> nonumpa
> https://g0v.hackmd.io/vKCvrqSQTlm7GEx9MAXGaw?view#op-Transcript-spam-處理
> 

Deploy process
> Scripts: https://github.com/cofacts/collab-server/pull/7
- [x] rumors-db schema update
- [ ] rumors-api populate new contributors
- [ ] migration script

Spam 案例
- User ID `96TY4n0BnX5-aOa4OpAo`
    - https://cofacts.tw/article/opw6J44BBMtPEaE0GCyM
    - https://cofacts.tw/article/mpw2J44BBMtPEaE09ixl
- User ID ???
    - https://cofacts.tw/article/5JzRIY4BBMtPEaE0BBcn

## 謠言惑眾獎

> Previous plan https://g0v.hackmd.io/dBog_HZ2TBuXjRxuJNrV-Q#%E8%AC%A0%E8%A8%80%E6%83%91%E7%9C%BE%E7%8D%8E

- 前次收錄票數：2.7K
- 本次收錄票數：截至 4/8 14:35 為 1.4k (Cofacts 0.4k, MGP 1k)
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7d85aab5dae73ac11c4dc2e241d66df5.png)
- 週二推一波？
    - 回覆率 60% 計，希望多 1K 票 = 點擊數須為 1.7K
    - Cofacts 推播 CTR [計算](https://docs.google.com/spreadsheets/d/1XjEQZ9esNKfkGd8XYd1p3E8DTgB0f5QPDl5ghf-JxE0/edit#gid=0)： Click / Delivered ~= 1%
    - 故推播到 170K 人，可得 1.7K Click、1K 完成問卷
    - 170K 人
        - 雙北 + 台南 + 高雄, or
        - 全部去掉雙北、台南


### 已實施
- iframe LIFF https://cofacts.tw/mgp
- LINE bot 最後顯示 quick reply 連到活動頁面 (週六開始)
- VOOM 貼文
- FB 貼文
- FB 活動 ＋ 邀請好友
- FB 上 tag 追蹤者

## 2024/4/3 Downtime

09:31 網站無法存取

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fc776464c26fae1f4a2aa4f23402df0b.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d92b79f881ff1668d5ef703dd540144e.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b4a297f588bdef9adba76d75bec75bd0.png)

09:41 重開 rumors-site 後解除
- crontab 網站從每小時重開，調整為每 30min 重開

## 逐字稿 429 error

> Logs: https://g0v.hackmd.io/i3DlTDBcRkahYOmTwcQ2hQ#%E9%80%90%E5%AD%97%E7%A8%BF-Error-429-%E5%95%8F%E9%A1%8C

待修 article: 約 120 則

```
query {
  ListArticles(
  	filter: {
      articleTypes: [VIDEO, AUDIO]
      createdAt: {
        GTE: "2024-03-26T22:00:00.000Z",
        LTE: "2024-03-30T16:00:00.000Z"
      }
    }
    orderBy: [
      {createdAt: ASC}
    ]
    first: 120
  ) {
    edges {
      cursor
      node {
        createdAt
        text
      }
    }
    totalCount
  }
}
```

- 這次想使用 WhisperX
https://g0v.hackmd.io/wkx286lmTDaFUpgRhnUawQ#WhisperX-on-replicate
    - Or 直接寫在 rumors-api 做成 script，之後還能重複使用？ 


## 國際交流

- https://nestmongolia.org/ on use of AI

## Issue discussion 

https://github.com/cofacts/rumors-site/issues/548


---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240401 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO Hub 出席：bil, mrorz, nonumpa
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: rumors-line-bot

宣傳用 URL: https://cofacts.tw/mgp
- 背後導向目標 LIFF URL： https://liff.line.me/1563196602-R1zEXaDB?p=mgp （若無登入則自動登入）

### :eye: Under review
- https://github.com/cofacts/collab-server

## CCPRIP
### [Op] Transcript spam
> nonumpa
> https://g0v.hackmd.io/vKCvrqSQTlm7GEx9MAXGaw?view#op-Transcript-spam-處理
> 

Deploy order
1. rumors-db schema update
2. rumors-api populate new contributors
3. migration script
  - 時間比較長
  - 但應該不用下線跑，因為很少有兩個人會同時編輯逐字稿 [name=nonumpa]
  - Update-by-query 容易有 conflict，所以寫成有 conflict 也繼續做 [name=nonumpa]

---
- 有發現好像還是有 snapshot 變成 unknown user，今年 2 月也還有，但數量不多 [name=nonumpa]
  - 理論上是去年 9 月就開始記錄 userid，可能是 yjs 自己的 bug
  - yjs yDoc 的歷史紀錄會有 client id --> userMap
  - 但有時候 userMap 裡面沒有那筆 client id，記錄寫說被 gc 了
  - UI 上面會顯示為 unknown user
  - 但因為很少人貢獻，回去看 userMap 只有一個 user，那就對得回 unknown user
  - 無法 reproduce
  - 但未來因為會另外紀錄貢獻，所以 yjs 裡面的就不會那麼重要 [name=nonumpa]

:::spoiler 這次對 staging 跑的
- 要用 nodejs 16 or 舊版的 18 才能跑，否則 ts-node 會[認不得 ts file (?)](https://github.com/TypeStrong/ts-node/issues/1997) [name=mrorz]
- 可能是因為本機 ssh tunnel 所以比較長，使得 update_by_query 會 timeout
- 實際 migrate 時會需要留意 error article 與其他 error

```
{
  "name": "TimeoutError",
  "meta": {
    "body": null,
    "statusCode": null,
    "headers": null,
    "warnings": null,
    "meta": {
      "context": null,
      "request": {
        "params": {
          "method": "POST",
          "path": "/articles/doc/_update_by_query",
          "body": "{\"script\":{\"lang\":\"painless\",\"source\":\"\\n            if (ctx._source.contributors === null) {\\n              ctx._source.contributors = new ArrayList();\\n            } else {\\n              ctx.op = 'noop';\\n            }\\n          \"}}",
          "querystring": "refresh=true&conflicts=proceed",
          "headers": {
            "User-Agent": "elasticsearch-js/6.8.8 (darwin 22.6.0-x64; Node.js v16.15.0)",
            "Content-Type": "application/json",
            "Content-Length": "236"
          },
          "timeout": 30000
        },
        "options": {
          "warnings": null
        },
        "id": 1
      },
      "name": "elasticsearch-js",
      "connection": {
        "url": "http://localhost:62222/",
        "id": "http://localhost:62222/",
        "headers": {},
        "deadCount": 4,
        "resurrectTimeout": 1711974684689,
        "_openRequests": 0,
        "status": "dead",
        "roles": {
          "master": true,
          "data": true,
          "ingest": true,
          "ml": false
        }
      },
      "attempts": 3,
      "aborted": false
    }
  }
}
unknown user in article:  FJSQ1ooBXtQmmeroVHki
unknown user in article:  ukcBUYcB800gity8EwLj
unknown user in article:  ukcBUYcB800gity8EwLj
unknown user in article:  ukcBUYcB800gity8EwLj
unknown user in article:  ukcBUYcB800gity8EwLj
unknown user in article:  ukcBUYcB800gity8EwLj
unknown user in article:  n0dbKIcB800gity8EQI1
unknown user in article:  qJSNzowBXtQmmerocXmd
unknown user in article:  GZSX1ooBXtQmmero-Xkk
88 / 88 Processed
usersMap:  Map(26) {
  'Evan Hsieh' => 'wClSOYkBFLWd9xY2KE4f',
  '林佳蓉' => 'mM9kSYoBrkRFoI6rN9b5',
  'Ronny Wang' => 'AWAPsV_qyCdS-nWhukFi',
  'LTSC1980' => 'AV48v7rkyCdS-nWhufRY',
  'murmur' => 'T93YInMBb3SlMKoAuqZi',
  'E' => 'xPyH-IYBC7Q3lHuU6oTY',
  'Eli' => 'wSlSOYkBFLWd9xY2NU6Y',
  '4000' => 'cjrfjGQBbZnN2I-EuZh1',
  'Dennis Bowden' => 'PilTJYkBFLWd9xY2fDqI',
  'MrOrz' => 'AVqVwjqQyrDaTqlmmp_a',
  '林倖君' => 'PinFP4kBFLWd9xY2flbd',
  'Ang Wang' => '4UKNBHoBgBgcuemXohpl',
  '米露露' => '71TdLoIBZ4FY5vnANQvs',
  'Chill' => 'GCkMmokBFLWd9xY2B7Z4',
  '鍾Bibby' => '_FTiLoIBZ4FY5vnATwsJ',
  '真師傅' => 'MM_iXooBrkRFoI6rLedW',
  'Amos Li' => 'Z2rdW4gBvEj1WkaUFatK',
  '壽司' => 'q4saVYQBv5it-Cx_isiF',
  '楊不悔' => 'js8xZYoBrkRFoI6rjelx',
  '雨莉吳' => 'nCnuOYkBFLWd9xY25k9F',
  '陳薇仲' => 'vClQOYkBFLWd9xY2VE4U',
  'Sarah Elliot' => 'PilXIYkBFLWd9xY2ozZF',
  'Lin Yu Xuan' => 'xiHzi4oBZifh7hHIVlIs',
  'Lin' => 'AVriAlOoyrDaTqlmmqhC',
  'NX' => 'iEJ5C3oBgBgcuemXUCAD',
  '邊緣人' => 'AWA_PbObyCdS-nWhukq-'
}
errorArticles:  [
  'FJSQ1ooBXtQmmeroVHki',
  'ukcBUYcB800gity8EwLj',
  'n0dbKIcB800gity8EQI1',
  'qJSNzowBXtQmmerocXmd',
  'GZSX1ooBXtQmmero-Xkk'
]
```
:::
## 謠言惑眾獎

> Previous plan https://g0v.hackmd.io/dBog_HZ2TBuXjRxuJNrV-Q#%E8%AC%A0%E8%A8%80%E6%83%91%E7%9C%BE%E7%8D%8E

```
🎁謠言惑眾獎・票選年度謠言拿禮物🎁

昨天的愚人節大家過得如何呢？
今天 4/2 是國際事實查核日，Cofacts 真的假的、 Mygopen 與假新聞清潔劑 FakeNewsCleaner 邀請您一起來票選去年最有代表性的謠言唷！
即日起至 2024/4/12，可以到 Cofacts 的 LINE 帳號參與投票。完成投票者可以獲得 Whoscall 進階版一個月的免費序號（送完為止），還有機會獲得贊助廠商的抽獎贈品唷 🎁

ℹ️ 活動詳情：https://www.mygopen.com/p/award_22.html
🗳️ 用 LINE 在 Cofacts 投票：https://cofacts.tw/mgp
（一人可在 Cofacts 與 MyGoPen 的 LINE 帳號各投一次唷！）
```

- MGP 主視覺（方形圖）![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8d483ba6a5dfa1b2d83e47bc137529d3.jpg)
- [x] Facebook 粉專 + Group + IG 貼文 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f86bdc8cb79e49a5dc9652a7947922fa.png)
- [x] LINE Voom 貼文 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4a6309ab902f0c6c8959f6093ffc2323.png)
- [x] LINE rich menu ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c3a03f1b0c67140b9b462e488fe725a5.png)
- [x] LINE Welcome message
  ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1789198b8515512c79917a007e0c56c2.png)


## 逐字稿 Error 429 問題

> 3/27 後影片沒有 AI 逐字稿的機率變高了
> https://cofacts.tw/article/5xCwgI4B0DEb0v6cXOgH
> https://cofacts.tw/article/KBD7go4B0DEb0v6ceevv
> [name=cai++]

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_53b05825398d73ebf2aae203cbc70da0.png)

- 3/25 Open AI 指出 You will need to pre-purchase credits to use the API.
- 3/25 OpenAI 回報 "The most recent attempt to charge your payment method failed, so auto-recharge has been disabled."
- 後來 Credit 好像變負的
- 3/27-30 的逐字稿狀況： ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2a36963b71758cdfd29beef4af174a61.png) ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_30698e45a7f2c8eec065d42c5f08f1b4.png)
- 3/30 手動付款 $30 並重新設定 auto recharge
- 遭遇問題的 article: TBA，用 API 框範圍來查

## Google workspace for non-profit

- 開 gmail、關 cloudflare 轉送 cofacts.tw 信件
- *@cofacts.org 已經會送進 gmail
- 開了 hi 的 Google group，啟動後 hi 跟 cofacts google group 會分家

## 四月開會時程
> Previous plan: https://g0v.hackmd.io/nJJJFw36RaWFJ4cUycgihA#%E5%9B%9B%E6%9C%88%E9%96%8B%E6%9C%83

- 4/15 --> 4/14 (日) 8pm
- 4/29 --> 希望換到 5/3 (五) [name=bil]




---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20230614 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：nonumpa
- Workis: bil, Dennis, Max, Mariah
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
- Fix logging https://github.com/cofacts/rumors-api/releases/tag/release/20230614

### :eye: Under review

- Rewriting opendata generation code to use less memory https://github.com/cofacts/opendata/pull/22


## Incident: docker loop device full

- Impact
  - Can create new image article, but no image file is saved
  - Cannot create video articles at all ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1a295fcb22118ca456ac0049d96b6902.png =x200)
- Impacted time range: 2023/06/13 05:55 - 19:18
- Root cause:
  1. We enabled API logging that logs a lot of information a few weeks ago
  2. `pm2` actually writes log files in `~/.pm2/logs`
  3. The log fills up the docker container's device mapper volume (9GB) ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_eede5ac01eee0a012c61142f764f0c67.png =x150)
  4. Google API client cannot write temp file during upload, thus causing error ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b96472fb5978eda9f5268fa3fc9d6018.png =x250)
- Articles with empty images: https://docs.google.com/spreadsheets/d/1Ua0KcXJgesOJDkNjV6Olrixv0zz6IiyDR-fQTy5nVcQ/edit?usp=drivesdk
  - All images are restored via the newly deployed `replaceMedia` script with `--force` option.
- Fix: https://github.com/cofacts/rumors-api/pull/306/files
  - Disables pm2 log files; logs are still write to stdin and recorded by docker / AWS cloudwatch
  - add flag `--force` to `replaceMedia` so that it works on articles that does not successfully writes files.

## CCPRIP

### [Comm] Crowd transcript

> https://g0v.hackmd.io/@cofacts/rd/%2FOhGIQzoxR5eF6audQuS_FQ
> [name=nonumpa]

#### site 
[PR - draft](
https://github.com/cofacts/rumors-site/pull/539)
collab editor 需要有圖片的 api esdata 測試一下

#### collab-server

[PR1](https://github.com/cofacts/collab-server/pull/1) 
修正 review 的東西

[PR2 - draft](https://github.com/cofacts/collab-server/pull/2)
把使用者編輯的 transcript 存到 article.text，需要有圖片的 api esdata 測試一下
- What does [schema.js](https://github.com/cofacts/collab-server/blob/d6c25028eb45ac69588231e01cdc46e61770f3ba/hocuspocus-extension-elasticsearch/src/schema.js) do? [name=orz]

#### rumors-db
https://github.com/cofacts/rumors-db/pull/64
跟其他 table 一樣，也做個版本管理
- ydoc 是 binary 還是字串呀? binary 好像要[多做 base64 encode / decode](https://www.elastic.co/guide/en/elasticsearch/reference/current/binary.html) [name=orz]
  - Ans: yes it is a binary


### [Comm] AI reply
- Azure OpenAI https://m.facebook.com/story.php?story_fbid=pfbid033AYEdvFvE6ge4AnRLCQ3Ubw28KS2j9dR5W1bKUqb8KeVramJQZt1e4tDjrzKeQ2zl&id=100064118048318&mibextid=Nif5oz
- ChatGPT 3.5 updates: API, larger context https://openai.com/blog/function-calling-and-other-api-updates


### [infra] Cloudflare Project Galileo

> From RightsCon

- 聊的對象是 enterprise solution sales
- Project Galileo 主要開給大型 NGO，東亞東南亞比較少
- 可以考慮跟 partner 聊聊 https://www.cloudflare.com/galileo/ 但程序他們 sales 也不熟
- 如果需要更高級的防護，可以考慮升級 Pro subscription https://www.cloudflare.com/zh-tw/plans/ 
- Project Galileo 也主要是升級到 business 方案，比較不會到 enterprise 方案


### [infra][op] API management

- Research doc: https://g0v.hackmd.io/@cofacts/rd/%2F51wwLHgvSUqtBDaP-yAVnA
  - Updates to Cloudflare zero trust goes [here](https://g0v.hackmd.io/51wwLHgvSUqtBDaP-yAVnA#Alternative-Implement-using-Cloudflare-Zero-Trust)
- Design doc: https://g0v.hackmd.io/@cofacts/rd/%2Fj27XFAQ0R0Cuqi2jDLJuWw
  - Not updated yet
- recruit engineer ? 7 月底以前要找到人做 3 個月 [name=bil]
  - Yes [name=mrorz]
  - Usage logging
  - Detailed access control on service tokens
  - Site, community builder 發 request 不能把 token 露出

### [Op] 分身帳號處理
https://g0v.hackmd.io/ndNDmEkiSHyTRMOEIy2q2Q?view#IP-investigation （Cofacts workspace owner only）
- 6/7 noon starts IP logging; observed on 6/8.
- Multi-account handling: CoC or terms of use?

:::success
寄信通知詢問開多帳號的原因
:::

## 小聚籌備

時間：7/29（六）：coscup
暫定 7/9 (日) or 7/8
本週六場勘
https://cofacts.kktix.cc/events/cofactseditor36

:::success
First contact 小胖
:::

## 7/1 大松

- Job description for API management [name=mrorz]
- Hugging face dataset user feedback [name=mrorz]
- 計時 & pitch [name=Dennis, Mariah]


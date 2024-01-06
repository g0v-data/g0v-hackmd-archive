---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20230131 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- workis 出席：bil, mrorz
- 線上出席：nonumpa, 4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
- Modify media API script https://github.com/cofacts/rumors-api/releases/tag/release%2F20230121

#### :busts_in_silhouette: Community builder
- API status page https://github.com/cofacts/community-builder/pull/16
  - [URL sample](https://cofacts.github.io/community-builder/#/stats?@$createdAt$GTE=now-2M;;&$createdAt$GTE=now-2M;&articleTypes@=VIDEO;;&$createdAt$GTE=now-2M;&articleTypes@=IMAGE)

### :rocket: Staging

#### :globe_with_meridians: Site
##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [x] Article list
  - [x] Filter works
  - [x] Sorting works
  - [x] Can go to article page
- [x] Replies list
  - [x] Filter works
    - [x] 不允許選擇 Replied by me
  - [x] Sorting works
  - [x] Can go to article page
  - [x] 不允許 upvote / downvote replies
  - [x] Can see vote reasons
- [x] Hoax for you
  - [x] Filter works
  - [x] Can go to article page
- [x] Article detail
  - [x] Can see similar messages
  - [x] Cannot submit, upvote, downvote reply request
  - [x] Cannot submit, upvote, downvote reply
  - [x] Cannot add, remove, upvote, downvote category
- [ ] Search
  - [ ] Can use global search to perform search
  - [ ] Can use textarea in header to perform searchs
     - Known issue: firefox 無法
  - [x] Can list searched articles
    - [x] Filter works
    - [x] Can go to article page
  - [x] Can list searched replies

登入自有帳號後檢測：
- [x] Replies search page
  - [x] can upvote / downvote replies
- [x] Replies list
  - [x] 可選擇 Replied by me
  - [x] can upvote / downvote replies
- [x] Article detail
  - [x] Can submit, upvote, downvote reply request
    - [x] Cannot upvote / downvote own reply request
  - [x] Can submit, remove own reply
  - [x] Can upvote, downvote other's article reply
  - [x] Can add, remove, upvote, downvote category
- [x] Can go to profile page on menu
    - [x] Can edit own name, bio, URL
    - [x] Can see own replies
- [x] Can logout

##### ⛔️ Release Blockers

##### 未竟項目


### :eye: Under review

#### :electric_plug: API
- Block spammer's articles https://github.com/cofacts/rumors-api/pull/295

#### :globe_with_meridians: Site

- Block spam articles https://github.com/cofacts/rumors-site/pull/523
- Hide reply request with score <= 0 for anonymous users https://github.com/cofacts/rumors-site/pull/524
- Typescript support https://github.com/cofacts/rumors-site/pull/500


## CCPRIP

### [Infra] Chatbot 穩定度

#### Errors
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4a02e66ed1b652b50aba83c4f79f6535.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_eabcca2cf07fa7e94b5e03752a1a22a8.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5694b18d623102ba95f7c640a570ee6d.png)


樣態都是 request_timeout
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_af2313b70e34291ebcca071b3b607fa2.png)

#### Investigation

- 是 1/21 API deploy 的關係嗎
  - 看 code change 不像⋯⋯ https://github.com/cofacts/rumors-api/releases/tag/release%2F20230121
- Server load
  - 下午 error 發生時有看過，load 正常（2~4），memory 也還有 [name=mrorz]
- API 被呼叫的次數？

#### Mitigation

### [Op] Anti-SEO spam

:::info
https://g0v.hackmd.io/XBJS-KEtScWyVCuQ9P_iNQ#M2-Script-for-setting-article-status
:::

- M2, M3 complete
- 整理可疑的帳號，下週討論

### [Comm] Crowd-sourced transcript

- [Collaborative editing](https://github.com/orgs/cofacts/projects/11?pane=issue&itemId=17843103) [name=nonumpa]
- **TipTap**
  - An editor toolkit integrates [**yjs**](https://github.com/yjs/yjs) to sync changes.
  - It works with any connection-oriented network protocol, which could be client/server (e.g. WebSocket), peer-to-peer (e.g. WebRTC), or entirely local (e.g. Bluetooth).
  - It's recommanded to use **WebSocket** because Webrtc doesn’t scale well for more than 100+ concurrent clients in the same document. 
  **Hocuspocus** is an official backend for Tiptap base on WebSocket and yjs.
- Firepad
  similar to TipTap, but [it's no longer under active development](https://github.com/FirebaseExtended/firepad#status)
- Automerge 
  is a CRDT implementation similar to yjs.
- Automerge vs yjs
  https://gitter.im/y-js/yjs?at=5d014e92049bf9263c5cdd5c
  - Yjs is more focused on shared editing
  - Automerge has more demo apps where state is shared to build some kind of application.
- **Hocuspocus + TipTap**
  - **Share client informations**
    https://tiptap.dev/hocuspocus/examples/awareness
    share whatever you like, for example a name, a color, the cursor position, or even a       position a 3D system
  - **Store document**
    Save to db through [onStoreDocument](https://tiptap.dev/hocuspocus/api/hooks/on-store-document) hook
    [debaunce](https://tiptap.dev/hocuspocus/api/configuration#debounce) defines the call of the onStoreDocument hook for the given amount of time in ms
  - `onAuthenticate` - https://tiptap.dev/hocuspocus/api/hooks/on-authenticate
  - History 存在哪
    - y.js 控制
    - 歷史紀錄要看 y.js 有沒有其他方式
    - tiptap 有歷史紀錄，但會與 y.js 的衝突，所以要停用 tiptap 的歷史紀錄
  - undo/redo
    uses yjs plugin that undo/redo local change
    https://github.com/ueberdosis/tiptap/blob/main/packages/extension-collaboration/src/collaboration.ts#L60

:::info
請 nonumpa 參考 https://g0v.hackmd.io/@cofacts/rd/%2FOhGIQzoxR5eF6audQuS_FQ 撰寫要改哪些地方的 design doc
（原 design doc 是以後版本複製前版本來設計的，可能不適用於即時共編）
:::

### [Comm] Discord

- 永久邀請連結：https://discord.gg/mmZS9sZuau
- URL preview 問題：og tag 沒設好
  - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6b06dc9e7cfa336167b7d86ce3dd6707.png)
  - og tag 好像要圖片才會正常運作
  - og tag 直接放謠言圖片 OK 嗎？文字跟影片怎麼辦？ [name=mrorz]
  - 學 dcard / github 把文字做成圖 [name=mrorz]
    - Github - https://github.blog/2021-06-22-framework-building-open-graph-images/
    - Vercel OG - https://vercel.com/blog/introducing-vercel-og-image-generation-fast-dynamic-social-card-images
- 在 FB 跟 Slack 宣布可以來 Discord 玩？[name=mrorz]
  - 沒公告 --> 好了
- Slack thread 好像完全不會送進 Discord

## GA4

- Research doc: https://g0v.hackmd.io/@cofacts/rd/%2FQRRlVa_URk-wT0QqahLN-w
- 網站 GTM 已掛好 GA4
  - 1/24 開始
  - 每個數字都不一樣⋯⋯ ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b282034b9fca03d11cc2c5f540c269a5.png)
  - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b3f2395af88cbae2ec1fb411ac0440b5.png)
  - BigQuery: intra-day events ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8e2bc4da5c484c5048509f52296bc719.png)
  - BigQuery: full day log ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2bef9a5562a3270d6583082f4775e457.png)
- Design doc: https://g0v.hackmd.io/cJFFXVzgT4OFT6bBLtulGg
  - Breakdown next week

## 色情 mitigation



## 會議時間

- 2/15 不行 [name=bil]
- 已經移動到 2/16 [name=mrorz]

:::success
維持週三，2/16 那週改週四
:::

## Upcoming events

- 2/11 大松
- 月底高雄小聚？

## 文宣
- https://www.figma.com/file/WbirxHjwl76NzorCaIGzBZ/Cofacts-文宣檔
 [name=豆腐] 
- https://drive.google.com/file/d/1akB_lj6hCiqxQtwxwMKb9_0_d8nzFcg_/view?usp=drivesd [name=Nick]
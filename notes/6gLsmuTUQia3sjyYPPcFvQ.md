---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20220803 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
  - Workis 出席：bil, mrorz
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :globe_with_meridians: Site

- https://github.com/cofacts/rumors-site/pull/499

##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [x] Article detail
  - [x] Can load and see analytics

##### ⛔️ Release Blockers

##### 未竟項目

- Mobile: shorten Cofacts translation https://dev.cofacts.tw/article/1kf4vrfen40rz ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f1574d9febec25b6c01def0bb152fd4f.png =x500)
- 改短：真的假的、美玉姨、防詐達人
- Sort: already sorted when we fetch data from Google analytics

### :eye: Under review

- https://github.com/cofacts/rumors-api/pull/
    - 實測 sync 2021/9 至今的資料，需時 404s
- https://github.com/cofacts/rumors-site/pull/499

## Image support
> https://github.com/orgs/cofacts/projects/9

- Documentation 還沒做（先處理下面資訊）

## Trend and contribution
> https://github.com/orgs/cofacts/projects/10

TODO:
- 改翻譯
- Code review
- Release
- All done!

## Youtube video processing exploration

https://g0v.hackmd.io/aJqHn8f5QGuBDLSMH_EinA?view#Videos-on-Youtube--links
- 可透過 schema.org microdata 從 HTML 中爬出 video duration、thumbnail (一張)、upload date、互動數、上傳作者等。
- 可以用在 youtube, rumble（不含作者）。tiktok 待查。

:::success
MrOrz
:::

Other topics
- 目前資料庫中的 youtube 影片數
  - youtube 
- 逐字稿與 youtube player 整合播放
- 參考 Invid 的截圖功能（484 只能用 extension？）
- 影片圖檔上下文（not for youtube）


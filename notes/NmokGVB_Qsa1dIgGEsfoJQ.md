---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20201021 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz, 宇彤, lucien, 斌綸, Paul, Cecil
:::

## Cofacts Next 追蹤

- RSS 教學
	- 上 Staging
	- Facebook 教學
	- RSS 使用率https://datastudio.google.com/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/hN8iB
	- 結案
- 推播
	- 推播數與使用率 https://datastudio.google.com/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/DtzfB
		- 沒有什麼人 block [name=mrorz]
		- 會 block 的還是會block ，可能是很久沒用然後都突然收到推播的那種 [name=nonumpa]
	- Facebook 教學
	- 結案
- User ID refactor
	- https://github.com/cofacts/rumors-api/pull/227
	- 結案
- Profile page
	- User page
	- Slug, edit photo API, description
- Landing page, 教學頁, final report
	- [x] 教學頁 [mobile design](https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=2011%3A0) done
    - [ ] 設計 final report
    - [ ] 實作
- [ ] 發文感謝斌綸的 highlight
	- improvement tickets https://github.com/cofacts/rumors-api/issues/229

## 大松

https://beta.hackfoldr.org/cofacts

- 協作頁面
- good first issues

## User ID refactor 上線

尚未執行
SOP 見 [1014 會議](https://g0v.hackmd.io/R3TffjwOSXefZBCFPkSrqA?both#User-ID-refactor-%E4%B8%8A%E7%B7%9A)

## :potable_water: Release pipeline

### :star: Released to production

#### :robot_face: LINE bot
https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20201017

#### :electric_plug: API
[DIFF](https://github.com/cofacts/rumors-api/compare/77f009788e5f011eb1a8acf7a56d5d1ebc5a6208...c678c946517685dd8b0a6764a0bd9af295a71def)

### :rocket: Staging

#### :globe_with_meridians: Site

##### Feature
- #351 New RSS UI
- #349 Reply page

##### Testing checklist

http://dev.cofacts.org/

**未登入**下檢測：

- [ ] Reply detail
  - [ ] Can see articles that has connected to this reply
  - [x] Can see similar replies
  - [x] Cannot submit, upvote, downvote reply

登入自有帳號後檢測：
- [ ] Article detail
  - [x] Can add new reply
  - [x] Can enter reply detial page for your new reply
- [ ] Reply detail
  - [x] Can upvote, downvote other's reply
  - [x] Can delete own reply from reply page
  - [x] After deleting own reply, it should show "deleted"

##### 未竟項目

- Reason dialog did not update accordingly 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a401fd49f321878316091ec8da0d8373.gif)


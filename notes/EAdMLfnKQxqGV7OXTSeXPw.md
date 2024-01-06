---
title: "vTaiwan.tw 前端架構"
tags: vTaiwan.tw, hackpad
---

# vTaiwan.tw 前端架構

> [點此觀看原始內容](https://g0v.hackpad.tw/SAG54HPVKK5)

上層：[vTaiwan.tw 行政院法規線上諮詢系統](https://g0v.hackpad.com/oWRxOF4ilfx)
> 2014/12/16 au&clkao first draft, to be reviewed by frontend team (ly/pm5/soidid)
> [name=Audrey T]

> 2014/12/30 reviewed, prototype to be verified 2015/1/6 morning by ey users
> [name=Audrey T]

> 2015/1/6 ey users reviewed & ok'd, [http://vtaiwan.tw/mockup/](http://vtaiwan.tw/mockup/) now reflects this design (in real time!).
> [name=Audrey T]


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_08445d09f75270006a1fd1d8fd75d41e)

### Social Object Mapping (Step 1)


GitBook <-> Discourse
- SUMMARY.md H1 = Discourse Category (e.g. "群眾募資")
    - Maybe: Turn README.md into pinned topic?
- Section.md H1 = Discourse Sub-Category (e.g. 發展需求)
    - Section.md H1+p(before first H2) = Discourse Topic (pinned 置頂文)
- Section.md H2 = Discourse Topic
    - (pre-populated with last paragraph?)

e.g. with [http://audreyt.gitbooks.io/vtaiwan-crowdfunding/content/1.html](http://audreyt.gitbooks.io/vtaiwan-crowdfunding/content/1.html) :
群眾募資 是 category，發展需求 是 sub-，股權模式或債權模式 是 topic，發言是回覆 topic

「未分類」討論的話，目前傾向於作為置頂文的回文，例如 [https://talk.vtaiwan.tw/t/topic/15](https://talk.vtaiwan.tw/t/topic/15) — 然後把權限設成這樣：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_28d3965d7363fae0a51f791295b6a26a)

### UX Ideas

- The left-side navigation panel collapses when user engages in the right-side comment discussions.
- User-selected annotation text becomes metadata of topical anchor for new posts within a topic.
-
### Notes

- Step 2 (react-ask) needs its own social object mapping, TBD.
- Step 3 (billlab) also needs its own social object mapping, TBD.


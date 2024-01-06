---
title: "Hackpad 搬家方案"
tags: hackpad
---

# Hackpad 搬家方案

> [點此觀看原始內容](https://g0v.hackpad.tw/INPcsSiqF8w)

- ===================
- 本 pad 已搬移至 [http://g0v.hackpad.tw/INPcsSiqF8w](http://g0v.hackpad.tw/INPcsSiqF8w)
- 詳情請見 ....
- ===================

- ===================
- 本 pad 已搬移至 [http://g0v.hackpad.tw/INPcsSiqF8w](http://g0v.hackpad.tw/INPcsSiqF8w)
- 詳情請見 ....
- ===================
-  comment test

### 搶救松共筆

[https://hackmd.io/EwU2GYDMDZoRgLTEpcCAsAOSBDBmBjOTBHEATgM3OAHYAjMSIA==?both](https://hackmd.io/EwU2GYDMDZoRgLTEpcCAsAOSBDBmBjOTBHEATgM3OAHYAjMSIA==?both)

### 起因

```
On July 19, 2017, Hackpad will be shut down.
https://g0v-tw.slack.com/files/acechen/F51H5CTFB/important\_information\_regarding\_your\_hackpad_account.txt

```
### 目標

盡可能讓多數使用者無痛轉移，並能兼容其他 NGO/NPO 需求。
> 預計要照顧到的 workspace：g0v, g0vus, ocf-tw, ... (待補)
> [name=AceChen]


### 需求

1.  多人同時編輯，任何人都可檢視
2.  嵌入表格、圖片，及基本排版功能
3.  作者標示(authorship)
4.  編輯紀錄(history)


## 近程

- 方案一：[whackpad](https://github.com/whackpad/whackpad) \- community fork of the Hackpad → [https://hackpad.tw](https://hackpad.tw)

    - [x] 匯出/匯入 Hackpad SQL：https://\[workspace\].hackpad.com/ep/admin/import-export
> 要怎麼處理 [https://hackpad.com](https://hackpad.com) 下面的 pad？下載的HTML會遺失 authorship
> [name=AceChen]

    - [ ] 下載過去上傳到 Hackpad 的圖片
    - [ ] 引導 g0ver 轉移到 [~https://pad.g0v.link/~](https://pad.g0v.link/) [https://](https://g0v.hackpad.tw)[g](https://g0v.hackpad.tw)[0](https://g0v.hackpad.tw)[v](https://g0v.hackpad.tw)[.hackpad.tw](https://g0v.hackpad.tw)
    - [x] 提供 Google/Facebook sign-in
    - [x] 依照註冊 Email 建立 authorship 對應
    - [ ] URL redirection: hackpad.com → hackpad.tw (Chrome extension?)
> 之後 hackpad.com 應該會被指向 paper.dropbox.com
> [name=AceChen]

> 也把 EtherCalc 和所有 pad 裡面全部的 g0v.hackpad.com 改到新網址？
> [name=AceChen]

    - [ ] 修復中文輸入bug
> 不知道這個容不容易？
> [name=chihao y]

    - [x] 註冊 hackpad.tw/ .io/ .club/ .space/ .site/ .link/ .gg/ ... 供其他社群使用？
> 可能會有trademark問題
> [name=AceChen]

> uspto [沒有找到 hackpad 的 trademark](https://search.uspto.gov/search?query=hackpad&op=Search&affiliate=web-sdmg-uspto.gov)
> [name=Audrey T]

> whackpad.tw/.io/... 也蠻幽默的 XD
> [name=chihao y]

    - [x] (community) 每個 workspace 跑一個 whackpad docker，subdomain 指向獨立 workspace
    - [x] (community) 提供使用者建立 workspace 並匯入 Hackpad SQL


- 方案二：[Dropbox Paper](https://www.dropbox.com/paper) \- 無痛官方[支援](https://www.dropbox.com/help/9156)
> 缺點？
> [name=AceChen]

> 社群繼續使用無法完全掌握的hosted service？
> [name=chihao y]

> 台北市政府（以下開放追加）擋dropbox
> [name=chihao y]

> 沒有 public workspace，記事無法設定完全開放編輯
> [name=Vdragon, Ｖ]

> 無法放在iframe裡面 -> hackfoldr沒辦法用？
> [name=chihao y]



- 方案三：[Google Docs](https://docs.google.com) \- 手動複製匯出/匯入，最多50人同時編輯同一份檔案
> <kiang> 經濟部連 google doc 都要特別申請才能使用
> [name=chihao y]

> 沒有明顯的作者標記(authorship)
> [name=AceChen]



- ~方案四：自行架設 Hackpad ~
> [查 Ronny 的講話](https://logbot.g0v.tw/channel/g0v.tw/2017-04-21#85) 可能會有難度 有原始碼 但是原設計的彈性並不夠
> [name=Rex T]

> 這個就是 whackpad，同方案一
> [name=AceChen]

> 自建hackpad(非whackpad) step by step教學：[http://jimmyb.ninja/post/1447447641](http://jimmyb.ninja/post/1447447641)
> [name=SCHsu01]



- 方案四：用「維基百科」那套Mediawiki系統
            （起因：參考了「維基醫學翻譯專題」的投票）
> 維基百科現在也有不必寫語法的編輯介面了，我覺得可以直接引進「維基百科」現成系統，不但功能強大，而且長期有人維護支援的系統，未嘗不是個好方向。（真的有人很喜歡寫語法的人，就可以讓他慢慢寫了）
> [name=Michael_Li]

> 可以用[Mediawiki.tw](https://Mediawiki.tw)的主機來建構，或者用[my-index.com](https://my-index.com) 這種google協作平台
> [name=陳柏諭]

> mediawiki 可以多人同時編輯，並且標示作者嗎？
> [name=AceChen]



## 中程

- 方案一：轉移到國產 open source 專案 [Hackmd](https://hackmd.io/)
    - [ ] 匯入 Hackpad SQL
    - [ ] workspace 功能
    - [ ] collection 功能
    - [ ] authorship 對應功能
> <最近被邀請參加一個演講的共筆協作，用的就是HackMD, 蠻好用的!
> [name=Lin,SF]

> [https://goo.gl/ZAiiJR](https://goo.gl/ZAiiJR) >
> [name=Lin,SF]


- 方案二：繼續開發 whackpad


## 遠程

- 分散式、去中心化(decentralized)共筆系統？
    - [https://cryptpad.fr/](https://cryptpad.fr/)
> :heart:
> [name=chihao y]





### 其他相關

[https://g0v.hackpad.com/Mh1LjzkizQf](https://g0v.hackpad.com/Mh1LjzkizQf)
[https://www.facebook.com/hackmdio](https://www.facebook.com/hackmdio)
[https://logbot.g0v.tw/channel/g0v.tw/2017-05-05/137](https://logbot.g0v.tw/channel/g0v.tw/2017-05-05/137)
[https://logbot.g0v.tw/channel/g0v.tw/2017-05-05/138](https://logbot.g0v.tw/channel/g0v.tw/2017-05-05/138)
[https://logbot.g0v.tw/channel/g0v.tw/2017-05-05/139](https://logbot.g0v.tw/channel/g0v.tw/2017-05-05/139)

### Hackpad 的幾個覺得重要的好處


- 有 workspace 功能
- 在 workspace 下任何 pad 修改，不管是多久以前的，都會自動：
    - email 通知訂閱的人（engage）
    - 移到 workspace 最上方（讓其他人知道最新的修改、哪些 pad 正在討論、哪些 pad 新增了）
- 看得到別人同時在寫（有共同編輯的感覺）
- 清楚的 authorship UI
- 白色部分可編輯（立刻上手）


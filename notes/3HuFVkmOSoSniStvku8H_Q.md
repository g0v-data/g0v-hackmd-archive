---
title: "公報自動化"
tags: 公報,hackpad
---

# 公報自動化

> [點此觀看原始內容](https://g0v.hackpad.tw/CULVn9DDzEU)


## 來龍去脈（想解決什麼問題）

靈感來源
    每週公報 & 每期(月)公報整理的時候需要耗費大量人力。
主旨
- 簡少公報編輯/整理時人力的浪費。
- 提供API給各種應用串接。

牽涉領域
> e.g.教育 / 環保 / 醫療 / 社福 / 核電 / 都市計畫 / 勞工權益 / 食品安全 ...（會變成專案 tag）
> [name=ET B]


現有類似專案
> 現成的是否可以直接使用？或者有什麼不足之處？國外是否有類似的專案可參考？
> [name=Chia-liang K]


相關組織單位
> e.g.公督盟/綠盟/司改會/苦勞網/泛科學...（會變成專案 tag）
> [name=ET B]


相關專案
> 衍生自某專案/衍生出某專案/API串接自某專案...etc.
> [name=ET B]

[Hackpad Converter](https://github.com/jessy1092/Hackpad-Converter)

授權方式
    CC-BY  、 MIT
> 程式碼部分（如 MIT/BSD）
> [name=ET B]

> 文件部分（如 CC-BY）
> [name=ET B]


使用資料
    每週公報
專案目前狀態
> 構想 / 規劃 / 雛形 / 實作
> [name=ET B]

    實作

## 目標與功能（要如何解決）

預定使用者
- 公報編輯人員
- 各專案人員
預定功能
- 簡化每期公報製作、提供API給各種應用串接。
使用方式
- ~每月第一週自動彙集前四周公報，產生每月公報，轉po到hackpad與tumblr上。~
- 月份公報中心 [https://moqups.com/jessy1092/U7Qmn93J/p:ad5095290](https://moqups.com/jessy1092/U7Qmn93J/p:ad5095290)
- 製作公報跑馬燈。 [http://g0v.tw](http://g0v.tw)

## 實做細節（非技術背景可跳填）


使用技術
- node.js
- [Hackpad API](https://hackpad.com/Hackpad-API-v1.0-k9bpcEeOo2Q)

- ~Java~
- [~Hackpad API~](https://hackpad.com/Hackpad-API-v1.0-k9bpcEeOo2Q)
- [~tumblr API~](http://www.tumblr.com/docs/en/api/v2)

協作工具
- github repo：
    - 每月公報：[https://github.com/jessy1092/AutoCommunique](https://github.com/jessy1092/AutoCommunique)
    - 公報API：[https://github.com/jessy1092/CommuniqueAPI](https://github.com/jessy1092/CommuniqueAPI)
- hackfoldr 工作資料夾網址：
- google drive 共用資料夾網址：
- google groups 討論群組：
- irc channel：

產出檔案格式
    html, hackpad, ~tumblr,~ json
> umm...目前想法是每期公報整理完之後 change to tumblr, 發佈。
> [name=lanfon]

> 或是由新聞中心發佈至 tumblr
> [name=lanfon]

> 標準HTML格式？（就像目前 irc log 一樣）
> [name=Michael_Li]


進度與 to-do
- [x] 公報所使用的 tag list
> 最佳解(?)是從專案中心撈...不過專案中心還沒出現(艸
> [name=lanfon]

> 另外會有類似詞指同一個分類(專案)的問題... 也許做一個主 tag 然後有相關的 子 tag 歸為同一類
> [name=lanfon]

> [公報規範](https://g0v.hackpad.com/JTSWsZHutsb)
> [name=Lee]

- [x] 每期公報分類的簡短介紹
> 初始想法見 [2013 年 8 月份公報](https://g0v.hackpad.tw/5yFP2C3hm3k) 已編完的(萌典、政誌...etc
> [name=lanfon]

> 在 tag list 能從專案中心撈之前應該會先由同一個( tag list的) hackpad 收集
> [name=lanfon]

> [月份公報各條目簡介](https://g0v.hackpad.com/Fe3VpeN42w9)
> [name=Lee]

- [x] hackpad 轉 post to tumblr, hackpad (或其他地方
> 這部份需要再討論，每期公報主要是對外發佈，因此「可能」還是會避免使用 hackpad ( 所以較有可能會轉到 tumblr 再由新聞中心發佈至FB/G+ )
> [name=lanfon]

- [x] Communique API
> 提供公報API，提供給各專案使用
> [name=Lee]

> [github](https://github.com/jessy1092/CommuniqueAPI)ex. [http://g0v-communique-api.herokuapp.com/api/1.0/entry/all](http://g0v-communique-api.herokuapp.com/api/1.0/entry/all)
> [name=Lee]

- [ ] irc log 的 filter
> this maybe undo. (((在 irc 上有討論關於 filter 的問題...
> [name=lanfon]

> 原始想法是簡化每週公報的製作
> [name=lanfon]

- [ ] 英文公報格式

## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）


測試公報: [201381925 ](https://g0v.hackpad.tw/FoG2qpiennh)  [201381218 ](https://g0v.hackpad.tw/obgBphEq1ur)
自動化產生公報 in hackpad: [公報自動化測試](https://g0v.hackpad.com/--2XCTDEMNQFH)
自動化產生公報 in tumblr: [http://jessy1092.tumblr.com/post/60939857626](http://jessy1092.tumblr.com/post/60939857626)

公報API: [http://g0v-communique-api.herokuapp.com/api/1.0/entry/all](http://g0v-communique-api.herokuapp.com/api/1.0/entry/all)

## 開發者


技術指導

分工與成員
- [ ] NeedsData: [lanfon](https://g0v.hackpad.tw/ep/profile/FhF2TCnIycW)  [Chun Wei Lee](https://g0v.hackpad.tw/ep/profile/v6ozRKwVLwr)  需要資料（擷取、清理）
- [ ] NeedsTech:  [Chun Wei Lee](https://g0v.hackpad.tw/ep/profile/v6ozRKwVLwr) 需要技術支援（程式、架站 etc)
- [ ] NeedsProcess: [lanfon](https://g0v.hackpad.tw/ep/profile/FhF2TCnIycW)  [Chun Wei Lee](https://g0v.hackpad.tw/ep/profile/v6ozRKwVLwr)  需要幫忙設計作業流程
> 設定成 project registry 中的 tags，需要幫忙的會自動 promote 到 g0v project hub
> [name=ET B]


## discuss

> 主要是自動彙整每一期公報，我覺得每天的公報還是需要人寫，不過有部分可以自動化
> [name=Lee]

> ex. 每個專案完成的issue自動可以通知，然後再整理在公報上這樣
> [name=Lee]

> 然後 四週的公報結束，到最後月報可以自動讀取四周內容，整理成你整理的那樣XD
> [name=Lee]

> 每月(期)公報目前主要的分類是以專案為分類，其實在 irc 上應該是可以從 log 中 parse 出關鍵字，這樣在整理每週(or 日)公報的時候速度上會比較快一點
> [name=lanfon]

> 前幾天有想到在 irc log 加上 filter ，本來是想說可以篩選出相關討論會比較好整理，不過如果(?) filter 不限定只能用在 ID 上的話，也許可以做為某專案討論的關鍵字查詢(這邊解釋的好像有點難懂0rz...)
> [name=lanfon]

> 我是想說，確定能做的就是每次公報的自動合併，在每天寫的時候增加tag，最後就依這些tag自動分類。
> [name=Lee]

> 其實在整理八月份公報的時候，主題是每個條目(?)都看過之後才分類出來的，昨天(今天早上?)在整理「未整理/無法分類」那部份的時候，有些條目其實是靠相關資訊去判斷...(像是tisa-map我本來以為是立院相關的，後來發現好像是服貿的...
> [name=lanfon]

> yep, 所以我的想法是，如果 irc log 可以做出 filter ( maybe we do this )，那也許可以請大家在討論的時候順手在對話框後 cc 專案名稱 or # 之類的 etc, 總之就是加個可以被 filter 濾到的關鍵字，那至少它可以先被自動加進當日的公報中，那在後續也許就不用每日整個重追 irc 靠人工的方式去篩，在每週(or..幾天後?)有閒再去比對 & 補充。 ( 這是 每週公報的 part )
> [name=lanfon]

> 我的意思是說相關的 tag , 像是服貿協議(專案)其實可以簡稱成「服貿」，或是立法院專案有時候可能會簡稱成立院之類的，這些專案的名稱來源是源自於 idea pool 之前或之後已經正在進行中或是被拿出來做的專案，所以才會有 tag（或是說會出現在 irc 上被討論 or 被寫進公報?）；因此 tags 的內容其實有一部份是「專案名稱」…但專案名稱也會有縮寫的問題，因此在公報加 tag 的時候，也許會需要一個 tag list 之類的東西，來避免指同一個專案但是用到不同的「表示」方式。 ok ya
> [name=lanfon]

> yes，跟我想的一樣，在每份公報前面(或哪裡)列個 tag list
> [name=Lee]

> tag list 的放置會有考量點
> [name=lanfon]

> 反正有共識是放 tag ， 最後每期公報依據 tag 分類，然後依據時間排序。
> [name=Lee]

> 有點覺得用 skype 之類的討論會比較快0rz
> [name=lanfon]

> 哈哈哈，應該在 irc 私人訊息聊就好XD
> [name=Lee]

> maybe 先看什麼做起來比較快的先完成(嗎?) 呣.......
> [name=lanfon]

> 我覺得在 hackpad 公開聊比較好... 大家都看得到 XDXD
> [name=ET B]

> 沒啦主要是 hackpad 要等對方打完字...(不然會亂碼...連嘸蝦米不用選字都無法避免0rz
> [name=lanfon]

> 不過這也許會是一個問題吧 囧…畢竟 g0v 的事還是比較傾向於公開討論 但在 irc 頻道上直接討論好像又有點洗板....0rz
> [name=lanfon]

> 也不是說要隱藏什麼秘密XD只是理由如上，哈哈哈，只是先討論好再打上hackpad。
> [name=Lee]




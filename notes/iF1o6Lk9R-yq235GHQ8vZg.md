---
title: "hackfoldr 災況資訊整合 SOP"
tags: 新手教學,saved,hackpad
---

# hackfoldr 災況資訊整合 SOP

> [點此觀看原始內容](https://g0v.hackpad.tw/QXHns2XZrIo)

這是各種 SOP 系列的其中一篇。若不會使用 hackfoldr 的話請參考==[使用說明](https://g0v.hackpad.tw/hackfoldr--b80fhUVlnBe)==。

使用時機請自行判定，~俗話說先搶先贏~....通常具有一定規模的災害情況，都有可能會需要。尤其是資訊很零散，事件又很緊急的時候。
簡單的判定方法：發現所有新聞台跳針的只播報該災害。

## 準備作業

**前置流程**
1.  在 irc 上討論並詢問意見。 (說不定有人已經先開好了 hackfoldr..
2.  確認有可能的資訊來源
3.  想個簡單好記的 hackfoldr 名稱，建立 hackfoldr
> 如果你還不會用 hackfoldr，請參考上方的==[使用說明](https://g0v.hackpad.com/hackfoldr--b80fhUVlnBe)==。
> [name=lanfon]

4.  編輯後台的基本資訊

**編輯提醒**
- hackfoldr 太長的話請善用短網址。
> 像是 bit.ly 之類的服務，簡短好記、可改名很重要。
> [name=lanfon]

- 有地圖的話請放在第一格。
    - 像是google 的 mapsengine 之類的，embed 話會像↓
    - mapsengine.google.com/map/embed?mid={ map_id }
- 順手上鎖
    - ethercalc 有 lock 功能，為了避免會進後台的人誤刪、故意刪、亂刪…etc，上鎖很重要
- 反序插入
    - 新的資料放置在最上方，較方便關心事件的人閱讀。
- 勤勞備份
    - 自動備份功能請洽 au...
    - 手動備份的方式可以參考 hackfoldr 的 [_使用說明_](https://g0v.hackpad.com/hackfoldr--b80fhUVlnBe)
- 不隨便留白
    - ethercalc 在多人編輯的情況下，很不方便刪除多餘的列(row)，因此「請不要隨地留白」
- 影片盡量用 embed 語法
    - youtube 的話請把 **watch?v=** 改成 embed/
    - ustream 的話點共用→迴紋針(取得連結)，把 **/channel/** 改成 /embed/

==**流量問題**==
這是一個慘痛的經驗... (0801高雄氣爆事件)
以往的後台(ethercalc.org)，在高流量的情況下都是鎖起來的(( like g0v.today(318), nonuke...etc
> g0v.today 會鎖是因為有人用 api 攻擊後台資料...
> [name=lanfon]

但 801 的情況是有大量鄉民在後台逗留跟編輯，造成 ethercalc 無法負荷，最後吐了 502 error。
```
\ 所謂流量可能看起來有點玄…總之如果可能編輯後台的人數非常多而且不間斷，請考慮使用替代方案。
\ ((為了整個 g0v 的 hackfoldr....

```
目前的解決方式是使用 google spreadsheets 的備案(使用方式參考[使用說明](https://g0v.hackpad.com/hackfoldr--b80fhUVlnBe#:h=使用-Google-Spreadsheet-管理-hackf))，
- 優點是：
    - 不會有流量問題(可以幫 au 省流量)
    - 前台無連結至後台(除非另外加)
    - 後台可以有管制編輯權限
    - 操作較近似 excel ，有中文、可以上色
    - 可以檢視修定版本記錄
- 缺點是：
    - 一開始讀取的速度，非--常--慢---
> 聽說[今天](http://logbot.g0v.tw/channel/g0v.tw/2014-08-01#791)一早村長修(?)好了.... 目前速度不會慢了!
> [name=lanfon]

    - hackfoldr 名稱不容易記(名稱 = spreadsheets id，通常是亂碼)
> 可搭配短網址如 bit.ly 服用
> [name=venev]

    - 不可以「留白」，每列(row)一定要有東西

## 散佈資訊

**發散**
- 把 hackfoldr 的網址散佈到可能關心事件的社群、討論區、PTT板中。
> 可以的話使用好記的短網址服務，例如 bit.ly
> [name=lanfon]

- 撐住第一波~鄉民DDoS~ 資訊海，然後著手整理。
**聚焦**
- 依事件的核心做分類(編成foldr)，例如志工、物資、災況、直播、影音、資訊回報區等。
- 若有現場地圖，務必放在第一頁。(會是打開hackfoldr第一眼看到的資訊)
> 若有針對事件產生的核心精神，可考慮取代地圖的位置(地圖改放第二頁)。 可參考 [g0v.today](http://g0v.today)
> [name=lanfon]

**維護**
- hackfoldr 有一定曝光度後，後台的編輯人數↑，維護的難度也會↑。
> 除了不熟悉 ethercalc 的編輯者外，也容易有想做亂的滋事份子XD
> [name=lanfon]

- 定時備份是一個很好的方式，自動備份的問題可洽 au 。
- 流量過大導致 ehtercalc 不穩定的話，可能需要轉成靜態或是定時更新。 (這部份也請洽 au
> 若是用 google spreadsheets 產生的 hackfoldr 比較不會有這個問題，但在**發散**的時期則會收到較少的資訊，google文件的編輯權控管會使得可編輯人數減少。
> [name=lanfon]

- 驗證資訊的來源
    - 這部份容易發生在**志工和物資**需求的部份，現場若沒有直播、管理中心(like 318)，容易造成關心事件的人一直想捐物資/當志工的情況。
    - 解決的方式是：先產生表單(google form)請他們填寫，若確認現場真的有需求時，再將收集到的資訊回傳給現場的窗口。
> 志工的部份需注意個資法的問題，建表單時需特別小心。
> [name=lanfon]

> 物資的部份可以請捐助者填寫能夠負荷的部份，及運送方式等；避免物資過剩，務必請對方不要先行購買(製作)。
> [name=lanfon]


## 事件檢討

這部份是發生在事件中(穩定) \- 結束後，通常會有一系列的檢討(討論/謾罵)文章出現。
> 大概就是一個把 hackfoldr 從 資訊集中地 打包成 事件懶人包 的概念。
> [name=lanfon]

**收歛**
- 在事件結束之前，可先針對相關的討論做個別的收集。(正反方)
> 這種時候通常需要的不是「這篇文章講得很中立」這件事，而是把有實質內容(討論/檢討型)的文章收集起來。
> [name=lanfon]

    - 可考慮另外開一個 spreadsheet 收集，或是直接在 hackfoldr 的最下方做收集。
    - 若有要收集報紙的專欄、專文等，可另外分類。
- 事件結束之後，請調整第一頁(landing page)的文章。
> 有考慮過放置 wiki 的條目，但似乎不太適合？
> [name=lanfon]

    - 第一頁最好能簡要描述完整事發經過。

## 救災模版

> pipi 在萌典松依人在高雄的公民記者的回報推的坑，形狀如下，歡迎跳坑建立 EtherCalc / Google Doc 模版
> [name=Audrey T]


第一層內容：
- UMap（OSM 在手機上比 Google Map 容易顯示）
- 公告（政府等，或像這次的即時 Google Doc）

分層內容模版：
- 人的 Foldr
    - 尋人、醫院、物資、志工
- 相關資訊
    - 電話、捐款、停班停課等
- 其他訊源
    - G8V、PTT、照片/影片...

## 補充資訊

> 討論可以寫在這(?)，**有任何想新加上去的東西也可以直接往上面編輯**。
> [name=lanfon]

> 噢噢像是一些蝙輯 ethercalc (hackfoldr 後台)的 tips 也請盡情補補補補補充....
> [name=lanfon]

> 以免大量鄉民入侵誤刪亂填隨便用....
> [name=lanfon]

> btw, 後台 link 的部份似乎可以放在spreadsheet 裡面 (自己 embed自己的感覺)，但不知道實做出來感覺如何(呃
> [name=lanfon]



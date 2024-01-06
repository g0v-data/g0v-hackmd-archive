---
title: "國會大代誌-完善議案追蹤"
tags: hackpad
---

# 國會大代誌-完善議案追蹤

> [點此觀看原始內容](https://g0v.hackpad.tw/iPNL16x8zdp)


提案題目：國會大代誌-完善議案追蹤

提案內容：
- [x] 架 api.ly
- [x] 了解 api.ly 的架構
```
calendar 對應 議程：同一時間可以有數個會議(不同地點)，同一個會議可以在不同時間開
sitting 對應 會議，一個會議可以有數個議案
motion 對應 議案(動作的概念)，一個議案可以有數個提案
bill 對應 提案
```
- [x] 了解 ly.g0v.tw 的架構
```
只有一個 index.jade，是 single page application
route, controller, model, view 皆使用 angularjs
```
- [x] 解 [g0v/ly.g0v.tw#132](https://github.com/g0v/ly.g0v.tw/issues/132)：目前只有院會會議與提案，尚未抓取委員會會議與提案
```
委員會會議(sitting)沒有 motions：
!
解法：
首先從 calendar 裡抓到該 sitting 的所有開會的日期
eg. 該 issue 的會議有四次日期：2014-01-06, 2014-01-06, 2014-01-08, 2014-01-08
到官網用 sitting 的屆別(ad)、會期(session)、開會日期搜索：
!
!
用 sitting 的 name 搜索頁面：
!
拿到 meeting\_no, meeting\_time, department_code：
!
call getMeetingAgenda (後來自幹了一個, 叫 page\_of\_bills)：
https://github.com/g0v/twlyparser/blob/master/src/misq.ls#L392
把這些 motions 放入資料庫
到每一個提案的頁面抓取 bill：
!
把這些 bills 放入資料庫，完成
成果：
!
```
- [x] 解「尚未命名的 issue」：把 [http://ly.g0v.tw/bills/1374L15430](http://ly.g0v.tw/bills/1374L15430) 綠色進度條做好
```
原本：(點擊「提案」後)
下方的列表應該要拿掉，然後整合到「點擊進度條出現的子進度條」
!
進度條資源：
https://etblue.github.io/semantic-ui-experiment/bill-progress.html
http://beta.semantic-ui.com/elements/step.html
進度條對應實際立法程序：
http://www.ly.gov.tw/02\_introduce/0201\_intro/introView.action?id=9
公佈的提案：
http://glin.ly.gov.tw/web/nationalLegal.do?isChinese=true&method=legalAnnounce&newQuery=true
http://www.president.gov.tw/Default.aspx?tabid=84
成果(桌上裝置，max-width > 1280px)：
!
成果(行動裝置，max-width <= 1120px)：
!
被退回的議案應該有驚嘆號(1374L15430)：
!
如果提案沒有日期，就把一讀的日期 copy 過去(1073L15722)：
!
複議/覆議處理：
1\. 「一讀」後「復議(另定期處理)」：1374L15430
2\. 「三讀」後「復議(另定期處理)」：1559L14887
4\. 「付委」後「復議(另定期處理)」：1013L15476
5\. 「三讀」後「覆議(全院委員會審查)」：882L13190
6\. 「三讀」後「覆議(交付審查)」：882L13190
7\. 「三讀」後「覆議(不維持原決議)」：882L13190
8\. progress: 「一讀」, resolution: 「逕付二讀 ...」：979L15307
9\. 「撤回」 471G14754
測試：
g0v/ly.g0v.tw#171
```
- [x] 解 [g0v/api.ly#62](https://github.com/g0v/api.ly/issues/62)：設定 pgq, plv8js 手續複雜，使用 docker 包裝成一個 app
```
pgrest 安裝指南：
https://github.com/pgrest/pgrest/wiki/Installation
成果：
1\. 安裝 docker
2\. 建立 image
    $ ./docker/scripts/build-image.sh
3\. 執行 postgres
    $ ./docker/postgres.sh
4\. 執行 api.ly
    $ ./docker/app.sh
5\. 開啟瀏覽器觀看 http://127.0.0.1:3000/collections/sittings
docker & chef-solo：
http://tech.paulcz.net/2013/09/creating-immutable-servers-with-chef-and-docker-dot-io.html
chef-solo：
http://docs.opscode.com/ctl\_chef\_solo.html
```
- [x] 新增熱門提案頁面
```
樣板：http://etblue.github.io/semantic-ui-experiment/ly-monitor.html
網站樣板：http://g0v.github.io/semantic-ui-experiment/public/ly-bill.html
桌上裝置：
!
行動裝置(max-width < 768)：
!
有網友反映看不到白色：
<Rhozan> 進行中流程好像比較少會用藍色來代表? (不過想試著修改看看的原因只是因為白色字太難辨識)
所以做了另一種樣式：
!
然後...
Rhozan> xsoameix: 嗯，這種方式比較好，如果太久沒進展再上顏色，會更明顯。或者是也可以再套用你用在提案人大頭貼下方的色條
!
Rhozan> 裡面15那種也很不錯
!
```
- [x] 解突如其來的 issue：ly.gov.tw 官網網頁更新，populate-calendar.ls 掛點
```
ly.gov.tw 官網網頁更新，日期和時間合併成一格了：
!
完成：
g0v/twlyparser#50
增加測試：
g0v/twlyparser#51
```
- [x] twlyparser fixtures 測試架構：
```
g0v/twlyparser#51
```
- [x] 替 ly.g0v.tw, api.ly 撰寫測試 (36 % coverage)
```
目前是提案的進度條：
g0v/ly.g0v.tw#171
```
- [x] ly.g0v.tw coverage report，跟 coveralls.io 整合
```
感謝大大的教學：https://coderwall.com/p/gzoxxw
```
ly.g0v.tw 404 error page
api.ly unit test by dredd
熱門議案熱門程度
議案頁面: [http://g0v.github.io/semantic-ui-experiment/public/ly-](http://g0v.github.io/semantic-ui-experiment/public/ly-bill.html)[b](http://g0v.github.io/semantic-ui-experiment/public/ly-bill.html)[i](http://g0v.github.io/semantic-ui-experiment/public/ly-bill.html)[l](http://g0v.github.io/semantic-ui-experiment/public/ly-bill.html)[l.html](http://g0v.github.io/semantic-ui-experiment/public/ly-bill.html)


[http://visualisiert.net/parteiengesetz/index.en.html](http://visualisiert.net/parteiengesetz/index.en.html)
tonyq__: 這個還沒做 基本上要把所有法律提案跟和沿革對起來 (tw-law-corpus)
12:37:54 clkaoud xsoameix: 疑 大坑突然出現了 就我剛說的那個 tonyq 問的 XD
12:40:13 xsoameix 要怎麼做呀？
12:40:58 xsoameix 去 tw-law-corpus 抓資料嗎？
12:41:41 Lee1092 突然的隕石坑
12:43:28 clkaoud xsoameix: 基本上 提案日期要 resolve 到 tw-law-corpus 的版本
12:43:54 clkaoud 也許之前用 git commit 不適合 就用他最後修過的版本的日期
12:44:40 clkaoud 譬如某法在 2012-10-12 2013-09-10 都修過，在 2013-05-02 的提案就要對到他是改 2012-10-12 的版本作為 base
12:45:44 clkaoud 所以簡單來說 因為提案已經有法編號... 基本上就是想辦法加上他的日期版本... 這樣資料就足夠讓前端做其他呈現了... 至於要如何呈現 再想想或問問大家有什麼看法
12:45:48 xsoameix 從提案的日期往前推最近的版本嗎？
12:46:27 xsoameix 現在的情況則是怎樣呢？
12:56:46 clkaoud 對 現在就只有提案日期 然後法律編號可能要跟 tw-law-corpus 的再對照一次 還有全國法規資料庫 最好能把法律 id 先對起來
13:23:55 yhsiang lanf0n: 一起延 :)
13:25:13 yhsiang xsoameix: 大坑 XD
13:28:11 kiang voller++, 又得 OCR 了 XD
13:31:27 xsoameix 法律 id 是指 bills/xxx 嗎？
13:39:44 dirty_ 沿革的呈現不是有人提要這樣嗎? # [http://visualisiert.net/parteiengesetz/index.en.html](http://visualisiert.net/parteiengesetz/index.en.html)
13:39:46 kcwu dirty_'s url: \[The Making of a Law\]
13:41:17 clkaoud xsoameix: no, bill json 裡面會有 law_id
13:41:30 clkaoud 但那是國會圖書館的編號
13:42:33 xsoameix amendments
13:43:04 xsoameix 是一個陣列
13:43:44 xsoameix 所以法律 id 要去哪裡找呢？
13:51:01 clkaoud amendment 會有 law_id
13:51:21 xsoameix 恩，我有看到
13:51:32 clkaoud 或用這個 : [http://api.ly.g0v.tw/v0/collections/laws](http://api.ly.g0v.tw/v0/collections/laws)
13:51:55 xsoameix 用 law_id 去推 bill id 嗎？
13:51:56 clkaoud 可以問問看 kong kao 有沒有整理過了 國會圖書館跟法規資料庫的 id
13:52:06 clkaoud 還是 Jcrt 之前有弄法規相關的
13:55:44 xsoameix 有對應的資料可以查喔？

<clkao> xsoameix: 最先的就是 amendment 要加上一個欄位 reference 到特定版本的 law
<xsoameix> 特定版本的 law 是指？
\* ensky_cloud has quit (Ping timeout: 246 seconds)
\* ensky\_cloud (~ensky\_clo@220.135.204.249) has joined
<xsoameix> 就是 latest 的 law 嗎？
<xsoameix> 然後之後再建立全國法規資料庫的 real\_raw\_id 是嗎？
<xsoameix> s/的 real\_raw\_id /的 real\_raw\_id 欄位/g
<xsoameix> 不好意思，先去睡覺，明天早上還有課
\* clkao xsoameix: 特定日期的版本
- [xsoameix](http://logbot.g0v.tw/channel/g0v.tw/2014-09-19/176)clkao: 現在 amendments 只有 bill\_ref 而已，不能看出是 base on 甚麼時候的法案做修訂，所以我應該加一個欄位，叫作 base\_bill_date，這個就是告知是甚麼時候的法案，這樣對嗎？
- [21:41:22](http://logbot.g0v.tw/channel/g0v.tw/2014-09-19#177)[clkao](http://logbot.g0v.tw/channel/g0v.tw/2014-09-19/177)是。不然就是從她第一次提出給一讀的日期為準

clkao> xsoameix: no, api-ly dump is data only. Table schema can be defined in meta.ls


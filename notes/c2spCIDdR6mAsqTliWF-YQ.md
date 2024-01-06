---
tags: cofacts, meeting note
---

20190102 會議記錄
====
文武, gore,ci,ggm,蝴蝶,bil,orz,辰
> 前次會議記錄：https://g0v.hackmd.io/s/rJNFo1xWN
> 

## 新功能

### LIFF 上線後檢討

:::info
20190101 理由（from opendata）

https://docs.google.com/spreadsheets/d/1fc90i6gt8gDC9hYhJOUamhxRn6MpEIpVzjdfrpxBsgs/edit#gid=795336465
:::

#### 理由太短，沒有參考價值

- https://cofacts.g0v.tw/articles?searchUserByArticleId=1s0i58e3kt6cs&filter=all&replyRequestCount=1 「太多」系列
- https://cofacts.g0v.tw/article/14jnz9teaynsk 這個人很誠實
- https://cofacts.g0v.tw/article/17c47ejwecs3x 你才查不到 你全家都查不到

> Orz:
>
> 我們再放個幾天收理由的資料，我這裡有幾個想改進的方向。
> 
> 1. 理由字數有個最低標（15 字），至少要這個字數，否則不能送出。理由跟訊息完全一樣也不能送。
> 2. 高於最低標，但沒超過某個標準，送出時會提示使用者下面文句，但若使用者執意送出，還是會送。文句如下：
> 
> 理由可以再豐富一些，越豐富的理由會讓編輯回覆越快唷！
> 
> 你可以試著 A. 闡述更多想法、B. 去 google 查查看、C. 把全文複製貼上到 Facebook 搜尋框，然後貼進來給編輯參考唷！
> 
> 3. 編輯的文章列表，理由認真填（字數夠多 / 覺得理由有道理的）的擺前面，優先解決

Gore
會有不好的理由，是因為現在一定要理由
但如果不寫理由，就會沒有人寫理由

Bil
如果編輯夠多，不寫理由也很棒，因為可以直接到收到什麼東西，降低思考門檻
但目前沒辦法，只能就真的有理由的來處理

Gore
很難判定會影響到什麼人

Ｏｒｚ
你可以想像老人是不會送訊息進來了
可以想像的是 user base

文武
現在可能還不用大量蒐集
但像之前選舉的時候，如果沒有查證大家就會不傳
可能那個時候就會想要放低限制

GOre
目前高字數沒有用是什麼狀況

Orz
闡述自己的直覺的那種理由
雖然對編輯來說可以知道為什麼他有疑惑
但對媒體是讀比較沒有幫助，也對查證沒有太大幫助

:::success
MrOrz

理由 15 字以下：禁止送出
理由跟訊息一樣：禁止送出
15~40 字：顯示警語（但還是允許送出）
:::


#### 無視規則的白目使用者

- https://cofacts.g0v.tw/articles?searchUserByArticleId=2o9b92qekch1&filter=all&replyRequestCount=1


Gore
我可以想像他的情境
我加了 bot，會想要

Bil:
是不是可以提供新手
就是跳出謠言列表

Gore
這比較像是演示給親友看

Orz
好像可以放在加入時的歡迎訊息後

https://github.com/cofacts/rumors-line-bot/issues/104

文武
我們 bot 還好，有些官方帳號我是要看訊息，menu 會擋住我

Gore
如果加範例
那要特別去過濾嗎

Ｏｒｚ
範例會挑已經查證過的

:::success
設計引導使用者點擊範例的文案

Billion
:::

#### 收進來的訊息不是轉傳訊息

From [1226 會議記錄](https://g0v.hackmd.io/s/rJNFo1xWN)：
> 另外，目前還有那種
> 「美玉姨含有木馬程式」「貓纜沒開」這種用手打的訊息被傳進來
> 我之後打算在 LIFF 填理由前問使用者說「請問你是在哪裡看到這個轉傳訊息的」
> 選項：「家庭群組」「朋友群組」「宗教群組」「旅行團群組」「我自己打的」
>
> 選「我自己打的」就會讓使用者選擇傳去 MyGoPen 或蘭姆酒吐司或 TFC
> 

文武：
但這應該不會擋住真正白目的使用者

Gore
他可能會踩進去，但踩了一次之後就不會再踩

文武
剛才那個人發了四篇耶

Gore
有強大動機的話，可能確實都會選選看

文武
但有個調查也不錯

GGM
如果有人打
「喝咖啡會長壽」
然後理由打「我覺得喝咖啡不會長壽因為媽媽不是這樣子教」

Orz
嗯擋在理由就會有這個問題，那你覺得他會按「我自己打的」這樣嗎

GGM
我會啦
防君子不防小人

:::success
可以做～

先開 ticket
:::

### 回應的排序

Request from TFC:
https://www.facebook.com/groups/cofacts/permalink/2298321457066337/?comment_id=2298813253683824&comment_tracking=%7B%22tn%22%3A%22R%22%7D

相關 issue: https://github.com/cofacts/rumors-line-bot/issues/78

Orz
想問大家覺得什麼樣的排序會比較好，如果你是使用者

500px 也是會有部分的新的在前面

文武的是第一個是新的，其他按照有用度
我覺得可以擴充，變成前 1/3 是最新的幾篇，後 2/3 是有用的

GGM & bil
投 1 篇的版本

:::success
結論：
最新的放前面，其他按照有用度排序
有用度：`positiveFeedbackCount - negativeFeedbackCount`

MrOrz
:::

### 編輯個人頁面

From [20181226](https://g0v.hackmd.io/s/rJNFo1xWN):
> 個人成就：網站瀏覽量、LINE bot 搜尋曝光量顯示、把哪些文章連在一起、幾人覺得有用/沒用
> 通知個人成就 maybe via notification or email
> 增加編輯貢獻牆（1 日、7 日、30 日）–> 輔助比鄰每週貼文
> 

目標：讓編輯願意自己主動拿出來，向外闡述推廣自己的所為

:::success
ci

資訊流
:::

## 2/16 （六）小聚
主題：春酒 ~~情人節明天過後？~~ 己亥年正月十二
場地：開吧
- 確認麥克風＆水
- 新貼紙 （GGM 挑一到兩款不一樣der 用line貼圖不能上架的那些囉）

- 設計：小豬中國風新年剪紙 要不要回收去年的設計呢 就把狗狗換成豬就好 ＠鹿

https://cofacts.kktix.cc/events/cofacteditor7

邀請過去來過的編輯，用 kktix 裡的 email 聯絡。

春酒食物 -
去年：潤餅換成片鴨

抽獎：上次抽紅包袋

幾個問題：
1. 食物到底要什麼？ 
鴨：片鴨三吃？
豬的押韻：烤豬、德國豬腳、萬巒豬腳、滷肉飯、香腸、豬頭皮、豬耳朵（餅乾）、朱古力

:::info

////文案////
去年新年到現在，真的假的使用者從3萬爆增到8萬啦啦啦！這個160%的業績成長都要歸功給編輯們撒下的汗水。

2019年2月16日，大家一定要來參加真的假的春酒，真的。

**食物**跟限量版貼紙當然少不了。都已經跟**210**位編輯一起熬過公投跟九合一大選，豬年還要有非洲豬瘟呢...來吃頓好的應該的吧？

Cofacts 真的假的 利用 LINE Bot 查證工具致力於協助使用者辨別假新聞。但是協助我們辨別訊息真假的，不只是軟體，還有「工人智慧」，因此我們歡迎每個致力追求真相的朋友加入我們，一起幫助人們辨識不實訊息。

Cofacts 作為一種以言論自由對抗假訊息的嘗試。


時間：2/16（六）14:00
地點：開吧餐飲顧問二樓（105台北市松山區敦化北路145巷12號2樓）

14:00 - 14:15 自我介紹＆真的假的闢謠簡介

14:15 - 15:55 歡樂春酒的光速闢謠

15:55 - 16:25 一年前的現在....春酒抽獎時間

16:25 - 17:00 自由交流 & 大合照

歡迎你在活動過程中，幫我們打卡 #真的假的 #闢謠cofacts

:::


## 開發 (g0v slack線上討論)

rumors-site refactor
https://github.com/cofacts/rumors-site/tree/refactor

- next7
- deprecate App, use onr of the below:
  - https://github.com/zeit/next.js/blob/canary/examples/with-redux-wrapper/README.md
  - https://github.com/huzidaha/next-connect-redux/blob/master/README.md
- FOUC 問題：https://github.com/zeit/next.js/issues?utf8=%E2%9C%93&q=Flash+of+unstyled+content+SSR

### rumors-site landing page 一直是英文

> GGM
理論上是讀 HTTP Accept-Language
---
tags: cofacts, meeting note
---

20181226 會議記錄
====

> 前次會議記錄：https://g0v.hackmd.io/s/rJjEBUPg4


## 新功能

### 準備上線： LIFF
Facebook: https://www.facebook.com/groups/cofacts/permalink/2295896103975539/

PR: https://github.com/cofacts/rumors-line-bot/pull/118

已經上 [staging](https://line.me/R/ti/p/%40nkq3195z)

新 copy：「理由」+ 提醒使用者要去查資料

Chatbot 裡請使用者去搬救兵的 wording:

> 遠親不如近鄰🌟問問親友總沒錯
> 說不定你的朋友裡，就有能替你解惑的人唷！
> 你想要 Call-out 誰呢？
>
> 按鈕1：LINE 群組
> 按紐2：臉書大神 

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_76251ecd53354277ed5bf641c7d12686)


Share 到 LINE 的欲填訊息：

> 我收到這則訊息的想法是：
> （理由）
> 
> 請幫我看看這是真的還是假的：(文章連結)


Share 到 Facebook：
> 
> hashtag: Cofacts求解惑
> quote: 
>

Orz
未來可以加上 twitter & plurk
像之前淘寶有豬瘟貨是 plurk 的人開始發動檢舉的

:::info
理由分析：
https://docs.google.com/spreadsheets/d/1YuX_KB0ziQByRjLiNcIcoDBkmQmSqrFeLpjRqnXNTfI/edit#gid=596839989

2018/12/23~12/25 約有 20% 的理由都是「下一篇訊息」。不少都是沒有查證價值的新聞訊息。

LIFF 上線之後，預計這 20% 的訊息都可以被擋在外面。
:::

Orz:

另外，目前還有那種
「美玉姨含有木馬程式」「貓纜沒開」這種用手打的訊息被傳進來
我之後打算在 LIFF 填理由前問使用者說「請問你是在哪裡看到這個轉傳訊息的」
選項：「家庭群組」「朋友群組」「宗教群組」「旅行團群組」「我自己打的」

選「我自己打的」就會讓使用者選擇傳去 MyGoPen 或蘭姆酒吐司或 TFC

:::success
晚上上線！
已知問題：share 到 FB 之後會一片空白
:::



### RFC：編輯組織

為了吸引編輯持續貢獻，尤其是闢謠組織或團體主動來 Cofacts 送出回應，我們設計了 Cofacts editor organization 機制（名稱暫定），任何人可以建立一個 editor organization，然後以 organization 名義發出的回應，會標注是這個 organization 回應的，然後 Cofacts 在讓編輯選擇回應的時候，會寫清楚某回應是這個 organization 所撰寫。

這個功能對 MyGoPen、蘭姆酒吐司或 TFC 來說應該是還不錯的功能，若使用者在選擇回應時能先看到「這個回應是哪個組織寫的」，對 branding 與流量應該是大加分。

目前實際要做的功能列在這裡：
https://hackmd.io/ktxqGDX4S4iuBd1MoZqDmQ#Cofacts-Editor-Organization-%E6%A9%9F%E5%88%B6

有任何想法都歡迎提出來討論唷！

TODO:
把想法變成 LINE bot designer mockup
然後到社團貼文 tag TFC、蘭姆酒吐司、MyGoPen、MedPartner、泛科學

:::danger
先做個人 profile 頁面唷
:::


## 討論事項

### 開會時間
ggm:
明定時間限制，例如一小時內開完。確保開會效率。
連假前後避免
換時間的話，二三四會是比較好的選擇。
ci：
九點半前結束比較理想
bil:早一點比較好，到11點的話，第二天白天會有點辛苦
ggm:那開會8點到9點半
howie:你們開會時間太長了，所以很隨性
這樣就全遠端啊，大家在線上講啊，可是你要實體開會就是一小時就好了。
確定你們8點半一定要開會。那如果不能到就要想怎麼辦
不然你們時間花了卻沒有效率
bil:我可以八點到
ci：我最晚8點半下班
ggm:我那邊時間還可以調整，如果有明確規定8點開始，我就可以跟大家講。
文武：我也是可以8點到，其他週幾都可以
ggm:會挑二三四
文武：這可能要看吧
有個問題是，平常在家不會做。我以前會上班做，但是現在換工作沒辦法。
假日想休息不會做。  

MrOrz
或許可以有一個 hackathon 約工作

Bil
可是開會歸開會，工作歸工作
也可以開完會之後留下來工作

Orz
那我們就

Bil
如果不能來開會怎麼辦?
要有一個規則在

文武
解決五條謠言

GGM
遲到的不能點飲料

Bil
沒來的就解 issue？
沒有來要做一點事情

ci
主辦下一次小聚？

Bil
可以，但沒那麼多次小聚

Bil
闢謠 20 條如何

文武
20 太多，廢文大家都會搶

orz
其實是有一些 task 可以做
例如說當信件的聯絡人
處理法律條款（一次性）
撰寫發粉絲頁 or medium 文章，寫最近的熱門謠言

bil:然後我們有個medium
ci:我寫我寫，我寫這個應該很快 

orz
像蝴蝶可以寫 tag 怎麼處理

bil
開發者不來的話要寫交換日記
我照顧我的 tag 寶寶長大

編輯小聚兩小時 10 篇，
那處罰 20 篇闢謠應該 ok

文武：
要看那一題難不難

:::info
結論：
開會二三四都可以
時間：8:00 ~ 9:00，1hr，最晚 9:30 結束
結束可以留下來

沒來的要寫 medium
medium 沒交就闢謠 20 篇

ci是medium小天使
:::


### 編輯動力
https://imgur.com/AlFrfQq

在有 analytica info 的現在回頭來看，其實可以開始做不少事

個人
- 1. 個人成就：網站瀏覽量、web 搜尋曝光量顯示、把哪些文章連在一起、幾人覺得有用/沒用
- 2. 通知個人成就 maybe via notification or email

組織
- 有幾個已經存在的闢謠組織給他一個credit！美的好朋友、蘭姆酒吐司、事實查核中心
- 也為他們建立品牌

Ci: 可以弄獎章嗎？我來畫:D

bil
先做個人好了，個人好了組織就會好
之後組織可以用個人換過去

ci
組織有很急著要 credit 嗎

bil
不如說我們會擔心組織禁止 cofacts 使用我們的內容
因為他們會怕我們搶他們流量

文武
還是要看使用者，
有些人只想知道真的假的，有些人想看完整流程，
就會點進去

orz
如果回應是組織自己寫的話，
他們可以寫得讓人很想點進去

文武
他們也可以看到有多少流量是 Cofacts 過去的。

orz
個人會想要顯名嗎，就是「比鄰把這篇標記成⋯⋯」而不是「有人」

ci, bil:
不會，想當沒有人

:::success
結論：「個人」先做

### 解決問題（from [mind map](https://imgur.com/AlFrfQq)）:
未能輕易看到自己闢謠文章的影響 ／ 受益人數

### 嘗試解法
增加使用者看見自身貢獻受益人數 & 觸及的介面
- 1. 個人成就：網站瀏覽量、LINE bot 搜尋曝光量顯示、把哪些文章連在一起、幾人覺得有用/沒用
- 2. 通知個人成就 maybe via notification or email

- 增加編輯貢獻牆（1 日、7 日、30 日）--> 輔助比鄰每週貼文

:::

### meetup with D4D and 美國智庫

any action plans?

#### D4D (哈佛甘迺迪學院學生)


#### 美國智庫

是否需要資源做 community building

Bil:

是否可以聘請專員、想 plan 來投之類的

工程師：可以變成作品集，可以用成就感

但文字作業是替代性高、成就感低，可能會需要付錢請人做

然後會需要一個全職的 PM / 組織專員

Ci

Community building 要想東西、讓編輯覺得闢謠好玩，會需要企劃。
遊戲化設計之類的。可是這是一個 case，以 case 來接

orz
case 方便算，像 facebook bot 就是用 case

Ci
小聚這種，讓真的人出現，會真的需要投入真人。

orz
我需要設計師

bil
外包設計師也可以

ggm
買一個 logo

bil
包給 lucien 好了
給你錢快做

### 台權會 1/16 人權星期三

> 介紹 Cofacts 的行動與理念

不開會囉～

### 美玉姨

是否要收 reply request？
或者是做 API-server analytics？（for search result hits）

爭議：美玉姨在蒐集資料。
https://www.facebook.com/groups/g0v.general/permalink/1961364513939945/

公布使用者條款 & 隱私權條款？
（我們沒有 API 使用條款囧）
https://beta.hackfoldr.org/cofacts/https%253A%252F%252Fhackmd.io%252FmFSlWs4IQke_9RnFAOWlfQ


## Dev items

### Chatbot issue: Puppeteer 斷線
近期斷線狀況：https://rollbar.com/mrorz/url-resolver/items/10/
20181225 一天斷線 13 次，被查詢 9.9K 次(RPM = 6.9)
平均每被查詢 700 次，瀏覽器就會 crash

### GraphQL Logging

Apollo Engine

### Staging 搬家

目前處置：
- Cofacts 主機 staging 系列 docker container 全數 stop，空出 1.5G memory (大多是 Staging DB 所佔用)
- Cofacts 主機上的 url-resolver 開到 1GB memory，目前長時佔用 memory 約為 300MB；放大 memory 之後有效減少 request latency
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c1c29d111c982a2cb5188f6da838ebee)
- answerfamily 增加 `compose-all.sh` 把 answerfamily-deploy 的 docker-compose.yml 與 rumors-deploy 的 docker-compose.yml 和在一起（使雙方用同一個 network）。使用同一個 nginx，複製 cofacts staging api & site 的 nginx config 到 answer-family 的 `enabled-sites` 底下。

### 美玉姨

- orz: ignore short messages - https://github.com/CarolHsu/rumor-checker/pull/1
- 桓誠：加 cofacts - https://github.com/CarolHsu/rumor-checker/pull/3
- orz: fix variable interpolation https://github.com/CarolHsu/rumors-api-client/issues/4

### Bugs

TBD: 蒐集 Rollbar
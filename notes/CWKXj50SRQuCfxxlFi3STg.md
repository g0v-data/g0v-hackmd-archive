---
tags: cofacts, meeting note
---

20190904 會議記錄
=====
orz, bil, 文武
線上：lora, 桓

> 上次開會紀錄：https://g0v.hackmd.io/@GuJ5fZ3uR-O09mlTi1w2UQ/HyY_eeQHS
> 

## 10 月小聚

- 10/5 (六) 2019年亞洲事實查核專業論壇
- 10/12 orz, bil 不在台灣
- 10/13(?)~11/23 bil 不在台灣

10/13 是國慶日連假

:::success
日期：10/6 (日)
:::


## 9/7 黑客松 material
> 坑主：文武

- [x] 報名: 文武、GGM
- [x] 材料: 已經填寫提案 10:17
- [x] 做什麼: 
    - 編輯
    - LINE bot good first issue
    - API server good first issue

## Rumors-site 升級 next9
改成 base on master 所以可以看 diff 了：
https://github.com/cofacts/rumors-site/compare/next9

- .babelrc, .env 大洗牌
- 移除 redux、ImmutableJS
- 引入 material-ui、apollo-client、ttag i18n
- landing page 換成由 next.js prerender （目前空的）
- 新的 `_document.js` 與 `_app.js`
- 盡量用 functional component & hooks
- 目前 migrate /articles 文章列表與相關 component

Orz
想從 master 開一個 dev branch
文章列表完成後發 PR 進 dev branch
然後再繼續 migrate article page, reply list, reply page


## 9/10 (二) NDI 拜訪 OCF 

> Email 主旨：NDI 來訪 _ 邀請cofacts

> 9月10日(二)下午3:30至4:30
> 此次訪台盼廣泛瞭解台灣民主發展，以及中國影響力對台灣政治與選舉系統之影響
> 團員另也希望藉此機會至貴會交流開放政府、開放硬體及網路自由等議題

bil 9/9 餐敘時會問

### 誰出席

:::success
bil
:::

### Facebook chatbot

MrOrz:
上次在 RightsCon 就被問進度噗噗
雖然是做完了，我覺得應該可以上線
但可能有些機制要改一下，否則會影響一般人聯絡我們：

1. 私訊時可以問一下是不是要來查詢資料庫的
2. （不確定是否做得到）被 tag 之後把答案私訊回 tag 他的人，或私訊問他是不是要查資料庫

> 過去討論： https://g0v.hackmd.io/@MODl5abnQpKy6ifB4DPGcQ/ry8jMZBJ4?type=view#Facebook-bot

誠
「如果下次要查詢就打 OOO」

真的想要找 cofacts 的人也不會想用 chatbot

原本在跟 chatbot 聊天，突然想要問我們一些事情，這個比較麻煩

當然可以第一次的時候問，但切換這兩邊是很麻煩的事情

orz
messenger 有 menu 嗎

文武：
有
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_871a3b1949e7e3839e712cd448a44525)

orz
Temporarily disabled chatbot function 
https://github.com/cofacts/rumors-fb-bot/issues/4

--> Menu

誠
第一次會問，
回答完之後就提醒他可以在 menu 作切換

orz
這個 FB page 好像可以切 bot 身份
https://www.facebook.com/sigonogames

誠
他可以 hand over 給另一個 page

orz
感覺好麻煩，那還是不要好了

關於之前提到的，tag bot 自動回話這件事情，是有的嗎

誠
現在 bot 會在那個 comment 下面回他
也不是所有 comment 可以回，必須要在公開 page 的公開 post 下 tag 機器人，他才會回。

其實 bot 一直都是開著的，只是把私訊擋起來，然後好像一直沒有人觸發「tag 機器人」這件事

orz
我好像有在群組文章內 tag cofacts page 但好像不在群組裡就不會動

:::success
1. 9/10 若 NDI 問起，就說會做切換的修改之後發表
2. 增加「第一次私訊 bot 時要問『請問您要跟 Cofacts 管理者對話，還是查詢這則訊息呢』」
並且提醒使用者可以在左下角 menu 切換模式

Github issue: https://github.com/cofacts/rumors-fb-bot/issues/4
:::

## LINE bot 不好用 - 流程 or Wording 檢討

### Context

> 艾：
假清夥伴提到他們最近去新竹，發現講師在簡報的時候把真的假的Cofacts拿掉了，原因是他們在跟竹松社大的人試講的時候，發現很難用，要經過兩層才會收到答案，想說長輩會學不起來，所以拿掉了。最近幾場講座，長輩跟竹松社大的年輕人都有反映這個問題，不知道流程有沒有辦法調整，讓對資訊不熟悉的人更方便？
>
> Bil：
這裡說的是這個嗎？
1.user發訊息給bot
2.bot回傳選項讓user選
3.user選擇自己提問的訊息後得到回應
> 
> 艾：
> 
> 應該是這個
相似度以後，還會有一個多元查證選擇
其實對我們自己來說好用，也清楚用意
但對一般大眾好像會有困難
推廣方面
> 
> Bil:
是指不想選，希望直接跳一個出來就好嗎@@"
> 
> Orz:
多元呈現這件事情還是我們想做的 @@
或許改變 wording 會比較好
> 
> 例如說在選擇之前，可以提醒「有很多人對這則訊息有發表看法唷，請在下面選一個觀看」
> 
> 艾：
對@@哈哈...
> 
> Bil:
嗯這樣說好了，我自己在演講報告的時候被問到這個也滿多次的，說這樣比較麻煩。
可是其實查核的目的不是告訴大家只有唯一解或是「我說的才是對的」
這兩個心態都很危險
> 
> Orz:
畢竟是真的不希望對方照單全收嗚嗚
讓他們誤以為可以信任
後來才發現其實不行
這樣的反彈會更大唷
（Cofacts Inbox「請更正」信件內容）
這種「以為可以相信但後來發現不行」情緒上的落差確實存在 QQ
> 
> 艾：
嘿啊....這很兩難
嗯嗯我們每次宣講也都會強調不要完全相信假清 也不要完全依賴這些查證軟體 這都只是幫助你的工具
不過踏出第一步如果長輩就感受到挫折，可能就不想用了Orz
> 
> Bil:
通常講到資訊安全跟對權威的信賴、錯誤知識的散布之後，體諒的人會比較多。
我自己會盡量好好說明使用機器人跟真人、或是群組內機器人的用法與差別
> 
> 艾：
推廣的時候怎麼說對方會比較願意嘗試？然後後續也會繼續使用
> 
> Orz:
「如果覺得這個訊息怪怪，可以到這些地方，看看其他人有沒有類似想法」
> 
> Bil:
機器人的優點：可以在任何時間發訊息、對方不是真人比較沒有壓力
一開始就說明會有兩個步驟，
1.機器人會問你問題
2.選一選哪一個比較像你想問的
這是為了，避免機器人亂猜你的問題，會發出錯誤的回應。
多一層步驟、多一層保障
正確與信賴，本來就需要多一點點不方便
這個過程也可以保護自己
機器人沒有要記錄那些羞於啟齒的私人問題或是讓人不好意思問的謠言與疑問，機器人只想確保回應到正確的謠言，所以才會有多一層的設計。
> 
> Orz:
但 wording 上確實可以引導使用者「選一個」之類的
如果更清楚指出「下一步」是否就可以解決長輩的問題呢
> 
> 艾：
嗯嗯好像是引導可以多一點
> 
> Orz:
我這裡可以幫忙列出所有 wording
大家可以一起來看看哪裡會卡卡
> 
> 艾：
如果是這樣的流程勒：
1.傳訊息
2.詢問相似度
3.得到A回覆
4.Wording：想再看看其他意見嗎？多一層資訊，多一層保障喔！（是）（否）
5.條列其他查證內容
> 
> Orz:
> 也可以
> 我把它加進今天的會議議程好了
> 我自己覺得可以先從改 wording 下手
> 搭配一些 emoji 
> 「👀 看他怎麼說」
> 之類的
> 
> 艾：
> 應該是說我們後來在每一場講座，都會帶著長輩一步一步操作，確保他們加入好友了，才進入下一步，轉傳完畢，再進入下一步介紹為什麼會有相似度的問題，還有「是否幫助到你」的用意是什麼，很仔細地手把手講解。但是長輩回去之後多數只會記得Mygopen。
>
> 然後我自己的感覺是，比鄰提到的觀念跟心態，我們也都是花兩個小時不斷地強調跟提醒，但是一般大眾尤其是長輩學習沒辦法那麼快速，或者是我們跟他講「多元」「事情沒有標準答案」，都還要特別解釋跟舉一大堆例子，這個東西離他們的經驗太遠。
>
> 我的意思是，不希望Cofacts這麼好的工具，因為長輩來不及跟上，而推廣不出去。第一步有好的體驗，才會引發人後續願意繼續使用。最需要查證軟體的其實是那些連孤狗跟主動轉台看看別的頻道都不會的民眾，所以也希望這些觀念慢慢進入他們的腦海裡
>
> 所以我們主要是從使用端提出觀察，但還是尊重Cofacts的用意，看你們覺得怎麼調整比較適合～也辛苦你們一直把這些態度完整呈現在流程中，觀念部分我們會繼續努力推廣
> 
> Orz
> 那如果訊息資料庫裡面有很多很像的，那一步要選「最像的」這一步，民眾在使用上有障礙嗎
> 就是傳訊息進來之後選最像的 or 「沒有我的訊息」那一步
> 
> 艾
> 這一步要講解用意以後，他們才會知道要點哪裡，哈哈
> 我們的說法是「因為謠言本身會不斷以訛傳訛，產生扭曲或是變化，所以機器人要幫你確保這個訊息跟你想查證的是100%相似，才不會給錯答案」
> 
> Orz
> 看起來也會需要一個說明
> 
> 艾
> 或是要有「那是一個按鈕」的感覺？XD

### 討論

MyGoPen 志工：
有聽到長輩説 Cofacts 很難用
因為有兩個步驟

bil
當初美譽姨就是因為覺得這個使用流程不是想要的，所以才自己寫

lora
美譽姨好像最近會改 wording 讓文字友善、軟一點


### Improvement

過去的 wording update:
- 單則 reply 呈現：https://hackmd.io/@mrorz/B1bb-hXhz?type=view#LINE-bot-wording-review
- 減少 reply 呈現的價值判斷：https://g0v.hackmd.io/@GuJ5fZ3uR-O09mlTi1w2UQ/B1X3aNfzE?type=view#Wording-%E6%AA%A2%E8%A8%8E https://g0v.hackmd.io/@GuJ5fZ3uR-O09mlTi1w2UQ/S1D8FVqf4?type=view#Wording-%E6%AA%A2%E8%A8%8E
- 送出訊息 wording https://hackmd.io/a-_er_PTQ6eSXhdrn9wSDw#%E4%BA%82%E8%BC%B8%E5%85%A5%E6%99%82%E6%89%80%E9%80%81%E7%9A%84%E8%B3%87%E6%96%99

過去的修改 PR: https://github.com/cofacts/rumors-line-bot/pull/71

#### 1. 分享後查詢 - 有多則 or 不夠像時

> 幫您查詢「⋯⋯」的相關回應。
> 請問下列文章中，哪一篇是您剛才傳送的訊息呢？
---
> [相似度:x.xx%]
> （節錄）
> 選擇此則
---
> 這裡沒有一篇是我傳的訊息
> 選擇

🔍 我們在資料庫裡，找到 3 則訊息，跟您傳給我的「⋯⋯」有點接近。

請選擇您想查看的訊息👇

|  |  |
| -------- | --------  |
| ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c23b9a70c78c739c73354a00a9cece97) |   ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_81581f0ba29fe05089bd4920123a40f8) |


##### 討論

bil
如果我是魯小小長輩，我會問「我怎麼知道要看哪一則訊息」

「轉傳訊息可能有很多變體」可以寫得煽情一點，"in case 你傳的是假新聞"


像之前修改回應顯示，第一線就回應說老人這樣看不懂，他們就要圈圈叉叉
我覺得有一好沒兩好，我也支持不改

MyGoPen 很長，但他會有 summary 吸引人繼續讀下去

orz
可是「第一段」這個應該是編輯技巧，我也會在第一段放 summary。

bil
但我們目前就是 free form 回應，這在粉專私訊也有人提。

orz
我覺得應該有 middle ground，可能不是「有一好沒兩好」
應該可以在「謹慎 wording」底下找出一個讓人清楚往下使用的說詞

bil
老人大學講師回應說
大家最有反應的是過貓的 case

如果找到年齡很接近的受害者，煽動年長者的銅鋰鋅，永遠都很有效

如果 wording 裡寫說「你是個善良的人」「你不想傷害人所以想要確認」會比較好
如果你背面一定是「修改謠言來欺騙你」「被騙不是你的錯」

:::success
https://github.com/cofacts/rumors-line-bot/issues/141
:::



#### 2. 有多則回應時

> 這個訊息有：
> A 則回應標成 ❌ 含有不實訊息
> B 則回應標成 ⭕ 含有真實訊息
> C 則回應標成 💬 含有個人意見
> D 則回應標成 ⚠️️ 不在查證範圍

---

> 不在查證範圍
> [還沒有人針對此回應評價]
> OOOO

##### 先顯示第一則的做法

網路上的好心人們，對這則訊息發表了多則回應唷！
最新的看法是：

OOOOOOOOO

出處：XXXXX

另外，也有 A 人說它 ❌ 含有不實訊息、B 人說它 ⭕ 含有真實訊息。選一則來閱讀吧：
(carousel 選項們)

:::info
Orz: 我發現一個問題：這樣我們就收不到「最新看法」是否有用了 QQ
那個「請問上面回應是否有幫助」其實還滿重要的
我們有打算加強這個 feedback loop 來提升回應品質

艾:
沒關係，看你們會議結論如何好了，總之我們就是努力推廣～辛苦了QQ
:::


##### 改 wording 的做法 - 加上 call to action

Cofacts 志工對這則訊息發表了多則看法唷！

👨‍👩‍👧‍👦有 A 人說它 ❌ 含有不實訊息、B 人說它 ⭕ 含有真實訊息。

選一則來閱讀吧👇

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_09a15b9d1143226aefe63fe9ee532925)

###### 討論
bil
「好心人」好像有點遙遠。Cofacts 編輯？
志工？義工？

orz
志工好了

按鈕上要有眼睛

:::success
https://github.com/cofacts/rumors-line-bot/issues/140
:::


- - -


## 例會參與方式

lora
想問有沒有參與開會的方式
因為 hackfoldr 雖然有會議記錄，但不知道怎麼參與討論

mrorz
目前是在 g0v slack #cofacts 會放會議記錄
想要參與開會的人會私訊我們

bil
可以在 hackmd 上面線上文字參與

桓
如果在 github 開 issue 勒，在上面討論

orz
那就會在 github 上討論

lora
許願也可以讓他們加進來

有朋友是認知心理學家，在國外無法參與，但有興趣查訊息的 pattern 做分析

orz
分析資料的合作，過去會透過 email 唷

hackfoldr 首頁「聯絡我們」區塊有寫「其他合作或聯絡」
https://beta.hackfoldr.org/cofacts/https%253A%252F%252Fhackmd.io%252Fs%252FByXgboon-

lora
可能在官網有會比較好

orz
Hmm 目前官網是確實假設參與者會來闢謠或寫 code，沒有考慮到其他種協作
不過把 open data 放進官網，似乎會有點資訊爆炸

bil
要 data 跟一起開發應該會是兩件事情

:::success
1. 先在 hackfoldr 看會議記錄，覺得有興趣跟會再私訊
2. 希望分析資料，可以來信
3. lora 可以問問朋友，期待這樣的資訊被放在哪裡
:::

---
tags: cofacts, meeting note
---

20190109 會議記錄
====
文武/ggm/bil/orz/ci/Lucien 
> 前次會議記錄：https://g0v.hackmd.io/s/SyN-sb8b4
> 

## 新功能

### 理由長度限制

> 理由 15 字以下：禁止送出
> 理由跟訊息一樣：禁止送出
> 15~40 字：顯示警語（但還是允許送出）

MrOrz: 還沒做囧

### 歡迎訊息裡附上範例

> Rich menu 中新增範例的文案，點擊後可發出

- 訊息結尾加上「`〖範例訊息〗`」以資辨識
- 範例訊息無法送出、沒有 analytics

比鄰：目前在 Staging 上測試 rich menu，請大家看看

GGM
所以 rich menu 裡面要顯示什麼

Bil
也可以用「我想送一則謠言」
我可能會挑那個月最多人傳的

ＧＧＭ
這樣你就會動態要改

Ｏｒｚ
但至少可以在 LINE@ 上面改
但不只 ＧＡ，連覺得是否有用也要擋
`ga()` 前面

Lucien
我覺得要做就做完全獨立
例如說導到 staging

Orz
但這樣使用者就要重新加好友

文武：要整套分開
Lucien：
如果是個sample的話就會走跟一般bot不一樣的流程，裡面的Data都用假的 (e.g. snapshot)
GGM:
如果用程式去寫rich menu就可以送action，就不一定要純文字
或是tutorial模式

Orz:
有一個折衷的做法是在LINE @做關鍵字回應，我可以在LINEbot裡面寫
丟掉進到statement裡面，但如果你在LINE裡面做就沒辦法做到
也沒有flex message


如果一個訊息進來只有一個回應
這樣的回應就不用到很複雜的那個，不用選也沒有flex message

ＧＧＭ
這是最快可以做的。
我怎麼記得 API 開啟之後就沒有關鍵字回覆？

orz:
這可以看一下。

:::success
確認一下 API 開啟之後就沒有關鍵字回覆
若可以的話就直接實作在 LINE@ 上

Richmenu 細節再說
:::

### 調查 + 引導對話去其他 LINE@

> 開發比較複雜，放去：
https://github.com/cofacts/rumors-line-bot/issues/121

### API server 回應排序

Implement https://github.com/cofacts/rumors-line-bot/issues/78

PR of Bugfix of feedback count:
https://github.com/cofacts/rumors-api/pull/117

API server: 文武's order 
https://github.com/cofacts/rumors-api/pull/118

:::warning
還有 LINE bot, site 要改
通通都用 API server 的順序
:::

### Cofacts Refactor

FOUC 問題需要研究

### 編輯個人頁面

> ci 資訊流

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_54d0700f1395acd8a733bca5bf91411c)

讓編輯有成就感這件事情，升級。有要做其他事情嗎？
現在的網站，編輯需要的東西落在不同的地方。
一開始需要知道的是教學的東西，他其實是在Cofacts的首頁hackfodr裡面
所以我想把它做個捷徑，讓他有個快一點的做法，加入Cofacts一天可以貢獻幾篇文章，這個可以量化。

如果說給他reward那就要去看他做多少貢獻可以給獎品，有點累。
加入幾天和貢獻幾篇文章可以自動生成。
旁邊是回應列表，現在功能完整，只是旁邊分支清楚一點。

每個禮拜有多少人
文武：那個不用放在一起吧 (應該是指google analytics不用放在編輯頁面的nav bar)

bil：我有想說加積分表
回應幾篇加點數、然後每天登入也有分數、連續登入獎勵就有更高的分數。
Ｌuc:列表頁嗎？
ci:比如大選前有很多某候選人的趨勢
ci:想要看熱門謠言的關鍵字。
Luc：可以增進設計想法裡
ci：很常看到健康的謠言，但不見得好查證。這可能是偏方。
能不能用熱們關鍵字雲視覺化
bil：遊戲化的做法
ci：做互動式的遊戲比如說選是或否
ggm:像是沃草的遊戲嗎

ci:做遊戲裡面會叮叮叮的箭頭
bil:那我們做假網頁
文武：我們可以做圖片(or popup text box)放在類似的位置，告訴他大概怎麼做
把東西擺上去，讓他看到什麼東西要點在哪裡。

就是假設我請他把字填在這裡
我就跳一個框框在上面，然後他就已經知道了，他就可以繼續教他下一步。
比如說哪裡要打字哪裡要做什麼，就不用直接把字貼上去。
遊戲其實就會把某一個地方強調起上面再去蓋一層塗或是別的東西，有個箭頭這個按這個。你只是按到那個圖而已。
這樣我們就不會把垃圾資料放進來。

ggm：教學嗎 

orz:
熱門的關鍵詞可以用文字雲之類的來做

- - -

Lucien
- 明亮色系
- 白金黑如 matters / earn

Orz
希望有親民感
讓人覺得連自己也可以回應

Lucien
但白黑金有點陽春白雪

Orz
希望可以下里巴人一些
https://bloom.co/
https://www.memrise.com/

如果白黑金的話或許可以讓 fact-checking org 比較願意來


:::info
- 編輯頁面的 navigation bar 加上 tutorial
- tutorial 尚未有結論
- 文字雲
- 更以後：讓編輯的獎賞更明確，例如說 positive feedback count 也可以升級

TODO:
- Lucien 會開 design report
:::


### Wording 檢討

Ref: https://www.facebook.com/groups/cofacts/permalink/2304873386411144/

> 我覺得，Cofacts 的初衷是「將即時訊息與不同意見與其佐證資料連接起來」而不要「讓讀者在不思考的情形下受人擺佈」。
>
> 只是，在與文章作者討論之後，我覺得 LINE 使用者光看目前 bot 上給的文句，可能無法想到這一層。使用者會看到第一句「含有正確訊息」、「含有不實訊息」的 judgement，就直接照單全收，而這跟我原本想讓 chatbot 達成的效果不太一樣。

1. 避免使用者只看「含有正確訊息」與「含有不實訊息」這一句，我們可以調整 chatbot 顯示回應的順序，先講回應的理由與出處，最後一句才是「綜合以上，這位好心網友認為此訊息 含有不實資訊」。既然「就算不顯示 judgment，編輯文字裡還是有 judgement」，我們就還是顯示，只是把它移到最後面，避免先入為主。

文武
這樣字會不會變更多

Orz
會，就是多一句「網路上有人查到這個資訊：」

文武
但是分開講的話好像還好，因為使用者可以自己決定要轉傳誰的

ci
轉傳時我會跟轉傳的人先說
「我是去哪裡查，然後是這樣子的」

Ｏｒｚ
那分享的一句話呢

文武
已經濃縮過所以還好
放哪裡還好

Orz
也可以說：

> 網路上有人針對『....』查過資料唷。
>
> 請至 <cofacts URL> 看看鄉親們針對這則訊息的回應、理由，與相關的出處唷！

Bil
這個不錯

Ci
有時候長輩也會說這看看就好，為什麼要查
放「含有不實訊息」會感覺像被打臉


:::success
結論：改
:::

2. 顯示回應後，提醒使用者「以上回應為熱心網友提供，請自行斟酌上面的出處與理由，並且自行思考判斷。」然後才問使用者覺得是否有用。

ci
應該要強調這是大家自願提供的意見
像是比較大的臉書大神

bil
如果我是有疑問的人，我會想知道是對還是錯
不然我會覺得這沒有用

ci
沒有判斷能力的人會希望你提供一個完全正確的東西

可以介紹臉書大神是什麼樣的一個概念
讓人知道說，如果你相信我們，你以後也會相信其他的東西

文武
但是是有分辨能力的人才會有質疑
就算我們打那麼明確，來教育使用者要自己思考
那些只想要得到真/假答案的人，可能因為回應太長，更不想要看這些訊息

ci
這些觀念比較適合在訪談裡面說，不適合在 LINE 上面說

文武
或許可以跟質疑的人解釋，我們是為了 TA 才這樣設計的?

Orz
但質疑的聲音就會說，我們作為平台，是否責任去點醒這類容易受影響的人這件事情

文武
這是滿困難的一件事

我們可以道德上這麼做，
但若讓使用者自己判斷、想更多事情，可能效果就比較差
大部分沒辦法判斷真假的人就是會想知道答案

bil
有爭議的都是真正有爭議的訊息
例如說選舉

大家有意見的會是，如果平常都對一般軟性訊息可以確認真假，大家就會相信這個 bot
但有爭議性的，應該要標成「個人意見」
只能說之前標得不夠好

關於有爭議的人，我們可以好好解釋
但是我們不需要因此換掉自己的 TA，然後讓大家自己改
不想要改變本來做這件事情的方法

Orz
其實我希望能教我們現在的 TA 一些新的東西

:::info
Orz 再回去想想

:::

文武補充或許可以這樣:
>網路上有人說『…』含有不實訊息喔！\n\n請至 {articleUrl} 看看鄉親們針對這則訊息的回應、理由，
>⚠️️請注意：網路訊息並不是只有100%的對或錯，建議大家閱讀完可以再思考一下回應是否合理！

把顯眼的圈圈叉叉拿掉，或許就不會讓人看到叉叉就直接得到結論：『假的。』，而不思考，至少他們還要在文字堆中搜尋一下真/假的關鍵字(?)，我們想傳達的教育理念就越有可能被看見。
請注意那段不知道要使用者按轉傳的時候附上這段、linebot回復附上，或者兩邊都附；linebot回復附上，後面剛好接是否有幫助的問答。

3. 針對只有一則回應的訊息，可以隱藏 judgement 只讓使用者看理由與出處；或者還是顯示 judgement，但特別強調這判斷僅由一名網友提供，希望能有更多不同聲音。

4. 針對多則回應的訊息，在顯示完一則回應後，提醒「這個消息很多人有不同看法，或許有爭議，建議到這裡讀完所有人的回應再下判斷：(cofacts 文章連結)」

### 資料庫膨脹問題

https://github.com/cofacts/rumors-db/issues/35

上週資料庫 8GB
本週資料庫 16GB

`urls` index: 
```
  "indices" : {
    "urls_v1_0_2" : {
      "primaries" : {
        "docs" : {
          "count" : 174328,
          "deleted" : 0
        },
        "store" : {
          "size_in_bytes" : 16289322993
        },
```

Orz
mark-sweep 的好處是不用跟程式邏輯 couple

GGM
不 mark 直接掃如何？

Orz
script query 好像可以改變 operator
但好像只能拿到 url 本體來決定 op
我是要看 `article.hyperlinks` 或 `reply.hyperlinks` 是不是有 URL

GGM:
看起來無論如何都要 mark 一次
但應該是 create article / create reply 時 mark reference 才合理？






## 小聚

Checklist

- [x] 文案—— done by ci : https://g0v.hackmd.io/s/SyN-sb8b4#216-%EF%BC%88%E5%85%AD%EF%BC%89%E5%B0%8F%E8%81%9A
- [ ] 視覺 by lucien (reuse 去年)
- [ ] kktix
- [ ] 散佈
    - [ ] Facebook fanpage
    - [ ] Facebook group
    - [ ] LINE bot 貼文
    - [ ] LINE bot richmenu
- [ ] 場地（包含茶水麥克風） by ggm

## 回應酸民的流言

草稿
https://hackmd.io/FPtD5w0zQcKupyO9_MdPEw

預計散佈：
- [x] Johnson Liang 個人牆上
- [x] Cofacts fan page
- [ ] FB group

## Email 主旨：國家圖書館: 有關資訊素養工作坊-網路謠言活動

> anyone? GGM

TA: 公務員
Maybe 加上闢謠介紹？

Ci: 這個是我們要去當講者嗎
orz: yes，ＴＡ是國圖的公務員
Ci:他們時間有開？
orz: 信裡面沒有寫詳細時間就是了
Ci:我可以去講但是需要特訓ＸＤ要講什麼呢？歷史嗎？
orz: 「主軸為主講避免誤信、傳播網路謠言」
好像有點空泛，也不確定 90min 是我們 solo 還是跟國圖館員共用


## Other emails

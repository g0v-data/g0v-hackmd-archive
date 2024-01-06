---
tags: cofacts, meeting note
---

20190116 會議記錄
====
ci/文武/orz/bil
> 前次會議記錄：https://g0v.hackmd.io/s/B1X3aNfzE
> 

### API server 回應排序
- API server PRs:
    - https://github.com/cofacts/rumors-api/pull/117
    - https://github.com/cofacts/rumors-api/pull/118
- LINE bot PR:
    - https://github.com/cofacts/rumors-line-bot/pull/122
- site PR:
    - https://github.com/cofacts/rumors-site/pull/150

文武：
LINE bot 要不要對最新回應放一個「最新」？

orz:
可是排序是後端邏輯，這樣有點前後端 coupling

ci:
這樣應該可以解決之前網友說回應過時的問題。

:::success
功能 ok

發一個預告在 group 裡
:::

### 資料庫膨脹問題
PR: https://github.com/cofacts/rumors-api/pull/120

已經在 staging 跑過，也準備好 [cronjob script](https://github.com/cofacts/rumors-deploy/commit/30e2f2320e85020446f04c5b4a623d9c7250b636#diff-04c6e90faac2675aa89e2176d2eec7d8R54) 了，待 PR review。

### 理由長度限制

> 理由 15 字以下：禁止送出
> 理由跟訊息一樣：禁止送出
> 15~40 字：顯示警語（但還是允許送出）

PR: https://github.com/cofacts/rumors-line-bot/pull/123

orz:
回應沒有用的話要擋字數嗎

文武
回應沒有用的話應該不用擋

orz:
那第二個送進來的人呢

bil
還是要擋
憑什麼第二個送進來就可以比較輕鬆

orz
因為第二個送的話就代表這真的在轉傳

:::success
已經變更
:::

:::warning
### Next: 重構 LIFF & Chatbot

重點：希望簡化 LIFF 與 chatbot 之間的 state 傳輸

1. LINE 透過 URL 把東西傳給 LIFF。但是，舊的 URL 依然存在於 chatroom，所以 LIFF 載入時，無論如何都要問 chatbot server「現狀是什麼」，才能決定自己是不是「舊的 LIFF」
2. 也因為橫豎都要問 chatbot server，不如直接在 URL 傳一個無法偽造 token（maybe JWT）給 LIFF，LIFF 拿該 token 再傳回 chatbot server 取得真正的參數，或顯示「失效囉」。
3. 參數包含：要送的訊息 or 要評論的回應 `text`、當下 `state`（用來選擇 copy）、`prefix`（讓 chatbot 分辨手動輸入與 LIFF 輸出）、`issuedAt`（用來判斷是否過期）
4. 換成 token 機制之後還可以包涵：上一次寫到一半的輸入框訊息（避免意外跳出之後文字要重打）
5. optional: LIFF 內解開 JWT，檢查 user ID 是否跟 liff API 拿到的一致。沒有太大用處就是惹。
:::


### rich menu 裡附上範例

> Rich menu 中新增範例的文案，使用「關鍵字回覆」功能

- 訊息結尾加上「`〖範例訊息〗`」以資辨識
- 範例訊息無法送出、沒有 analytics

:::info
上週結論：希望透過 rich menu + keyword reply 直接模擬回應：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_bf482d6db81a57aaa50f6bfa3cd98ac0)
:::

模擬結果：失敗(？)

雖然開啟 messaging API 之後仍有 keyword reply 功能，但 keyword reply **必須要是 100% match 才行**，而每個 keyword 有 30 字長度限制，根本塞不下整個範例訊息。


:::warning
【待討論】
30 字夠嗎？若不行，那要採[原案](https://g0v.hackmd.io/FmJ7ZkbVR6mPffDeQMuFGg?both#%E6%AD%A1%E8%BF%8E%E8%A8%8A%E6%81%AF%E8%A3%A1%E9%99%84%E4%B8%8A%E7%AF%84%E4%BE%8B)？如何與原處理途徑分開處理？
:::

Orz:

因為 keyword match 只能 30 字
目前呈現的字太短，會有不好的示範，讓大家以為可以送片段訊息。

另一提案是就不用 keyword
寫在程式裡，如果 handleInput 偵測到 `〖範例訊息〗` 就不進 state machine，直接回傳設定好的一篇回應。

觸發：rich menu

或者是我們可以在 spreadsheet 之類的地方設定 article ID / reply ID
我們可以在 LIFF 裡面讓使用者選擇要傳哪個範例，
然後 LINE bot 收到`〖範例訊息〗`就回傳單篇的回應，不會有選擇回應的步驟。

缺點就是沒辦法顯示 Cofacts 正反並陳的狀況。


文武
所以不用示範多篇回應嗎

bil
大家想跟機器人聊天是因為不知道要傳什麼
所以主要是示範要傳什麼就好
讓他們定錨在那邊說，是要傳一個這種有篇幅的文字

文武
但是這樣做不知道會不會讓不會用的人變成會用

對於那種人，還是要拍一些影片

orz
可以放在歡迎訊息裡。

:::success
Action item:
- LIFF 選擇範例訊息
- 準備簡短使用影片教學，放在 welcome message 以及 Rich menu （URL 填 youtube）
    - 第一段：轉傳訊息進來得到回應的樣子，鼓勵轉傳回去
    - 第二段：正反並陳狀況
    - 第三段：都找不到時的新增流程
:::

### Design report

> Lucien
> 

## Wording 檢討

Ref: https://www.facebook.com/groups/cofacts/permalink/2304873386411144/

### 1. 避免使用者只看「含有正確訊息」與「含有不實訊息」這一句，我們可以調整 chatbot 顯示回應的順序，先講回應的理由與出處，最後一句才是「綜合以上，這位好心網友認為此訊息 含有不實資訊」。既然「就算不顯示 judgment，編輯文字裡還是有 judgement」，我們就還是顯示，只是把它移到最後面，避免先入為主。

:::success
原決議：照樣通過
:::

### 2. 顯示回應後，提醒使用者「以上回應為熱心網友提供，請自行斟酌上面的出處與理由，並且自行思考判斷。」然後才問使用者覺得是否有用。

:::info
前情提要：

討論到後來其實跟 TA 有關：
1. 不希望為了本來就知道要懷疑要查證的人，放掉原本這些不知如何判斷的 TA。
2. 但也希望對現在的 TA 多教一些東西。


會後提議 By 文武：

網路上有人說『…』含有不實訊息喔！

請至 {articleUrl} 看看鄉親們針對這則訊息的回應、理由，

⚠️️請注意：網路訊息並不是只有100%的對或錯，建議大家閱讀完可以再思考一下回應是否合理！

> 把顯眼的圈圈叉叉拿掉，或許就不會讓人看到叉叉就直接得到結論：『假的。』，而不思考，至少他們還要在文字堆中搜尋一下真/假的關鍵字(?)，我們想傳達的教育理念就越有可能被看見。
請注意那段不知道要使用者按轉傳的時候附上這段、linebot回復附上，或者兩邊都附；linebot回復附上，後面剛好接是否有幫助的問答。
:::

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6fb7c41f0ebdff2fb8f94f8c9c69b03d)

Bil
網友有說葉佩雯通常會七分真三分假

但我覺得只要有一分是假的，基本上就是沒有參考價值的
也不是有責任的文章

本來就不會 100% 是真假。

如果我們想傳達「不能完全相信我們」這件事，那就改成

>「以上資訊由好心人提供，請斟酌出處與理由，思考判斷」

盡量簡短就好

一開始做 fact checking 就是在處理傳了一二十年的訊息

如果他要討論的是「我們文章不想被標成謠言」那應該標成「含有個人意見」我們再來處理

但只要有錯我們就應該勸長輩不能相信，這才是保守的做法

例如說詐騙裡面可能有真的，但應該還是要教他們這是假的

要教他們，希望不要相信他們，做到「謠言就到這裡」然後不要傳了
而不是「這資訊裡還有兩成對你有幫助」然後他又發出去

比起「不要相信我們」而是「不要相信任何網路上的東西」

orz:
那 share 出去的文字要加「斟酌出處」嗎？
使用者可以自己打字

bil:
我覺得不用

### 3. 針對只有一則回應的訊息，可以隱藏 judgement 只讓使用者看理由與出處；或者還是顯示 judgement，但特別強調這判斷僅由一名網友提供，希望能有更多不同聲音。

bil
比起說「這個只有一個回應，所以我不告訴你這真的還假的」
不如鼓勵大家多多回應

可以把原本的 URL 給他，說這個回應來自這裡，
如果對這個訊息有不同想法，歡迎在這裡加入你的回應

```
⬆️ 綜合以上，回應者認為它含有不實訊息。

💁 以上資訊由好心人提供。請斟酌出處與理由思考判斷。

⁉️ 如果你對這則訊息有不同看法，歡迎到下面這裡寫入新的回應： https://cofacts.hacktabl.org/article/r1ml04vtjqhw 

```

:::success
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4f72050d6b5059d53cc267d17215dac3)
:::


### 4. 針對多則回應的訊息，在顯示完一則回應後，提醒「這個消息很多人有不同看法，或許有爭議，建議到這裡讀完所有人的回應再下判斷：(cofacts 文章連結)」

好。

```
⬆️ 綜合以上，回應者認為它含有不實訊息。

💁 以上資訊由好心人提供。請斟酌出處與理由思考判斷。

🗣️ 這則訊息有很多不同回應，建議到這裡一次讀完再下判斷：https://cofacts.hacktabl.org/article/r1ml04vtjqhw 

⁉️ 如果你對這則訊息有不同看法，歡迎到下面這裡寫入新的回應：https://cofacts.hacktabl.org/article/r1ml04vtjqhw 
```

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d556a30b0132fa04a1d8952654f57ed3)

桓:
有美玉姨之後，會不會我們的 TA 就不會來我們這裡來了
但因為他可以直接告訴他們是真的是假的

我們在想要教育 TA，但他們可能不來用了，
選擇使用美玉姨，可能就不會看到我們的一番苦心

orz
我們想做的還是坐在上面

bil
我們的使用者可能是同一批人

如果我們沒有良好的溝通的話，不確定是不是能做到幫助人這件事，會變成討論平台

媒體識讀的 TA 可能會到不了

ci
美玉姨會讓 cofacts 回應更多，但官方 account 流量可能會變少

orz
只要我們使用者還在上升，上面改的就不是徒勞無功吧

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_bc64c3831b12dc1883a917f0e58f05e4)

所以好像還好


### 同場加映：美玉姨 footer

現況：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_eda7436bb21ab4c16b8dc6ea76f95466)


改成文章 URL，邀請覺得有錯的人直接修正回應？

桓誠:
我加這個的時候是想說我們的網頁有個很明顯的「立刻開始闢謠」，大家比較方便直接加入

也許上面「包含個人觀點」那邊應該加上文章網址？


:::success
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c1508272d7d2d41d0d4864558d022d5d)
:::

orz:
把美玉姨的使用者導來網站上闢謠

但這樣亂闢謠的人會變多

- https://cofacts.g0v.tw/reply/ygDnO2gBP8WrztivAg79
- https://cofacts.g0v.tw/reply/-_-WNWgBP8WrztivFdU1


bil
就變多吧
要先讓這樣的人變多，才能決定標準要放在哪裡



## 小聚

- [x] 文案—— done by ci : https://g0v.hackmd.io/s/SyN-sb8b4#216-%EF%BC%88%E5%85%AD%EF%BC%89%E5%B0%8F%E8%81%9A
- [ ] 視覺 by lucien (reuse 去年)
- [x] 邀請人：ci
    - 10~15 talk + Q&A
    - 可以 recruit
    - 車馬費實報實銷（台中上來很遠所以要這個）
- [x] kktix
- [ ] 散佈
    - [ ] Facebook fanpage
    - [ ] Facebook group
    - [ ] LINE bot 貼文
    - [ ] LINE bot richmenu
- 場地 by ggm
    - [x] 包含茶水麥克風
    - [ ] ~~開吧樓下的餐廳直接送上來？？~~ -- 那是實驗廚房，週末沒開
    - [ ] 片鴨、韓式飯捲

## Lulu proposal

https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP#ts-1547456950.066600

### 1/22下午 學生營隊

> Lulu: 我是想說或許我就以自身使用闢謠後台的經驗，向核心的學生志工介紹怎麼使用，因為你們網站上其實也已經有非常詳細的介紹。
> 當然，如果 cofacts 團隊有興趣親自跟學生交流介紹怎麼使用編輯平台，那就更棒了，1/22 也可以安排你們直接說明。
> 


### 1/22 出席 meeting

GGM 去

### LINE today 協助

GGM 跟 lulu 聊

### 幫我看看這篇關於美玉姨的稿子 放在真的假的Medium用

https://medium.com/p/12f58d0081c9/edit

Profile: https://developers.line.biz/en/reference/social-api/#get-user-profile

- displayName
- userId （不是使用者設定的 ID，是 LINE 另外發的）
- pictureUrl
- statusMessage
基本上就是點開一個 avatar 可以看到的資訊


因為 LINE 這裡收到的 user id 不能沒辦法賣廣告（作為廣告標地來弄再行銷([retargeting](https://transbiz.com.tw/retargeting-%E5%86%8D%E8%A1%8C%E9%8A%B7/))之類）
，所以收到對話紀錄裡即使有「我要買什麼」之類的瀏覽紀錄，也沒有什麼商業的獲利空間，因為我們沒辦法在 LINE 之外找到這個人再投遞廣告給他。

「你應該要小心任何人被加進群組」
因為性質跟加一個不認識的人進去群組的意義一磨一樣
真人看得到的東西機器人也看得到
看不到的也看不到
API 只看得到照片、顯示名稱、status message

而且你可以懷疑
懷疑都是
這不是做不到的事


價值僅止於輿情分析
獨家性

但是沒有什麼商業價值
要錄下來不是不行

技術上可行

像這種類似的東西
165反詐騙
趨勢科技防詐達人
解決臉書賣場的詐騙 跟假的臉書頁面

Orz 補充：
防詐達人的首頁也有提到關於隱私的部分：
https://www.getdr.com/


防詐達人完全沒有開源，被加入群組也不會打招呼，就是在網路上擺一個聲明而已。

到頭來就還是基礎的人際信任問題，你如果相信他，他沒給你證據，你也會死心踏地地相信；如果你一開始就不信任，就算給你再多分析、說再多實話給你聽，你還是會懷疑。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7eede3123b72ea075da1500b78e5180e)



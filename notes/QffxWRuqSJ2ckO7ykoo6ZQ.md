---
tags: cofacts, meeting note
---

20190320 會議記錄
=====

> 上次開會紀錄：https://g0v.hackmd.io/s/Hk5zZw8v4

## 四月小聚！！

- 4/13
- 4/20 * Most vote - Billion, Lucien, ci, GGM, johnson
- 4/27

主題：紫藤花

## 讓群組 bot 更友善

bil
如果大家對美玉姨覺得直接回應不友善，那有沒有方法可以私訊查證給轉傳的人，或者是轉傳的人的朋友？

ggm:
使用者私訊跟在群組裡面的 user id 好像是不同的 id，
所以好像做不到。

:::warning
結論：
好像做不到。
:::

## 大松發文 ＆ FB group
> 上次還沒發 ＱＱ

### URL preview bug ＆ "good first issue"
(eddy 做的 URL preview)
感謝闢謠的人：
- yingtso
- Haku 
- Lin

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_67f90496587d7bf8f7fc28e776a7bab3)

```
大家有沒有發現，Cofacts 網站上的 URL preview 變得不太一樣呢？即使在手機上，URL 也不會破版囉！

感謝 agameofprivacy 在 3/9 大松的貢獻！

- - -

現在 Cofacts 網站仍然也有很多待解的 issue 唷，如果會 React.js、有興趣一起來幫忙的話，可以參考這些 Good first issue: https://github.com/cofacts/rumors-site/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22

```

### Copy button 功能介紹
https://github.com/cofacts/rumors-site/pull/155

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b5380f78818269e0ce68fdd939219fc3)

```
複製貼上 Cofacts 的回應，現在更方便囉！

回應的下面現在有「複製到剪貼簿」按鈕，按下去就能把理由、出處與頁面網址一併複製，方便貼到其他地方。

對想複製修改他人回應的 Cofacts 編輯來說也很好用唷！

- - -

如果會 React.js、有興趣一起來幫忙的話，歡迎一起讓網站更好用: https://github.com/cofacts/rumors-site/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22
```

### 新報表 Message lifetime
https://datastudio.google.com/reporting/18J8jZYumsoaCPBk9bdRd97GKvi_W5v-r/page/SWyk
- 感謝 ttcat 研發

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5e0f529ea97c1ef814588a2e23ac7416)

```

```

## LINE bot 訊息送不出去 bug
https://www.facebook.com/groups/cofacts/permalink/2346671315564684/

Github issue: https://github.com/cofacts/rumors-line-bot/issues/129
滿常發生的⋯⋯


orz:
好像是因為 truncate 字的時候切到 emoji
`encodeURIComponent` 

這樣只要講話就會出錯。

ggm:
好像滿嚴重的
要怎麼修

orz:
好像可以 try catch
如果 catch 起來，就傳個「你的訊息」進去

ggm:
好呀那就不 preview

:::success
把修理的方式記錄在 issue 129
:::


## 我愛家我聯絡 - 按讚版

TODO: 更好的分類器⋯⋯

## 比鄰錄音

bil：
先看反應如何

ggm:
好像可以錄成 podcast 然後上 spotify 之類的

bil:
想要 for 成人
爐邊談話

ggm:
滿好玩的噎

bil
那你也來錄

ggm:
但使用者會因為聽起來舒服而聽

orz:
但可能要錄到一個量之後才會有很多人聽

:::info
發現有 1/10 的 FB 粉絲看了～
:::

ggm:
但粉絲頁貼文 https://www.facebook.com/cofacts.tw/posts/349961788951205 一次放了兩個連結，會讓大家不知道要點哪個

orz:
應該用 picsee~

你可以給我稿子 我就會幫你生圖
可以把聲音 CC0

開源圖庫：https://g0v.hackmd.io/7aeYEbErQrOXnYiAvlIkVQ

:::success
如果鶴覺得有人看，就會再錄下一集ㄛ
:::


## Wiki & Cofacts
https://docs.google.com/document/d/1HJ7kxMUpU_N-HILZ5QbLbmvPgOmHEeTkdMBVDGxKivQ/edit?ts=5c909f26
sorry wiki婉拒了 等青發署回應

orz:
其實 wiki 那裡的提案應該可以跟假訊息或媒體識讀無關，他可以做維基編輯培訓（從改錯字那些開始）。

bil:
可能是 Reke 那裡就是沒有資源吧

orz
那我們這裡如果要執行我們自己的計劃，要做什麼呢

bil:
出講師講課

那就是我們這裡計算積分
然後會有志工名冊
我們就輸出這些志工的積分

想說可以做獎狀呀

但教育部說獎狀有限量所以不行

他有短期的專款專用，可以來台南或高雄

orz
那就會變成我們要出講師

bil
可能台北台南高雄，然後住一晚之類
交通的部分有經費就經費出

ggm
確定的地點有哪些呀

bil
沒有，教育部去忙別的案子，就沒有講這件事情

:::success
現況：
目前已經寄出 proposal，等待教育部回信
:::

## 假新聞清潔劑在約學生講座
臺北大學有學生也想舉辦像是樂齡中心的講座，可是他們沒有辦法提供講師費。

比鄰回覆沒有講師費沒關係，時間許可的話很樂意幫忙，但希望能早點確認時間表。


## Review article list page

> cc. Lucien

Lucien: 上週的對話作為 spec 沒問題。

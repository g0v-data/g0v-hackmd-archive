---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20200715 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：orz, bil, 文武, Zoe, GGM, Lucien
:::

## Cofacts Next! 追蹤

- [收尾] Category 標記
    - 待大松收 feedback
- [收尾]  Chatbot notification
    - GA
        - Owner: MrOrz
        - 因為不用追 feedback，所以做到 LIFF 內用 `utm_source` 追點擊就好
            - 不做「追蹤回 chatbot」的部分了
            - 點 article item 會送 GA event
                - utm_source 來 filter 出 event 數 (?)
                - 還沒測
        - 已改 README、PR 開放 review：https://github.com/cofacts/rumors-line-bot/pull/206
    - Notification
        - owner: 文武
        - PR: approved https://github.com/cofacts/rumors-line-bot/pull/207
            - Blocked by GGM's https://github.com/cofacts/rumors-line-bot/pull/201
                - 等 #201 進之後 rebase
            - Line Notify 是在外部視窗，可能要請使用者回 `https://line.me/R/ti/p/@cofacts` 自己點開 menu (無法追蹤 utm_source)
            - article id --> user 的 query 可以加 pagniation
            - 可能用 list of user id 找 list of user settings (?)
            - 會放在一起
        - ETA: 7/22
    - New `userArticleLink`
        - owner: GGM
        - PR: change pending https://github.com/cofacts/rumors-line-bot/pull/201
        - ETA: 大松前？
- Article analytics from GA
    - Owner: Zoe
    - Tracking board: https://github.com/orgs/cofacts/projects/7
    - ETA Plan: 8/10 for API, 9/7 for UI
    - 遭遇問題：
        - Page URL 2 會包含 query param 如 fbclid
            - 雖然可以濾掉，但不同 query param 會使 row 數大幅增加
        - [content grouping + regular expression](https://support.google.com/analytics/answer/3333221
) 可解，但只會 apply 在之後
        - 目前使用：![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_16b9a4e7cfb4e6d9615b1879292f94b0.png)

- `ArticlePageLayout` refactor
    - Owner: MrOrz
    - Spec: https://g0v.hackmd.io/h8rP0TOGTh2Clxi_Oi_QKw
    - Plan
      - 1st PR 已發 [#267](https://github.com/cofacts/rumors-site/pull/267) , [#268](https://github.com/cofacts/rumors-site/pull/268) 無人 review 故 merge
      - 2nd PR:
        - 前置作業: [#287](https://github.com/cofacts/rumors-site/pull/287), [#289](https://github.com/cofacts/rumors-site/pull/289), [#290](https://github.com/cofacts/rumors-site/pull/290)
        - 主 PR: https://github.com/cofacts/rumors-site/pull/288 希望 7/20 ready
      - 3rd PR: 希望松前

- User ID refactor
    - Owner: MrOrz
    - Spec: https://g0v.hackmd.io/ZcoUOX_-RQSkJyl5xz4_Zg?view#%E6%96%B9%E5%90%91-2-%E9%87%9D%E5%B0%8D%E6%AF%8F%E5%80%8B-backend-user-%E9%83%BD%E7%94%A2%E7%94%9F%E4%B8%80%E5%80%8B-user-document
    - Plan: GG

- 教學頁 spec
    - owner: Lucien
    - ETA：下週

## Cofacts Next! 未竟事項

- [上週項目](https://g0v.hackmd.io/ehzopA3fScSn9PjkBM79bA?both#Cofacts-Next-%E6%9C%AA%E7%AB%9F%E4%BA%8B%E9%A0%85)已開票，更新票號在上週 hackmd。
- 比鄰回報 Add this reply 功能不能複製出處 https://github.com/cofacts/rumors-site/issues/285
- TFC 回報 iOS 上網站無法搜尋 https://github.com/cofacts/rumors-site/issues/280

### 確認：Landing page & No result

https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=994%3A111

search

MrOrz:
灰階最右邊
因為比較細比較跟 UI 融合
而且很瘦很滄桑 (?)

Lucien
搜尋找不到 灰階比較能跟 ＵＩ融合
如果是整頁 404 (無此文章) 的話，也可以考慮用彩色版本
ex: https://cofacts.org/askldfjalksdfjasdf
ex: https://cofacts.org/article/asdfasdfasdfasd

ggm
灰階好像整頁都灰階比較好
單獨灰階有點怪怪的
想一想還是選彩色

彩色：bil、lucien (整頁都空白的如 404 時)

灰階3：文武、ggm、(zoe 選灰階)
灰階4: orz、(zoe 選灰階)、lucien (search page only)

lucien
螢幕（臉）的部分可以閃不同顏色

orz
如果是整頁空白的 404 我覺得可以比較 fancy 例如螢幕閃顏色
但 search result 我想讓使用者快點捲回去放寬搜尋條件

lucien
灰階 3 的線條有修過嗎

orz
好像沒有，
就變淡而已

:::success
Landing page: 最右邊 :heavy_check_mark: 

Search result: 灰階粗版（第三個選項）
:::

### 討論：搜尋回應功能顯示「自己剛回過」的回應

- Issue: https://github.com/cofacts/rumors-site/issues/243
- 3 月許的願: https://g0v-slack-archive.g0v.ronny.tw/index/channel/C2PPMRQGP/2020-03#ts-1584415185.236800
- 是否要在沒搜尋的時候顯示最新幾篇自己的回應？

MrOrz
我自己的情境是，上次在回全聯消費券的訊息的時候，就是寫了一個回應，但還要複製自己回應的一部分，才能到另一篇一樣的訊息底下搜尋自己的訊息

bil
這是比較少發生的狀況，通常這篇跟下一篇完全是不同的訊息

:::info

發現其他問題：

- 搜尋框漏了「參考過往回應」的 placeholder
    - iOS 上點按「Add this reply to my reply」會直接送出回應！
- 無法拉大，結果呈現在很小的地方
- 有時候其實只是想看一看，按搜尋旁邊的 X 關掉實在太不直觀
- Enter 搜尋不直觀，而且 iOS 上 enter 會顯示「換行」
- loading state

先把上面基礎的 UX issue 修掉，才會有人真的在使用、進階 use case 才比較有意義

開票～
:::

### 討論：讓作者能編輯回應

- Previous discussion: [20200212 meeting](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2F%40mrorz%2Fr1dQQZbmU)
- Ticket: https://github.com/cofacts/rumors-api/issues/184
  - API response 可以[參考 Medium 使用 union type](https://medium.com/@sachee/200-ok-error-handling-in-graphql-7ec869aec9bc)

> 雖然當時討論的結論是「有用在多個回應就無法編輯」，但我在疫情期間回應那些「某某某處有確診者」的訊息時，確實會用一則回應回到複數文章底下，然後想要一起修改的。再者，檢查「是不是所有 articleReply 都是目前使用者的」跟「目前有沒有 articleReply」技術上是一樣的（持 reply.replyId 查找 article.articleReply），所以就把需求改回「只要回應都是作者加的，被用在多則文章下也一樣可以編輯」囉。
> [name=MrOrz]
> 
> 放寬修改的限制我覺得很棒，但如果思考一下，如果改成，被引用的瞬間， duplicate 一份所有被引用的回應，讓所有引用都是對應到一個副本，是不是可以解決這個問題。
> [name=Lucien]
> 
> 這樣確實可以解決 article reply feedback 對應到 reply 文字的問題
但這也代表修改回應文字時，只會修改在一個 article reply 上這樣嗎？
如果是這樣的話，我想到會有下面 issue:
我自己的使用習慣是會蒐集 N 個類似訊息、寫一個回應，然後通通連結到同一個回應。如果我發現原始回應有錯字想改、或是想到更好的寫法或出處，我就要改 N 次。
duplicate 之後再進行修改，此 articleReply 的 id 仍然保留原本 reply，但 reply text 可能已經不同。在 text 不一樣的狀況下，我們還能說這個 reply id 有連結到此 article 嗎？
承 2，目前「加入現有回應」搜尋結果，其實會過濾掉已經被加過的回應。如果現在某人加了回應 R 並且修改內容為 R'（但仍然使用 R 的 ID）。之後，另外一個編輯看到了，覺得應該要用 R 比較好，但他搜尋時就會很納悶怎麼沒有 R 。
> [name=MrOrz]
> 
> 我的用意是，不想讓原作者修改自己的意見會被 Blocked ，目標是他可以改自己以及自己引用自己的結果，但其他已被引用的回覆，與原文隔離開，不受影響原作者修改影響
> [name=Lucien]

bil
其實讓已刪除回應只有作者自己看得到就好了

目標都是讓使用者看到比較好的資訊，
那刪除比較好，因為可能會誤觸到已經被刪除的回應
不是每個人都看得到那個「本回應已經被刪除」這個小字

orz
我自己是有從「已經刪除的回應」裡面，
看到過自己之前沒有找到的資料
不過只有發生過一兩次

不過編輯的話應該就不用複製貼上，應該還是有用？

bil
現在已經有複製到剪貼簿功能
可以繼續用

orz
好的那編輯功能看起來 priority 不高

:::warning
Deprioritized this item
:::

## 開放 Category 編輯
> - [0708 討論新分類](https://g0v.hackmd.io/ehzopA3fScSn9PjkBM79bA?both)
> - [0408 討論 description 是否足夠](https://g0v.hackmd.io/@mrorz/rksKX45D8#Category-%E4%B8%8A%E7%B7%9A%E7%BC%BA%E4%BB%80%E9%BA%BC)
> - [0304 討論大松開放](https://g0v.hackmd.io/@johnson/ByAb_n24U#314-%E5%A4%A7%E6%9D%BE%E7%B1%8C%E5%82%99)
> 
> 正反案例https://docs.google.com/spreadsheets/d/1EEj1VMEvCHzrhIivRsCTtzYAW_zrD3jaMRddqs_8tJQ/edit#gid=484232713

- 大松時要讓大家開放標記
    > 如果大松要準備開放讓大家體驗標記 category，那我們要在大松之前把這些文件資料備齊呢？
    - 如何讓大家知道定義？
    - 如何劃定「這種標籤有人會看」
    - 是否要表列正反例
- 如何決定新增新標籤
    - 有意義但原本沒地方放
    - 有地方放但太廣、太滿
        - ex: 通通塞在保健 or 政治
    - 0708 提案：`COVID-19 疫情`、`國際關係`

orz:
其實[案例文件](https://docs.google.com/spreadsheets/d/1EEj1VMEvCHzrhIivRsCTtzYAW_zrD3jaMRddqs_8tJQ/edit#gid=484232713) 的 stakeholder 才是真正的 definition
要判斷的時候其實是在想像「這種人會不會想看」在標的

甚至還有連 description 都沒有的：
- 有意義但不包含在以上標籤
- 無意義
- 廣告
- 只有網址其他資訊不足
- 政治、政黨
- 轉發協尋、捐款捐贈

兩種解法：

1. 改 category 的名字
    - 換成用人 / persona / expertise 取名，但很難取
2. 把 stakeholder 寫進 description（「會對這個主題有興趣的人」/「此主題的目標群眾」）

沒有真正 target audience 的標籤 (11, 12, 14)
就先說「AI 專用，請勿選擇。」

:::success
orz 先開一個 hackmd
把 [category 的 definition](https://docs.google.com/spreadsheets/d/1EEj1VMEvCHzrhIivRsCTtzYAW_zrD3jaMRddqs_8tJQ/edit#gid=484232713) 改寫之後
放到 slack 大家討論
:::

## :potable_water: Release pipeline

### :star: Released to production

#### Chatbot ([20200710 Release](https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20200710))

No visual change, mostly prepare for user-article link related logic

> 這次上的主要是跟「已讀訊息列表」以及 notification 設定相關的變更。不過，測試時就有發現設定上似乎有些問題、導致「已讀訊息列表」一直打不開。
> 所幸目前兩個功能都還沒開放讓使用者直接使用，先把這些 code 放上 production 看看是否會影響正常功能運作，就是這次觀察的重點了。
> [name=mrorz]

### :rocket: Staging

#### Chatbot

> Should fix Staging chatbot's LIFF

#### Website

##### Feature
- #268 "Replied by me" and reply type filters

##### Bugfixes

- #272 Add category

##### Others

- #267 Global style adjustment; storybook style update

##### Testing checklist

http://dev.cofacts.org/

**未登入**下檢測：

- [x] Article list
  - [x] Filter works
  - [x] Sorting works
  - [x] Can go to article page
- [x] Replies list
  - [x] Filter works
    - [x] 不允許選擇 Replied by me
  - [x] Sorting works
  - [x] Can go to article page
  - [x] 不允許 upvote / downvote replies
  - [x] Can see vote reasons
- [x] Hoax for you
  - [x] Filter works
  - [x] Sorting works
  - [x] Can go to article page
- [x] Article detail
  - [x] Can see similar messages ( https://dev.cofacts.org/article/1fi7dla9wtwjn )
      - 可能會誤觸隱形的「reply to this message」⋯⋯
  - [ ] ~~Can see deleted replies~~ 會拿掉所以不測
  - [x] Cannot submit, upvote, downvote reply request
  - [x] Cannot submit, upvote, downvote reply
  - [x] Cannot add, remove, upvote, downvote category
- [x] Search
  - [x] Can use global search to perform search
  - [x] Can use textarea in header to perform searchs
  - [x] Can list searched articles
    - [x] Filter works
    - [x] Sorting works
    - [x] Can go to article page
  - [x] Can list searched replies
    - [x] Can go to reply page

登入自有帳號後檢測：
- [x] Replies search page
  - [x] can upvote / downvote replies
- [x] Replies list
  - [x] 可選擇 Replied by me
  - [x] can upvote / downvote replies
      - 好像變得可以 upvote / downvote 自己的回應了 ._. https://dev.cofacts.org/article/jo5fzdblep6k
- [x] Article detail
  - [x] Can submit, upvote, downvote reply request
  - [x] Can submit, remove own reply
  - [x] Can upvote, downvote other's article reply
  - [x] Can add, remove, upvote, downvote category
- [x] Can logout

##### ⛔️ Release Blockers

##### 未竟項目

orz:
好像可以 upvote / downvote 自己的回應了 
https://dev.cofacts.org/article/jo5fzdblep6k
但又不是每個都可以?

bil:
Upvote 按下去之後框框會讓人不想繼續 upvote

文武：
搜尋按 enter 比較習慣是送出搜尋吧
related: https://github.com/cofacts/rumors-site/issues/281

可以貼上多行的訊息
但 enter 應該是送出

另外，搜尋結果的 filter 因為在外面也有看過，會沒有意識到這個是搜尋的 filter

或許應該跟搜尋框一起放在黑底上

:::success
未竟項目開票
無 release blocker
可以 release~
:::

### :eye: Under review

All mentioned in Cofacts Next! 追蹤

## 回應「沒有」的正評

> 這些 feedback 寫「沒有」兩個字的，都是覺得回應有用的。
> 看來是因為我們在使用者回報一個回應有用時，會這樣問使用者：
> ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2a1ef51b635b849f96df867e3ddb83d6.png =x400)
> 這個提問導致使用者輸入「沒有」然後送出。但在 Cofacts 網站上，就會看到有一堆人 upvote 然後又表示「沒有」，有點沒頭沒尾。
> 這 copy 該怎麼改呢 :thinking_face:
> [name=MrOrz]
> 「想補充回應、或有話想跟編輯說，可以在下面留言唷！」這樣嗎
> [name=MrOrz]
> 可以用 place holder 寫「沒有其他意見」之類的，這樣使用者應該會直接按送出？
> [name=stimim]

ggm
改長之後使用者還是會打「沒有」送出

bil
現在 UI 上面就一個送出按鈕
使用者就是會想輸入然後送出

orz
其實看到這頁的時候 vote 已經按了「是」
按之前不會知道要填
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b84cbed2ba3798ee6a8995cf3f29afae.png)

bil
右上角關閉也不直覺
使用者會記得那個「是」「否」要填東西很討厭
下一次就直接不按

ggm
我覺得有用還是會按

bil
把「送出」換成「謝謝」

orz
送出（黃色） + 關閉（刪除）

zoe
如果不希望大家寫「沒有」
還是再多一個步驟要點開什麼的
要真的很想寫才會寫

lucien
但我們希望他寫些東西

bil
如果很想寫謝謝，那就提供按鈕

orz
像蝦皮嗎
超讚的出貨速度

做得跟 reply template 一樣

bil
編輯不會看到被通知好評價
所以編輯還好

ggm
之後 profile page 應該會撈出來
（資料庫要加欄位）

ｏｒｚ
拍賣的 scenario 下看到罐頭會反感嗎
我是還好，最後都看人頭數

ggm
無感

orz
我覺得先用 stimim 的作法ㄅ

:::success
use stimim
:::


## 回應小技巧整理

我自己在寫 Cofacts 回應的時候，有掌握到一些讓回應比較好讀好入口的小技巧，整理在這裡（草稿）：
https://hackmd.io/@cofacts/S1XQu2c1D
大家可以把看到覺得寫得很好的 Cofacts 回應提供給我唷，這份文件的每一個 tip 都需要案例 QQ
也說不定可以從案例中歸納出新的技巧。
目前 hackfoldr 裡面，針對編輯的有 [UI 操作說明](https://beta.hackfoldr.org/1yXwRJwFNFHNJibKENnLCAV5xB8jnUvEwY_oUq-KcETU/https%253A%252F%252Fhackmd.io%252Fs%252FSyKNjDUCe)，或者是涵蓋比較全面（從分析到撰寫）的[奇幻旅程](https://hackmd.io/@mrorz/B1ul5U86-/%2Fs%2FSJyNsLIpb?type=book)。此份文件聚焦在寫作技巧，希望讓編輯有不同的靈感

:::info
- Continue?
- Examples?
:::


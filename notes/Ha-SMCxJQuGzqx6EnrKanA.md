---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20201118 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：bil, mrorz, nonumpa, hsiao
:::

## FB 教學

:::info
一直沒空做啊⋯⋯
:::
see [20201104](https://g0v.hackmd.io/Sl_84QO8TQ6WKKI0bT4pYw?both#Cofacts-Next-%E8%BF%BD%E8%B9%A4)

## 十傑檢討
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_70b5a60a61e3f2c83e10f3d3798457ec.png)

### New login method

- Google
- Instagram
- AppleID

:::success
開票: https://github.com/cofacts/rumors-api/issues/234
:::


### Login issue
> ~~API 目前 Facebook redirect 回來一律會到 cofacts.g0v.tw
所以如果從 cofacts.org 登入的話
第一次登入會遇到 session redirect 不存在的問題 @@~~
> [name=mrorz]

即使是使用 cofacts.org 登入，登入時也是導向到 `cofacts-api.g0v.tw`，
與 `XXX_CALLBACK_URL` 設定一致。因此，login cookie 應該會有正確設定。
除非瀏覽器有特別擋 not same-site 的 cookie。

重現方式：
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fc6269cb6dfbd4076070ee0ed1dd0eae.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f38e19de0c96c54ef211c3b5eee7a7cf.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6cdb12b1c677829f275352f8f60ffda6.png)

但事實上 cookie 是有正確設定 `SameSite=None, Secure=true`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_26fba974fe79e5c3d1b695eb802c01f0.png)

(當天有出問題的使用者，確實習慣使用 Chrome for iOS + 無痕模式，可能預設有開啟「封鎖第三方 Cookie」⋯⋯)


### 手機版 spreadsheet 無法改 tab

--> 用電腦。要帶電腦。

### 手機版寫回應時沒有擋「沒寫 reference」的狀況
> 手機版送回應的時候沒有檢查 reference 是否存在
> 會送到後端然後再噴出英文的 error

:::success
--> https://github.com/cofacts/rumors-site/issues/278
:::

- - -

bil
需要前置志工訓練

ex:
可以開放 staging 練習，確認大家知道怎麼用
練習 20 篇之後再寫回應之類的

orz
如果編輯人不夠
可能就不要教寫新回應，主要讓他們按有用沒用
先觀摩

去年是兩人兩人一組，所以我們要顧的人比較少，而且他們討論過後的東西也比較有品質

bil
要先讓他們練習
這樣比較不會害怕

文武
應該有範例？

bil
範例很精美，很難回的不會放在裡面

文武
有問題應該會在現場問？

bil
主動提問

文武
在 staging 應該不會解決問題

bil
可以幫他按有用沒用，提供理由

文武
這樣的話我們會比較辛苦

bil
這可能是必要的支出

社群要長大的話應該要志工訓練時間

小聚 20 min 可能不太夠

不會再要求小聚裡要回完 10 篇
而是應該要注重品質

學會技能更有意義

- 看到不知所云的訊息怎麼找
- 如何找關鍵字
- 說明不在查證範圍的部分
- template button
	- ⋯⋯拿掉
	- 日期拿掉

新小聚流程

2:00 - 5:00 

- 2:00 ~ 3:00 教學

:::success
想一個新的小聚教案
:::

## SEO for landing page

> 關於 SEO，我之前有個想法忘記在會議上提出。
> 大致上的概念是：既然 Google 搜尋不支援 accept-language 自動偵測，那我們一個 domain 就固定用一種語言好。
> 我提議我們改成
> cofacts.org, cofacts.g0v.tw, zh.cofacts.org  三個 domain 永遠 serve 中文版
> en.cofacts.org 永遠 serve 英文版
> 無論是哪個版本，都採用 google 建議，使用 <link rel="alternate" hreflang="lang_code" href="url_of_page" /> 指向所有語言
> 在瀏覽器用 navigator.language 偵測瀏覽器語言，如果語言與 UI 不同，則顯示一個切換語言的 banner，顯示同一個頁面的不同語言 URL
> 這樣應該可以讓最長被使用的 cofacts.g0v.tw, cofacts.org 的 <html lang 在 index 時是受眾最常用的中文，也解決中文首頁 SEO 的問題。
> See: https://github.com/cofacts/rumors-site/issues/347#issuecomment-718878471
> [name=mrorz]

> 關於有三個版本都 serve 中文版這件事情，中文版可能要挑一個 URL 當作 canonical URL。
> https://developers.google.com/search/docs/advanced/crawling/consolidate-duplicate-urls?hl=zh-Hant&visit_id=637408030503556838-3312092471&rd=1
> 目前 cofacts.g0v.tw 是被 index 最多的版本，如果換 canonical url 到 cofacts.org 的話，page rank 會掉嗎？
> [name=mrorz]

> 會掉page rank吧
> [name=lucien]

> 我發現 Google 其實不認為只翻譯 UI 字串的網站就多語網站。
> > Translating only the boilerplate text of your pages while keeping the bulk of your content in a single language (as often happens on pages featuring user-generated content) can create a bad user experience if the same content appears multiple times in search results with various boilerplate languages.
> https://developers.google.com/search/docs/advanced/crawling/managing-multi-regional-sites#make-sure-the-page-language-is-obvious
> 
> 那我覺得我們還是
> 把基於 http request header 的自動語言偵測功能拿掉；en.xxx server 英文 UI，其他一律 serve 中文 UI
> 無論哪個版本的網址，canonical 一律使用 cofacts.org/xxx 避免重複爬取
> 除了整頁都英文的 landing page 之外，其他頁面都不下 hreflang 標籤了，就通通當中文ㄅ
> 

所有頁面
移除現有的 accept-language 偵測機制

一般頁面
- cofacts.g0v.tw, zh.cofacts.org, en.cofacts.org --canonical--> cofacts.org

Landing page
- cofacts.g0v.tw, zh.cofacts.org --canonical--> cofacts.org
- cofacts.org: canonical self, --hreflang=en--> en.cofacts.org
- en.cofacts.org: canonical self, --hreflang=zh--> cofacts.org

:::success
把結論記錄到 https://github.com/cofacts/rumors-site/issues/347
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API

[Diff](https://github.com/cofacts/rumors-api/compare/c678c946517685dd8b0a6764a0bd9af295a71def...2c0769ea2273fe96efee24006607e8f9bf934b95)

User ID migration 執行完畢。

#### :robot_face: LINE bot
[2020/11/18 Bug fix](https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20201118)


### :eye: Under review

#### :robot_face: LINE bot

- [#235 Dialogflow NLP](https://github.com/cofacts/rumors-line-bot/pull/235)
    - Support for [environments](https://cloud.google.com/dialogflow/es/docs/agents-versions)?
    - ML settings threshold
    	- confidence 參考性很低，最高就 0.5 之類
    	- 直接中 training phase 的話是 1
    	- 建議很長的時候就不要採用 dialogflow 的 intent (10 個字以上的 dialogflow 如果 confidence 不是 1 就不要用，會當成訊息繼續處理)

#### :electric_plug: API
- PR + migrate -> down

----

官網
"武漢肺炎" "輕鬆賺錢" "抗癌"
"COVID-19" "Donald Trump" "China"

landing page 英文版大圖

-----

Tutorial 需要填肉
https://www.figma.com/file/ajFwwef2wqv5z4ydl0PgTZ/Wireframe-Pages?node-id=872%3A218

之前填的 https://g0v.hackmd.io/sB_zayWjTo-W0R7xe_U34w


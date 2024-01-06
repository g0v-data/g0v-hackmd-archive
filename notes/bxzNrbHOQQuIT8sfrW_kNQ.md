---
tags: cofacts, meeting note
---

20190313 會議記錄
=====
ttcat/lucien/bil/orz

## 大松檢討

- 要發文感謝 (after this is merged: https://github.com/cofacts/rumors-site/pull/155 )、提醒大家 good first issue 還有很多可以解
- eddy 做的 URL preview 太寬了要修 - eddy PR merged
- 感謝闢謠的：
 yingtso
 Haku 
 Lin


## 我愛家我聯絡 - 按讚版

- 掃立委貼文 comment & visitor post
- 標出挺同訊息
- 放進 embedded facebook post / comment plugin

TODO:
lazy loading

## Lucien 與 ttcat 討論網站

Legacy added to:
https://github.com/cofacts/design/tree/master/legacy

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_20f61b604391be8ed8b2645dbdcb50d7)

- - -

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c7bb9a318587df3195539b3130877967)

- - -

Lucien：
這樣吧，第一個問題應該是

文章頁面要什麼

ttcat
可能要分 for 編輯還是 user

站在編輯的角度，他需要什麼

### 文章列表

Lucien
trend 放在一個獨立的 navitagion page 吧
不要放在 article 裡面

ttcat
使用者進來的話，第一個反應就是「怎麼沒東西」
要跟他互動才有東西

lucien
這個有歷史脈絡
我想知道這一頁有哪些是不夠的
有 trend 的

mrorz
trend line 可以在顯示列表的時候才去 google analytics reporting API 拿
這樣不能搜尋
但也不確 ＡＰＩ是否有 ｑｕｏｔａ
我覺得應該滿久以後才會做

也可以放在文章頁面裡，
甚至可以做一個連結，點進去就到 analytics

一個 [trend line](https://github.com/cofacts/rumors-site/issues/111)

lucien
有人在用 quick reply 嗎

bil
我只會用「已讀」。
但文字不夠多，所以不會用 quick reply
希望可以在文章列表就能複製關鍵字去 google 去查
從前面才能全選是不夠的，不能直接挑關鍵字查
會造成很大的困擾
要打開這件事情有點不方便

orz
會在文章列表複製，是因為想要使用 quick reply 嗎

ttcat
總之希望編輯可以在列表上就複製關鍵字
如果是個網址呢？如果是網址就非點進去不可？

bil
對我不喜歡
最好網址都不要送進來

ttcat
可不可以顯示爬取的內容，或者是在文章列表就能點擊連結

lucien
如果是 expand mode，可以複製可以點進去
這樣應該就可以

mrorz
或者是切 listview 與 gridview 
gridview 比較大顆，可以讓編輯複製

lucien
所以 grid contain 的內容比較多

還有缺什麼資訊

filter & sort 還可以寫什麼

mrorz:
「需要被 review 的回覆」：所有回覆的負評 > 正評
「列出特定時間區段」---- 但比較有意義的是「在某時間區段有『被查詢』的訊息」，而這個可能 analytics 就能做到。

https://github.com/cofacts/rumors-api/issues/35

ttcat
現在 user 傳資料要比對相似度，相似度很高的謠言，含有相關連結，有沒有辦法有一個地方可以看到所有相似的

那個下面是全部嗎

mrorz:
LINE bot 裡面的相似文章，其實更像文章列表的搜尋功能，但相似度門檻比較高。


「自己回應過的文章」⋯⋯這個不好做

lucien
可以做在 profile 頁面，就不用那麼複雜的 sort，profile 頁面提供有限制的 sort


mrorz

這個是 profile 頁面的
https://g0v.hackmd.io/s/BJ2XBWAX4#Cofacts-TODO

DB mappings:
https://beta.hackfoldr.org/cofacts/https%253A%252F%252Fhackmd.io%252Fs%252FBkxbQ8ZbM


luicen

回應列表有人在用嗎

orz
我黑客松的時候會拿來講剛才回應的人
bil 會計算本週有誰回應
但好像更想要看的是「站上最近回應的『文章』有哪些」

我會找回自己的回應

lucien
前兩個感覺像是某種 ａｄｍｉｎ 才會用的東西
站上最近回應的文章像是某種 trend 列表
「我會找回自己的回應」-> 這個 profile 就有

reply 列表可以留著，但可以先不做太多設計

### 文章頁面

lucien:
article 頁有什麼沒有 你想加的
假設說 LINE 看答案的 user 會需要這麼多功能嗎？會不會只要看原文跟回應就好

bil:
我想收美玉姨 click
因為我不知道回應有沒有明確地被看到

如果想要用 voting 評估弟好不好
我期待那裡點這裡會不會有 hit

lucien
這等於要開 api 讓美玉姨打

bil
如果是個人的 content 那基本上會希望有用沒用的數據是有效的資料，而不是抽樣只抽了一半。

比如我想看回過的訊息，幾個人有用幾個人沒用
要點進去才看得到

ttcat
美玉姨的群組機制好像很難計算

bil
群組的話可以不計
但個人的應該可以

mrorz
那這個可以寫信給 carol

ttcat
文章頁面
我想知道這一篇第一次回報時間、上一次回報時間

mrorz
這其實有點像是 trend line

ttcat
在 ＬＩＮＥ裡面回我的就是理由跟理由出處，整串給我
但是如果是我，我要把訊息全部轉傳給我媽，要把很多訊息一次轉傳
取而代之的是，希望可以轉一個連結給他，可能就是 ａｒｔｉｃｌｅｐａｇｅ然後得到所有跟他講的事情

包含多少編輯覺得正確、多少覺得不正確，
另外很多謠言是今天開始昨天開始，希望日期很明顯

需求不伊樣，我覺得我想要用一個連結回他，那個就可以點

orz
(demo) 其實已經有了，在「覺得有用」之後會有「分享給朋友」按鈕
不過文章頁面確實可以更好用

lucien
公司有用什麼元件庫

orz
material-ui
我沒很喜歡
但頭都洗下去了

lucien
也可以用比較輕量的呀
segment

:::success
下次做什麼：
- Review Article List Page
:::

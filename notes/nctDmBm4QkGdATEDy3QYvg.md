---
title: "Redesigning MoeDict 草稿 by hlb"
tags: hackpad
---

# Redesigning MoeDict 草稿 by hlb

> [點此觀看原始內容](https://g0v.hackpad.tw/jQBgUXQX7UI)

萌典是民間版《教育部辭典》的開放資料界面與應用範例，收錄十六萬筆國語、兩萬筆台語、一萬四千筆客語條目、常用字的筆順動畫、英法德文翻譯，以及中華文化總會的《兩岸常用詞典》。
本 talk 以萌典為例，闡述零食政府專案的 UI 規劃進行方式。

\-\-\-\-,

幾乎所有 g0v project 都是想到就做了，所以沒有設計，沒有設計，沒有設計。很重要所以要講三次。
au 在「漢字產業創意工作坊」提到開源的重要概念是 "release early, release often"，不要怕丟臉。

[http://youtu.be/iW5x5wkyQTU?t=17m17s](http://youtu.be/iW5x5wkyQTU?t=17m17s)
總是有設計師會非常看不慣，就會跳進坑裡.....
[https://github.com/g0v/style-guide](https://github.com/g0v/style-guide)

因為沒有 mascot，所以 miau 就跳出來做了一個：

[https://twitter.com/moedict/status/328934213032218625](https://twitter.com/moedict/status/328934213032218625)
你可以在 [https://github.com/g0v/moedict-design](https://github.com/g0v/moedict-design) 取用。
講個秘訣：萌典頭像是用 miau 心中「乖乖牌的好孩子」形象製作的。

開發者的速度永遠比較快
→ 設計要能夠 pluggable
歷屆 MoeDict 設計比較

### redesigning

先研究字典

借鏡 Wikiwand
范可欽：有參考

#### 全文注音

當你的孩子開始上小學，你就知道為什麼需要他了。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f96145651f4a407aeef4a83d02b97eaa)

#### tweet integration

借鏡 [https://www.wordnik.com/words/love#see](https://www.wordnik.com/words/love#see)
成語超級準確
[https://twitter.com/search?q=三隻小豬](https://twitter.com/search?q=三隻小豬) （咦找不到這個成語了）
[https://twitter.com/search?q=敗家](https://twitter.com/search?q=敗家)

DEMO

\-\-\-\-

講個秘訣，從 [https://www.moedict.tw/%E4%B8%80%E5%88%87%E6%AD%A3%E5%8A%A0%E9%80%9F%E9%80%B2%E8%A1%8C%E4%B8%AD?font=srcb](https://www.moedict.tw/%E4%B8%80%E5%88%87%E6%AD%A3%E5%8A%A0%E9%80%9F%E9%80%B2%E8%A1%8C%E4%B8%AD?font=srcb) 找到圖片，直接拖到 Keynote 裡面，就可以做好投影片了喔


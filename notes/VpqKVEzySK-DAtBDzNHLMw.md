---
title: "新聞用的統計學"
tags: hackpad
---

# 新聞用的統計學

> [點此觀看原始內容](https://g0v.hackpad.tw/Qj05fEknwDS)


怎麼幫助記者從平均的迷思脫離呢？最重要的就是讓大家了解統計學的活用方式，要知道統計不是只有總和跟平均。可是在其他統計的方式中，到底什麼樣的 use case 會需要怎麼去做不同的運用呢？當我們在看一則新聞時，要怎麼知道記者用的統計方法到底適不適用呢？

（平均與標準差好像都第一堂課就上了，後面都在上機率，然後是分布，接下來上 inferential XD)
> 對耶你電機系有上過機率與統計 XDD
> [name=Claire T]

> 電機系上了4/5學期的機率，都在做證明題。剩下三個禮拜老師台上亂講完丟一小本課本的部分跟你說回家自己念。這個是我最近自己在上的課是這樣排啦
> [name=I-Chiao H]


case: [https://money.udn.com/money/story/5641/2832693](https://money.udn.com/money/story/5641/2832693)

這個例子我比較不懂的是怎麼解讀 sampling 的數據。


先找些 reference，之前數感的以威跟阿賢也有合開過
- [https://www.facebook.com/events/357409967930437/](https://www.facebook.com/events/357409967930437/)
- [https://www.thenewslens.com/article/27295](https://www.thenewslens.com/article/27295)
- [https://knightcenter.utexas.edu/blog/understanding-statistics-journalists-guide](https://knightcenter.utexas.edu/blog/understanding-statistics-journalists-guide)
- [https://knightcenter.utexas.edu/blog/00-16082-math-journalists-made-easy-understanding-and-using-numbers-and-statistics-%E2%80%93-sign-now-n](https://knightcenter.utexas.edu/blog/00-16082-math-journalists-made-easy-understanding-and-using-numbers-and-statistics-%E2%80%93-sign-now-n)
- [https://cyborgus.com/2017/04/15/how-to-lie-with-data/](https://cyborgus.com/2017/04/15/how-to-lie-with-data/)
-

敘述統計量、及其應用
所以會直接談應用嗎？
> 感覺用應用開頭接受度比較高？
> [name=Summit S]

> 但是敘述統計量應該要先講，不然連工具都沒有
> [name=Summit S]

> 敘述統計量是指？
> [name=I-Chiao H]

> 應用開頭也不是不行，只是只講應用的話我覺得基礎太不穩。我自己很容易換個scenerio就不太確定要怎麼辦 XDDDD
> [name=I-Chiao H]

> 敘述統計量就是平均中位數那些，還沒有做推論直接從資料算出來的
> [name=Summit S]

> 繼續誠摯推薦小八（我這樣好像壞掉的收音機）
> [name=Claire T]

> XDDD
> [name=Summit S]

> 不過要教的話我也贊成用 case 入手不然很難想像～就是 case -> 概念 -> 各種不同 case 讓大家討論練習
> [name=Claire T]

> 我自己在上的課程是先簡短介紹概念，然後很快切入case，也是不錯
> [name=I-Chiao H]

> 對耶想一想給記者的課（因為不是要真的跑統計）（應該）的話直接討論問題也不錯，就是不要管概念，先討論看看大家拿到一組資料，或是有個問題想驗證的時候，會怎麼設定問題跟找答案，以及如何驗證答案的合理性。
> [name=Claire T]

> 可以請大大們分享經驗，或是在做統計時（說不定有) 的起手式 SOP？
> [name=I-Chiao H]

> 用 case 開始，也不是不能講統計計量，只是講法上會不一樣，應該不要「第一課：機率，第二課：統計分布...」之類，而是用 case 看：「這個 case （資料），我們可以用 XXX，因為在這個 scenerio 裡，我們要討論的是...」之類的
> [name=Hsin-chan C]

> 同意樓上，有點像是國小數學，螺旋式教法，每一輪一直複習類似的概念但越來越深
> [name=Summit S]


我推薦小八！（ps 我之前跟小八有在討論要開資料分析入門課～但他一直擺爛
> ++
> [name=Summit S]



另一個問題是 TA，有一部份當然是「覺得自己有在用／做數據但是其實用不好」的人，這群人算是認真型，所以其實可能可以跳過把他們當（數學）白痴的部分，可以針對個案或是常誤用的部分有點類似眉角秘技分享小提示這樣；另外一群是大家常常罵「小時不讀書長大當記者的那種天天在新聞報紙上看到的傻眼記者」，這樣的人會不會來？是不是我們真正想要「導正視聽」的人？還是其實要找他們的主管／編輯？但是如果他們的高層就是不想要這樣怎麼辦？
然後這兩群人也剛好是需求曲線的兩端，i.e. 相對小眾⋯⋯XD
另一個角度就是教閱聽人「讀報」，可能從 user 端去給媒體壓力，但是我想應該不是很多人想要動腦看新聞，這可能也是真正台灣媒體環境會變成這樣的原因。


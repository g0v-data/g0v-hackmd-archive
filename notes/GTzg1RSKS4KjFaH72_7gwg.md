---
title: "第三次視覺化分享會 (5/29) - 筆記"
tags: hackpad
---

# 第三次視覺化分享會 (5/29) - 筆記

> [點此觀看原始內容](https://g0v.hackpad.tw/NHqIMXvEcPh)

[分享會專用 hackpad](https://g0v.hackpad.tw/MyKS5lDFtNu)
[視覺化學院](https://www.facebook.com/groups/datavis.tw/)

## The Magical Number Seven, Plus or Minus Two: Some Limits on our Capacity / George A. Miller

講者: Kimi
原文: [http://www.psych.utoronto.ca/users/peterson/psy430s2001/Miller%20GA%20Magical%20Seven%20Psych%20Review%201955.pdf](http://www.psych.utoronto.ca/users/peterson/psy430s2001/Miller%20GA%20Magical%20Seven%20Psych%20Review%201955.pdf)
哈佛教授 G.A. MILLER
信息測量 \- 1bit ( 是或否 )
音符超過七個的時候不容易記，但只有兩三個就相對簡單了 ( 播放 mary has a little lamb 中 )
圖中的點數不多時，很容易重製，也會去算多少個
太多時：
- 就會從絕對判斷轉向估計判斷了, 也不容易再被重製出來
- 若再加上面積與密度，會更容易判讀
重新編碼
- 雖然波可能代表了 2 bit 式的資料，但我們比較會直接注意波形 ( ? )
- 一堆 10 很難記, 但重新編碼就會比較好記
    - e.g., 1000100011011001(超過7個) -> 20203121(超過7個) -> 88d9 (好記)
- 回憶是「建構」記憶而非提取

這個blog有提到本paper的內容，該網站也有很多ui設計的有趣文章可以自行看看
[http://blog.fourdesire.com/2014/12/11/bang-ui-fen-lei-wo-men-shi-ru-he-ji-yi-de/](http://blog.fourdesire.com/2014/12/11/bang-ui-fen-lei-wo-men-shi-ru-he-ji-yi-de/)



## D3: Data-Driven Documents, by Mike Bostock

講者: Muyueh
原文: [http://vis.stanford.edu/files/2011-D3-InfoVis.pdf](http://vis.stanford.edu/files/2011-D3-InfoVis.pdf)


Data Driven Document
_or what makes d3.js great_


Level of abstraction
- encapsulation
- intermediate representations

```
            sprite.graphics.drawCircle(0, 0, 10);

```
vs.

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5ab2c9f0ce09eb027541185382a008ff)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_75d3253d85349a599de884db426d58c8)

### trade-off

1.  **Efficiency**: human effort required to specify a vis
2.  **Expressiveness**: diversity of visualizations
> c3.js, NVD3.js and other are limited in expressiveness
> [name=Muyueh L]

3.  **Accessibility**: difficulty of learning the representation (due to internal structure)


### key goals for d3.js

1.  **Compatibility**: works with other system (CSS), evolves with standard, native expressiveness
2.  **Debugging**: vs. encapsulation of control
3.  **Performance**: avoid redundant computation by letting dev. controls transition

### What is d3.js

1.  Data Driven DOM manipulation (Like jQuery)
2.  add/remove elements
3.  high-level helper ( helper function (format, d3.csv), and hopefully stats model as in R)


### Difference between d3.js and Protovis

1.  **implicit or explicit transformation**
    (Protovis specify scene changes, have to re-evaluate all properties vs. d3.js specify changes)
2.  **deferred or immediate evaluation**
    (Prototis users need to understand internal control flow)
3.  **access to a native representation**
    (Protovis Line, Wedge all prototypal inheritance vs. d3 circle cx and rect x)
    -\> selection can be retrieved at any time vis console





## Useful Junk? The Effects of Visual Embellishment on Comprehension and Memorability of Charts / Scott Bateman

講者: Kirby
原文: [http://hci.usask.ca/uploads/173-pap0297-bateman.pdf](http://hci.usask.ca/uploads/173-pap0297-bateman.pdf)

## The Structure of the Information Visualization Design Space, by Stuart K. Card

講者: Summit
原文: [http://www.cs.ubc.ca/~tmm/courses/old533/readings/card96structure.pdf](http://www.cs.ubc.ca/~tmm/courses/old533/readings/card96structure.pdf)



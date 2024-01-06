---
title: "判決書懶人包"
tags: hackpad
---

# 判決書懶人包

> [點此觀看原始內容](https://g0v.hackpad.tw/suxchYnyCBR)


覺得判決書又臭又長嗎?
[http://judicial.ronny.tw/TPB/A/103/](http://judicial.ronny.tw/TPB/A/103/訴/1627)[訴](http://judicial.ronny.tw/TPB/A/103/訴/1627)[/1627](http://judicial.ronny.tw/TPB/A/103/訴/1627)

以  [1031627](https://g0v.hackpad.tw/1uK4O8K4IwZ)  為例，裡面我試著用一句話來取代一整句話

這個專案的目標，是想要做出一個網頁，可以將判決書全文自動載入，並且自動分段，然後讓大家可以自行提供這一段內容的摘要，讓大家可以分享較短的判決書

### 需要幫忙

- 文字處理: 將判決書內容能做出分段
> 這是人工作文字處理嗎?
> [name=Bany H]

> 程式應該也可以簡單的先做分段
> [name=Timothy L]

> 這裡我可以用程式作作看
> [name=Bany H]

> 其實判決書的分段還滿單純的，說不定用前面空幾格然後以 (1) , 甲. 一. 開頭之類的就可以判斷為一段，說不定不需要用到自然語言分析
> [name=Ronny W]

> 會不會有半形跟全形空白XD
> [name=Timothy L]

> 下面我來收集十個判決書，然後今天的程式看看能不能先對這十個為主
> [name=Ronny W]

- 前端: 將分段後的判決書，可以切換每一段要顯示摘要還是全文，並且可以讓任何人投稿摘要，或者讓大家~投稿~票選摘要
    - 程式碼:
> 想幫忙前端XD
> [name=Timothy L]

> 搬椅子來follow
> [name=劉宇庭]

> ++
> [name=Ping C]

> 我只做了摘要編輯功能，程式在下面
> [name=Timothy L]

- 後端: 處理摘要的投稿以及投票
> 應該可以幫忙做後端
> [name=雨蒼 林]

> ++
> [name=Ping C]

- 法律人: 將一些指標性的著名判決加上每一段的摘要
> 這個我可以找人來幫忙，可以先給我判決，我去司改會提案
> [name=雨蒼 林]

> 下面我列出十個判決書，來以這些為先好了，或者大家覺得有更重要的或是指標性的也可以貼上來
> [name=Ronny W]

> 小弟我是法律系畢業，現在在寫code，超有興趣，先搬椅子來Follow看何時可以幫上忙。
> [name=Danny Y]

- 法律小知識
> 雨蒼兩三週內整理出來
> [name=雨蒼 林]


### 測試用判決書

> 可以用 ronnywang.github.io/tw-court-parser 產生下面的判決書短網址
> [name=Ronny W]

1.  [http://judicial.ronny.tw/TPB/A/103/訴/1627](http://judicial.ronny.tw/TPB/A/103/訴/1627)
    1.  教育部必需要公開課綱審議會會議記錄及出席記錄的行政判決
2.  [http://judicial.ronny.tw/TPD/A/103/簡/107](http://judicial.ronny.tw/TPD/A/103/簡/107)
    1.  太陽花 324 清場國賠
3.  [http://judicial.ronny.tw/TPD/V/101/重國/30](http://judicial.ronny.tw/TPD/V/101/重國/30)
    1.  張博崴登山山難國賠
4.  [http://judicial.ronny.tw/TPB/A/103/訴/1046](http://judicial.ronny.tw/TPB/A/103/訴/1046)
    1.  公平會判蘋果違反公交法兩千萬元，蘋果抗告敗訴
5.  [http://judicial.ronny.tw/CHD/M/96/](http://judicial.ronny.tw/CHD/M/96/訴/25)[訴](http://judicial.ronny.tw/CHD/M/96/訴/25)[/25](http://judicial.ronny.tw/CHD/M/96/訴/25)
    1.  襲胸十秒無罪
6.  [http://judicial.ronny.tw/TPS/V/103/%E5%8F%B0%E4%B8%8A/102](http://judicial.ronny.tw/TPS/V/103/%E5%8F%B0%E4%B8%8A/102)
[http://judicial.ronny.tw/SLD/V/89/%E9%87%8D%E8%A8%B4/188](http://judicial.ronny.tw/SLD/V/89/%E9%87%8D%E8%A8%B4/188)
    1.  劉德華弄壞直升機賠錢

### 規劃判決書 JSON

- "裁判字號": {"年": "101", "字": "重國", "號": 30}
- "裁判日期": {"year": 2015, "month": 5, "day": 27}
- "裁判案由": "國家賠償"
- "裁判種類": {"ID": "V"} // V 民事，A 行政，M 刑事
- "法院": {"ID": "TPD"} // 看法院列表
- "法官": \[

### 文字處理 Todo List

1.  ~(進度0%) 給判決書的網址，自動下載判決書~
    1.  Ronny Wang 已經有現成的 [http://judicial.ronny.tw/](http://judicial.ronny.tw/)
2.  ~(進度90%) 給下載後的判決書，自動將判決書處理成json格式，範例如下~
    1.  Ronny Wang 已經有現成的 [http://judicial.ronny.tw/](http://judicial.ronny.tw/)
3.  (進度55%) 給json格式的判決書，自動找出關鍵字之間的關聯強度
    1.  **需要的協助: 法學相關的關鍵字清單**
    2.  需要的協助: 關鍵字合併相關論文
4.  (進度90%) 給關鍵字列表及關聯強度，畫出圖形化的directed graph
    1.  初步成果 [http://i.imgur.com/PXdcaMO.png](http://i.imgur.com/PXdcaMO.png)
5.  (進度0%) 給關鍵字列表及關聯強度，找出判決書中的十大金句
    1.  需要的協助: 自動摘要相關論文

### 前端摘要編輯器

- [http://ctiml.github.io/judicial-summary/text.html](http://ctiml.github.io/judicial-summary/text.html)
- 把 [http://ronnywang.github.io/tw-court-parser/](http://ronnywang.github.io/tw-court-parser/) 產生出來的 json 文字全選後貼到上面的 textarea，按下 Edit
- 可以用滑鼠多選行，然後底部可以輸入 "標題" 及 "摘要"，然後送出產生 json
- 可以直接貼 json 或編輯 json，按下匯入



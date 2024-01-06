---
title: Project Hub
tags: infras, 2019, 14nd, 基礎松, 基礎建設松, 第拾肆次基礎建設松, g0v, Project Hub
---
# Project Hub 2019-10-20 基礎松討論筆記

## 與會人員

ronny, tmonk, kirby, york, chiao, ipa

## 討論

ronny：之前為什麼要請工讀生來整理 g0v 這些提案？

ipa：最初是想做 g0v json ，但後來發現並沒有誘因讓這些坑主願意提供專案的結構化資料，所以就先花錢請工讀生做一個整理。

ronny：其實從過去到現在有不少人嘗試做過類似 Project Hub 的專案。

ronny：之後還有人做幫所有 g0v 在 Github 上的專案自動 PR g0v json 上去，坑主沒有填，其他人可以幫忙填。

---

kirby：像 Facebook 他們廣告投放分類選擇的 auto complete 是怎麼做的？

york：那個一定是靠機器學習去做出來的。

tmonk：照目前 g0v database 上的專案數量有 600 多個，說實在這個數量對電腦來說很小 case，做好 tag 後可以去試試看分類演算法。

---

kirby：前段搜尋 project 的介面可以跟 g0v grant 的頁面一起做，提案產生器，產生過程中推薦標籤，讓使用者填寫 project 是否符合 SDGs 的分類。

tmonk：如果可以的話希望用 SDGs 做分類。

---

tmonk：新版的 g0v grant 也會有 social login 嗎？

kirby：其實 g0v-jothon 之前有嘗試做過 g0v login，新版的看看有沒有機會加進去，當然還是會維持目前 FB、Google 跟 Github login，另外目前大松提案用的 google spread sheet 現在也是支援匿名協作，所以不登入提案其實也是可以允許的。

---

tmonk：沒有一個分類法是完美的。每一個分類方式下都會出現一些難以處理的 edge case。

york：對，所以處理這些 case 最好的方式就是用複標處理，就是一個 project 可以在一個分類底下出現。

---

ronny：g0v 基礎建設的 project 沒有在 SDGs 分類理頭。有很多跟社會公平正義有關的提案也不知道分在 SDGs 的哪一個項目理。

tmonk：雖然很想用 SDGs ，但的確這些 project 並不是一開始說先參考自己是在哪一個 SDGs 的分類才開坑的，而是在 Taiwan 的 social norm 裡頭產生出來的坑。

kirby：那我們還是從整理標籤開始，然後再從標籤去找出一個適合 g0v 這些 project 的分類方式。

york：要從上次臺北市議會大松整理的 g0v database 做嗎？

kirby：那我們再開一個 google spread sheet 複製 g0v database 協作。

---

tmonk：Tag 跟分類的差別在哪？

---

tmonk：有不少失效連結的確很可惜。

ronny：hackpad 要轉 hackmd，放在 spread sheet 、 doc 跟 slide 做 archive。

---

ronny：有一些失效的網址如果是 hack.g0v.tw 只要把 hack 改成 hack-old 就可以。

kirby：我看看能不能在揪松網自動轉址。


## 相關連結

- g0v 第參拾陸次臺北市議會黑客松 [g0v database](https://docs.google.com/spreadsheets/d/1C9-g1pvkfqBJbfkjPB0gvfBbBxVlWYJj6tTVwaI5_x8/edit#gid=1563040282)
- 2019-10-20 第拾肆次基礎建設松 [提案列表整理](https://docs.google.com/spreadsheets/d/1GND-IKNIPJfQ4Ry2hfHQpEm8_CuBZa7ZchTedlWiO08/edit#gid=0)

## 本日小松果

依照[提案列表整理](https://docs.google.com/spreadsheets/d/1GND-IKNIPJfQ4Ry2hfHQpEm8_CuBZa7ZchTedlWiO08/edit#gid=0)在子 sheet 「分列列表」中共整理出主分類共約 19 項。

- 政治
- 媒體
- 法律
- 開放資料
- 環境
- g0v
- 社會議題
- 科技與工具
- 健康與醫療
- 教育
- 語言
- 生態
- 能源
- 交通
- 藝術
- 經濟
- 農業
- 財政
- 社群活動

今日工作：

- 由下而上標記所有專案的tag，將之視為子分類
- 從tag（子分類）歸納出主分類

未來可做：

- 邀請大家（cloudsourcing）來標記所有專案的tag，再由機器去做分類

- 有標記過的 tag 能藉由 same char 與常見並陳的 tag 做推薦的 auto complete 

- 用演算法判斷 tag 之間的關係 

- 由上而下從新對照目前的主分類是否合適


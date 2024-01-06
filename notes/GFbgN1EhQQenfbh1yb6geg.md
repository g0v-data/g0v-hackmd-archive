---
title: "無障礙網站設計的坑"
tags: hackpad
---

# 無障礙網站設計的坑

> [點此觀看原始內容](https://g0v.hackpad.tw/bvDAvE2nDKs)


要幫政府寫網站，常常會遇到NCC的無障礙網頁標準，但問題是，這個標準是WCAG 1.0版，只針對靜態網頁，而沒有升級到WCAG 2.0。
> 今年七月份的時候，NCC 曾經說預計八月中旬要讓新的 WCAG 2.0 對應的規範上線，取代舊規範；目前不知道什麼原因還沒有實現。
> [name=Jedi L]

> 政府網站版型與內容管理規範 [http://www.webguide.nat.gov.tw/index.php/ch/speci/](http://www.webguide.nat.gov.tw/index.php/ch/speci/)
> [name=林仔魚]

> 政府網站版型與內容管理規範裡面的無障礙相關附件還是舊版的喔～
> [name=雨蒼 林]

> 對他是直接連到ＮＣＣ那邊去，不過因為感覺是母法想說貼一下XD
> [name=林仔魚]

> ++
> [name=雨蒼 林]

然後廠商製作的validate工具有bug，有動態網頁、ajax都會炸，還會進入無窮迴圈....此問題不解決，政府網站就是都給那幾個廠商做....

## 坑：


- [x] 翻譯 WCAG 2.0
[https://www.w3.org/TR/WCAG20/](https://www.w3.org/TR/WCAG20/)
- [ ] →這裡有簡體中文W3C授權翻譯的版本，所以只要做繁中化校對與名詞對應即可
[https://www.w3.org/Translations/WCAG20-zh/](https://www.w3.org/Translations/WCAG20-zh/)

[Jedi Lin](https://g0v.hackpad.tw/ep/profile/oMK18WBMRvv) 舊版《網頁親和力》書稿（2008 年做的，後來沒有放進印行的版本中）第三章包含完整的繁體中文 WCAG 2.0 翻譯（部分術語可能需要修正）：
[https://dl.dropboxusercontent.com/u/784910/p4/Web_Accessibility/Book01/Content/chap03.html](https://dl.dropboxusercontent.com/u/784910/p4/Web_Accessibility/Book01/Content/chap03.html)

[Jedi Lin](https://g0v.hackpad.tw/ep/profile/oMK18WBMRvv) 在 2010 年翻譯過的文件（臨時網址，請協助備份／轉換格式等；部分術語可能需要修正），可以參考：
- [ ] Understanding WCAG 2.0 中英對照 [https://www.dropbox.com/s/](https://www.dropbox.com/s/e1fpsal53vi4abh/01-Understanding%20WCAG%202%200-CHT.r5.doc?dl=0)[e1fpsal53vi4abh/01-Understanding%20WCAG%202%200-CHT.r5](https://www.dropbox.com/s/e1fpsal53vi4abh/01-Understanding%20WCAG%202%200-CHT.r5.doc?dl=0)[.doc?dl=0](https://www.dropbox.com/s/e1fpsal53vi4abh/01-Understanding%20WCAG%202%200-CHT.r5.doc?dl=0)
- [ ] Comparison of WCAG 1.0 Checkpoints to WCAG 2.0 中英對照 [https://www.dropbox.com/s/](https://www.dropbox.com/s/a50eo28qlravv8k/01-Understanding%20WCAG%202%200-CHT.r3.doc?dl=0)[a50eo28qlravv8k/01-Understanding%20WCAG%202%200-CHT.r3](https://www.dropbox.com/s/a50eo28qlravv8k/01-Understanding%20WCAG%202%200-CHT.r3.doc?dl=0)[.doc?dl=0](https://www.dropbox.com/s/a50eo28qlravv8k/01-Understanding%20WCAG%202%200-CHT.r3.doc?dl=0)

- [ ] 翻譯 WAI-ARIA
[https://www.w3.org/WAI/intro/aria](https://www.w3.org/WAI/intro/aria)

- [ ] 製作各個平台都能用的validate工具
> 現階段我會推 Deque System 的 aXe，見 [http://www.deque.com/products/aXe/](http://www.deque.com/products/aXe/)
> [name=Jedi L]



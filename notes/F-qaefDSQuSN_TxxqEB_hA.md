---
title: "hackpad轉sayit許願池"
tags: SayIt,hackpad
---

# hackpad轉sayit許願池

> [點此觀看原始內容](https://g0v.hackpad.tw/8VcgnEfx4Uz)


- [ ] import hackpad一段新的談話後，無法整段刪除，例如現在的「[untitled](http://g0v.sayit.mysociety.org/speeches)」無法被刪除。
> 可以刪 section （手動在網址後加 /delete 即可）  
> [name=Audrey T]

> 但是裡面的話就會變成 orphan ("[Speeches not in a section](http://sayit.archive.tw/speeches) ")
> [name=Audrey T]

> 之前是想過寫個 useragent bot 來刪掉這些...
> [name=Audrey T]

> 記得某個地方可以再刪掉的時候把 orphan 指定給別人
> [name=Yuan C]

> 求救！「手動在網址後加 /delete 即可」是指：
> [name=羅佩琪]

> 1\. import speeches的時候，[http://pad.archive.tw/+hackpad網址](http://pad.archive.tw/+hackpad網址) 後面再加/delete?
> [name=羅佩琪]

> 2\. import speeches的時候，填上該sayit網址 後面再加/delete?
> [name=羅佩琪]

> 3\. 直接在sayit的網址後面加/delete?
> [name=羅佩琪]

> ....以上三個方法我都試過了都宣告失敗XDDDD  有高手可以救一下嗎？
> [name=羅佩琪]

> 是 3 也就是把手動加 .an 的網址改成手動加 /delete （需先登入）
> [name=Audrey T]

> Section: [http://sayit.archive.tw/la-nuit-des-id%C3%A9es-un-jour-dans-le-monde](http://sayit.archive.tw/la-nuit-des-id%C3%A9es-un-jour-dans-le-monde)
> [name=Audrey T]

> XML: [http://sayit.archive.tw/la-nuit-des-id%C3%A9es-un-jour-dans-le-monde.an](http://sayit.archive.tw/la-nuit-des-id%C3%A9es-un-jour-dans-le-monde.an)
> [name=Audrey T]

> Delete: [http://sayit.archive.tw/la-nuit-des-id%C3%A9es-un-jour-dans-le-monde/delete](http://sayit.archive.tw/la-nuit-des-id%C3%A9es-un-jour-dans-le-monde/delete)
> [name=Audrey T]


- [ ] my society帳號下新增的「你的引述 (網域)」，新增後無法刪除。

- [ ] import完的對話，按「speaker」會呈現錯誤狀態，[像這樣](http://g0v.sayit.mysociety.org/speakers)。
> 這是因為[有人的 ID 是「？」](http://g0v.sayit.mysociety.org/20160109-%E9%81%B8%E8%88%89%E6%9D%BE-%E5%8F%B0%E7%81%A3%E7%95%B6%E5%89%8D%E5%9B%B0%E9%9B%A3%E8%AD%B0%E9%A1%8C%E8%A8%8E%E8%AB%96.an)
> [name=Audrey T]

> <TLCPerson href="/ontology/person/g0v.sayit.mysociety.org/" id="" showAs="？"/>
> [name=Audrey T]

> 如果用「匿名」或「不確定」等非標點符號就好了
> [name=Audrey T]

> 或是開個 [issue](https://github.com/audreyt/pad2an/issues)  讓 id 保持 nonempty (uuid? random?)
> [name=Audrey T]


> 我把「？」的都改掉了，但還是不行耶....QQ
> [name=羅佩琪]

> 那是因為舊的 speaker 的 ID 還沒有改... 試一個新的 sayit instance 看看?
> [name=Audrey T]


- [ ] [村長的頭像](http://g0v.sayit.mysociety.org/20160109-%E9%81%B8%E8%88%89%E6%9D%BE-%E5%8F%B0%E7%81%A3%E7%95%B6%E5%89%8D%E5%9B%B0%E9%9B%A3%E8%AD%B0%E9%A1%8C%E8%A8%8E%E8%AB%96#s652104)不知道為什麼出不來，[speaker介紹](http://g0v.sayit.mysociety.org/speaker/clkao)裡面是有的。
> 試看看用 .png 或換一張? 可能是 .jpg metadata 問題
> [name=Audrey T]


- [ ] 除了按「[邀請朋友來幫忙](http://g0v.sayit.mysociety.org/)」之外，有其他方式可以直接讓這個頻道可以讓所有人都可以編輯嗎？(類似google文件，有連結就可以編輯，的功能)
> 目前似乎沒有。我通常是邀請 hackpad 編輯，而不是在 sayit 層編輯...
> [name=Audrey T]

> 目前雖然沒有，不過應該可以實作
> [name=Yuan C]




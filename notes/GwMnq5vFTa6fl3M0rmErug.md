---
title: "moedict no pangcah 阿美語萌典"
tags: 萌典,moedict,hackpad
---

# moedict no pangcah 阿美語萌典

> [點此觀看原始內容](https://g0v.hackpad.tw/R2LBqjAdMwM)


### 進度/雜項

- [x] 把字典掃描檔切成一行一行的工具 (CindyLinz)
- [x] ~上傳到 pixnet~    直接放上 TANET
    - [x] 有 14681 個豆腐 (含空白)
- [x] ~租 Linnode~  R~onnyWang 出借 Heroku ^^;~ 在 TANET 上直接寫 SQLite3
- [x] 寫讓鄉民 OCR 的小程式
    - [ ] 要不要先用程式 OCR 是另一個議題了...
> [miaoski/amis data#1](https://github.com/miaoski/amis-data/pull/1) <\-\- x4base 送了 PR 來，不過 tesseract OCR 過後其實蠻慘的，所以還是維持手打的局面吧...
> [name=Zhemin L]


- [x] 開放出去
> 建議除了數位化之外，提供可以讓網友校對錯字和修正語句的機制介面，但也許要取得原編寫者的同意
> [name=Hanyu C]

> [http://www.eastgate.org.tw/f2/index.php?load=read&id=532](http://www.eastgate.org.tw/f2/index.php?load=read&id=532) 這本原來這麼多人一起編；方敏英傳教士已經過世了。
> [name=Lafin M]

> 網友一起校對字典，我覺得可以放在第三個階段。第一階
> [name=Zhemin L]

> 段，我們先把原本的字典 key 進去，因為做 diff (校訂過/原本) 的比對，在學術上也是一個好題目。第二階段，我們多談幾本授權，把字典裡的字擴充到族人用起來覺得方便的程度。第三階段再來修正語句、或新增例句。這是我個人的看法啦。如果有人 coding, 三個階段一起做也是可以的 :)
> [name=Zhemin L]

> 第一階段最後釋出是哪種形式呢？
> [name=Lafin M]

> JSON.  然後我會想辦法把它裝進萌典的介面... 唯一會修改的地方應該是 g => ng 不然現在已經沒人用 minegneg 這種寫法了，都嘛寫 minengneng
> [name=Zhemin L]

> 講到 ng for ŋ 恁爸就賭啉
> [name=Theo Y]

- [ ] 書寫系統校對
               根據 2005年公布原住民族語言書寫系統 -[http://www.edu.tw/userfiles/url/20121127164752/aboriginal.pdf](http://www.edu.tw/userfiles/url/20121127164752/aboriginal.pdf)
               之後應該要想一下如何做修正或是不修正以阿美語方敏英版呈現
               我還蠻懂阿美語書寫的; 建議還是用 ' ^ ng 方案
    不過應該注意 n-g 的可能性


### 可以爬的網站

- [http://e-dictionary.apc.gov.tw/Index.htm](http://e-dictionary.apc.gov.tw/Index.htm)  原民會詞典 (合理使用)
    - [ ] 詞條列表 (ch0upi) [https://gist.github.com/choupi/32fd095d67c965128bfe](https://gist.github.com/choupi/32fd095d67c965128bfe)
    - [x] 賽夏語
        - [ ] 爬完了要開始處理...


### 線上詞典

阿美語
傳說中阿美族翻譯系統
- [http://web.pts.org.tw/php/news/abori/view\_abori.php?HTENO=137&HBENO=422&DETAIL=1&TB=ABORI\_DEPTNEWS](http://web.pts.org.tw/php/news/abori/view_abori.php?HTENO=137&HBENO=422&DETAIL=1&TB=ABORI_DEPTNEWS)
- [ ] 法拉漢 老師 （已聯絡，目前等待回信）
- [http://somowal.amis.org.tw/somowal/index.htm](http://somowal.amis.org.tw/somowal/index.htm)
- [ ] 阿美族語查詢系統（寫信談授權中）
賽德克語（flash)
- [http://bnuhun.qmalup.org/dictionary/index.htm](http://bnuhun.qmalup.org/dictionary/index.htm)
- [ ] 賽德克圖解詞典
達悟/雅美語
- [http://yamiproject.cs.pu.edu.tw/elearn/search.php](http://yamiproject.cs.pu.edu.tw/elearn/search.php)
蘭嶼達悟語線上學習網（詞典）

### 可以談的授權

- [ ] ~陳金龍老師~  (陳金龍老師編寫的是教材，不是字典。不過可以去要一些例句也不錯)
- [ ]


## 字典原本有誤之處

問題回報請改道：開了獨立一頁[阿美字典OCR問題回報區](https://g0v.hackpad.tw/OCR-pJmvFdqwWE1)，也把該連結放進說明書。


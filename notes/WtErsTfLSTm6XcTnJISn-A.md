---
title: "抵制小幫手 app"
tags: g0v idea pool,hackpad
---

# 抵制小幫手 app

> [點此觀看原始內容](https://g0v.hackpad.tw/gmVxuYAk5R9)

掃barcode，來抵制：行動小幫手家族，你的生活秘書
- 逛街小幫手 = 美食優惠卷+求職小幫手+抵制小幫手+公司關係圖+避稅富豪列表
- 採購小幫手 = grocery list+採購清單+抵制小幫手+食品小幫手
- 投票小幫手 = 公民團體不推薦+立委投票指南+選票成分分析器
> 上面這列表是要做成 行動小幫手app 嗎XD
> [name=lanfon]


==頂新相關共筆請改到這裡：====[抵制大幫手-Opernation Decent](https://g0v.hackpad.tw/-Operation-Decent-tf4txwcUKV8)==

## 一、主旨

收集壟斷、黑心企業以及旗下品牌，購物時，用手機或平板拍照產品條碼，遇到這些無良企業的產品會像求職小幫手一樣跳出警告，然後附上此商品的替代方案。
> 要再加上+[關箱小幫手](https://g0v.hackpad.com/0hzIFc3qCIM)嗎?
> [name=Wen-Chi C]


### 文案

之前太陽花運動期間，有人在大腸花論壇上告訴大家：你的每一張鈔票都是選票，當你走進商店、購買一個產品的時候，你就是在投票給這個產品、這個商店。

在黑心產品越來越多的現在，如何知道自己可能會投錯票，可能資助了無良商人，可能幫助了慣老闆剝削員工，可能讓好的產品被埋沒在黑心商品中？g0v零時政府鄭重發起「小幫手家族」計畫，只要把小幫手裝上手機，輕鬆掃描，你就能知道自己手上的產品是不是黑心產品。

<可加上使用說明>
有了小幫手，您再也不用擔心會投票給黑心商人、慣老闆了！讓我們一起用鈔票，鼓勵更多良心商人，鼓勵更多善待員工的企業！一起用鈔票讓台灣的黑心商人再也賺不到錢！
＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝
> 頂新相關資料搬到抵制大幫手
> [name=ipa c]


### 相關概念

[http://www.seinsights.asia/news/131/1240#sthash.xPmANYqW.dpbs](http://www.seinsights.asia/news/131/1240#sthash.xPmANYqW.dpbs)
[Idea Pool:  Alternative To 壟不斷，你來亂（名稱暫訂 X](https://g0v.hackpad.tw/ZhayTz2Om0n#:h=-Alternative-To-壟不斷，你來亂（名稱暫訂-X)
[iQC](http://blog.fashionguide.com.tw/4245/posts/67375-%E3%80%8E%E5%BB%A3%E5%AE%A3%E3%80%8Fiqc-%E5%95%86%E5%93%81%E8%B3%87%E8%A8%8A%E7%B6%B2%E2%94%80%E9%A3%9F%E5%93%81%E5%AE%89%E5%85%A8%E9%9B%B2%E7%AB%AF%E6%9F%A5%E8%A9%A2%E5%B9%B3%E5%8F%B0)

### 原始資料

- 國外
    - [http://productdb.org/](http://productdb.org/)
    - [http://www.productwiki.com/](http://www.productwiki.com/)
- 直接 Google 條碼 ex. [https://www.google.com.tw/](https://www.google.com.tw/#q=4710022009207)[#q](https://g0v.hackpad.tw/ep/search/?q=%23q&via=gmVxuYAk5R9)[=4710022009207](https://www.google.com.tw/#q=4710022009207)
- [經濟部智慧財產局商標 API](http://www.tipo.gov.tw/ct.asp?xItem=531533&ctNode=7127&mp=1): 基本上是 ftp, mirror TrademarkRegXMLB* 即可，含商標圖樣。
    - [砍站工具](https://github.com/g0v/tmsearch)
    - 要注意的是單筆商標申請資料（有一個申請編號）是「商品類別」+「商標名稱」，因此常會有 A 品牌有多筆資料，因為跨不同商品類別（食物、飲料等）


## 二、技術知識

> 我以前幫公司申請過[加入會員](http://www.gs1tw.org/twct/web/gs1_contact.jsp)（GS1 Taiwan），通常是廠商自己維護自己產品清單，然後上傳到資料庫中，如果是轉手賣別人工廠的東西，而且原本就有商品條碼，就不必再次登記，會重複。
> [name=Michael_Li]

[條碼（barcode）維基百科](https://zh.wikipedia.org/wiki/%E6%A2%9D%E7%A2%BC)　　//這裡指一維條碼
[QR碼（學名為快速響應矩陣碼；Quick Response Code）維基百科](https://zh.wikipedia.org/wiki/QR%E7%A2%BC)　　//這裡指二維條碼
    - 是屬於開放式的標準
    - 跟傳統美國超商業者推行的條碼不一樣，不須要加入會員才能使用。
    - 參考：[二維條碼　維基百科](https://zh.wikipedia.org/wiki/%E4%BA%8C%E7%B6%AD%E6%A2%9D%E7%A2%BC)
GS1 Taiwan（國際組織）
> 需要花錢加入會員
> [name=Michael_Li]

    1.  [認識本會](http://www.gs1tw.org/twct/web/f001.html)[GS1 Taiwan 大事記](http://www.gs1tw.org/twct/web/memorabilia.jsp)
    2.  [Q15 :GS1的條碼標準，真的是通行全世界嗎？](http://www.gs1tw.org/twct/web/BarCode/gs1_barfaqshow.jsp?MKIND=BarCodes&MFAQ=one#15)
    3.  [如何正確編印國際條碼（使用國際條碼的10個步驟）](http://www.gs1tw.org/twct/web/BarCode/barcode_implement.html)
    4.  [GS1前置碼一覽表](http://www.gs1tw.org/twct/web/BarCode/set04.html)
        中國大陸製造商的會是 690 - 699  開頭，一眼就能知道。
        臺灣製造的會是 471 開頭。
> 補充：前幾天到美聯社，看到裡頭擺了一些罐頭，是大陸工廠製造的東西，條碼也是 69 開頭，有興趣可以去瞧瞧看。（敢不敢買回家吃就再說了）
> [name=Michael_Li]

[各種條碼的一覽表（設備廠商弄的頁面，很容易消化）](http://www.a8.com.tw/Tagasp/know_list.asp)
條碼小知識[（2009年我寫的文章）10月7日是發明條碼的日子](http://kunminginternational.blogspot.tw/2009/10/10-07.html)
【國碼 471】【廠商 MMMM】【產品 PPPPP】【檢查碼 C】[http://www.cyut.edu.tw/~lschen/bma/bma-ch4.pdf](http://www.cyut.edu.tw/~lschen/bma/bma-ch4.pdf)

### 開源套件

    補充一下:[http://sourceforge.net/projects/zbar/](http://sourceforge.net/projects/zbar/)
    這個開源的套件應該可以使用



## 建議事項

要不要先求有再求好？意即，先縮小範圍到「食品安全」的部份，針對食品來做，把塑化劑、有毒澱粉、稻米等問題食品納進來，在 scan 條碼的時候，可以提示什麼時間發生過什麼新聞，有疑問的內容物，或著這兩天爆出來的米老鼠之類的？
其實我覺得要把功能簡化到只有一個掃描器
掃描條碼之後只要回傳是不是屬於問題企業的產品即可
詳細的資料可以附上連結之類的


## 討論中


> 我以前做過一支app 是可以掃一維條碼的 app。其實一維條碼分解出來後也就只是一些數字，拿到那串數字之後再去跟資料庫裡撈資料出來比對。但我現在卡到的問題是：我要去哪裡取得一個資料庫，該資料庫裡有各項問題商品條碼及商品細項資料？
> [name=Dolphin S]

> 或是直接條碼＋\[關鍵字(例如: 黑心)\]上 google 去查？但關鍵字要用哪些好呢？還是讓使用者自己定義？
> [name=Dolphin S]

> 自問自答：剛試了一下，感覺不是個好解法。因為"4710088410313 餿水油" google 出來的結果比 "統一蔥燒牛肉麵 餿水油"的結果還更模糊。
> [name=Dolphin S]

> GS1 Taiwan　看看能否下載清單
> [name=Michael_Li]

> GS1 TW的資料庫似乎需要申請會員，通過人工審核才進得去
> [name=逸凡 陳]

> 您好，這專案目前是開發在 Android嗎？我是 iOS & Web開發者，是否能一起加入此專案呢？
> [name=kuei]

> 以一般消費者角度來想，是不是能試著先和 g0v公司查詢專案整合 [http://company.g0v.ronny.tw](http://company.g0v.ronny.tw)
> [name=kuei]

> 讓消費者先知道產品是否與某邪惡財團有關
> [name=kuei]

> １）如果是這樣子的話，我認為已經可以延伸變成一個大型資料庫網站（[暫名：人類商業產品大全](https://g0v.hackpad.tw/Xs65FqdSPxJ)），初步從小小的台灣出發。
> [name=Michael_Li]

> 我另外開個　hackpad　公佈出去試試看有沒有人會關注與跳坑。（[ＵＲＬ](https://g0v.hackpad.tw/Xs65FqdSPxJ)）。
> [name=Michael_Li]

> ２）用途就是原本我們就有資料庫是「台灣全部的商業法人統一編號跟股東名冊」，現在另外建立一個資料庫，靠群眾（工人智慧）來存檔目前在消費市場的「商品／產品」其中的資訊，甚麼資訊呢？例如基本的外觀（商品照片）、商家資訊、委託製造工廠的資訊、成分資訊……等等。
> [name=Michael_Li]

> 有點像amazon的fire phone，但是這是商業版。[amazon fire phone](http://www.amazon.com/Fire_Phone_13MP-Camera_32GB/dp/B00EOE0WKQ/ref=sr_1_1?s=wireless&ie=UTF8&qid=1413410412&sr=1-1&keywords=fire+phone)的firefly technology就是拍一個物品的照片，它就自動幫你辨認出這東西是什麼產品，然後告訴你amazon有沒有賣。不過那是因為amazon是美國網路零售龍頭，所以自然什麼都有什麼都賣。
> [name=Tzu-Yao L]




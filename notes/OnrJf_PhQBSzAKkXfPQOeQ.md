---
title: "農作物生產紀錄 app"
tags: 開發,hackpad
---

# 農作物生產紀錄 app

> [點此觀看原始內容](https://g0v.hackpad.tw/8c3ZyeuaKfF)

> 又是我們公司想做的app耶 XDDDD
> [name=Yuan C]

> 看樣子很多人都準備做啊
> [name=曼 奧]

> 而且我的確正在做生產紀錄的東西 
> [name=Yuan C]

> 合體？！？！
> [name=ET B]

> 合體\+\+ 之前很苦惱合體會出現的一個大問題，後來想到方案了!
> [name=曼 奧]

> 不過我在做的是植物工廠的部分, 然後目前著力於和感測器資料整合
> [name=Yuan C]

> 超宅 = =b
> [name=ET B]

> Q_Q 工作啊 ....
> [name=Yuan C]

> 我想加入～～請問要怎麼參與
> [name=rice]



### 命名

小農故事（暫）
## 融合提案

提案和[植物疫情と藥劑系統と栽培診斷](https://g0v.hackpad.com/8Hlh2hux8xg) 之後進行組合
下面是擷取IRC
直接跟農民買農產品這件事情
有一個我困擾的點
就是 藥劑殘留將沒有辦法被管控 目前農產品直銷市場確實有這種問題
就算使用生化法  也只能檢驗 氨基甲酸鹽類  以及 快被禁光的有機磷
其他是沒辦法的
後來我想到
既然生產紀錄的系統  是和 直接跟農夫買  或 一些幫助農民的團體合作
那麼 就有目標了  而且有可能可以讓  檢驗單位進行檢測  對消費者也有保障
另外一個融合的原因是 原本我設計的栽培者的栽培管理系統 是會和試驗改良場所做一個橋接的動作  所以有問題要診斷 要看田 或是 希望試驗單位給建議 又或者是試驗單位有好的東西想推廣
都可以直接受惠到農民身上  同時 也可以讓有加入的人可以第一手就拿到輔導的資訊
之後可以開農業小松:Q  我會斷續找一些專家來給各種觀點



### 緣由

ipa: 今天跟一位新朋友聊到，他在做直接跟農夫買的銷售和教育（[好食機](http://www.howsfood.com/)，[社區菜市長](https://sites.google.com/site/foodmayor/)），需要一個方便農夫上傳圖片、語音輸入/選單選擇的APP


### 構想

架一個任何農夫都可以建立生產履歷、跟任何一個通路合作的平台，讓我外公也可以用

### 預期目標


1\. 降低農民紀錄生產過程的門檻
2\. 讓農民可以在田間工作時，就隨時紀錄
3\. 讓農民可以不用輸入寫字，就能達到田間生產紀錄的目的

### 使用方式-農夫版 (app only)

1.  註冊→建立生產者資料
2.  登入→以生產者帳號發表資訊
-----------以上步驟只要做一次，可以請人協助操作-----------
1.  選擇/新增作物種類、預定的產品等級→建立生產履歷（同時設定預定出貨期間）
2.  每次巡田水時，在該生產履歷介面中新增拍照→自動紀錄拍照時間、產地
3.  選擇成長階段、肥料分類（或直接拍肥料包裝）→替該組照片加上標籤
4.  可以用錄音描述生產過程的細節
> 是語音輸入嗎？
> [name=ipa c]

> 語音輸入最好，可是多數農民用台語...，可否是錄音檔？消費者可以撥來聽就好？
> [name=謝昇佑]

5.  上傳→將照片和meta資訊上傳至該生產履歷並發佈
> 拍照部分, 我有做一些protoype了
> [name=Yuan C]

> where1
> [name=ET B]

> 私訊orz..
> [name=Yuan C]

> oh ok XD i'm doing prototype
> [name=ET B]

> 美國的app也有針對栽培者製作過栽培紀錄和用藥用肥紀錄的app可以參考
> [name=曼 奧]

> where?
> [name=ET B]

> 美國的晚點貼，先貼日本的
> [name=曼 奧]

> [https://www.cropnet.jp/login](https://www.cropnet.jp/login)
> [name=曼 奧]

6.  可以選擇資訊轉換成排版好的貼紙格式輸出（方便後端包裝使用）

### 使用方式-消費者版 (app/web)

1.  註冊→建立消費者資料
2.  登入→以消費者帳號發表資訊
\-\-\-\-\-\-\-\-\-\-\-
1.  瀏覽農產品
    - 依距離：找離我近的（google maps整合）
    - 依種類：找我想要吃的
    - 依等級：找我偏好的產品等級
    - 依通路：找我常去的地方有在賣的
    - 依評價：找最多人書籤或追蹤的、找我朋友推薦的
    - 可以同時看該產品的履歷、生產者的過往紀錄、其他消費者的書籤和追蹤數量
2.  加入書籤
3.  追蹤產品/農夫動態，出貨時通知我
4.  揪團買 \- 通常農夫一次出貨都是整箱的，例如20斤、30斤，一次送到一個地點，再由某人分送(社區菜市長)，所以想揪團的人，先發起一個團購，上面會看到要揪團的農產品(可連結回去看農夫故事跟生產歷程)、集貨地點，想參與的人，可以直接跟團，例如跟5斤、10斤，待湊滿整箱出貨標準後，會自動發信給平台及農夫跟所有團購者，平台跟農夫可以再確認接單、並且將出貨日期一起回覆。
> 之前有找過美國的，他們有針對距離和購買製作app
> [name=曼 奧]

> 伸網址
> [name=ET B]

> 日本人有做媒合的網站, 可以幫你根據農產品的等級送往不同的地方, 例如外觀好看的就送到五星級餐廳, 外觀差的就送到果醬工廠
> [name=Yuan C]



### 需要資料

- 農作物、畜牧產品清單
- 每一種產品各自有哪些等級分類
- 每一種產品的每一種等級各自有哪些製程、每個階段各需多久時間（成長階段）
- 每一種產品的每一種等級的每一階段各自會使用到哪些肥料或藥物
- 支援直接跟農夫買的通路清單，讓農夫在生產履歷註明哪裡可買到該產品
> 問農會？.
> [name=ET B]

> 哈囉 你們超厲害的 這些資料比我想著手推廣的完備 
> [name=SunshineWei]

> 程式我不會寫 但如果需要實際測試樣本 我可以幫忙找+協助使用 
> [name=SunshineWei]

> 本想私訊 但不知如何.... 總之 致敬 
> [name=SunshineWei]


資料標準
- [TraceCore](http://www.tracefood.org/index.php/Tools:TraceCore_XML_Overview), TAFT-XML [http://taft.coa.gov.tw/public/data/012221322871.pdf](http://taft.coa.gov.tw/public/data/012221322871.pdf)
> 看起來超複雜 QQ
> [name=ET B]

- _日本有一個相關的protocol_ [http://www.fujitsu.com/global/news/pr/archives/month/2012/20120725-02.html](http://www.fujitsu.com/global/news/pr/archives/month/2012/20120725-02.html)
> UECS
> [name=Yuan C]


### 介面設計

考慮到外公的老花眼，以平板為主，手機為輔


### 雛形

[http://g0v.github.io/farmers/public/](http://g0v.github.io/farmers/public/)




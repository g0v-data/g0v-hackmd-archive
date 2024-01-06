---
title: "助教專區"
tags: hackpad
---

# 助教專區

> [點此觀看原始內容](https://g0v.hackpad.tw/0.rbbkkmpcmqtihpvi)



## 8/9 試教疑問與 feedback

> 很多人沒有登入但也可以打字，導致 pad 一直沒有更新而不自知... 
> [name=Kirby W]

> 若有使用到 hackpad 的課程可能要提醒大家登入
> [name=Kirby W]



**點飲料 XD**  :+1:
### 「Honus Coffee 赫諾斯咖啡」

\- 菜單： [http://www.ipeen.com.tw/shop/806162/menu](http://www.ipeen.com.tw/shop/806162/menu)
看過菜單後請在自己的名字後面寫想要喝的飲料
> （不用 spreadsheet 順便練習樞紐分析嗎？）
> [name=Liang K]

> 可惜我不是第一場，不然就可以惹 XD
> [name=Kirby W]

> 疑！
> [name=Jimmy H]

- 慶徽 \- 經典鮮奶茶
- 皓翔 \- 日月潭紅玉
- 呈逸 \- 羅馬咖啡
- 維元 \- 蜂蜜鮮奶茶
- 偉倫 \- 黑糖拿鐵
- 依桃 -  宇治抹茶拿鐵
- 曉凡 \- 榛果拿鐵
- 宜婷 -  羅馬咖啡 :pig:
- 貞樺 -  經典鮮奶茶 :coffee:
- 珮伊 \- 黑糖拿鐵
- 柏任 \- 榛果拿鐵
- 榮泥 \- 宇治抹茶拿鐵
- 幾米 \- 冰拿鐵
- 科比 \- 榛果拿鐵
- 慕約 \- 經典鮮奶茶
- 村長 \- 拿鐵


### 資料在哪裡？

- 實價登錄網站操作可以錄 screencast
- 提到 csv 時可以看如何呼應前面 jimmy 已經講到的 spreadsheet
- segis 的資料有一些在內政部 OD portal 有，也許用那個當例子比較不用等註冊
- 練習一：匯入實價登錄 csv
- 練習二：轉換 xml (xml2csv)
> 純好奇， xml 真可正常轉 csv 嗎？不是有巢狀
> [name=Jimmy H]


- JSON View
> JSONView 我會放在行前準備，請大家先安裝
> [name=Jimmy H]


- 練習題要不要有一個「對資料的問題」，不然會不會大家不知道為何要匯入這個資料

- 我覺得直接告訴大家做什麼可能比較沒有感覺，或許可以：
    1\. 出一個題目，讓大家做
    2\. 遇到問題試著用自己的方法解決
    3.. 分享一些好方法
> 我的session下面有列出一些主題，應該可參考
> [name=Jimmy H]


- 分享自己平常會遇到的問題
- 分享自己平常的解決方法

- 剛剛發現 Kimono 也可以產生 RSS，或許能這樣解釋 Kimono 可以如何派上用場XD

### 穿越時空的資料新聞呈現

- 案例離真正能做到的太遙遠：（eg. 洪水地圖）
- 有些案例可以拿掉（eg. 種族隔離，因為 David 有提到更完整）
- 案例要與後面的作法連結
    - Ronny: JSON to CSV
    - Kirby: Spreadsheet 技巧
        - 日期 weekday
        - unique count  --> count table
        - geocode add on --> 經緯度轉換
    - Muyuan:
        - 樞紐分析 / importhtml
        - 選舉圖表案例（時間 \+ 費用）

### 迎戰壞資料 \- 實用工具與技巧


- Open Refine 可能需要預先壓力測試，有時網頁會卡在載入專案的畫面 .__.

- Facet 跟 Clustering 步調或許可以放慢一點點，尤其是 Clustering 一開始會顯示不出資料（要手動換成 nearest neighbor），很容易產生高挫折
> 感覺可以再把 open refine 的部份拉長， google spreadsheet 縮短一些
> [name=Kirby W]

> 可是我覺得 spreadsheet 講的滿好的
> [name=Jimmy H]


- 試算表的 slide A-B 1-3 (col/row name) 可以用不同顏色

- 可否介紹日期函式（把年月日切成年、月、日分欄），用樞紐分析很常用
-

### 資料視覺化：簡介與討論


- 選區 fill 好像可以跳過
- pivot table 多層可快速帶過
> 範例看看這個可用嗎？可用的話，我前面會分析下
> [name=Jimmy H]

> [http://elections.nytimes.com/2014/results/house](http://elections.nytimes.com/2014/results/house)
> [name=Jimmy H]



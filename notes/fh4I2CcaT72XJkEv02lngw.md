---
title: "天龍特公地－需求功能列表"
tags: 土地,公有地大行動,hackpad
---

# 天龍特公地－需求功能列表

> [點此觀看原始內容](https://g0v.hackpad.tw/quQyYm7cGrH)

> 加入foldr囉 [http://hackfoldr.org/POPonFire/quQyYm7cGrH](http://hackfoldr.org/POPonFire/quQyYm7cGrH)
> [name=che l]

> thank you 
> [name=Renee L]


taskList
把討論完，確定要做的功能列下來。為了讓之後想要加入的工程師，可以直接找到切入點，知道什麼是等待開發且未被認領的功能。之後若需求調整，此表也要跟著維護，才會有使用的效益哦！

## 背景資料

**Demo site:** [http://taipei-pop.herokuapp.com](http://taipei-pop.herokuapp.com) 這是針對台北市的一批資料來建置的
```
_pre-alpha 版_ http://codepen.io/dz1984/full/zLgjr/
```
> sorry, I  have no idea which one is latest
> [name=Renee L]

> codepen.io  是放 pre-alpha 版.
> [name=Donald Z]


** 程式位置：**[**~GitHub~**](https://github.com/g0v/POPonFire) [Taipei-POP](https://github.com/dz1984/taipei-pop)
> 2.0版後，正式切換到 Taipei-POP ，會在 Wiki 補上文件，方便讓想加入的工程師，能快速瞭解整個專案狀況。
> [name=Donald Z]


** 程式架構**
```
目前使用node.js
資料層取層
    透過資料存取API，讀取檔案，依據條件回傳結果的GeoJson
```
> 以上是我猜想的描述，不知道對不對
> [name=Renee L]

```
    公有土地資料作資料前處理，最後以geojson格式儲存為純文字檔供使用
GIS層不明


```
** API清單**
    待補

- sherry> 各位好 (小聲，查詢臺北都更進度的API現在可以把結果轉成json了，有案件號碼 進度等等，[https://github.com/solring/UrbanRenewProgress](https://github.com/solring/UrbanRenewProgress)
- 地圖化+土地形狀呈現+所有權單位呈現+面積呈現 [https://github.com/g0v-data/POP-data/tree/master/taipei](https://github.com/g0v-data/POP-data/tree/master/taipei)

## 功能需求項目

** 資料前處理**
1.  ~台北市可建築且無建築物登記的公有空地地號 ~
        - [x]  跳坑者：
```
   詳細功能描述： 將資料處理成geojson
原始資料： http://data.g0v.tw/dataset/70
geojson格式參考：https://github.com/g0v-data/POP-data/tree/master/taipei
```
> 偷問一下 這不是已經有ronny大提供的geojson了嗎 . _ .?
> [name=sherry l]

> 當時寫的時候這項還沒好 XD，我明天來更新一下目前狀況 因為原本爬討論的那份看不是很懂有哪些項目做了和沒做
> [name=Renee L]


**後端**
    1.  DB建置
        - [ ]  跳坑者：
```
   詳細功能描述： 未定案 maybe mongo?因為資料格式已經都轉為geojson，可以直接塞進去?


```
 ------------------------------------------------------------------------------------------------------
地址定位
        - [x]  跳坑者：已完成
```
   詳細功能描述：於下拉選單的最右方加上地址定位
              將地址轉為經緯度坐標後，直接貼點到地圖上標示，定位的位址
googleAPI資料： http://goo.gl/DhFVe
```
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-
單筆土地資料
        - [ ]  跳坑者：
        1.  呈現
```
       詳細功能描述：

```
        1.  協作
```
       詳細功能描述：
```
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-
```txt






```
**前端介面請至：**[**http://hackfoldr.org/POPonFire/6UvvtZqOfN5**](http://hackfoldr.org/POPonFire/6UvvtZqOfN5)



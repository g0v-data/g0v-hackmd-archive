---
title: "提案：小蜜蜂簽名檔產生器"
tags: hackpad
---

# 提案：小蜜蜂簽名檔產生器

> [點此觀看原始內容](https://g0v.hackpad.tw/IAcggxN9suJ)

## 構想

因為現有的小蜜蜂官方傳單，只有附總隊網址的QR code，對平常就是以使用桌上型電腦為主的人來講，不是那麼有親和力，而且沒有宣傳在地蜂巢的效果，所以想要一個自動產生器，在傳單的底部加入總隊跟在地蜂巢網址。

## 簽名檔範例

例如說
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_25484e4606e23dd9bfaac995286f13ba)
[https://i.imgur.com/ycyLHQC.jpg](https://i.imgur.com/ycyLHQC.jpg)
這張傳單，下面加上
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b5b50ba2a67cfdd26fbf59a032d92f60)

這樣的簽名檔以後
變成這樣
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_354a7a8c995a2724b673bcfc2e0f33ff)
[https://i.imgur.com/II2NiiE.jpg](https://i.imgur.com/II2NiiE.jpg)

## 希望能夠實作的形式

希望是網頁表單，例如說像報告產生器 [http://taphy.com/taphyd/bb3](http://taphy.com/taphyd/bb3)
這種
只要使用者打入蜂巢網址跟名字，還有傳單網址，就會在伺服器上面生成傳單的pdf檔。

## 流程

1.  匯入pdf檔，並轉換成A4大小的圖檔 **(『圖片1』)**
2.  接收使用者提交的表單
3.  把表單內容自動作成一張簽名檔圖片 (『圖片2』)
4.  把圖片1縮小，跟圖片2合併在A4大小的圖檔裡(『圖片3』)
5.  (optional)把圖片3匯出成pdf
6.  提供使用者下載連結





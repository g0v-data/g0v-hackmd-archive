---
title: "Bifrost"
tags: hackpad
---

# Bifrost

> [點此觀看原始內容](https://g0v.hackpad.tw/KADph5GahW1)


本頁面紀錄 Bifrost 改寫的進度以及需求。

Bifrost 是一個用來可以接受物資捐獻的網站，並且在同網站上可以知道目前有多少人認領了那些物資的捐贈，以及實際收到多少物資。可以參考這份投影片第十七頁開始，前面在介紹 g0v


[https://speakerdeck.com/yurenju/wu-zi-guan-li-xi-tong-yu-zai-min-zheng?slide=17](https://speakerdeck.com/yurenju/wu-zi-guan-li-xi-tong-yu-zai-min-zheng?slide=17)

前情提要：Bifrost 在 2015 年三月 Demo 雛形，並且在 10 月跟社會局第一次較深入的討論後比較理解要做出怎樣的系統他們會比較合用，另外之前後台的部份實作的也不完整，在這次也會一起實作完畢。

另外因為正在熟悉 react，所以這個網站由 angular.js 改由 react.js 撰寫。所有新版本的程式都在 \`develop\` branch 裡面

使用者介面設計請見這份文件 [https://vectr.com/yurenju/designs/bifrost](https://vectr.com/yurenju/designs/bifrost)

### 2015/1/24


本日希望完成的工作
- 後端的 model 依照介面設計重新調整 model，並且建立 sample 資料
- 把前台的 router 都設定好
- 至少第一頁可以完成



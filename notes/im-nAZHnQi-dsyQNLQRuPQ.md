---
title: "「少點 Less,More」友善環境App規劃"
tags: hackpad
---

# 「少點 Less,More」友善環境App規劃

> [點此觀看原始內容](https://g0v.hackpad.tw/bBclKtkhC3L)


> g0v 公民科技創新獎助金提案 [https://grants.g0v.tw/](https://grants.g0v.tw/projects/5a641bb5900e86001bf9f517)[projects/5a641bb5900e86001bf9f517](https://grants.g0v.tw/projects/5a641bb5900e86001bf9f517)
> [name=Starhead]


### 發想緣由


友善農業、不塑生活、重視生態環境的族群日益增加，但相關資訊尚無便利整合的平台查詢。

「我想知道附近哪些店家支持不塑行動」
「我想享受用在地食材用心烹調的料理」
「我想知道這些包裝材料可拿去哪裡回收使用」
「我想從生活中支持理念相同的人，他們在哪？」
「我想知道哪些地方提供非一次性餐具 / 不使用美耐皿餐具」

### 現況

    - 同溫層力量分散
    - 相關討論社團月經文頻頻
    - 想開始行動卻不知是否有就近資源

### 現有類似做法

    - 好日子 無痕購物地圖（使用 Google My Map）
    - 全台灣＋全球環保地圖 [https://rischa.blogspot.tw/2017/07/blog-post_58.html](https://rischa.blogspot.tw/2017/07/blog-post_58.html)

- **缺點**
    - 沒辦法以使用者本身需求為出發點
    - 列表各縣市全混在一起，排版控感到難過
    - 很不便民，使用率低（瀏覽次數 16,000，資料筆數 100 多筆）


### 我想這麼做


    - 自己挖的坑自己跳
    - 透過串連交流經驗與資源
    - 以力量的凝聚取代厭世無力

### 坑主能做的

    - 發想規劃
    - 界面設計
    - 測試修正

### 坑主需要的

    - 了解執行需要的技術、難度、資源，討論出確切可開始動手做的程度
    - 程式人員
    - UX人員或技術諮詢
    - 討論出一個響亮的名字


### 預期功能/使用方式

- 初階功能
    開啟程式後，可依照個人需求查詢如下：
    1.  地圖顯示特定類型之商家
    2.  所在地周遭所有登錄於資料庫中的商家
    3.  點選商家，顯示店家資訊與細節分類
    （如：分類-「不塑店家」→「食材」「清潔用品」「裸賣分裝」「鼓勵自備容器」）

- 進階功能
    加入帳號匯入，使用者登錄資料功能與評論記錄
    導航功能
    評分排名
    常用店家

分類規劃
    不塑店家（菜市場、夜市、餐飲店、其他類型-無包裝商店、民宿、書店）
    小農市集（大型、傳統市場中的攤販）
    有機/友善環境店家（連鎖、獨立，食材、生活用品）
    城市修理站（物件/工具交流/包裝材料索取）
    二手物件/衣
    剩食/共食
    星等搜尋

### 視覺呈現


2018/01/08版本（目前想到的簡略版本）
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9432ef61981c38e60df6615bd1578342)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0f131c9f241324913830162e1f897476)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6bd6789d78997e0eabee1a4285654a33)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_da4de5f5b08d50739a7a5bfcd1c53dc1)

### 0112會議討論

對工程師來說會不會太簡單所以沒有挑戰性導致沒人想加入？
資料正確性篩核機制


iOS上架費 100美元/年（頁面設定 1.78:1 1920x1080）
Android 25美元（永久）

系統搜尋關鍵字抓資料，後台審核上架（臉書行事曆、活動網站）

推薦伺服器位置

後續設備維護費用可用

如何避免成為只有同溫層使用的東西

Q：網站版與App版資料庫是否能共用？
A：前端（呈現方式網站、App）後端（資料庫可共用）

如何抓資料？

### 0113會議討論

工作分配
獎助金提案撰寫
[https://docs.google.com/document/d/1KnpUiokW2IG5aP9AiDlgu4u7CnXAtTrraS4u_890AUo/edit#](https://docs.google.com/document/d/1KnpUiokW2IG5aP9AiDlgu4u7CnXAtTrraS4u_890AUo/edit#)

[今日進度報告](https://docs.google.com/presentation/d/1LZMBng6xYoczslGHaXSsh9zVnPCfykTW9uADAJnN1yY/edit?usp=sharing)
網站界面設計 / 每一頁面的功能與視覺（提供整張圖，一般圖檔格式）

家齊：下週可以開始寫簡單的 iOS 版本看看（臉書、Google 登入和地圖上的資料及選單等）

- 討論名稱
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8fa1bbacc36066afaed3d98cf17c98bc)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a0d179a523924bad8fbdf32bca0d4d9c)


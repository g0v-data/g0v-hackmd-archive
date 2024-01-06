---
title: "虎神快閃認領行動"
tags: 醫療,hackpad
---

# 虎神快閃認領行動

> [點此觀看原始內容](https://g0v.hackpad.tw/wBQa0t7bAmM)



## 專案簡介

**提供匿名的醫療勞動條件爆料平台，並搭配** [Digital 虎神快閃認領行動](https://www.facebook.com/digital.nurses)  **，整合實體快閃與網路爆料的資訊。**

**發起人/拋磚人**：ddio、[基層護理產業工會](https://www.facebook.com/powerful.nurses)

## 目標與功能（要如何解決）

### 目標

- 要好玩
- 不需要填 gps 座標，但就要能顯示在地圖上
- 盡量自動化，因為基護工會也沒多少人 T___T
    - 自動化對應醫院 \- LatLng
    - 協助找出重複醫院名稱，像是「台大醫院」、「台灣大學附設醫院」等等

### 預定功能

- 讓人爆料各個醫療場所的勞動問題
- 用地圖、排行榜來呈現
    - 使用者只需填基本的醫院資訊（城市、醫院/診所名稱），就可以自動在地圖上顯示
    - 可以瀏覽特定醫院的爆料們
    - 其他有趣的資料呈現方式
- 整合快閃的資料，像是照片、臉書狀態更新等

### 預定使用者

- 基護工會組織者，可以直接看目前爆料狀況、連結照片等等
- 想要爆料的人，像是護理人員、親友、病人等


## 要解決的問題


授權方式
- MIT
- CC-BY
- 使用者貢獻的資料，則是 copy right （目前基護沒有特別限制授權）

使用資料
- google geocoder

專案目前狀態
實作中～正在根據狀況自我演化～




## 徵求協作者

發起人/拋磚人：ddio

因為資料涉及個人資訊，所以後端暫不公開徵求協作（而且 ddio 不知道怎麼把 app script 弄進 git...）
不過如果有人有好點子，還是歡迎提供！

分工與成員

- [ ] NeedsDesigner: 需要介面設計
- [ ] NeedsBackEndIdea: 需要後端問題處理

## 實作細節（非技術背景可跳填）



協作工具
- github repo：[https://github.com/ddio/MuscidaeFlash](https://github.com/ddio/MuscidaeFlash)
- hackfoldr 工作資料夾網址：
- google drive 共用資料夾網址：

進度與 to-do

- [x] web front-end
- [x] web back-end
    - [ ] 協助基護工作者，自動/半自動找到重複的醫院名稱
- [ ] ui / visual design


## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）


網站：[http://ddio.github.io/MuscidaeFlash/](http://ddio.github.io/MuscidaeFlash/)


## 功能討論/問題回報


### 地圖圖標相關

- 點地圖上的蒼蠅，跳到醫院的爆料內容
- 滑鼠移到蒼蠅上時，變成便便，旁邊出現醫院名字

### 個別醫院互動

- 可以針對各家醫院留言、討論

###  問題回報

-  Safari , mercury on iphone 開不起來，疑似有 js error ， ko 沒跑起來
- 爆料文太長，會被擋住，沒有捲軸



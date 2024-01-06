---
title: "公有土地資料庫－介面設計"
tags: 公有地大行動,hackpad
---

# 公有土地資料庫－介面設計

> [點此觀看原始內容](https://g0v.hackpad.tw/5wyYu217bLy)


## 近期討論


### 20140831

[http://poponfire.herokuapp](http://poponfire.herokuapp)
- 案簡報：opd檔[下載按這裡](http://www.openfoundry.org/of/download_path/openlegal/Open_Government_Data_license_for_Taiwan_from_a_bottom_up_perspective/20141220-proposal.odp)，pdf檔[下載按這裡](http://www.openfoundry.org/of/download_path/openlegal/Open_Government_Data_license_for_Taiwan_from_a_bottom_up_perspective/20141220-proposal.pdf) 。
- 專案英文
    - 全稱：Taiwan Open Government Data License - Citizens Community Version
    - 縮寫：**TWOGD - CC version**
- 2014/12/20-hackthon11-下午專案報告簡報：odp檔[下載按這裡](http://www.openfoundry.org/of/download_path/openlegal/Open_Government_Data_license_for_Taiwan_from_a_bottom_up_perspective/20141220.odp) ，p[df檔下載按這裡](http://www.openfoundry.org/of/download_path/openlegal/Open_Government_Data_license_for_Taiwan_from_a_bottom_up_perspective/20141220.pdf) 。
[.com/](http://poponfire.herokuapp.com/)

### 20140702 Pre-Alpha版 from Donald

根據手稿Mockup做出來的[Pre-Alpha版](http://codepen.io/dz1984/full/aldfI)，請給點建議。另外，請大家協助一下：
1.  下拉式選單：地點，開發方式，經營單位，應該放些什麼資料？
2.  LOGO：每個人心中都有一位畢卡索，請釋放它，幫公有地大行動生出一個LOGO

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_29933e9c712851d61cd2497fae7a7078)


## LOGO 醞釀中！

[方案](http://hackfoldr.org/POPonFire/XS4mBmUhr8u)

##  Mockup與功能描述

網頁構想

#### 第一階段

- 火線地圖
    - 標記最近十筆由國產署標租地點。
    - 依照地點面積調整紅圈大小。
- 網站介紹與說明
    - 火線定義
- 檢索入口（地區、開發方式、政府機關、相關人物）
    - 依檢索條件顯示結果。
#### 第二階段

- 每一筆公有土地的被開發方式資訊，個案歷程
- 「一天抓一次資料」的動態擷取顯示
- 手動輸入資料
- 歷史資料與事件

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3001245f9df496f869b1c55a91f05f8f)


## 地圖介面設計

需要處理的問題：
- 現在的「火線地圖」如果用多邊形呈現在地圖上，在大尺度（例如顯示整個中部地區）大概會小到看不清楚。
    - 可能要：地圖旁邊需要條列出每塊地的地址
        - mouseover 的時候，那塊地的多邊形會亮起來
        - click 的時候，地圖會捲到那塊地的位置
- pre-alpha 版的上下兩區操作有點混淆，也可以更節省空間。
    - ~可能要：移除下方的檢索結果，把檢索結果顯示在上方的地圖裡，讓整個介面只有一份地圖。~
- 現在搜尋不到「我的位置（例如我家）附近的公有地」
    - 可能要：增加「搜尋附近的公有地」的功能
- 現在沒有追蹤特定某塊地的頁面，這樣無法形成討論
    - 可能要：每塊地有自己的條目頁

預計會改成：
- [ ] 底下的檢索結果改成用表格或條列
- [ ] 加一個「在上面地圖呈現」的按鈕
- [ ] 加一個「下載檢索結果」
- [ ] 「主管機關」選單加上文字篩選
- [ ] 顯示出來的地圖要有 permalink，最好有 full screen 版本可以嵌入其它地方
- [ ] 加一個「看我的位置附近」

> 可以參考之前有個「服貿地圖」專案 [https://github.com/g0v/tisa-map](https://github.com/g0v/tisa-map)
> [name=Pomin W]

> 檢索的功能：關心某個地點（中和 or else）；關心各種開發方式
> [name=Pomin W]

> 跟 [che wei liu](https://g0v.hackpad.tw/ep/profile/zsVEYFJyWhm) 討論過，我在黑客松前大概會上面列的介面修改做好dd
> [name=Pomin W]

> 在OSM meeting碰到~
> [name=che l]

> [Pomin Wu](https://g0v.hackpad.tw/ep/profile/oGf5HRRuJSf)  :+1:
> [name=Donald Z]


公有土地主管機關也是有不同的區分，是否能在介面上用不同的顏色框來作區分呢？台北市政府、各校產管理單位、教育部xxx辦公室、交通部、國防部、退輔會......



## 其他功能

- 可設置 google 表單，來詢問：
    - 詢問大家對於此資料庫的使用想像：「會拿來怎麼用？」
    - 意見回饋
    - 此表單是否本身也是個公開的留言板，看得到以前的人發表的意見


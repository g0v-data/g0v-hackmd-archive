---
title: 累積實體環境營造願景的方法
description: 
tags: tree
image: https://talk.pdis.nat.gov.tw/uploads/default/original/2X/1/1ed43ffbba0fac00d4d9f67a754995dcacfe24bd.jpeg
---

# Site-visioning Platform Solution

累積實體環境營造願景的方法 / 平臺方案評估

:::warning
目錄
[TOC]
:::



## site-vision disscusion
- Unlimited Cities DIY
    - 介紹影片：https://youtu.be/044OpAFvaXg
    - 網站透過「透視角度場景+物件選用拼貼」的方式，蒐集不同使用者對於空間改造的構想，影片內容是針對台北市文山區的五處社區空間進行空間願景蒐集。
        - 依山小綠洲 https://wenshanoasis.wixsite.com/mysite
        - 願景網站 https://wenshanoasis.wixsite.com/mysite/professional
    - 木柵一塊公有地
        - 推動單位：[Urban Taiouan](https://urbantaiouan.com/2020/02/11/ateliers-participatifs-et-terrain-vague-unlimited-cities-muzha/)
        - https://www.unli-diy.org/dev/muzha/muzha
    - 比利時布魯塞爾市區植樹探討 針對布魯塞爾市區的五處廣場空間，讓使用者挑選 喬木與植栽，以及街道傢俱，在平板畫面上拼貼出環境改造的願景。
        - 推動單位：https://www.woodwideweb.be/en/
        - webpage: https://www.unli-diy.org/dev/WoodWideWeb-BXL/bxl
    - 單張使用
        - https://unli-diy.org/dev/DIY/#/gallery
        - [link](http://unli-diy.org/dev/DIY/?fbclid=IwAR3JSMTShrslw7OkAQL6e-ED_ZUsT0sFUICKUAGTKbHAbkZfHFj7d36r-xI#/gallery)
    - 觀點文章
        - 無限城市在台灣：合作性都市規劃，公民參與及數位工具 https://eyesonplace.net/2019/08/28/12416/
    - 發想
        - 素材選用，連動 造價與費用計算 ?
    - Open Source
        - https://gitlab.com/7billion-urbanists/unlimitedcities
        - https://github.com/Monaludao/unlimitedcities
- GREENIFICATION : Planting + Augmented Reality
    - https://airtable.com/shr4f3DnuXOslFyss/tblPtI3b0UhzUT1fH/viwq0grXbLsYekbkL/rechqQAMjhoD41thY?blocks=hide
    - gitlab
- Hub2 - designing a real park in Second Life
    - https://youtu.be/7PtkmROOToQ
    - https://www.boston.gov/civic-engagement/hub2
- voxel.js
    - http://www.voxeljs.com/
    - 待了解特點

### 個案 Demo
- 總統府對面兩塊「廣場用地」目前為停車場 
    - FB 社團：http://bit.ly/tree-taiwan-fb-plaza
    - 視訊空間：
        - 操作畫面影片：https://youtu.be/4Ftyc4v-eT8
        - https://hubs.mozilla.com/fRm5XWo/chewei-test/
        - 建模：https://hubs.mozilla.com/spoke
        - 建模方案：
            - 衛星圖當底圖，週邊建物（台北市資料）+總統府模型
            - 總統府 3D 模型：[link1](https://3dwarehouse.sketchup.com/model/1b964e37a78c1f39cc38ce9903ace7d8/Office-of-the-President-TAIWAN-%E5%8F%B0%E7%81%A3%E7%B8%BD%E7%B5%B1%E5%BA%9C-csc-v10?hl=zh-TW&login=true)、[link2](https://3dwarehouse.sketchup.com/model/793c1821908a79653e88ee415313f03e/%E5%9C%9F%E6%9C%A8%E7%B5%84%E7%AC%AC%E4%B8%80%E9%A1%8C-%E7%B8%BD%E7%B5%B1%E5%BA%9C?hl=zh-TW&login=true)
            - issue
                - skp 檔案，透過 sktechup 單機版軟體，轉出 stl 格式
                - stl 格式，轉成 glb 格式
                - glb 格式，才能匯入 spoke (Mozilla Hubs 的場景建模器)
                - 場景中問題：
                    - 【建物模型】屋頂少掉一邊、材質無法一併轉出
                    - 【行走範圍】局限於建物前的平面，不利於使用者在廣場移動，目前僅能用飛行模式，但其實不方便移動
                    - 【提醒使用者】WASD 前後左右， G 開啟飛行模式
                - [Discord 社群發問區](https://discordapp.com/channels/498741086295031808/537726109555359745)
- 廣場使用
    - [總統府府前廣場使用須知](https://www.president.gov.tw/Page/284/1258/%E7%B8%BD%E7%B5%B1%E5%BA%9C%E5%BA%9C%E5%89%8D%E5%BB%A3%E5%A0%B4%E4%BD%BF%E7%94%A8%E9%A0%88%E7%9F%A5)


- 非都市土地
    - 參考 115 個指標基地來挑選
    - 例如鄉村的、海岸的、與地方創生在地產業地景相關的基地




## multi-sites platform
- explorer.land platform
    - https://explorer.openforests.com/
    - Transparency builds trust. explorer.land is a map-based platform to demonstrate the impact of your forest project. Connect with donors, investors and product buyers by combining exciting storytelling and data on an interactive map.
- Free Space Berlin 
    - 針對閒置公有空間，舉辦實體活動蒐集市民意見，網路上僅作展示，並無線上討論功能
    - http://www.freespaceberlin.org/
- Livinglots
    - 將紐約的公有空地與社區農園，每一塊設立一個專屬的頁面，提供會員登入機制，留言討論的論壇
    - https://livinglotsnyc.org/
    - https://github.com/596acres/django-livinglots
    - 一塊地有一個專屬頁面，論壇化，不過就要看使用者是否常回訪 https://livinglotsnyc.org/lot/59126/
- CONSUL open source (https://github.com/consul/consul)
    - cases 實例 
        - [參與式預算提議＆討論工具](https://demo.consulproject.org/budgets)
        - [紐約市參與式預算](https://pbnyc.participatorybudgeting.org/budgets)，地區居民對地區公共建設需求直接提案、討論、投票，最後由政府撥款執行。
        - [馬德里 Decide Madrid](https://decide.madrid.es/vota)



# 基於好植地專案用地盤點成果，來評估方案

## Needs 需求
- 數量預估 500-1000 sites
    - 已找出 100+ 個指標基地，需要累積每個基地的改造願景
    - 官方提供待認養土地數量，也是數百為單位
    - 使用者可能會自己圈繪一個關注基地
- 要討論什麼 Content
    - 希望每一塊地，能夠有專屬的「討論版」
    - 需要能夠拍照上傳基地現況
    - 可以留言說明接洽管理單位的進度，以及提供一些想法或參考資料等


## 國內可能相關論壇：JOIN 平台
- 主題相近的既有案例：[眾開講-中興新村厚德殯儀館活化工作坊-議題徵詢及報名](https://join.gov.tw/policies/detail/08e289ba-6bbf-4ab4-bc55-be157cb26b1f)
- 新增工具來輔助空間願景類的民眾討論
    - [頁面](https://docs.google.com/document/d/1Ev7LJ3gIAZhBBY3CDsYhyoMzAzCqVbMWYUjD_GO-GzI/edit#)
- 總統府南北廣場願景共擬


## 自架論壇

### 探討

運用既有開源方案
- CONSUL open source (https://github.com/consul/consul)
- [用 discourse 建立一個討論區呢？每塊地是一個版，缺點是要定期維護](https://g0v-tw.slack.com/archives/CQSH4F276/p1584437428038300)
- 參考 [「你覺得線上意見徵集系統應該要長成什麼樣子？」工具試用](https://g0v.hackmd.io/@aPX46l3cTnCLGYYFJv8mfg/HkKmTUIrI)

社群媒體討論功能
- 設立一個 FB 社團，每一塊地設立一個相簿，用相簿來累積照片、資料網址、留言討論串，好處是可以就這個社團的成員，可以總覽每一塊地促進交流，但土地總數量蠻多，難以想像例如 500 個相簿在一個社團內如何管理
    - 【用地篩選網頁】https://tree-planting.tw/
    - 各個基地的相簿 https://www.facebook.com/groups/2695218770596909/

文件屬性
- 設立一個 google my map 開放編輯權限，每一個關注基地是一筆資料，好處是地理式呈現，但是沒有留言功能，也無法用多元標籤，頂多用 10 個圖層來分類
- 每一塊地 設立一個專屬的 google doc 累積圖文，但不容易知道是誰留言，對於使用者來說頁面會很單調沒有其他人存在

moogoo 曾建立過「個案頁面」
- Github：https://github.com/tree-planting

探討
- https://g0v.hackmd.io/H2j1KBOETJiSA-EuzriArA

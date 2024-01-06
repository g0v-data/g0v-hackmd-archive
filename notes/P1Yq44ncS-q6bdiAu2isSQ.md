---
tags: tree
---

# Photo 用地踏查拍照 - 方案討論

:::warning
目錄
[TOC]
:::

## 使用情境描述：
- 必要
    - 需要把既有的[基地](https://bit.ly/tree-taiwan-map)位置呈現給使用者
    - 可以得知「(舉例)臺南市馬雅各長青公園」所有相關的現場通報拍照影像，以及總計可新植數量數字
- 流程：
    - 查看基地分佈地圖 -> 至現場拍照上傳
    - 路過並發現一處潛力地點(不論是否為已盤點用地) -> 現場拍照上傳
- 工具討論
    - 基地分佈地圖-方案一：uMap (網頁)
        - uMap 沒有衛星影像底圖
    - 基地分佈地圖-方案二：使用者 Google My Map (APP 內開啟)
        - 但其實不一定好操作，很多時候會因為顯示原因很難順利在螢幕畫面中瀏覽基地輪廓線
    - 上傳照片的工具：群眾標註
        - 欄位要填哪些？
            - 此照片地點的估計新植數量
        - 資料整理
            - 所上傳的照片都是 Point，潛力基地則是 Polygon，兩邊需要綁定關聯性
    - 上傳照片的工具：FB 社團該基地的相簿
        - 文字描述可以用留言方式，但無法資料結構化

---

## 工具盤點

### 使用「群眾標註」工具，拍照上傳與填寫回報欄位

方案內容：
- 群眾標註
    - 網頁：https://commutag.agawork.tw/
    - 社團：https://www.facebook.com/groups/573697330058183
- 企劃草稿文件
    - https://docs.google.com/document/d/1PgsGOfweobobXh3bAAFlhzW2rlvE_byStVA9i5NzR6c/edit

### 幫潛力基地開 FB 相簿

方案內容：
- 工作社團：臺灣好植地 - 潛力用地討論
    - https://www.facebook.com/groups/2695218770596909/permalink/3743685855750190/
- 操作流程：
    - 使用者拍照
    - 使用者在 FB 社團，幫一個基地，設置相簿，上傳該基地的照片

課題歸納
- 用地的地理位置，需要另外建立


### 使用「Airtable + AwesomeTable」

方案內容：
- 主要架構
    - Airtable 的用地資料內有經緯度與編輯連結
    - Coupler.io 每小時匯出至 Googlesheet
    - Awesome Table 把Sheet 產製為地圖
    - 使用者於手機網頁上點擊地圖，提供該基地文字填寫 Airtable 編輯網址，以及該基地的 FB 社團相簿網址，上傳該用地的照片
- 測試地圖
    - https://app.awesome-table.com/-McxyfR3GvzXOqsPInUX/view
- 操作影片
    - https://www.facebook.com/groups/573697330058183/posts/959199314841314
- 工作文件
    - https://docs.google.com/presentation/d/1MAijLJ-MjcB0y732hJEtgVLMek1PYvvcG7ZM47-TQ0Q/edit

課題歸納
- 使用者操作
    - 如果看到一個新的地點，無法在現場新增新的用地
- 工具
    - Airtable 開始針對使用頻率高的文件，不提供免費方案，種樹計畫的 airtable 預計 12/10 停止新增資料列

### 台南也要特色公園 by Kiang

https://parks.olc.tw/
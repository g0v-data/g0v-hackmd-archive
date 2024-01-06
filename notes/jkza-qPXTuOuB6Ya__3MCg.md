---
tags: GIS
---

# Awesome-table & Spreadsheet

## 工具介紹

<iframe width=100% height="490" src="https://www.youtube.com/embed/SgIWQGUW-c4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br>
<br>
==AwesomeTable 操作教學影片：https://youtu.be/SgIWQGUW-c4==
工具網址：https://awesome-table.com/

🔻 Awesome-table 地圖模式，以「民間社群標註官方公布的確診者足跡 😷 」資料為例
另開網頁：https://app.awesome-table.com/-MevBcqxlbvI5ec5ab5I/view
<iframe referrerpolicy="no-referrer-when-downgrade" height="600px" width="100%" style="border:none;" src="https://app.awesome-table.com/-MevBcqxlbvI5ec5ab5I/view"></iframe>

特點：
- 優點：以 spreadsheet 作為資料集，同步更新於地圖
- 優點：提供「Filter 篩選器」
- 優點：提供「街景服務」
- 缺點：無法呈現「線型資料、面狀資料」，因為 google spreadsheet 無法支持線與面的地理資料型態
- 缺點：沒有「圖層」功能

資料
- 資料來源：[民間社群標註官方公布的確診者足跡 😷](https://g0v.hackmd.io/GNfNQ8NbQ5KXJNTyftRLgA)
- 透過試算表的函式，與資料來源同步更新資料
    - `=IMPORTRANGE("1eNgxy1nP36rhugQ5tcti2a7MHsDVYipHYDfOGFbaqIU", "Merged!A2:X")`
- 本次示範地圖所使用的 [Spreadsheet 資料集](https://docs.google.com/spreadsheets/d/1GBAyWId91JAU0kxpCkN28mWpE-tdt9BcCVIiRxP5P7U/edit?usp=sharing)

地圖樣式編輯方式說明
- (1) Spreadsheet 資料集
    - 在資料集的「第二列」，給予每一個欄位，特定的文字代碼
    - 各種文字代碼的用途
        - 指定該欄位為「經度」：`NoFilter - MapsLong - Hidden`
        - 指定該欄位為「緯度」：`NoFilter - MapsLat - Hidden`
        - 指定該欄位為可以透過「關鍵字」的方式進行篩選：`StringFilter`
        - 指定該欄位為可以透過「選項」的方式進行篩選：`CategoryFilter (C)`
        - 指定該欄位「不顯示」於前臺地圖中：`Hidden`
    - 官方釋出的篩選器文字代碼，種類說明
        - https://support.awesome-table.com/hc/en-us/articles/115001068189-Filters-select-data-to-display
- (2) 地圖編輯區
    - 可參考此介面 https://app.awesome-table.com/-MevBcqxlbvI5ec5ab5I/edit
- (3) 記得確認一下瀏覽權限有沒有打開喔！
    - Awesome-table 的地圖瀏覽授權，會沿用來源 google spreadsheet 的瀏覽授權
    - 可以用無痕狀態，不登入 google 帳號的情況下，點開地圖網址，看看是否能順利看到內容
    - 若沒有看到地圖內容，表示「來源 google spreadsheet」的瀏覽授權要打開
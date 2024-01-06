# 2020/1/17 里伯提案分享
## Add-on for 單一陳情系統
### 回顧現行流程
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a9ce571ed26b7468d312e14b9114ab83)

### 什麼是 Add-on？
- 一小段程式可以隨意的（optional）加裝在主要的服務上。
- 舉例：行車記錄器與汽車的關係。
- 舉例：備份 add-on for website。
- **適合描述里伯與單一陳情系統的關係。** 並以此為大方向。
### 專注於里伯想解決的問題
- 不用重造輪子處理單一陳情系統已經能解決的問題
    - 符合法規：行政程序法、臺北市政府及所屬各機關處理人民陳情案件注意事項
    - 符合行政單位內部處理流程（陳閱流程）
- 讓里伯專注於解決使用者體驗的問題
    - 快速找到案件類別（**民眾好了解的分類**與**依組織架構分類**，兩種分類的協作）
    - 快速選定地圖上的點位（單一陳情系統很難標路燈位置）
    - 提案件時整體流程的優化
## 設計問卷
### 有憑有據的指出問題（以里長年齡分布為例）
- 資料來源：[臺北市第13屆里長名錄](https://www-ws.gov.taipei/Download.ashx?u=LzAwMS9VcGxvYWQvMzM0L3JlbGZpbGUvMTYxMTkvNzk5OTgwOC8zMDIyNzA2OC1mZThmLTQ1ZjQtOGNlYS0wYTM1M2U2NjY1MzAucGRm&n=56ysMTPlsYbph4zplbflkI3pjIRfMTA4MDYyNC5wZGY%3d&icon=.pdf)
- 年齡分布：[Google Spreadsheet](https://docs.google.com/spreadsheets/d/1wzV6QelKDx4R97i9g1HVNP9_6jDIfuqxd0-wZX-CrBU/edit?usp=sharing)
- 年齡分布的前三名分別是：

|年齡區間|百分比|
|:-|:-|
|61~70|44.30%|
|51~60|30.48%|
|71~80|12.72%|

### 你從問卷中想知道的是...？（歡迎協作）
- 里長
    - 會不會操作 google map 標定點位？
    - 會不會拍照上傳？
    - 會不會螢幕截圖？
    - 會不會使用單一陳情系統？
- 公務員
### 去識別化
- 釋出的資料是統計結果不是單一問卷內容，避免太針對個人。

問卷可以參考這個 Jobs to be done framework：

https://jobs-to-be-done.com/jobs-to-be-done-interviews-79623d99b3e5
https://www.askattest.com/blog/innovation/the-jobs-to-be-done-survey-template

問卷的執行：
是誰用什麼名義發？
---
tags: 法律查詢器
---
# 更新記錄 / 已知問題
## 更新記錄
- 2023-06
    - 匯入 [立法院法律系統](https://lis.ly.gov.tw/lglawc/lglawkm) 三讀資料和修法歷程
    - 從 [立法院議事暨公報資訊網](https://ppg.ly.gov.tw/ppg/) 抓出代碼列表
    - 法案對照表用顏色顯示差異部份
- 2023-06-18
    - 自動抓取議案的支援
        - Ex: [政治獻金法內政委員會審查版本](https://law-history.g0v.ronny.tw/law/0101218/bill-1061225070300500)
- 2023-06-19
    - 支援一個關係文書裡面包含多個法律版本，Ex: [外交部組織法](https://law-history.g0v.ronny.tw/law/0101013/bill-1000427070300200)
- 2023-06-25
    - 加上連回立法院法律系統
    - 多處理一些不同的法律案例

## TODO
- 修正部份法條未被顯示出來問題，像是刑法、民法親屬編（未被顯示是因為在法律系統內有錯字造成解析錯誤，需人工處理）  [46條未解析成功的法案](https://gist.github.com/ronnywang/9173fb7e6435a6cbd2bac8fba9f78326)
- 沒有三讀歷程的法律 https://law.moj.gov.tw/LawClass/LawHistory.aspx?pcode=A0030343
- 法案內容的搜尋
- 顯示未三讀通過的議案
- 針對單一法條搜尋議案
- title/description 加上描述和內容，以便分享時顯示更多資訊
- 加入行政命令（Ex: 施行細則...)
- 同一議案關係文書裡面包含多個法律版本 Ex: [18歲成年議案](https://ppg.ly.gov.tw/ppg/bills/1091013070100100/details)
- 採用 akoma ntoso 或是 docxml 等開放格式?
- 處理只有 PDF 的議案 Ex: [公務人員任用法審查報告](https://ppg.ly.gov.tw/ppg/bills/1111201070300200/details)
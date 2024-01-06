怎麼爬下政治獻金平台所有的資料
====

- 先到 https://ardata.cy.gov.tw/
- 使用 Developer Tools (Mac: command + option + i)
- 點選「選舉查詢」，看 Developer Tools 的 Network 分頁，找找看哪個可能是選舉列表
    - 通常看大小最大的，然後回傳結果又是 JSON 的內容
    - 找到 https://ardata.cy.gov.tw/api/v1/search/elections?page=1&pageSize=50&
    - 看到內容有 paging->recordCount = 269 ，表示資料只有 269 筆，那可以把 pageSize 改成 300 ，這樣就可以一頁抓到全部的內容了
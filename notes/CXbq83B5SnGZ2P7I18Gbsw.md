---
tags: 公有地大行動
---

# 國有非公用邊際土地


## 業務

國產署 > 認養促進環境保護業務 
- https://www.fnp.gov.tw/singlehtml/9a089b35781148a5bf7e3e1dd7fe186d?cntId=a7bf93623ada412e897f479ec127334e
- 有提供 3748 公頃，國有非公用邊際土地地號清冊
- 案例：
    - 20191217 環資新聞：國產署釋保育善意 護鳥團體認養452公頃鹽田、濕地
        - https://e-info.org.tw/node/222278
    - 20230118 財政部 FB 粉絲頁貼文
        - https://www.facebook.com/mof.gov.tw/posts/pfbid02NCUBRj46u7HWRuXLWPxsnNg3DdJ4j8RpKdYu1gSshBccsK2XCuUCoQpjUys2QH45l

## 工作事項

工作資料夾
- https://drive.google.com/drive/folders/1AQmtVh7A6NqdgQK8kCkW8duLXClDzmHK?usp=share_link

資料狀況
- 20221216 之前，國產署釋出 [國有非公用邊際土地地號清冊](https://docs.google.com/spreadsheets/d/1rVYgo8gmI2OdadTyNeh7OuH0rcBWS94Hk5WfmYbIgA4/edit)
    - 需要手動整理
    - 可能要運用 [地號API](https://twland.ronny.tw/) 才能取得輪廓
- 20221216 chewei 有提問，20221228 國產署回覆，並提供在網頁上
    - 提問與回覆頁面：https://data.gov.tw/suggests/136642
- 20221228 財政部於政府資料平台上釋出資料集 https://data.gov.tw/dataset/160359
    - [KML 格式，國有非公用邊際土地圖資.zip](https://www.fnp.gov.tw/singlehtml/9a089b35781148a5bf7e3e1dd7fe186d?cntId=a7bf93623ada412e897f479ec127334e)
    - 20221228 版本的 KML 資料課題：
        - 網址：https://data.gov.tw/dataset/160359
        - 國產署提供的是全國國有非公用邊際土地的「聯集輪廓」，所以只有一個 polygon
        - 並沒有提供單筆土地的欄位資料
    - 民間加工：
        - 用 QGIS 把非連續圖塊拆解成單筆資料
        - 注意! 每一個輪廓並非真的是單一地號! 因為可能兩個地號連接在一起已變成同一個輪廓
    - 線上地圖與 KML 檔案：
        - 20221228 國有非公用邊際土地-線上地圖 https://maps.app.goo.gl/285irmohWs3AyNkm8

<iframe src="https://www.google.com/maps/d/embed?mid=1lXsFymLQw6-j1dQIEaFKqEHff46ET_Q&hl=zh-TW&ehbc=2E312F" width=100% height="480"></iframe>


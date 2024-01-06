# Rentea db Spec

Data model: 

- ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_76a119891ea1c9a115aa4e64706fb508)

- Raw House
    - 從租屋網站取得的每一筆租屋資料
    - 裡面可能有多筆資料都指向同一個租屋位置
    - 例如 591 網站: 因為其推銷機制，爬蟲會取得多筆重複的租屋資料
- Unique House
    - 將 Raw House 的資料做整理，去除重複的租屋資料
    - 重複的定義方式: 兩筆租屋資料中每一個欄位都擁有相同的內容
    - 重複的實作方式: 在 SELECT query 的 WHERE 後面加入所有比較的欄位，看看是否能找出一筆資料，如果有就代表重複
- House Meta
    - 需求: 因為網站上的租屋資料可能和實際看屋情況不同，所以讓使用者能夠 feed back 描述實際的租屋、看屋情況
- Filtered House
    - 需求: 使用者透過分類功能，搜尋所有擁有相同分類的租屋資料
    - 實作: 可能在後端去除重複資料之後，將資料新增到 Unique House 時也要根據分類新增到 Filtered House。
- Search Filter
    - 需求: 列舉所有分類項目，Filtered House 中的分類項目來自於這個資料表
    - 疑問: 分類是由誰來新增? 或是我們自己決定有幾種分類項目?
- User
    - 需求: 讓使用者登入並且使用相關功能，例如提供租屋資訊回饋
    - 實作:
        - 使用電子郵件登入，需要電子郵件驗證
        - 使用社群網站登入
        - 帳號密碼登入
        - 忘記密碼
        
## API

### Internal API (For Crawler)

### Public API (For Client)



## Goal: 

1. 處裡 Raw House/Unique House 在 Insert/Update/Delete 之間的交互邏輯
2. 讓 crawler、api server(future work) 有共同的介面可以重用
    - crawler 用 rentea-db 塞資料、更新資料
    - api server 用 rentea-db 撈資料（？） 

ddio 表示在 https://github.com/g0v/tw-rental-house-data 處裡過在更新時，比對不同欄位、確定新增 unique house 的邏輯

rentea-db 這一邊就抄起來，再補齊刪除的部分

- 然後決定要用哪種 DB!
    - MySQL: 
        - 一開始線上聚會討論的結果，想要穩定的話是比較好的選擇
    - PostgreSQL 一票！
    - Elasticsearch: 
        - 雖然擁有儲存功能，但是本質上還是一個搜尋引擎，沒有保證 ACID 中的 Durability 所以會有掉資料的問題。有詢問過 ddio 並表示，雖然爬蟲每天都會撈租屋資料回來，但還是無法接受會遺失的情況，每次遺失都只能等到明天後再將資料補回，這樣可能太慢了。
    - 混用: 
        - 資料庫使用 MySQL，配合 Elasticsearch 輔助搜尋
    - 其他: 
        - 前端有一個需求是在地圖上畫圈，然後搜尋圈內所有租屋資料。所以希望資料庫支援多邊形(Polygon)搜尋

## High Level Tasks

- 先來搞懂目前的 tw-rental-house-data 架構
    - https://rentalhouse.g0v.ddio.io/about-data-set/0.2/#住宅與重複物件過濾條件
    - https://github.com/g0v/tw-rental-house-data/blob/af583ef91aab6927698d381b3bc0b36965cdfad2/backend/rental/libs/filters.py 判斷是否為同一筆 House Data 的 filter，因為 tw-rental-house-data 會每次全爬所有的資料
- 



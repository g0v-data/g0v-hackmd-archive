---
title: "縣市開放資料集索引"
tags: Open Data,hackpad
---

# 縣市開放資料集索引

> [點此觀看原始內容](https://g0v.hackpad.tw/XIDdqdefsJZ)


為了加速縣市政府開放資料的推動，平行單位釋出資料的比對是常見工作，但現在除了 OKFN 評比( [http://tw-city.census.okfn.org/](http://tw-city.census.okfn.org/) )之外並沒有其他相關索引； OKFN 評比是透過指定主題的方式，但實際執行時只希望找出一個簡單的答案，也就是 "xx縣市開放了這個資料集，oo縣市有沒有類似的？" ，因此希望開發一個程式去建立縣市資料集之間的連結（標籤）

管理介面： [https://github.com/tainancity/city_datasets](https://github.com/tainancity/city_datasets)
- 目前狀態的操作展示： [https://www.youtube.com/watch?v=QdKQ9t1IFfo](https://www.youtube.com/watch?v=QdKQ9t1IFfo)
- 已連結資料展示
    - 社會 \- [https://i.tainan.gov.tw/city_datasets/tags/view/57284832-4ab8-4b7b-af6d-2d8cacb5b862](https://i.tainan.gov.tw/city_datasets/tags/view/57284832-4ab8-4b7b-af6d-2d8cacb5b862)
    - 都市發展 \- [https://i.tainan.gov.tw/city_datasets/tags/view/572849a4-bd8c-46b6-8779-14a2acb5b862](https://i.tainan.gov.tw/city_datasets/tags/view/572849a4-bd8c-46b6-8779-14a2acb5b862)
    - 財政 \- [https://i.tainan.gov.tw/city_datasets/tags/view/5728486f-5a98-4dc1-9ce7-1be9acb5b862](https://i.tainan.gov.tw/city_datasets/tags/view/5728486f-5a98-4dc1-9ce7-1be9acb5b862)
    - 主計 \- [https://i.tainan.gov.tw/city_datasets/tags/view/57284706-6034-4500-9b54-2d97acb5b862](https://i.tainan.gov.tw/city_datasets/tags/view/57284706-6034-4500-9b54-2d97acb5b862)
    - 工務 \- [https://i.tainan.gov.tw/city_datasets/tags/view/57284882-2270-4ddf-83a2-2e21acb5b862](https://i.tainan.gov.tw/city_datasets/tags/view/57284882-2270-4ddf-83a2-2e21acb5b862)
爬蟲： [https://github.com/tainancity/city\_datasets\_crawlers](https://github.com/tainancity/city_datasets_crawlers)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_15fa564d2582af40c0f6c638af623bad)

### 資料庫規劃

- table organizations - 組織/單位
    - id 使用 uuid
    - foreign_id 在各縣市資料平台的 ID
    - foreign_url 在各縣市資料平台的網址
    - parent_id, lft, rght 樹狀結構索引欄位(MPTT)
- table datasets - 資料集/資源
    - id 使用 uuid
    - organization_id 組織 ID
    - foreign_id 在各縣市資料平台的 ID
    - foreign_url 在各縣市資料平台的網址
    - parent_id, lft, rght 樹狀結構索引欄位(MPTT)
- table tags - 標籤
    - id 使用 uuid
    - model 設定使用的資料表， Organization or Dataset
    - parent_id, lft, rght 樹狀結構索引欄位(MPTT)
- table links_tags - 標籤連結
    - foreign_id Organization/Dataset 的 id
    - model 設定使用的資料表， Organization or Dataset

### 功能需求

- 各縣市資料集的爬蟲
- 需要 API 介面接收由爬蟲取得的資料，避免直接資料庫存取
- 在檢視資料集時以資料集名稱建立標籤，接著進入檢視標籤的頁面可以看到剛建立的連結，進一步可以用關鍵字搜尋其他資料集建立更多連結
- 也許各種連結需要進一步的審核機制

### 爬蟲 Todos

- [x] [臺北市政府](http://data.taipei/)
> [https://github.com/tainancity/city\_datasets\_crawlers/blob/master/taipei.php](https://github.com/tainancity/city_datasets_crawlers/blob/master/taipei.php)
> [name=Finjon K]

- [ ] [新北市政府](http://data.ntpc.gov.tw/)
- [ ] [臺中市政府](http://data.taichung.gov.tw/GipOpenWeb/wSite/mp?mp=1)
- [ ] [宜蘭縣政府](http://opendata.e-land.gov.tw/)
- [ ] [高雄市政府](http://data.kaohsiung.gov.tw/Opendata/)
- [ ] [新竹縣政府](https://data.hsinchu.gov.tw/index.aspx)
- [x] [新竹市政府](http://opendata.hccg.gov.tw/)
> [https://github.com/tainancity/city\_datasets\_crawlers/blob/master/ckan.php](https://github.com/tainancity/city_datasets_crawlers/blob/master/ckan.php)
> [name=Finjon K]

- [x] [南投縣政府](http://data.nantou.gov.tw/)
> [https://github.com/tainancity/city\_datasets\_crawlers/blob/master/ckan.php](https://github.com/tainancity/city_datasets_crawlers/blob/master/ckan.php)
> [name=Finjon K]

- [x] [臺南市政府](http://data.tainan.gov.tw/)
> [https://github.com/tainancity/city\_datasets\_crawlers/blob/master/ckan.php](https://github.com/tainancity/city_datasets_crawlers/blob/master/ckan.php)
> [name=Finjon K]

- [ ] [臺東縣政府](http://www.taitung.gov.tw/opendata/Default.aspx?themesite=BAA86C8F16BADDE6)
- [ ] [金門縣政府](http://data.kinmen.gov.tw/)
- [x] [桃園市政府](http://data.tycg.gov.tw/)
> [https://github.com/tainancity/city\_datasets\_crawlers/blob/master/ckan.php](https://github.com/tainancity/city_datasets_crawlers/blob/master/ckan.php)
> [name=Finjon K]



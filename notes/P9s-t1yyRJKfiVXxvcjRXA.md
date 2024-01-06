---
title: "國會調查兵團開放API"
tags: hackpad
---

# 國會調查兵團開放API

> [點此觀看原始內容](https://g0v.hackpad.tw/bSmx3h922jc)


## 介紹


這邊是[國會調查兵團網站](https://cic.tw)的開放API，歡迎介接。
內容以CC-BY 4.0釋出。

國會調查兵團網站介紹：

[https://cic.tw/about](https://cic.tw/about)

網站code以MIT釋出。

[https://github.com/billy3321/cic-website](https://github.com/billy3321/cic-website)


## API內容


### 立委列表

[https://cic.tw/legislators.json](https://cic.tw/legislators.json)

#### GET參數

limit：限制筆數
offset：從第幾筆開始
query：查詢立委姓名
callback：JSONP用的callback參數

#### 回應

\-\-\-
-   status: "success"
-   legislators:
    - id: 立委id
    - name: 立委名字
    - image: 圖片
    - in_office:  是否在職
        - party:
        - id: 黨id
        - name: 黨名
        - image: 黨圖片
        - abbreviation: 黨縮寫
- count: 筆數



### 有記錄的立委

[https://cic.tw/legislators/has_records.json](https://cic.tw/legislators/has_records.json)

#### GET參數

limit：限制筆數
offset：從第幾筆開始
query：查詢立委姓名
callback：JSONP用的callback參數

#### 回應

\-\-\-
-   status: "success"
-   legislators:
    - id: 立委id
    - name: 立委名字
    - image: 圖片
    - in_office:  是否在職
        - party:
        - id: 黨id
        - name: 黨名
        - image: 黨圖片
        - abbreviation: 黨縮寫
- count: 筆數



### 無記錄的立委

[https://cic.tw/legislators/](https://cic.tw/legislators/no_record.json)[n](https://cic.tw/legislators/no_record.json)[o](https://cic.tw/legislators/no_record.json)[_record.json](https://cic.tw/legislators/no_record.json)

#### GET參數

limit：限制筆數
offset：從第幾筆開始
query：查詢立委姓名
callback：JSONP用的callback參數

#### 回應

\-\-\-
-   status: "success"
-   legislators:
    - id: 立委id
    - name: 立委名字
    - image: 圖片
    - in_office:  是否在職
        - party:
        - id: 黨id
        - name: 黨名
        - image: 黨圖片
        - abbreviation: 黨縮寫
- count: 筆數


### 單一立委

[https://cic.tw/legislators](https://cic.tw/legislators/:id.json)[/](https://cic.tw/legislators/:id.json)[:](https://cic.tw/legislators/:id.json)[i](https://cic.tw/legislators/:id.json)[d.json](https://cic.tw/legislators/:id.json)
ex:
[https://cic.tw/legislators/1738.json](https://cic.tw/legislators/1738.json)

立委使用g0v的資料，id相同。

#### GET參數

callback：JSONP用的callback參數

#### 回應

\-\-\-
-   status: "success"
-   legislator:
    - id: 立委id
    - name: 立委名字
    - image: 圖片
    - in_office:  是否在職
    - party:
        - id: 黨id
        - name: 黨名
        - image: 黨圖片
        - abbreviation: 黨縮寫
    - elections
        - legislator_id: 立委id
        - id: 選舉id
        - ad_id: 屆次id
        - party_id: 黨id
        - constituency: 參選區域
        - ad:
            - id: 屆次id
            - name: 屆次名
            - vote_date:投票日期
            - term_start: 任期開始
            - term_end: 任期結束
- interpellations: 質詢列表，內容請參見下面
- entries: 新聞列表，內容請參見下面
- videos: 影片列表，內容請參見下面


### 單一立委的新聞記錄

[https://cic.tw/legislators/](https://cic.tw/legislators/:id/entries.json)[:](https://cic.tw/legislators/:id/entries.json)[i](https://cic.tw/legislators/:id/entries.json)[d/entries](https://cic.tw/legislators/:id/entries.json)[.json](https://cic.tw/legislators/:id/entries.json)
ex:
[https://cic.tw/legislators/1738/entries.json](https://cic.tw/legislators/1738/entries.json)

#### GET參數

limit：限制筆數
offset：從第幾筆開始
query：查詢新聞標題、內容
callback：JSONP用的callback參數

#### 回應

-   status: "success"
-   entries:
    - id: 新聞id
    - title: 新聞標題
    - content: 新聞內容
    - source_url: 新聞來源網址
    - source_name: 新聞來源名稱
    - date: 新聞日期
    - created_at: 建立時間
    - updated_at: 更新時間
-   count: 新聞筆數


### 單一立委的影片記錄

[h](https://cic.tw/legislators/:id/videos.json)[ttps://cic.tw/legislators/](https://cic.tw/legislators/:id/videos.json)[:](https://cic.tw/legislators/:id/videos.json)[id](https://cic.tw/legislators/:id/videos.json)[/](https://cic.tw/legislators/:id/videos.json)[v](https://cic.tw/legislators/:id/videos.json)[ideos](https://cic.tw/legislators/:id/videos.json)[.json](https://cic.tw/legislators/:id/videos.json)
ex:
[https://cic.tw/legislators/1738/videos.json](https://cic.tw/legislators/1738/videos.json)

#### GET參數

limit：限制筆數
offset：從第幾筆開始
query：查詢影片標題、內容
callback：JSONP用的callback參數

#### 回應

\-\-\-
-   status: "success"
-   videos:
    - id: 影片id
    - title: 影片標題
    - content: 影片內容
    - video_type: 影片種類："ivod" or "news"
    - committee_id: 委員會id
    - ad\_session\_id: 會期id
    - meeting_description: 會議內容
    - youtube_url: youtube網址
    - youtube_id: youtube id
    - image: 影片縮圖
    - ivod_url: ivod網址
    - source_url: 來源網址
    - source_name: 來源名稱
    - time_start: 開始時間
    - time_end: 結束時間
    - date: 影片發生時間
    - created_at: 建立時間
    - updated_at: 更新時間
    - target: 質詢對象
    - ad_session:
        - id: 會期id
        - name: 會期名稱
        - ad_id: 屆次id
        - date_start: 會期開始時間
        - date_end: 會期結束時間
    - committee:
        - id: 委員會id
        - name: 委員會名稱
    - ad:
        - id: 屆次id
        - name: 屆次名
        - vote_date:投票日期
        - term_start: 任期開始
        - term_end: 任期結束
-   count: 影片筆數



### 單一立委的質詢記錄

[https://cic.tw/legislators/](https://cic.tw/legislators/:id/interpellations.json)[:](https://cic.tw/legislators/:id/interpellations.json)[id](https://cic.tw/legislators/:id/interpellations.json)[/](https://cic.tw/legislators/:id/interpellations.json)[interpellation](https://cic.tw/legislators/:id/interpellations.json)[s](https://cic.tw/legislators/:id/interpellations.json)[.json](https://cic.tw/legislators/:id/interpellations.json)
ex:
[https://cic.tw/legislators/1738/](https://cic.tw/legislators/1738/interpellations.json)[interpellation](https://cic.tw/legislators/1738/interpellations.json)[s.json](https://cic.tw/legislators/1738/interpellations.json)

#### GET參數

limit：限制筆數
offset：從第幾筆開始
query：查詢質詢標題、內容
callback：JSONP用的callback參數

#### 回應

\-\-\-
-   status: "success"
-   interpellations:
-     -
    - id: 質詢id
    - title: 質詢標題
    - content: 質詢內容
    - committee_id: 所屬委員會id
    - ad\_session\_id: 會期id
    - meeting_description: 會議內容
    - ivod_url: ivod網址
    - time_start: 開始時間
    - time_end: 結束時間
    - target: 質詢對象
    - date: 質詢發生時間
    - comment: 意見
    - created_at: 建立時間
    - updated_at: 更新時間
    - ad_session:
        - id: 會期id
        - name: 會期名
        - ad_id: 會期所屬屆次id
        - date_start: 會期開始
        - date_end: 會期結束
    - committee:
        - id: 委員會id
        - name: 委員會名字
    - ad:
        - id: 屆次id
        - name: 屆次名
        - vote_date:投票日期
        - term_start: 任期開始
        - term_end: 任期結束
-   count: 質詢筆數



### 所有的新聞記錄

[https://cic.tw/](https://cic.tw/entries.json)[e](https://cic.tw/entries.json)[ntries](https://cic.tw/entries.json)[.json](https://cic.tw/entries.json)

#### GET參數

limit：限制筆數
offset：從第幾筆開始
query：查詢新聞標題、內容
callback：JSONP用的callback參數

#### 回應

-   status: "success"
-   entries:
    - id: 新聞id
    - title: 新聞標題
    - content: 新聞內容
    - source_url: 新聞來源網址
    - source_name: 新聞來源名稱
    - date: 新聞日期
    - created_at: 建立時間
    - updated_at: 更新時間
    - legislators
        - id: 立委id
        - name: 立委名字
        - image: 圖片
        - in_office:  是否在職
            - party:
            - id: 黨id
            - name: 黨名
            - image: 黨圖片
            - abbreviation: 黨縮寫
-   count: 新聞筆數


### 單一新聞記錄

[https://cic.tw/entries/](https://cic.tw/entries/:id.json)[:](https://cic.tw/entries/:id.json)[id](https://cic.tw/entries/:id.json)[.json](https://cic.tw/entries/:id.json)
ex:
[https://cic.tw/entries/1.json](https://cic.tw/entries/1.json)

#### GET參數

callback：JSONP用的callback參數

#### 回應

-   status: "success"
-  entry:
    - id: 新聞id
    - title: 新聞標題
    - content: 新聞內容
    - source_url: 新聞來源網址
    - source_name: 新聞來源名稱
    - date: 新聞日期
    - created_at: 建立時間
    - updated_at: 更新時間
    - legislators
        - id: 立委id
        - name: 立委名字
        - image: 圖片
        - in_office:  是否在職
            - party:
            - id: 黨id
            - name: 黨名
            - image: 黨圖片
            - abbreviation: 黨縮寫


### 所有的質詢記錄

[https://cic.tw/](https://cic.tw/interpellations.json)[interpellation](https://cic.tw/interpellations.json)[s](https://cic.tw/interpellations.json)[.json](https://cic.tw/interpellations.json)

#### GET參數

limit：限制筆數
offset：從第幾筆開始
query：查詢質詢標題、內容
callback：JSONP用的callback參數

#### 回應

\-\-\-
-   status: "success"
-   interpellations:
-     -
    - id: 質詢id
    - title: 質詢標題
    - content: 質詢內容
    - committee_id: 所屬委員會id
    - ad\_session\_id: 會期id
    - meeting_description: 會議內容
    - ivod_url: ivod網址
    - time_start: 開始時間
    - time_end: 結束時間
    - target: 質詢對象
    - date: 質詢發生時間
    - comment: 意見
    - created_at: 建立時間
    - updated_at: 更新時間
    - ad_session:
        - id: 會期id
        - name: 會期名
        - ad_id: 會期所屬屆次id
        - date_start: 會期開始
        - date_end: 會期結束
    - committee:
        - id: 委員會id
        - name: 委員會名字
    - legislators
        - id: 立委id
        - name: 立委名字
        - image: 圖片
        - in_office:  是否在職
            - party:
            - id: 黨id
            - name: 黨名
            - image: 黨圖片
            - abbreviation: 黨縮寫
    - ad:
        - id: 屆次id
        - name: 屆次名
        - vote_date:投票日期
        - term_start: 任期開始
        - term_end: 任期結束
-   count: 質詢筆數

### 單一質詢記錄

[https://cic.tw/](https://cic.tw/interpellations/:id.json)[interpellation](https://cic.tw/interpellations/:id.json)[s/](https://cic.tw/interpellations/:id.json)[:](https://cic.tw/interpellations/:id.json)[id](https://cic.tw/interpellations/:id.json)[.json](https://cic.tw/interpellations/:id.json)
ex:
[https://cic.tw/](https://cic.tw/interpellations/1.json)[interpellation](https://cic.tw/interpellations/1.json)[s/1.json](https://cic.tw/interpellations/1.json)

#### GET參數

callback：JSONP用的callback參數

#### 回應

\-\-\-
-   status: "success"
-   interpellation:
-     -
    - id: 質詢id
    - title: 質詢標題
    - content: 質詢內容
    - committee_id: 所屬委員會id
    - ad\_session\_id: 會期id
    - meeting_description: 會議內容
    - ivod_url: ivod網址
    - time_start: 開始時間
    - time_end: 結束時間
    - target: 質詢對象
    - date: 質詢發生時間
    - comment: 意見
    - created_at: 建立時間
    - updated_at: 更新時間
    - ad_session:
        - id: 會期id
        - name: 會期名
        - ad_id: 會期所屬屆次id
        - date_start: 會期開始
        - date_end: 會期結束
    - committee:
        - id: 委員會id
        - name: 委員會名字
    - legislators
        - id: 立委id
        - name: 立委名字
        - image: 圖片
        - in_office:  是否在職
            - party:
            - id: 黨id
            - name: 黨名
            - image: 黨圖片
            - abbreviation: 黨縮寫
    - ad:
        - id: 屆次id
        - name: 屆次名
        - vote_date:投票日期
        - term_start: 任期開始
        - term_end: 任期結束

### 所有的影片記錄

[https://cic.tw/](https://cic.tw/videos.json)[v](https://cic.tw/videos.json)[ideos](https://cic.tw/videos.json)[.json](https://cic.tw/videos.json)

#### GET參數

limit：限制筆數
offset：從第幾筆開始
query：查詢影片標題、內容
callback：JSONP用的callback參數

#### 回應

\-\-\-
-   status: "success"
-   videos:
    - id: 影片id
    - title: 影片標題
    - content: 影片內容
    - video_type: 影片種類："ivod" or "news"
    - committee_id: 委員會id
    - ad\_session\_id: 會期id
    - meeting_description: 會議內容
    - youtube_url: youtube網址
    - youtube_id: youtube id
    - image: 影片縮圖
    - ivod_url: ivod網址
    - source_url: 來源網址
    - source_name: 來源名稱
    - time_start: 開始時間
    - time_end: 結束時間
    - date: 影片發生時間
    - created_at: 建立時間
    - updated_at: 更新時間
    - target: 質詢對象
    - ad_session:
        - id: 會期id
        - name: 會期名稱
        - ad_id: 屆次id
        - date_start: 會期開始時間
        - date_end: 會期結束時間
    - committee:
        - id: 委員會id
        - name: 委員會名稱
    - legislators
        - id: 立委id
        - name: 立委名字
        - image: 圖片
        - in_office:  是否在職
            - party:
            - id: 黨id
            - name: 黨名
            - image: 黨圖片
            - abbreviation: 黨縮寫
    - ad:
        - id: 屆次id
        - name: 屆次名
        - vote_date:投票日期
        - term_start: 任期開始
        - term_end: 任期結束
-   count: 影片筆數


### 單一影片記錄

[https://cic.tw/videos/](https://cic.tw/videos/:id.json)[:](https://cic.tw/videos/:id.json)[id](https://cic.tw/videos/:id.json)[.json](https://cic.tw/videos/:id.json)
ex:
[https://cic.tw/videos/](https://cic.tw/videos/1.json)[1](https://cic.tw/videos/1.json)[.json](https://cic.tw/videos/1.json)

#### GET參數

callback：JSONP用的callback參數

#### 回應

\-\-\-
-   status: "success"
-   video:
    - id: 影片id
    - title: 影片標題
    - content: 影片內容
    - video_type: 影片種類："ivod" or "news"
    - committee_id: 委員會id
    - ad\_session\_id: 會期id
    - meeting_description: 會議內容
    - youtube_url: youtube網址
    - youtube_id: youtube id
    - image: 影片縮圖
    - ivod_url: ivod網址
    - source_url: 來源網址
    - source_name: 來源名稱
    - time_start: 開始時間
    - time_end: 結束時間
    - date: 影片發生時間
    - created_at: 建立時間
    - updated_at: 更新時間
    - target: 質詢對象
    - ad_session:
        - id: 會期id
        - name: 會期名稱
        - ad_id: 屆次id
        - date_start: 會期開始時間
        - date_end: 會期結束時間
    - committee:
        - id: 委員會id
        - name: 委員會名稱
    - legislators
        - id: 立委id
        - name: 立委名字
        - image: 圖片
        - in_office:  是否在職
            - party:
            - id: 黨id
            - name: 黨名
            - image: 黨圖片
            - abbreviation: 黨縮寫legislators
        - id: 立委id
        - name: 立委名字
        - image: 圖片
        - in_office:  是否在職
            - party:
            - id: 黨id
            - name: 黨名
            - image: 黨圖片
            - abbreviation: 黨縮寫
    - ad:
        - id: 屆次id
        - name: 屆次名
        - vote_date:投票日期
        - term_start: 任期開始
        - term_end: 任期結束


### 整體公督盟記錄

[https://cic.tw/](https://cic.tw/ccws/:id.json)[c](https://cic.tw/ccws/:id.json)[cws](https://cic.tw/ccws/:id.json)[/:id.json](https://cic.tw/ccws/:id.json)
ex:
[https://cic.tw/videos/1.json](https://cic.tw/videos/1.json)

#### GET參數

callback：JSONP用的callback參數

#### 回應

\-\-\-

- status："success"
- ad_session 會期資料
    - id： 會期id
    - name：會期名稱
    - ad_id：會期所屬的屆次id
    - date_start：會期開始時間
    - date_end：會期結束時間
    - session：會期所屬的次數（第四會期）
    - regular：是否為正式會期
- ccw
    - citizen_score：公民評鑑分數
        - ad\_session\_id
        - id
        - total：該會期公民評鑑滿分
        - average：該會期公民評鑑平均得分
        - ccw_link：公民評鑑相關連結
    - committees 各委員會數據
        - ad\_session\_id
        - id
        - committee_id
        - should\_attend\_count：應出席數
        - actually\_average\_attend_count：平均出席數
        - avaliable\_interpellation\_count：可質詢數
        - actually\_average\_interpellation_count：質詢平均次數
        - committee：委員會資料
            - id
            - name：委員會名稱
            - kind：委員會種類，yc院會，sc普通委員會，ac特種委員會
    - legislators：立委個人數據
        - ys\_attend\_count：院會實際出席數
        - sc\_attend\_count：委員會實際出席數
        - sc\_interpellation\_count：委員會實際質詢數
        - first\_proposal\_count：主提案第一人案數
        - not\_first\_proposal_count：非主提案第一人案數
        - budgetary_count：預算案提案數
        - auditing_count：決算審查提案數
        - citizen_score：公民評鑑得分數
        - new\_sunshine\_bills：陽光公益法案-新立
        - modify\_sunshine\_bills：陽光公益法案-修正
        - budgetary\_deletion\_passed：預算刪減案-三讀通過
        - budgetary\_deletion\_impact：預算刪減案-重大公益
        - budgetary\_deletion\_special：預算刪減案-特殊事蹟
        - special：特殊事蹟
        - conflict_expose：利益衝突接露
        - allow_visitor：開放旁聽
        - human\_rights\_infringing_bill：侵害人權法案提案
        - human\_rights\_infringing_budgetary：侵害人權預算案
        - judicial_case：司法案件
        - disorder：脫序表現
        - legislator：立委資訊
            - id
            - name：立委姓名
            - description：描述
            - image：立委圖片
            - in_office：立委是否在職
            - fb_link：立委FB連結
            - wiki_link：立委wiki連結
            - musou_link：立委國會無雙連節
            - ccw_link：立委公督盟連結
            - ivod_link：立委ivod連結





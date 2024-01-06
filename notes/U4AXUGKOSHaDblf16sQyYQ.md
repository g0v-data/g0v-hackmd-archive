台灣賄選實價登錄群眾外包
===
###### tags: `台南小松`

台灣賄選實價登錄地圖是以司法院所開放的判決書資料為基礎，去整理可能跟賄選有關的判決，希望可以把各地的買票行情標記在地圖上，透過增加透明度希望降低賄選發生的機率。

司法院所公開的判決資料有 14,912,381 件，上次黑客松試著縮小範圍到 16,363 件，後來進一步把有關案件集合後有 7861 件（一到三審視為單一案件），只是這樣的資料量對於人工處理來說還是很大的負擔，因此希望透過群眾外包方式加速整理這些資料。

這些判決書還進一步透過中研院的語意分析引擎(CKIPTagger)找出跟金錢有關的字串，讓參與整理資料的朋友可以取得提示來提昇效率，但這些資料都還是以原始格式存在，需要一個前端介面讓大家可以更容易參與其中幫忙整理資料，希望選舉前就可以有初步的成果可以展示，就看有沒有朋友可以協助

API 目前沒有任何設限，會試著避免太多人處理同一個案件，歡迎跳坑 ;)

初步完成的群眾外包介面：
1. Howard: http://bribes.goodideas-campus.com/

---

1. 判決書資料在 https://github.com/kiang/bribes_data
2. case 目錄中的 json ，每個案件包含一或多個判決，代表該案的不同階段（一到三審）
3. history 裡面以該判決字號作為索引，裡面是逐行判決主文，每一個陣列的第一個元素是判決文字，第二個元素則是程式自動取出的關鍵字，目前只有放入程式判斷為金額的關鍵字，因為其他項目看起來效果不太好 ( 參考 https://github.com/ckiplab/ckiptagger/wiki/Entity-Types )
```
[
"投票權或為一定之行使者，處五年以下有期徒刑，得併科新台幣四十萬元",
"四十萬元"
],
```
4. 每次執行 http://bribes.olc.tw/issues/task 可以取得一個任務，任務資料結構如下
    1. Issue.id = 資料庫 id
    2. Issue.fid = 對應到 case 目錄中可以找到的判決字號
    3. Point[] = 已經在資料庫建立的點位
範例資料：
```
{
    "Issue": {
        "id": 1,
        "fid": "CCEM,91,潮簡,128,20020423,1"
    },
    "Point": [
        {
            "Issue_id": 1,
            "city": 64000,
            "town": 64000130,
            "cunli": 64000130006,
            "year": 105,
            "title": "議員",
            "candidate": "甲圈圈",
            "money": 1000,
            "modified": "2020-01-10 17:11:28"
        },
        {
            "Issue_id": 1,
            "city": 64000,
            "town": 64000130,
            "cunli": 64000130020,
            "year": 105,
            "title": "議員",
            "candidate": "乙圈圈",
            "money": 1000,
            "modified": "2020-01-10 17:11:28"
        }
    ]
}
```
5. 完成後透過 http://bribes.olc.tw/issues/save 送進結果，結構像這樣
```
[
    {
    Issue_id: 上述的 Issue.id
    city: 縣市代碼
    town: 鄉鎮市區代碼
    cunli: 村里代碼
    year: 發生年度，民國年
    title: 發生賄選的公職類型，例如議員、里長
    candidate: 發生賄選的候選人姓名
    money: 賄選金額，數字
    }
]
```
送出範例資料，以 POST 方式送出 JSON 字串
```
[
    {
        "Issue_id": "1",
        "city": "64000",
        "town": "64000130",
        "cunli": "64000130006",
        "year": "105",
        "title": "議員",
        "candidate": "甲圈圈",
        "money": "1000"
    },
    {
        "Issue_id": "1",
        "city": "64000",
        "town": "64000130",
        "cunli": "64000130020",
        "year": "105",
        "title": "議員",
        "candidate": "乙圈圈",
        "money": "1000"
    }
]
```
6. API 只會持續寫入不做更新，因此每次取得任務時送進的資料會建立一個版本保存
7. API 傳回的 Point 只有最新版本，因此基本上流程就是取得最新版本 -> 修改或新增 -> 送進資料庫儲存
8. 各種行政區代碼以 https://data.moi.gov.tw/MoiOD/Data/DataDetail.aspx?oid=A9A30724-C3EF-4553-AC3F-2D53A606DABC 為主
    1. 範例 json - https://gist.github.com/kiang/bb9c70ebe4a88992455d162ddbc5b1bd
    2. 三個層級的行政區，希望表單都用行政區的代碼送出
9. 每個判決可能涉及的對象會有多個，因此 Issue 跟 Point 之間是一對多的關聯
10. 如果有興趣加強後端 API 的可以參考 https://github.com/kiang/bribes_api
    1. 主要 API - https://github.com/kiang/bribes_api/blob/master/Controller/IssuesController.php
    2. 資料表結構 - https://github.com/kiang/bribes_api/blob/master/Config/schema/schema.sql
    3. 案件資料匯入 - https://github.com/kiang/bribes_api/blob/master/Config/sql/issues.sql
11. 並非所有案件都可以找到賄選資訊，如果確定找不到請在介面留一個按鈕，像是 "這個判決找不到賄選票價" ，在金額的部份填上 -1 後送出表單

相關專案：
1. [台灣賄選實價登錄地圖](https://g0v.hackmd.io/qbQKVKIeRcCTb3pr_r7y_Q)
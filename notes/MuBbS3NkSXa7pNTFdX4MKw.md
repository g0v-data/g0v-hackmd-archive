---
tags: 0archive, disinfo
---
# 0archive 公開資料集

## 說明 Intro
《0archive 零時檔案局》相關軟體，除非另外標示，以 MIT 2020 0archive project 授權釋出。
The software of 0archive are released under an MIT 2020 0archive project license unless otherwise noted.

《0archive 零時檔案局》公開資料集資料夾的短網址是 https://tinyurl.com/0archive-data 。
Short URL to the 0archive public datasets Google folder: https://tinyurl.com/0archive-data.

基於法律原因，公開資料集只提供部分內文（前280字）。
Due to legal reasons, content of publications (publication.text) in 0archive’s public datasets are truncated to the first 280 characters.

## 目錄 Table of Contents
- [資料標準 Data Standard](#資料標準)
- [資料集說明](#資料集說明)
- [讀取資料集 Code snippet](#讀取資料集-Code-snippet)
- [申請全文資料集 Full-text datasets application](#申請全文資料-Full-text-datasets-application)

## 資料標準 Data Standard
有關資料欄位請參考文件 [資料標準 Data Standard](https://g0v.hackmd.io/@chihao/0archive/%2F0Mt45bP_TQ2g0jRFP0tfTA)。

## 公開資料集說明 Public Datasets
:::info
👉 [公開資料集](https://drive.google.com/drive/folders/1ckDs03tdXhLdeF0N2St5OP0EeqxFC1bm)
:::

    ├── 公開資料集 Partial-text datasets
    │   ├── <producer> (e.g. "Ptt 政黑版 (www.ptt.cc) 5030a...")
    │      └── 2020-05.zip
    │          ├── 2020-05-01.jsonl
    │          └── 2020-05-02.jsonl
    │          └── ...
    │      └── 2020-05-tokenized.zip
    │          ├── 2020-05-01.jsonl
    │          └── 2020-05-02.jsonl
    │          └── ...


- `YYYY-MM.zip`
    - 其中一天為一個 [jsonl](http://jsonlines.org/examples/)，存有當天發表的文章。
    - jsonl 中每一個 json 為一篇文章。若發現多個json屬於同一篇文章 (i.e. 擁有同一個`id`)，則是該文章有更改過，以欄位`version` 來區分同一個文章不同版本。
- `YYYY-MM-tokenized.zip`
    - tokenized過的文章。同樣是一天一個jsonl
    - 每一個json只有以下欄位：
        - `id`: publication id
        - `producer_id`: producer id
        - `version`: 抓到這篇文章的時間
        - `title`: list of tokens
        - `text`: list of tokens
        - `comments`: list of comments，其中每一個comments的`text` 為list of tokens。
        
    ```json
    {
        'id': '27236399-8256-11ea-8627-f23c92e71bad',
        'producer_id': '5030a557-81fe-11ea-8627-f23c92e71bad',
        'version': 1586095706, 
        'title': ['討論', '中華民國', '和', '台灣', '都', '是', '國家'],
        'text': ['國家', '名稱', '本來', '就', '可以', '有', '多種', '比如', '日本國', '正式', '名稱', '可以', '叫', 'Nippon', '或是', 'Nihon', '英文', '及', '國際', '習慣', '稱呼', 'Japan', '與', '上面', '二個', '日文', '正式', '稱呼', '完全', '無關', '所以', '我國', '國名', '憲法', '只', '規定', '正式', '名稱', '為', '中華民國', '國際', '習慣', '稱呼', '我國', '為', '台灣', '中華民國', '和', '台灣', '都', '是', '這個', '國家', '的', '名稱', '自然', '都', '是', '國家', '就是', '與', '支那', '無關', '不要', '跟', '我', '講', '英文', '那個', '支那', '那個', '名字', '根本', '錯誤', '憲法', '中', '並', '沒有', '那個', '骯髒', '下賤', '的', '名字', '國際', '也', '沒有', '人會', '用', '那個', '噁心', '的', '名字', '稱呼', '台灣', '希望', '民進黨', '能', '早點', '把', '護照', '改掉', '別', '再', '用', '那個', '錯誤', '的', '名字', '了'], 
        'comments': [
            {
                'id': 0, 
                'reaction': '推', 
                'author': 'VWVIl1', 
                'text': ['柯文哲', '可以', '當', '台北', '國', '的', '總統'], 
                'published_at': '03/31 16:02', 'connect_from': '39.10.135.105'
            }, 
            {
                'id': 1, 
                'reaction': '噓', 
                'author': 'Mitzunari', 
                'text': ['都', '不是', '國家', '中華', '冥', '國是', '流亡政府'], 
                'published_at': '03/31 16:03', 
                'connect_from': '223.136.250.72'
            }
        ]
    }

    ```
    
## 讀取資料集 Code Snippets

### Read jsonlines
#### python
```python
# read as csv
import pandas as pd
pd.read_json("2020-04.jsonl", lines=True, encoding="utf-8")
```

#### R
https://stuff.mit.edu/afs/athena/software/r/current/lib/R/library/jsonlite/html/stream_in.html

#### JavaScript


### Read json
#### python
```python
# read as json
import json
json.load(open("2020-04.json", "r"))

# read as csv
import pandas as pd
pd.read_json("2020-04.json")
```

## 申請全文資料 Full-text Datasets Application
Due to legal reasons, full text datasets access is available through application. Please email intl@g0v.tw to apply.

Access to full-text datasets is granted per-“Site.” Please list the Sites you need in the application. A list of Sites currently tracked by 0archive can be found here: https://airtable.com/shrd0utGHlTWmQsYt
---
tags: 0archive
---
# 0archive 武漢肺炎相關內容分析

在武漢肺炎的文章中，針對特定主題（例如：口罩、藥局、藥師、WHO、...）內容網站有沒有特定的風向（例如：寫到藥局的時候一定是寫『藥局很累、藥師很煩、政府政策很糟』）、什麼風向，以及如何利用這些主題。

0archive 現在累積了很多資料，可以怎麼使用它們呢？

## 分身伐樹 - NEED DB
### publication
- publication_id
- title
> [name=chihao] 居然忘了 title XD
- play_count
- first_play_at
- last_play_at
- published_at

### play_record
- record_id
- publication_id
- play_at
- content (json)

## 分身伐樹

### API
#### GET https://api.0archive.tw/playground/random

response
```json
{
    "text": "美各地现解封示威 专家：太早解封会有反效果",
    "publication_id": "..."
}
```

先回傳 play_count 最少的
> [name=wenyi] 再加一個sort by last_play_at 最早的 (after play_count sort)
> 
不需要 auth
鎖 10/s

#### POST https://api.0achive.tw/playground/add_record
body
```json
{
    "publication_id": "...",
    "tokens": [
        {
            "text": "美",
            "pos": "名", // part of speech
            "sentiment": "中性"
        },
        ...
    ]
}
```

不需要 auth
前端 & 後端 verify: 不能有 empty field
鎖 10/s

### UI
https://0archive.tw/ai


input
美各地现解封示威 专家：太早解封会有反效果

output
| 美 | 各地 | 现 | 解封 | 示威 | 专家 | 太早 | 解封 | 会 | 有 | 反效果 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|名 | 名  |  時副 | 動 |動 |名|副|動|副|動|名|
| | | | | 負面 | | | 負面 | | | 負面 |

- 顯示一段文字（一篇文章的標題）
- 工人斷詞
- 工人 tag 詞性
- 工人判斷情感（正面、負面、中性）
- submit

mobile 介面！
[UI圖](https://drive.google.com/file/d/1rO7jUrbJXyzbZRU8OCGfi73EXZFOIwbk/view?usp=sharing)

## 分身伐樹 todo:
- [x] 倒2000筆publication資料到taichung-lo
- [x] 畫 UI
- [x] 建立API
    - [x] get
    - [x] post

## Data export
> [name=chihao] 0archive 團隊處理中，請耐心等候（？）

目前的公開資料集可以在這邊找到
https://docs.google.com/document/d/1Yy-TkMkUu967tcgbdLO0eX7wG2WeJYn_fhtrBv6x6kg/edit#

## 斷詞

- ckip
- jieba
- elasticsearch 內建
- elasticsearch plug-in
    > [name=chihao] 0archive 團隊處理中，歡迎自幹
- [教育部常用字詞](https://github.com/irvin/moe-common-phrases-of-zhtw/tree/master/2011-2015/csv)

## 標註詞性

- 萌典 API
    - 例如 - https://www.moedict.tw/raw/%E8%90%8C
- 其他中文詞性的資料來源？

## 找主題

- 自己搜尋名詞
    - 找職業或特定主題（e.g. 藥局、藥師、口罩、WHO...）
    - 幫助找主題
- 自動看 - topic modeling
    - ...

## 情感分析

- 自己看標題中的形容詞
- 先把標題放到人家做好的 model 跑跑看（可以先做看看model合不合用）
- chinese sentiment analysis 
    - https://github.com/Tony607/Chinese_sentiment_analysis
    - others...

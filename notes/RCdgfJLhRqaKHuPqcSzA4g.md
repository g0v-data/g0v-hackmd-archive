---
title: "太陽花紀實 - API Document"
tags: 太陽花學運,hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/668AHTZTehn)


#### 逐字稿資料

- [逐字稿工作區](https://sunflowerdocumentary.hackpad.com/)
- [街頭民主教室](https://docs.google.com/spreadsheet/lv?key=0AgrKKMBahhsEdC1PSU8xRFZ4cXZrNEN3R1d1d2xMSmc&f=true&noheader=true&gid=0)
- [文播組逐字稿](https://hackpad.com/410-FRzDUBto4Vj)


## Data Format

- 時間
- 地點
- 事件名稱
- ~簡介~
- ~講者~
- 影片位置 (youtube ID)
- 影片開始位置 (Time  format,)
- 相片位置  (多個相片位置之間用 空格 相隔)
> 開google docs 資料夾放照片檔
> [name=劉宇庭]

> 整個upload到server, 欄位內只放檔案名稱
> [name=劉宇庭]

- 逐字稿位置
- 類型 (tag list  ex. 街頭民主教室)

## Tag list

來源
- 國際媒體
- 國內電視媒體
- 國內平面媒體
- 國內網路媒體
- 公民媒體 (個人/直播組/ ...)

類型 (主題?)
- 街頭民主教室
- 草根論壇
- 人民憲政會議
- 民主加課
- 賤民解放區
- 大腸花論壇
- 割闌尾
- 包圍ＯＯＯ
-

評論 (談話/節目/ ...)
紀錄 (直播/錄影/SNG/ ...)
官方 (記者會/ ...)

定點
機動



## JSON Format


### 時間軸 Timeline


#### REQUEST


    [http://sunflower-documentary-api.herokuapp.com/api/1.0/timeline](http://sunflower-documentary-api.herokuapp.com/api/1.0/timeline)
- **data/gist.json ( 概要時間軸 )**
- **data/speech.json ( 演講時間軸 )**

#### RESPONSE

```
[
 {
        "event_id": 1,
        "focus": 1,
        "title": "兩岸經貿如何影響民主？",
        "date": {
             "full" : 2014-03-21T00:00:00+08:00,
             "yyyy" : 2014, "mm" : 3, "dd" : 21,
             "hh" : 0, "ii" :0, "ss" : 0 }
    },...
]

```
> focus 0 跟 1 有什˙麼差別阿??
> [name=Lee]

> 在時間軸上是否為粗體顯示 ( 表示較重要的事件 )
> [name=Phiricen A]

> 了解!
> [name=Lee]

> 還有我們好像沒有 category 的分類 ，只有 tag  XD，我這邊用 tag 篩?
> [name=Lee]

> 新增 full 時間欄位。
> [name=Lee]


### 事件 Event


#### REQUEST :


    [http://sunflower-documentary-api.herokuapp.com/api/1.0/events](http://sunflower-documentary-api.herokuapp.com/api/1.0/events)
- **data/events/###(event_id).json**

#### RESPONSE :

```
[
    {
        "event_id": 1,
        "title": "兩岸經貿如何影響民主？",
     "description_ch": "逐字在此",
     "description_en": "英文逐字在此",
        "site": "濟南路",
        "thumbnail": ["img/event/1.jpg"],
        "media": [
     "https://www.youtube.com/watch?v=UKbOavrerNQ&t=53m37s",
     "https://www.youtube.com/watch?v=UKbOavrerNQ&t=53m36s"
        ],
        "tag": [
            { "id": 1, name": "街頭民主教室" },
            { "id": 2, name": "太陽花" },...
        ],
     "hackpad_ch": "https://318.hackpad.com/--F0W0Fnhkakl",
        "hackpad_en": "",
        "date": {
             "full" : 2014-03-21T00:00:00+08:00,
             "yyyy" : 2014, "mm" : 3, "dd" : 21,
             "hh" : 0, "ii" :0, "ss" : 0 }
    }
]
```
> 新增英文逐字稿的欄位
> [name=Lee]

> 新增 full 時間欄位
> [name=Lee]


### 標籤 Tags


#### REQUEST :


    [http://sunflower-documentary-api.herokuapp.com/api/1.0/](http://sunflower-documentary-api.herokuapp.com/api/1.0/tags)[tags](http://sunflower-documentary-api.herokuapp.com/api/1.0/tags)
- **data/tags.json**

#### RESPONSE :


```
[
    { "id" : 1, "name" : "街頭民主教室" },...
]

```
### 組織列表 Groups


#### REQUEST :


    暫無資料
- **data/groups.json ( 組織列表 )**

#### RESPONSE :


```
[
    {
        "id" : 1 ,
        "name" : "組織 A" ,
        "logo" : "img/group/1.jpg" ,
        "intro" : "組織介紹 A"
    },...
]

```
### 無名英雄 Characters


#### REQUEST :


    暫無資料
- **data/characters.json ( 無名英雄組織列表 )**

#### RESPONSE :


```
[
    {
        "id" : 1,
        "name" : "陳OO",
        "group_id" : 1,
        "history" :
        [
            "經歷一",
            "經歷二",
            "經歷三"
        ],
        "link" :
        [
         { "title" : '連結1', "url" : 'http://g0v.tw'},
         { "title" : '連結2', "url" : 'http://g0v.tw'}
        ],
        "intro" : "人物簡介"
    },...
]


```
### 文宣列表 Literature


#### REQUEST :


    暫無資料
- **data/literature.json ( 文宣列表 )**

#### RESPONSE :


    暫無資料

####

## 討論資料結構

（[開個臨時的檔案庫](https://drive.google.com/folderview?id=0B6ASgY1GMSOhWmFBMDFuZWt1LUE&usp=sharing)）
現況：正在設計新的表格了～文播組～
> 表格接近完成，4/22會上線(開放第一周給大家開始接力)做逐字，本週內會完成相關連結建置～
> [name=淑華]

2014-04-05／只准「零時政府」用電　議場插電有分階級？（2014-04-05中天新聞／記者唐薏程、黃琡雯）
濟南路／2014-04-02_1950to／by 劉宇庭／.mp4




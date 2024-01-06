---
title: "開放都市-委員會會議記錄資料庫 資料結構"
tags: planning,hackpad,開放都市計畫
---

# 開放都市-委員會會議記錄資料庫 資料結構

> [點此觀看原始內容](https://g0v.hackpad.tw/CDUPc1zHil2)

專案母體：[委員會會議記錄資料庫](https://g0v.hackpad.tw/--BpW2Xt7s8AH)

## MySQL資料結構

note_table: //會議紀錄meta
    id: INT(10) (AI)
    origin: VARCHAR(100) (url) //原始文件
    admin: CHAR(4) //行政區+改制前後(O/N) e.g. TPEO(台北市), KHHN(高雄市改制後)
    session: INT(4) //第n次會議
    round: TINYINT(1)//紀錄是否續會 e.g. 1=首次召開, 2=續會, 3=續會第二次
    note_code: CHAR(9) (unique) //admin+session+round e.g TPEO06731
    title: VARCHAR(100) //會議記錄title
    date: DATE
    start_time: TIME
    end_time: TIME
    location: VARCHAR(100)
    chairman: VARCHAR(12)
    note_taker: VARCHAR(12)
    attend_committee: TEXT (json format)
    attend_unit: TEXT (json format)

case_table: //案件列表
    id: INT(10) (AI)
    note_code: CHAR(9) (non-unique index)
    type: TINYINT(1) (1=report/2=confirm/3=deliberate/4=discuss/5=extempore)
    case_title: TINYTEXT //案名
    case_code: VARCHAR(6) (non-unique index) //亂碼編號
    description: TEXT (json format)
    committee_speak: TEXT (json format)
    response: TEXT (json format)
    resolution: TEXT (json format)
    add_resolution: TEXT (json format)
    attached: TEXT (url)

petition_table: //陳情案列表
    id: INT(10) (AI)
    note_code: CHAR(9) (non-unique index)
    case_code: VARCHAR(12) (non-unique index)
    petition_case: TEXT
    petition_num: VARCHAR(10) //陳情案編號
    name: VARCHAR(100)
    location: VARCHAR(100)
    reason: TEXT (json format)
    suggest: TEXT (json format)
    response: TEXT (json format)
    adhoc: TEXT (json format)
    resolution: TEXT (json format)

## 資料結構討論

- 現在以 json 的方式將會議記錄結構化 (NoSQL?) [example](http://urbancode.tw/json_example.json)
- 如果要製作搜尋功能，是不是要改成SQL?
- 租用的主機是 php + MySQL 5.6
- MySQL 5.7 新增對於 json資料的支援 [http://voicefromoldsoul.blogspot.tw/2017/01/mysql-json.html](http://voicefromoldsoul.blogspot.tw/2017/01/mysql-json.html)
- ronny建議要有搜尋功能的話，就利用google drive存放資料
> 裝上google drive api的example，租用的主機不給跑@@ 回傳error500
> [name=Richard H]

- 貌似需要UUID跟時間戳記

## 跨會議記錄文件之間的資料關係

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_93e9af4b0cc189f6a8b637281377cbe1)
> 提問：是否會有案名變更的情況？例如案名文字修改
> [name=che l]

> 有時候會有，或是合併審理之類的，所以資料庫結構可能要對案件index
> [name=Richard H]



## 會議紀錄文件結構歸納

```txt
1.標題
  a.委員會名稱
  b.第xxx次委員會議紀錄
2.時間
3.地點
4.主席
5.紀錄者
6.簽到表
7.確認事項
8.報告事項(報告案)
9.審議事項(審議案)
  a.案名
  b.說明
  c.委員發言摘要
  d.發展局回應
  e.決議
  f.附件
  g.陳情意見表
    i.編號
    ii.陳情人姓名
    iii.陳情理由
    iv.建議辦法
    v.市府回應說明
    vi.委員會決議
10.研議事項(討論事項)
11.臨時動議案

```
## JSON 資料結構規劃

試作範例：[http://urbancode.tw/json_example.json](http://urbancode.tw/json_example.json)
```txt
[
  {
  "title": "臺北市都市計畫委員會第 670 次委員會議紀錄",
  "session": 670,
  "date": "2015/5/7",
  "start_time": "09:30",
  "end_time": "12:50",
  "location": "市政大樓 8 樓西南區本會委員會議室",
  "chairman": "林欽榮",
  "note_taker": "陳福隆",
  "attend_committee": [],         出席委員
  "attend_adviser": [],            出席顧問
  "attend_unit": [                出席單位
    {
      "unit":"",                    出席單位
      "attendee":[                  出席者姓名
        "","",""
      ]
    }
  ],
  "report_item": [],              報告事項
  "confirm_item": [],             確認事項
  "deliberate_item": [            審議事項
     {
      "case": "擬定臺北市中華路二段（愛國西路至汀州路）兩側商業區細部計畫案",      案名
      "description": [        說明
         "一、 計畫位置：本計畫範圍...",
         "二、 計畫緣起：「變更...",
         "本案係配合主要計畫擬定..."
         ],
      "committee_speak": [          委員發言摘要
        {
          "committee":"林崇傑",        發言委員
          "speak":["",""]             發言內容
        }
      ],
      "response": [],               發展局回應
      "resolution": [],             決議
      "add_resolution": [],         附帶決議
      "attached":[],                附件
      "petition":[                        陳情意見綜整表
       {
        "pet_case": "擬定臺北市中華路二段（愛國西路至汀州路）兩側商業區細部計畫案",                                        陳情案名
        "pet_num": "1",                                 陳情案編號
        "pet_name": "李",                             陳情人姓名
        "pet_location": [""],                         陳情位置
        "pet_reason": [                               陳情理由
        "大同國小孩子大量分佈在..."
        ],
        "pet_suggest": [                              (陳情)建議辦法
          "1、提供接駁車。",
          "2、請將都更說明會訊息..."
          ],
        "pet_response": [                               (對陳情案)市府回應說明
          "1\. 本計畫係規劃現...",
          "2\. 另有關都市更新"
          ],
        "pet_adhoc": [],                           專案小組審查意見
        "pet_resolution": [                           (對陳情案)委員會決議
          "1.依市府回應說明辦理。",
          "2.本案一、二樓..."
          ]
        }
      ]
    }
   ],
  "discuss_item": [],            研議事項
  "extempore_item": []           臨時動議
 }
]


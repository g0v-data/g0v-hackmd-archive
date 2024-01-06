---
title: "立院資料標準化"
tags: g0v ly,hackpad
---

# 立院資料標準化

> [點此觀看原始內容](https://g0v.hackpad.tw/vIjKnuA5jYA)


## 立委個人資訊

[JSON output](https://github.com/g0v/twly_crawler/blob/master/data(pretty_format)/merged.json)

| 欄位 | 欄位中文 | 資料格式 | 描述 | 範例 |
| --- | --- | --- | --- | --- |
| uid | 唯一識別id(from國會圖書館) | int |  | uid=22 |
| name | 姓名 | string |  | name="王金平" |
| former_name | 以前的名字 | string |  | former_name="" |
| each_term | 各屆期的詳細資訊 | list |  | 如下表 |
each_term：
| 欄位 | 欄位中文 | 資料格式 | 描述 | 範例 | 備註 |
| --- | --- | --- | --- | --- | --- |
| **ad** | 屆別 | int |  | "ad": 8, |  |
| **name** | 姓名 | string |  |  |  |
| **gender** | 性別 | string |  |  |  |
| **party** | 黨籍 | string |  |  | 可能要用 relation 才能定義「一段時間的黨籍」（因為可能中途變更 |
| **caucus** | 黨團 | string |  |  |  |
| **constituency** | 選區 |  |  |  | TPE,1 |
| **committees** | 委員會 |  |  | "committees": \[  
{  
"chair": false,  
"name": "教育及文化委員會",  
"session": "0801"  
},  
{  
"chair": false,  
"name": "教育及文化委員會",  
"session": "0802"  
},  
{  
"chair": true,  
"name": "教育及文化委員會",  
"session": "0803"  
},  
{  
"chair": true,  
"name": "紀律委員會",  
"session": "0803"  
},  
{  
"chair": false,  
"name": "教育及文化委員會",  
"session": "0804"  
}  
\], | maybe something like: committees: \[ {session: ..., name: ... , chair: true/false }, {name: ..., chair: }\]  
加入session判別會期如何？\[ {session: "1", name: ..., chair:true/false}, {....}\]  
已更改如左列 |
| **term_start** | 到職日期 | string | YYYY-MM-DD | 2012-02-01 |  |
| **term_end.date  
term_end.reason  
term_end.replacement** | 離職 |  |  | "term_end": {  
"date": "2012/11/28",  
"reason": "因案於101年11月28日經最高法院判決褫奪公權確定，並自判決確定之日起，註銷名籍。",  
"replacement": "顏寬恒"  
} |  |
| **in_office** | 在職 | boolean |  |  |  |
| **contacts.address  
contacts.fax  
contacts.phone** | 聯絡資訊 |  |  | "contacts": {  
"address": \[  
"國會研究室：10051臺北市中正區濟南路1段3-1號2102室",  
"豐原服務處：臺中市豐原區南村路20號",  
"東勢服務處：臺中市東勢區第五橫街32號"  
\],  
"fax": \[  
"國會研究室：02-2358-6730",  
"豐原服務處：04-2515-6798",  
"東勢服務處：04-2577-3167"  
\],  
"phone": \[  
"國會研究室：02-2358-6726",  
"豐原服務處：04-2515-9998",  
"東勢服務處：04-2577-3099"  
\]  
} |  |
| **education** | 學歷 |  |  | "education": \[  
"東海大學政治系學士",  
"東海大學政治學碩士"  
\], |  |
| **experience** | 經歷 |  |  | "experience": \[  
"鹿鳴國中教師",  
"伸港國中教師",  
"大慶商工教師",  
"大葉大學兼任講師",  
"彰化縣議會第13、14、15屆議員",  
"鹿港鎮第15、16屆鎮長",  
"鹿菁獅子會會長",  
"晴光文教基金會董事長",  
"救國團鹿港團委會會長",  
"彰化縣青工會總會長"  
\], |  |
| **image** | 立院大頭照連結 |  |  | [http://www.ly.gov.tw/upload/01\_introduce/0103\_leg/LGpicture/80007.jpg](picture_url": "http://www.ly.gov.tw/upload/01_introduce/0103_leg/LGpicture/80007.jpg) |  |
| **links.ly** | 立委的全球資訊網個人網頁 |  |  |  |  |
| **remark** | 備註 |  |  |  |  |
| social_media |  |  |  |  |  |

contacts的address的部份能否加入經緯度變成一個object?
如 contacts: {address: blahblah,    latlng: ?????,????  }}
這樣在跑[民代地圖](http://g0v.github.io/mapView/ly.html)時可以快很多倍(目前是每一筆都要去查詢一次latlng，所以比較慢) :)

好阿！請問有API可以傳入地址後回傳經緯度嗎？

之前查經緯度，是用這個服務查的 :)
$.getJson([http://query.yahooapis.com/v1/public/yql?q=select+%2A+from+geo.placefinder+where+text%3D%22](http://query.yahooapis.com/v1/public/yql?q=select+%2A+from+geo.placefinder+where+text%3D%22)[" \+ addr + "%22+and+locale%3D%22zh_TW%22&format=json"](https://g0v.hackpad.tw/eObSuFJgxM7#http://query.yahooapis.com/v1/public/yql?q=select+%2A+from+geo.placefinder+where+text%3D%22&quot;-+-addr-+-&quot;%22+and+locale%3D%22zh_TW%22&format=json&quot;)[http://query.yahooapis.com/v1/public/yql?q=select+%2A+from+geo.placefinder+where+text%3D%22](http://query.yahooapis.com/v1/public/yql?q=select+%2A+from+geo.placefinder+where+text%3D%22)[" \+ addr + "%22+and+locale%3D%22zh_TW%22&format=json"](https://g0v.hackpad.tw/TG7UXHCZgGd#http://query.yahooapis.com/v1/public/yql?q=select+%2A+from+geo.placefinder+where+text%3D%22&quot;-+-addr-+-&quot;%22+and+locale%3D%22zh_TW%22&format=json&quot;) , function(){} );



reference:
    - [https://github.com/g0v/twlyparser/blob/master/data/mly-8.json](https://github.com/g0v/twlyparser/blob/master/data/mly-8.json)
    - [https://github.com/ronnywang/TWLegislativeYuanData/blob/master/8.json](https://github.com/ronnywang/TWLegislativeYuanData/blob/master/8.json)
    - [https://github.com/thewayiam/twly_crawler/blob/master/](https://github.com/thewayiam/twly_crawler/blob/master/merged(pretty_format).json)[merged](https://github.com/thewayiam/twly_crawler/blob/master/merged(pretty_format).json)[(pretty_format).json](https://github.com/thewayiam/twly_crawler/blob/master/merged(pretty_format).json)

## 立院表決

## 議案

## 法條修正草案

## 委員會的附帶決議、臨時提案




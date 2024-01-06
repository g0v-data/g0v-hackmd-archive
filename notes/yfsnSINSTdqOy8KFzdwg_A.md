---
title: MOG (Mapping Open-whatever-data to Gov-data)
---


| Data set name | Gov data | Overpass query |
| ------------- | -------- | -------- |
| 公共場所 AED 資料集 | https://tw-aed.mohw.gov.tw/SearchPlace.jsp https://github.com/pm5/taiwan-aed | https://overpass.nchc.org.tw/api/interpreter?data=%2F*%0AThis%20has%20been%20generated%20by%20the%20overpass-turbo%20wizard.%0AThe%20original%20search%20was%3A%0A“emergency%3Ddefibrillator%20in%20TW”%0A*%2F%0A%5Bout%3Ajson%5D%5Btimeout%3A25%5D%3B%0A%2F%2F%20fetch%20area%20“TW”%20to%20search%20in%0Aarea%283600449220%29-%3E.searchArea%3B%0A%2F%2F%20gather%20results%0A%28%0A%20%20%2F%2F%20query%20part%20for%3A%20“emergency%3Ddefibrillator”%0A%20%20node%5B%22emergency%22%3D%22defibrillator%22%5D%28area.searchArea%29%3B%0A%20%20way%5B%22emergency%22%3D%22defibrillator%22%5D%28area.searchArea%29%3B%0A%20%20relation%5B%22emergency%22%3D%22defibrillator%22%5D%28area.searchArea%29%3B%0A%29%3B%0A%2F%2F%20print%20results%0Aout%20body%3B%0A%3E%3B%0Aout%20skel%20qt%3B |

## 問題

1. OSM 資料集的 URI。這需要一個轉址服務。（由 OSM 資料集的 URI 轉到 overpass api url）
2. 多對一的 mapping 本身需要一個 URI。
3. Gov data set 有 CSV、JSON、XML 等格式。

## 假目標

1. 可以很容易做出 OSM data set 疊加 gov data set 的視覺化呈現。

## API response

```json
{
    "id": "12345",
    "title": "公共場所 AED 資料集",
    "description": "公共場所 AED 資料集",
    "gov": [
        {
            "maintainer": "mohw",
            "url": "https://tw-aed.mohw.gov.tw"
        },
        {
            "maintainer": "pm5",
            "url": "https://github.com/pm5/taiwan-aed/tree/data"
        }
    ],
    "open": [
        {
            "service": "osm overpass turbo",
            "query": "[out:json];{{geocodeArea:TW}}->.searchArea;(node[\"emergency\"=\"defibrillator\"](area.searchArea);way[\"emergency\"=\"defibrillator\"](area.searchArea);relation[\"emergency\"=\"defibrillator\"](area.searchArea););out body;>;out skel qt;",
            "url": "https://overpass.nchc.org.tw/api/interpreter?data=%2F*%0AThis%20has%20been%20generated%20by%20the%20overpass-turbo%20wizard.%0AThe%20original%20search%20was%3A%0A%E2%80%9Cemergency%3Ddefibrillator%20in%20TW%E2%80%9D%0A*%2F%0A%5Bout%3Ajson%5D%5Btimeout%3A25%5D%3B%0A%2F%2F%20fetch%20area%20%E2%80%9CTW%E2%80%9D%20to%20search%20in%0Aarea%283600449220%29-%3E.searchArea%3B%0A%2F%2F%20gather%20results%0A%28%0A%20%20%2F%2F%20query%20part%20for%3A%20%E2%80%9Cemergency%3Ddefibrillator%E2%80%9D%0A%20%20node%5B%22emergency%22%3D%22defibrillator%22%5D%28area.searchArea%29%3B%0A%20%20way%5B%22emergency%22%3D%22defibrillator%22%5D%28area.searchArea%29%3B%0A%20%20relation%5B%22emergency%22%3D%22defibrillator%22%5D%28area.searchArea%29%3B%0A%29%3B%0A%2F%2F%20print%20results%0Aout%20body%3B%0A%3E%3B%0Aout%20skel%20qt%3B"
        }
    ]
}
```
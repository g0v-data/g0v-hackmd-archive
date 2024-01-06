---
title: "台灣市場分析儀表板說明"
tags: hackpad
---

# 台灣市場分析儀表板說明

> [點此觀看原始內容](https://g0v.hackpad.tw/sclXnjvQw7f)


台灣市場分析儀表板是 Ronny Wang 在 2018/5/5 第參拾次零時政府佛系黑客松所做界面，主要是想要當作一個起點，能夠看到起點，能夠看到各產業在各縣市的分布和成長情況，以便觀察到各產業的情況。

網址：[https://ronnywang.github.io/taiwan-company-table/index.html](https://ronnywang.github.io/taiwan-company-table/index.html)

## 說明

- 資料來源
    - [https://data.gov.tw/dataset/9400](https://data.gov.tw/dataset/9400) 財政部財政資訊中心 全國營業(稅籍)登記資料集
        - 裡面包含目前營業中各公司或商號的統一編號、事業名稱、營利事業別、設立日期；資本額等資訊，共約 140 萬左右事業單位
        - 其中營利事業別部份是依照報稅的事業項目，因此會比經濟部商業司的登記項目更準確，但是缺點是最多只會有三項，而且無法知道三項的比例
        - 結束營業的事業就會被排除不顯示，因此若要做跨時間比較時（例如近一年與近三年筆）無法包含到已經結束營業的事業單位。
        - 營利事業別代碼好像包含6, 7, 8 的代碼(未確定)
        - 登記資本額不等於公司收益或是規模
    - [https://data.gov.tw/dataset/28483](https://data.gov.tw/dataset/28483) 財政部統計處 稅務行業標準分類

## 閒聊區

> 如果對於這儀表板有什麼看法或心得的，歡迎在這邊閒聊喔～
> [name=Ronny W]

> 希望有固定網址 XD -> [ronnywang/taiwan company table#1](https://github.com/ronnywang/taiwan-company-table/issues/1)
> [name=kiang]

> 似乎會延伸分析就業勞動與縣市的產業特性，或許會與「工廠廠房」有關聯
> [name=che l]



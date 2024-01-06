---
title: "巴拿馬文件 - Panama Papers"
tags: hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/CWkeuAXb1Tb)


相關專案：
- [Panama Papers Taiwan Index](http://kiang.github.io/Panama_Papers_Taiwan/)\- [https://github.com/kiang/Panama\_Papers\_Taiwan/](https://github.com/kiang/Panama_Papers_Taiwan/)
- [地圖版](http://billcccheng.github.io/pages/subpages/panama_taiwan.html)\- [https://github.com/billcccheng/Panama-Taiwan-Visualization](https://github.com/billcccheng/Panama-Taiwan-Visualization)
- 姓名比對 \- [https://www.ptt.cc/bbs/Gossiping/M.1463023778.A.5E8.html](https://www.ptt.cc/bbs/Gossiping/M.1463023778.A.5E8.html)
- 住址英翻中 \- [https://gist.github.com/ronnywang/2ae9ee7b43d3b662a0f9257f513ba797](https://gist.github.com/ronnywang/2ae9ee7b43d3b662a0f9257f513ba797)
- 2016 候選人姓名中翻英 - [https://github.com/kiang/Panama\_Papers\_Taiwan/blob/master/2016.json](https://github.com/kiang/Panama_Papers_Taiwan/blob/master/2016.json)
- 2014 候選人姓名中翻英 - [https://github.com/kiang/Panama\_Papers\_Taiwan/blob/master/2014.json](https://github.com/kiang/Panama_Papers_Taiwan/blob/master/2014.json)
- 2012 候選人姓名中翻英 - [https://github.com/kiang/Panama\_Papers\_Taiwan/blob/master/2012.json](https://github.com/kiang/Panama_Papers_Taiwan/blob/master/2012.json)
- 2012, 2014, 2016 候選人配對結果 - [https://github.com/kiang/Panama\_Papers\_Taiwan/blob/master/match.csv](https://github.com/kiang/Panama_Papers_Taiwan/blob/master/match.csv)

在 [https://offshoreleaks.icij.org/pages/database](https://offshoreleaks.icij.org/pages/database) 可以下載原始資料，解壓縮後會得到下面幾個檔案
- Addresses.csv - 股東登記住址
    - address
    - icij_id
    - valid_until
    - country_codes
    - countries
    - node_id
    - sourceID
- Entities.csv - 註冊公司
    - name
    - original_name
    - former_name
    - jurisdiction
    - jurisdiction_description
    - company_type
    - address
    - internal_id
    - incorporation_date
    - inactivation_date
    - struck\_off\_date
    - dorm_date
    - status
    - service_provider
    - ibcRUC
    - country_codes
    - countries
    - note
    - valid_until
    - node_id
    - sourceID
- Intermediaries.csv - 仲介
    - name
    - internal_id
    - address
    - valid_until
    - country_codes
    - countries
    - status
    - node_id
    - sourceID
- Officers.csv - 股東
    - name
    - icij_id
    - valid_until
    - country_codes
    - countries
    - node_id
    - sourceID
- all_edges.csv - 關聯
    - node_1
    - rel_type
    - node_2
    - rel_type 有下面幾種
        - intermediary_of
        - officer_of
        - registered_address
            - 一般來說是 Officer, registered\_address, Address ，但有部份是 Entity, registered\_address, Entity ，也就是某個境外公司的登記住址連結到另外一個境外公司
        - similar
        - underlying

sourceID = Panama Papers 就表示是新上線的巴拿馬文件資料
country_codes = TWN 就表示是台灣的資料，香港是 HKG 、中國是 CHN


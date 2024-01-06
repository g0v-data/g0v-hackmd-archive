---
tags: COVID-19, open data
---

# 疫苗接種統計資料詢問

## Ｑ：各縣市施打 COVID-19 疫苗統計資料集
- 資料釋出網頁 https://covid-19.nchc.org.tw/dt_002-csse_covid_19_daily_reports_vaccine_city2.php
    - 欄位：日期、縣市別、總人口數、前次累計接種人數更新、新增接種人數、累計接種人數、累計接種率(%)、累計配送劑數
- 授權
> 格式還 ok ，但是這個網頁的 Terms of Use 有問題，有發信詢問他們表示會考慮改為 cc-by ，只是不確定進度 [name=kiang]
> 6/18 查看後發現，採用 CC BY 4.0 釋出！
> https://covid-19.nchc.org.tw/terms.php
> Terms of Use
> This data sets are licensed under the Creative Commons Attribution 4.0 International (CC BY 4.0) by the Johns Hopkins University on behalf of its Center for Systems Science in Engineering and CDC Taiwan.

- todo：
    - 寫「我想要更多」：https://data.gov.tw/suggests/136414
        - 確認目前的資料釋出方式，算是有 API 嗎？
        - 寫「我想要更多」，聚焦在授權確認，以及是否還有其他事項

## Ｑ：各類 COVID-19 疫苗接種對象累計接種人次資料
- PDF https://www.cdc.gov.tw/Category/Page/9jFXNbCe-sFK9EImRRi2Og
    - 欄位：縣市別(?)、對象別、AstraZeneca第一劑、AstraZeneca第二劑、Moderna第一劑、Moderna第二劑
- 民間開發者對於此 PDF 資料的意見
    - https://twitter.com/gugod/status/1403268461598437382
> 希望系統直接輸出 csv 格式，然後不要任意異動欄位，定期更新，目前最大問題就是放假期間檔案不會更新 [name=kiang]
> 希望至少除了 pdf 的同時，也同步提供 csv 檔案格式
> 希望能提供 API，看能否放到 opendata 平台上

- todo：
    - 寫「我想要更多」：https://data.gov.tw/suggests/136413
        - 程度一：同步釋出 csv 於網頁
        - 程度二：若能夠釋出 api，建議透過 opendata 平台釋出本資料集

其他：
- 縣市接種措施內容彙整
    - 民間彙整，全台 COVID-19 疫苗接種資訊 https://g0v.hackmd.io/@tmonk/Hy7q7SMsO/
    - 民間彙整，COVID-19 台灣疫苗施打站清單 http://bit.ly/TaiwanVaccineSites
        - 疫苗施打地點，包含醫院診所大型施打站等等


## 預計從這裡詢問資料開放：
- https://data.gov.tw/suggests
- https://dataopener.tw/requisition
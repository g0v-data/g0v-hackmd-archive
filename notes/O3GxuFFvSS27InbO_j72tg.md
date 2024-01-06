---
title: vaxx.tw 2.0 2021/07/02 小聚
tags: vaccine, COVID-19
description: vaxx.tw 2.0 2021/07/02 小聚
---

# vaxx.tw 2.0 2021/07/02 小聚

[上次共筆](https://g0v.hackmd.io/Hio1gaGBTuymJH18_73BVg?both)

:::info
議程：
- 討論 use cases
- 釐清資料整理流程
- 討論尚未得手的資料要如何入手
- 確認scope（哪個地區の哪種接種點の哪些資訊）
- 分工方式
:::

## USE CASES

簡單的 wire frame ([連結](https://docs.google.com/presentation/d/1SbpBH_EDQFcoaHnP1-XvCERq4tvfUxpMzt4OFmu_0Lo/edit?usp=sharing) )



## 資料整理流程

* [流程的overview ](https://docs.google.com/presentation/d/1nFB5tjLWO61Uc-xEiwNQo7lih4EAJHCHQ6izN_IN3hk/edit#slide=id.p)
* [詳細的欄位設計](https://airtable.com/tblJCPWEMpMg86dI8/viwkkEKIYKsVkxKgO?blocks=hide) 

會議中想釐清：
* 確認資料欄位和 table 的設計是方便工程師協作的
    → 已經更新到airtable
* 時段這個資料格式要怎麼填比較好
    → 跟施打點的table分開，另開table
* 施打對象資格要不要直接接 READr
    → 因為是瞄準之後全民開打時推出2.0，所以先把施打對象資格的判斷列為 nice to have

## 資料入手方式

- 各縣市施打點清單
    - [CDC那邊的資料](https://antiflu.cdc.gov.tw/Covid19)看起來不齊全
    - 各縣市的衛生局資料會比較齊全


- 施打點的預約方式＆預約狀況
    - 預約方式可能要靠人工判斷
    - 預約狀況以蒐集可以爬蟲的地點為主（網站、Google 表單等）



## 1.0的沿用性
網域可以用啦
前端code可以沿著用
爬蟲程式要重寫（因為想要的資料不一樣了）


## SCOPE


- 以有能量大量施打的院所為主
- 名額先以“有”跟“沒有”為主
    - 因為各間醫院更新頻率不一樣
    - 資料和 vaxx.tw 一代一致



1. 需要哪些人工整理可以幫助爬蟲？
2. 
3. 哪些 table 是給人看的還是給機器看的
4. 想問 Teemo 若是未來政府或醫院開放資料，我們需要哪些 primary key / 資料欄位需要做未來的介接




## 分工


- **初步整理清單｜yoyow,SL**
    - 判斷現有清單上，每個地方的實際預約網址是什麼
    - 判斷有沒有屬於某個醫院體系共用的系統（例：衛福部醫院用的預約系統是一樣的，就算是不一樣的醫院，也可以用同一套爬蟲程式處理」）

- **將airtable接上vaxxtw｜Kevin, SeanGau**

- **清單更新（自動的部分）｜SeanGau**

- **解開reurl&bitly｜seangau**

- **開始爬蟲｜ronny**
    - 看能不能整理出不同施打點的預約狀況
    - 將爬蟲結果新增在airtable裡

- **網站UI設計｜SL,豆腐**
    - 根據1.0去衍生新的排版
    
- **問施打站代碼可以哪裡取得｜ael**



## 其他討論

- 目前爬蟲先不切開，全部放備註
- 因為沒有辦法確保所有的資訊都是最新的，所以要顯示最後更新時間

- @Cai 之前整理的各縣市長者施打資格與流程
檢視版：https://bit.ly/AZ-how  今天的還沒更新
討論串：https://g0v-tw.slack.com/archives/C020EQ0R8TW/p1623477422069500
    - 建議大概是一開始設計的時候欄位靈活度要高，不然就像我一樣卡住了www
    - 各縣市的敘述沒有相同標準
    - 開打前或者預約前一天的資料才是最準的，前面只是參考。粉絲頁會寫的比較白話
    - 當批開打後還是要稍微巡有沒有臨時修年齡，之前打氣不夠就有縣市下修。
    - 離島資料很難找

## 施打點診所資訊連結彙整
- [台北市地區醫院（0701更新）](https://www-ws.gov.taipei/Download.ashx?u=LzAwMS9VcGxvYWQvNjg0L3JlbGZpbGUvMTAxNzMvODQwNTc3Mi9lOTc0MDE5ZC1hNTdhLTRkNjAtODVjYS0xOTc0MWRmZTQ5ZjcucGRm&n=MzTlrrblnLDljYDphqvpmaIwNjI5LTEucGRm&icon=..pdf&ccms_cs=1)
- [台北市社區診所（0701更新）](https://www-ws.gov.taipei/Download.ashx?u=LzAwMS9VcGxvYWQvNjg0L3JlbGZpbGUvMTAxNzMvODQwNTc3Mi9lZjJiYmNkNi04Njg2LTRmZTctYmMwMC0wNTlkNzcxOGE2MWEucGRm&n=MjA45a6256S%2b5Y2A6Ki65omAMDYyOS5wZGY%3d&icon=..pdf&ccms_cs=1)
- [桃園市醫療診所（即時更新）](https://covid-19.tycg.gov.tw/home.jsp?id=82&parentpath=0,54&websiteid=202105260001)
- [新竹縣醫療院所（0622更新）](https://ws.hcshb.gov.tw/Download.ashx?u=LzAwMS9VcGxvYWQvNDAyL3JlbGZpbGUvOTA2OS84NTM2Ni82NTk4ODdkMC0yZjE1LTQ4YjItYjAxMi0zZmRlMTZlOGQ3MDMucGRm&n=6ZmE5Lu2MTctQ09WSUQtMTnmjqXnqK7pmaLmiYDmuIXllq4xMTAwNjIy5b2Z5pW0LnBkZg%3d%3d)
---
title: Rentea 第 1 次小聚
tags: Rentea
---
# Rentea 第 1 次小聚

Rentea 的第 1 次小聚來啦～延續[上次小聚挖出的坑](https://beta.hackfoldr.org/rentea/https%253A%252F%252Fg0v.hackmd.io%252F-yz5uLxAQHGX_3bkz6ngHA)，這次依然以專案開發為主題，可以來找人討論，或是繼續填坑，無論你是設計師、工程師，或是對專案有興趣，都歡迎來參加！

- 時間：2019-09-24（二） 19:00 - 21:00
- 地點：[NPO Hub](https://g0v.hackmd.io/BNHyH7ESSxSlu12BV2U9TQ)，[台北市中正區重慶南路三段 2 號](https://goo.gl/maps/LAXhWdwUAXV3aUHv6) 四樓會議室（捷運中正紀念堂步行 7 分鐘）
  - 場地備有飲水機，請自備杯子水壺喔～
- 專案資訊：
   - [Hackfoldr](https://beta.hackfoldr.org/rentea) / [Slack](https://g0v-tw.slack.com/messages/CJTBP7YRK/details/)
   - [Figma Wireframe](https://www.figma.com/file/Z0Wsc63DYpXLouSC7vvpw5aR/rental?node-id=0%3A1)
   - [程式開發指南](https://g0v.hackmd.io/jg_TRTEbRxyV-osQptSqwQ) / [爬蟲設計](https://g0v.hackmd.io/Bv_1JeHoT1O8gIjFBEJROg?view#%E8%A8%8E%E8%AB%96%E7%B4%80%E9%8C%84%E3%80%81%E7%B5%90%E8%AB%96%E3%80%81%E5%BE%85%E4%BD%9C) / [資料庫設計](https://g0v.hackmd.io/BFd56MJAQqu242x_oqYP2w)

## 參加者打卡區

想要參加的人請先在這裡打卡，方便確定人數，也記得寫一下想來作什麼，可以是開發東西、學程式、幫忙紀錄，或是任何想做的事情都可以～

- ddio - Rentea 專業打雜 - 想做完爬蟲的更新流程 + 想收集有趣的小聚地點！
- yukai - 持續進行一個跳坑的動作 :joy: 
- Aaron : 爬爬蟲～～
- york - 入坑推坑
- Steven - ++1
- Darren - 不確定能不能去，能去就當個 NPC
- Ronny - 負責開門 XD
- chriske - 補進度
- yellowsoar - NPC一枚
- 星翰 - 新手 打雜(現場小記?)
- alextan - 遠端潛水人員(?)
- Chloe - 廢廢的拖延者尋找一個做設計的時間
- brody 跟公司打架中，一個lazy
- roro - 初入坑 ^^



## 任務認領

1. [x] 現場小記 - [name=Aaron]
2. [ ] Rentea Monthly 2019-09 （[範例](https://g0v.hackmd.io/KM6GyMh8SgCdUTjoFxWFXw)）
3. [x] 每月固定小聚時間調查 - [name=ddio]
4. [x] 想要討論開發類小聚流程 - [name=ddio]
   - [暫定] 現場小記認領，新手教學，自介，開坑，各自跳坑，各坑成果分享，後續待作認領

:::info
<i class="fa fa-home fa-lg fa-fw"></i> [回到 Hackfoldr](https://beta.hackfoldr.org/rentea/https%253A%252F%252Fhackmd.io%252Fs%252FSJbOIFHpE)
:::

## 現場小記
1. 大家自我介紹
2. 今天有 UI 、資料庫、爬蟲三組工作進行中
3. 決定後端要以 PostgreSQL / postgis + Django ，方便 GIS 操作
4. UI - 以塗鴉來畫自己所需之範圍,定義選取和圈選概念。目前定義四個圈選選項的初始頁面，使用者切換筆刷用與圈選功能需要再討論。
5. DB - 測試料庫和 Api 之環境,暫定不用 container, python以3.7 版本
6. 爬蟲
   - mac 的機器順利跑起來了～專案文件的安裝步驟還可以再更清楚，註明 docker 的安裝頁面、以及和 virtualenv 二選一
   - window 版本用 WSL 有些卡關， docker 裝好後，爬蟲跑步起來
   - Ronny: 要跑參數測試時，一台 aws ec2 可以黏兩張網卡，[一張網卡可以有兩個 IP](https://doc.scrapy.org/en/latest/topics/request-response.html#std:reqmeta-bindaddress) ，就不用開很多台
7. 小聚為了讓大家都可以參加，短期內還是用每月調查的方式進行，ddio 會繼續當小聚坑坑主
8. 本次出現的各種新工具、新用法：
   1. 結尾的成果分享時，可用 [meet.jit](https://meet.jit.si/rentea) 分享螢幕，就不用交換螢幕線和座位
   2. Ronny Wang 的 PostGIS 欄位建議請看 ``### 資料庫組`
   3. yellowsoar 提到 [語義化 commit message](https://seesparkbox.com/foundry/semantic_commit_messages)
      - commit message to change log 可以用 gitchangelog
https://pypi.org/project/gitchangelog/
      - 使用上要自己修一個 bug… 因為 maintainer 一直沒 merge PR…
https://github.com/vaab/gitchangelog/pull/116

### 資料庫組


> 關於 PostGIS 的 table schema ，如果租屋只是點位的話，建議 table 可以直接建成
```sql
CREATE TABLE house (
   id SERIAL,
   geom GEOMETRY(POINT, 3857),
   data JSON
);
CREATE INDEX house_geom ON house USING GIST(geom);
```
> 3857 是以公尺為單位的全球平面座標系，速度會比經緯度快很多，因為經緯度要算距離範圍因為是球面會需要很多 sin, cos 的計算，但是變成以公尺為單位的球面座標就只要平面建索引可以讓查詢速度變快很多然後 PostgreSQL 的 JSON type 真的超好用，可以把 PostgreSQL 當作 NoSQL 用 XD 
> 
> 如果要插入資料，可以用
```sql
 INSERT INTO house (geom, data) VALUES (ST_Transform(ST_SetSRID(ST_Point(經度, 緯度), 4326), 3857), ‘{…json資料…}’)
 ```

> 然後要找某個多邊形範圍裡面包含的租屋的話，可以用
```sql
SELECT * FROM house WHERE ST_DWithIn(geom, ST_Transform(ST_SetSRID(ST_GeomFromGeoJSON(‘這邊塞經緯度的 geojson’), 4326), 3857), 0);
```
> 就可以列出範圍內資料。ST_DWithIn() 是 PostGIS 官方推薦效率最好的查詢是否有重合的函式 
>
> 4326 是經緯度，透過 ST_Transform 可以轉換座標系
> [討論出處](https://g0v-tw.slack.com/archives/CJTBP7YRK/p1569340370012600) [name=Ronny Wang] 


### 每月固定小聚時間調查

需要考量的因素（歡迎增修）：
1. 固定週末或平日，是否會排除想要參與的人
2. 場地挑選方式，可接受的花費金額
3. 舉辦流程


### 開發類小聚流程

因為不想要每次都重新想一次，也方便之後活動複製，所以想要是是有沒有什麼固定流程可以套用。這次先來試試看：

1. 現場小記認領
   > 本次實驗結果，覺得突兀，覺得先找好主要幫手，會比開始時公開詢問好 [name=ddio]
3. 新手教學：介紹專案 hackfoldr 有哪些東西、定期活動
4. 自介：關鍵字、想做什麼
5. 開坑：從自介列出今天的坑
6. 各自跳坑
7. 各坑成果分享：結束前，每個坑五分鐘介紹
8. 後續待作認領：列出待作（最好開成 ticket）、決定下次小聚發起人（？）

### 活動照片
https://drive.google.com/drive/folders/1LrgPse8HyPVUgWcz37BLntIi794Zj6fO?usp=sharing
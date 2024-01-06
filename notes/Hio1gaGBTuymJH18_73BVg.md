---
title: vaxx.tw 2.0 2021/06/26 大松共筆
tags: vaccine, COVID-19
description: vaxx.tw 2.0 2021/06/26 大松共筆
---

# vaxx.tw 2.0 2021/06/26 大松共筆
參與者：
teemo
Tofus (Terry)
yoyow
SeanGau
ael
SL
Carmen
Hou
Isabel
ael
Mai
Howard
pofeng


## 前期提要

[白板連結（Miro）](https://miro.com/welcomeonboard/R3pQbUJlbjAwbzhXU2xIUjJPZExUaHVsODRnNlJybUdXaUZMN3dxTUlIZnZmdHZkV3FnWWVPbDc5Z3VJT29neXwzMDc0NDU3MzQ3NzgwNDk4NDQ5)
[大松簡報連結](https://docs.google.com/presentation/d/13cowWSJzfDl0DjUQ4NfXMP6PfZbLd6Q1XrfsegADcEs/edit?usp=sharing)

為什麼想要重啟 vaxx.tw？

* 青壯年比較容易因為「不方便」（時間不好安排、沒有及時得到資訊）而結果沒去打疫苗，因此若有一個可以簡單查詢疫苗資訊的地方會很棒：
    * where 哪裏
        * [COVID-19疫苗接種院所地圖](https://antiflu.cdc.gov.tw/Covid19)
        * [COVID-19疫苗接種院所](https://www.cdc.gov.tw/Category/List/hlrN4cZsF2Pe4C6DFhggqQ)
    * time 門診時段
        * [新北市合約醫院COVID-19疫苗服務時間](https://www.health.ntpc.gov.tw/basic/?mode=detail&node=8342)
    * availibility 尚可預約數
        * [新北市政府新冠肺炎COVID-19疫苗接種預約系統](https://vacbooking.ntpc.gov.tw/ntc_vaccination/index.php) 接種報名系統 施打區列表
    * reservation channel 預約管道（不管是醫療機構的預約系統或是地方/中央政府的預約平台，甚至是電話等等）
        * [全台COVID-19疫苗接種院所](https://www.cdc.gov.tw/Category/List/hlrN4cZsF2Pe4C6DFhggqQ)
        * [臺北市政府衛生局新冠肺炎COVID-19疫苗接種預約系統](https://booking.health.gov.tw/Home/notyet)
        * [新北市政府衛生局COVID-19 疫苗接種資訊整合平台](https://vaccine.ntpc.gov.tw/info/)
    * vaxx brand 疫苗品牌
        * [新北市政府衛生局COVID-19 疫苗接種資訊整合平台](https://vaccine.ntpc.gov.tw/info/)
    
* 疫苗最好大量的人同時段打，比較不會有交叉感染/疫苗失效問題

最後我們繞了一大圈的結論是，還是可以有個網站方便年輕人、青壯年（那些上班很難請假的人）

1. 知道自己是否符合資格
2. 方便快速找到可預約的時段和醫院
3. 有餘力的話多語言版本

所以還是希望有個像是 vaxx.tw 的東西，**只是我們還沒想好怎麼解決資格一直變、醫院網頁一直變爬蟲會很容易死掉的問題**。

## 待確認事項
* 專案授權方式：MIT? CC by 4.0?



## 現有資料（門診地點、門診時間）
* 可以[看到的施打機構地圖（CDC）](https://antiflu.cdc.gov.tw/Covid19?gclid=Cj0KCQjw_dWGBhDAARIsAMcYuJzvhXDNJAFqIwolHDKmDL2XYyx-peSnrlEY_zzDkJDTF0Uzh1kDEhIaAlZhEALw_wcB)，有當天門診時間、疫苗種類
* [各縣市衛生局回報的施打機構清單（CDC）](https://www.cdc.gov.tw/Category/MPage/7QiOF0wy5I0cTpFvFy0V2Q)

所以疾管署已經有施打的**門診地點**、**門診時間**，還差還**剩多少預約名額**，跟清楚的**施打資格說明**

## 現有還不確定怎麼取得的資料
* 預約狀況（志工人工找？爬蟲？）
    * 剩餘名額
    * 是否暫停接受預約

* 施打資格
* 各施打地點的疫苗種類
* 沒有預約系統的地方的預約方式



## 靈感
#### 查詢地點/時間
* vaxx.tw
* [口罩地圖](https://g0v.hackmd.io/@kiang/mask-info)
* [施打院所地圖](https://antiflu.cdc.gov.tw/Covid19)
    ```
    curl 'https://antiflu.cdc.gov.tw/Covid19/GetHospitalData' -H 'x-requested-with: XMLHttpRequest' --data-raw 'bottom=22&left=100&right=130&top=27'
    ```
* https://curative.com/covid-19-vaccine


#### 查詢資格
* [澳洲資格查詢](https://www.health.gov.au/resources/apps-and-tools/covid-19-vaccine-eligibility-checker)
* 日本用 salesforce 開發疫苗管理, 預約(?) https://www.mhlw.go.jp/content/10906000/000707430.pdf

## 討論：網站可以有什麼樣的內容？


#### 使用者可能有什麼樣的考量？
- 距離（因為是相對健康的　減少移動軌跡）
- 疫苗廠牌
- 民眾的排隊數
    - 現場人數的多寡
- 我會不會排擠到其他要打疫苗的人？（前11類）
    - [台灣 COVID-19 疫苗公費接種統計](https://covid-19.nchc.org.tw/dt_002-csse_covid_19_daily_reports_vaccine_city2.php)
- 自己有空的時間、最早可以預約到的時間
- 多國語言
- 哪裏有夜診可以晚上打疫苗

:::info
### 可能功能
#### Filter功能:
* 地點
    * 
* 預約狀況

#### 施打點資料呈現：
* 預約狀況
* 預約方式
* 疫苗種類

#### 疫苗之前注意事項：
* 有哪些人不適合
:::


## 討論：「剩餘預約名額」的資料哪來？

**提案一**：搞不好可以先只找最有辦法大量施打疫苗的醫學中心/教學醫院資料（全台58間，有網站，可能可以爬蟲）
* 有統一的csv欄位定義，請工程師各自爬蟲，想辦法把各自負責的醫院資料爬到，更新。

    * 總列表(列出所有可施打的地點資料，以及是否已經有爬蟲可抓)
        * 地點名稱 (要用機關名?或院所?或施打站? 因為有體育館施打站之類) 
        * 施打站地點（地址、經緯度）
        * 爬蟲資料位置（可以直接指到讀到 CSV 的位置)
            * 這邊可以是 https://raw.githubusercontent.com/g0v-data/mirror/master/aec/gammamonitor.csv 這樣的網址，寫爬蟲的人只要定時把最新資料傳到 github 上去就行了
            * 也可以是用 Heroku 的網址，各別程式志工可以自行把程式傳到 Heroku ，一個程式只處理一個院所
        * 爬蟲程式碼位置（爬蟲的 github 位置，協助其他人 review ，或是如果爬蟲停擺其他人可以接手)
        * 預約網址（給人類看的網址）
        * 施打站代碼 (醫事機構代碼)
    * 各別地點資料(上面各別「爬蟲位置」內可以抓到的 CSV 欄位)
        * 疫苗代碼
        * 時段 / 剩餘名額 (夜診資訊很重要)
        * 資料抓取時間（給使用者判斷資料是否有過時，也給總爬蟲可以判斷各醫院爬蟲是否還存活著）
:::success
舉例：台大總院
資料擷取時間：20120626 PM01:49
| 午別 | 2021/6/28   | 2021/6/29   | 2021/6/30  | 2021/7/1    | 2021/7/2   |
|----|-------------|-------------|------------|-------------|------------|
|    | 星期一         | 星期二         | 星期三        | 星期四         | 星期五        |
| 上午 | 74診(剩餘93名)  | 74診(剩餘112名) | 74診(額滿)    | 74診(剩餘12名)  | 74診(額滿)    |
| 下午 | 74診(剩餘121名) | 74診(剩餘123名) | 74診(剩餘82名) | 74診(剩餘108名) | 74診(剩餘39名) |
| 夜間 | 額滿加開        | 額滿加開        | 額滿加開       | 額滿加開        | 額滿加開       |
:::
    * Nice to have欄位
    * Ex.
    * 身分證號
    * 生日
    * 身分
    * 手機
    * 劑別
   
   
   

搜尋醫院和中央系統的預約名額網址
需要 push 中央提供 URL、NIIS open data
中央不太可能有即時資料
可能可以用過去的資料預測未來的資料

Howard: 會有大規模預約，四種方式預約
要查詢量和地點民眾應該很方便

Special cases: 中央直接配發地方衛生局、醫療院所

政府可能不會鼓勵進行遠距離移動，因為疫苗副作用發生時，離原始施打院所太遠，可能會來不及。

網站上可能要加疫苗注意事項警語


**提案二**：志工分責任區塊，排班更新資料




**可能可以用過去幾天施打資料，可以預測哪些施打點比較容易有位置**

## 討論：醫學中心會同時有很多的預約管道？（1922系統、醫院自己的系統、專案預約）
1922預約系統的預約名額跟醫療院所可以預約的名額，是分開來算的。因此如果要發揮portal的價值的話，要同時呈現
- 全部可爬到的施打點剩餘名額（例：1922系統＋醫院）
- 不同名額的預約連結
- 大型施打的名單會從1922來


---
### Q&A

1. 關於距離的選擇
2. 關於施打場所的先天限制
3. 關於品牌為何能開放選擇
4. 關於疫苗廠牌的先天限制
5. 餘劑無法像有友善食光地圖/口罩地圖的原因


---



## 下一步
用兩個禮拜，先製作一個MVP，裡面先整理雙北市裡可獲得的資訊（以醫學中心/區域醫院為主）。

- 定義資料格式和來源 
- 取得資料（爬蟲、人工） 進[airtable](https://airtable.com/invite/l?inviteId=invVDpunT8QxEfgLa&inviteToken=b3c85f0a1a264384c01b3700ef9e8d127b50a74e227fc45b86fa560cbbb9edec&utm_source=email)(這次的後端資料庫) 
- 網站設計 ：wireframe+與前端工程師保持聯絡
- 前端網站開發：有時間就寫一個地圖呈現的前端，沒時間就用sheet2site整理資料

**台北市**
院所資料：https://gist.github.com/ronnywang/b6ec3f0cb6bd73f726a2a090261ce0a0
預約狀況：各醫院各自的預約網站

**新北市**
院所資料 & 預約狀況：https://vacbooking.ntpc.gov.tw/ntc_vaccination/index.php?action=ntc_vaccination_front_index

Next 小聚：7/2（五）8pm （線上地點未定）
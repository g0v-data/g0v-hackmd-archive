---
tags: jothon
---

# g0v Database

:::info
收錄內容種類
(1) 歷年大松提案列表
(2) 專案清單
(3) 基礎建設清單
(4) 社群活動場地清單
(5) 專案圖鑑簡報
(6) g0v Slack 頻道列表與簡介短句
:::

# 專案圖鑑簡報

用 簡報方式，製作各個專案的介紹頁面
https://docs.google.com/presentation/d/1S4rWtCGAe99Vy_bLd6CjuHtAdrCYzN1k7TqhIrG-u5g/edit#slide=id.p

# g0v Slack 頻道列表與簡介短句

https://g0v.hackmd.io/NuhdUaTVRNykTqcstpM8VQ

# 以 csv 格式整理歷年大松提案列表、專案清單、基礎建設清單

[資料庫連結](https://docs.google.com/spreadsheets/d/1C9-g1pvkfqBJbfkjPB0gvfBbBxVlWYJj6tTVwaI5_x8/edit#gid=1563040282)

## 起因
想要整理過去出現的專案，先前有 sense.tw 整理的社群關心議題，但前者偏向視覺化呈現， g0v database 則是想要透過表格將相關文件跟聯絡資訊整理出來。
>由 Lora 整理第一版，大助接手正規化與詳細文件補齊&大松再次提案。

## 項目名稱

在這個資料庫中，我們列出各個專案被提出的時間地點場合，希望後續的人無論是想進行研究或者參與新專案可以透過這個資料庫找到對應的人參與貢獻，以下個別介紹每欄欄位名與格式。

### 專案基本資料
> 專案名稱、提出時間、屆數、提出活動類型、投影片連結等資訊。
* project 專案名稱
    * 格式：文字
* date 專案提出日期
    * 格式：yyyy/mm/dd
> [name=tmonk]
> 建議格式使用 yyyy-mm-dd
* term 專案提出的活動屆數
    * 格式：數字
* event name 專案提出的活動名稱
    * 格式：文字
* three brief 專案的關鍵字（第三次大松以前為提案人的三個關鍵字）
    * 格式：文字
> [name=tmonk]
> 目前三個關鍵字的分隔符號並無統一
* manpower 專案需要徵求的人（第三次大松前無此欄位）
    * 格式：文字
* dummy event type 紀錄此專案是從哪個場合提案的
    * 格式：文字（大松、小松、其他黑客松）
* guideline 跟專案有關的文件
    * 格式：文字 （連結網址）
* other document 其他文件，包含提案投影片，多餘一個標註 2,3
    * 格式：文字 （連結網址）
* video link g0v.tw youtube 頻道上找到的影片
    * 格式：文字 （連結網址）

### 專案聯絡資訊
> 如果想要找當初提案人，可以透過以下欄位去尋找
* owner name 提案者名字
    * 格式：文字
* facebook 提案 FB 聯絡方式
    * 格式：文字 （連結網址）
* slack id 提案 Slack 聯絡方式
    * 格式：文字 (@id)
* slack channel	該專案開了個別的 slack channel
    * 格式：文字 (#channel)
* email 提案 Email 聯絡方式
    * 格式：文字 (jothon@g0v.tw)
* telegram 提案 Telegram 聯絡方式
    * 格式：文字 (連結網址 or @id)

### 專案的其他資訊
* continue contribute 是否持續貢獻，若有持續運作或更新請填 yes，已經結束或專案停擺沒有持續更新請填 no，剩下請填 other
    * 格式：文字
* license code	程式碼的授權形式
    * 格式：文字
* license data 資料的授權形式
    * 格式：文字
* education project 教育相關的類別，若是與教育有關的類別，則在此欄標記為 yes，若否則標記為 no
    * 格式：文字


## 我能做什麼？
如果你曾經提案過，你可以找自己的 ID，填寫缺少的資料，順便更新一下專案的近況，像是持續開發中的專案在 continue contribute 中選擇 yes，也可以把已經告一段落，不再開發的專案寫 no，other 則代表說這個專案還在收集資料，或者你不知道怎麼寫。

另外一件可以做的事情，則是把其他場提案的內容填上去，現階段的資料庫仍舊以大松為主，如果你曾經舉辦過其他活動，自己的坑自己填，幫忙補上資料！
可以加入小松、基礎松的列表

## 後續應用
1. 資料視覺化，有名稱、屆數、影片等資訊可以拼湊起來。

## 可以增加的欄位或功能
1. 提案在哪場活動出現過
2. project hub
3. 加入大松小松整理
4. 把三個dummy event type合併成一個欄位 (done)
5. 新增一欄提案編號
6. 紀錄相關提案的編號，以半型逗號,隔開
7. 新增一欄最後活動日期(如最後一次出現在g0v或gihub最後一次submit)
8. 不同場次的提案，實際上是同樣的專案，這樣專案之間的關係有需要標注嗎？

## 2019/09/07 討論
> 問題: 從各專案名稱，無法基本瞭解該專案內容，且點進該專案仍不知道該專案的內容

解法
1. 建立各專案的成立目的，未來顯示在網站上

作法
1. 搜尋各專案的目的

>問題: 各專案沒建立分類，使用者只能從標題瀏覽

步驟:
1. 研究各提案網站的分類
2. 建立完善的分類架構
*  如何建立?
    *  一個主題有重複分類，還是要建立一個主分類給他?
    *  另一個分類當作相關分類?
> 問題:　初次參加 g0v 的人，不確定哪些專案適合自己

定義各分類代表意涵

地理位置

## 專案主題分類架構
分類的目的是在於讓想參與的人找可以想加入的專案。
尋找專案的可能方向：
1. 議題取向
2. 解決方案（例如各種地圖、App、Chatbot）
3. 參與者技能

> 目前的專案分類：g0v公民科技創新獎助金計畫的專案類別
> * 新媒體應用
> * 開放資料
> * 公共政府
> * 社會參與
> * g0v社群基礎建設

其他分類方式參考 https://g0v.hackpad.tw/0.bdfmogr4it

### 提案分類整理
https://docs.google.com/spreadsheets/d/1GND-IKNIPJfQ4Ry2hfHQpEm8_CuBZa7ZchTedlWiO08/edit#gid=0

### 架構發想
> 專案的大類
> 較為固/穩定的架構

### 分類方式
「應用資料類別/議題類型」+「解決方案/應用技術」

### 「應用資料類型/議題類型」參考架構

* 國發會政府資料開放平臺 https://data.gov.tw
* 臺北市資料大平臺 https://data.taipei/#/dataset/topic
* 英國政府開放資料 https://data.gov.uk
* 美國政府開放資料 https://www.data.gov

### 「解決分案/應用技術/參與者技能」
> 輔助應用資料類型，作為層面分類篩選。
> 呼應資料庫的manpower
> 但manpower要當作層面分類要權威化名稱

## 層面分類
* 專長 (可以選擇多項聯集)針對坑主、參加者對自己專長查詢自己能夠做的事情
規劃
行銷
UI
UX
資料整理
前端
後端
全端
Android、iOS
查資料
贊助
領域專家
* 應用技術: 提供各專案目前用到的技術
java
SQRL
Python
React
...

* 同一專案: 歷年提出的專案、但名稱不同，建立連結
* 產出結果:
APP
網站
Chatbot
資訊視覺化
通報工具
地圖
資料庫
OCR


## Social tagging(Owner)
> 提案者自由下標籤
> 彈性的架構
> 

---

##  網頁版瀏覽頁面 

### 零時政府專案列表 by 骨董
https://tomliau33.github.io/G0vProjectList

### 卡片化網頁 Sheet2Site
所使用的功能：[Sheet2Site](https://www.playpcesor.com/2018/03/sheet2site-google-sheet.html)
呈現：http://bit.ly/g0v-project-list-sheet2site
後台：http://bit.ly/2kylbNS
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ccf00098d32475e3598e5b40934d7a68)

### 「如果把專案加上經緯度？」
此地圖中嘗試將 g0v Grants 部份專案進行地圖化 
http://bit.ly/2o0Lj5I

### Airtable2sheet2site
- 我先用我的 Airtable 帳號開了一個頁面 (Q: 這個頁面是不是就已經可以讓不特定對象，將資料接走了呢 ?)
    - http://bit.ly/g0v-project-list-airtable
- 另外，透過 Airtable Importer 外掛也整理一份到這個頁面 (需要給它 APIkey)
    - http://bit.ly/g0v-project-list-airtable2sheet
- 然後，我再使用 sheet2site 的網頁服務弄出個網頁 (麻瓜流派 orz)
    - http://bit.ly/g0v-project-list-sheet2site

### 令人驚奇的零時政府

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d3f66dda2b1f0a0390bbc37ac516d068.png)

https://chunyenhuang.github.io/awesome-g0v-projects/

不同於以往的專案整理設計，我改用新的專案索引

[專案架構包含](https://github.com/chunyenHuang/awesome-g0v-projects/blob/master/data/projects.csv)
- 提案 (根據g0v database的資料)
- GitHub Repos
- GitHub Issues
- HackMd (根據 tags 與標題相關性 自動抓)


| 以 [Cofacts 真的假的](https://chunyenhuang.github.io/awesome-g0v-projects/#/project/Cofacts%20%E7%9C%9F%E7%9A%84%E5%81%87%E7%9A%84/dashboard) 為例 | [過往提案會被整理在一起](https://chunyenhuang.github.io/awesome-g0v-projects/#/project/Cofacts%20%E7%9C%9F%E7%9A%84%E5%81%87%E7%9A%84/proposals) |
| -------- | -------- |
| ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6b72cb05e8cda5dcecbb6031168a41af.png)     | ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d527bb39b2ed4ae96f3f9571fb35dd54.png)     |

## 過去也做過歷年專案整理的專案

awesome-g0v
https://github.com/g0v/awesome-g0v
http://g0v.github.io/projectPool/

g0v 歷來關心議題
https://trello.com/b/tDEQfv5N/g0v-%E6%AD%B7%E4%BE%86%E9%97%9C%E5%BF%83%E8%AD%B0%E9%A1%8C

g0v hackathon 提案一覽表 (By kirby)
https://docs.google.com/spreadsheets/d/12ZIlJU0Pnhi_uLTlnE2utyZka6QvUjz7SW7sfmJvFEg/edit#gid=0

YA0H: Yet Another g0v Hub
https://grants.g0v.tw/projects/5969ed35d60a0d001ed1f7f6

### 實作
* Download csv file via link
    * http://drive.google.com/uc?id=[file_id]&export=download
* Download csv file via Google API
    * [Downloaded Files](https://drive.google.com/drive/folders/1L7YtTuzPWMXcCVYJRJLKYrkaO9RpBOqk?usp=sharing)
    * [Fix encoding problem](https://data.gov.tw/node/18765)
    * [Install Google API / [Errno 2] No such file or directory: 'credentials.json'](https://developers.google.com/sheets/api/quickstart/python?hl=zh-TW)

``` python=
#!/usr/bin/env python
# coding: utf-8

import pickle, csv, os.path
import os.path
from googleapiclient.discovery import build
from google_auth_oauthlib.flow import InstalledAppFlow
from google.auth.transport.requests import Request

# If modifying these scopes, delete the file token.pickle.
SCOPES = ['https://www.googleapis.com/auth/spreadsheets.readonly']

# The ID and range of a sample spreadsheet.
SAMPLE_SPREADSHEET_ID = '1C9-g1pvkfqBJbfkjPB0gvfBbBxVlWYJj6tTVwaI5_x8'
SAMPLE_RANGE_NAME = ['大松提案列表!A1:AB', '資料庫欄位說明!A1:C']

def get_credential():
    creds = None
    # The file token.pickle stores the user's access and refresh tokens, and is
    # created automatically when the authorization flow completes for the first
    # time.
    if os.path.exists('token.pickle'):
        with open('token.pickle', 'rb') as token:
            creds = pickle.load(token)
    # If there are no (valid) credentials available, let the user log in.
    if not creds or not creds.valid:
        if creds and creds.expired and creds.refresh_token:
            creds.refresh(Request())
        else:
            flow = InstalledAppFlow.from_client_secrets_file(
                'credentials.json', SCOPES)
            creds = flow.run_local_server(port=0)
        # Save the credentials for the next run
        with open('token.pickle', 'wb') as token:
            pickle.dump(creds, token)
    return creds


def get_sheet(creds):
    
    service = build('sheets', 'v4', credentials=creds)    
    values = []
    
    for sample_range in SAMPLE_RANGE_NAME:
        sheet = service.spreadsheets()
        result = sheet.values().get(spreadsheetId=SAMPLE_SPREADSHEET_ID,
                                    range=sample_range).execute()
        values.append(result.get('values', []))
    
    return values
    
creds = get_credential()
values = get_sheet(creds)

for sheet_i, sheet_name in enumerate(SAMPLE_RANGE_NAME):
    with open('g0v_data_%s.csv' % sheet_name.split('!')[0], 'w',encoding='utf8', newline='') as csvfile:

      writer = csv.writer(csvfile)
      
      for i, v in enumerate(values[sheet_i]):
        if i != 0 and sheet_i == 0: # Add Serial Number to collumn E
            v[1] = "%08d" % (i)
        writer.writerow(v)
        if sheet_i == 1: print(v)
  

```

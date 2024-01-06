---
title: "小蜜蜂戰鬥隊覆蓋率地圖視覺化工具"
tags: 小蜜蜂戰鬥隊,hackpad
---

# 小蜜蜂戰鬥隊覆蓋率地圖視覺化工具

> [點此觀看原始內容](https://g0v.hackpad.tw/KOsFaCMi6u0)


\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ef279d77f7c99add1606a7ecdb91fc52)

hackth8n當天翦影, 感謝 [Kirby Wu](https://g0v.hackpad.tw/ep/profile/BpuuLk9nZsO)大神

專案介紹 | Project Readme / Meta
小蜜蜂戰鬥隊: [https://www.facebook.com/groups/739964776043615/](https://www.facebook.com/groups/739964776043615/)
基本上是一個類似"樁腳 2.0"的自發性團體, 根據其團體介紹:"
【小蜜蜂戰鬥隊】在幹嘛
我們期望能夠以傳單發送的方式，將關於國家政策、公共議題的訊息傳播給非網路使用者，讓更多關心「台灣-我們摯愛的這塊土地」的人知道台灣正在發生什麼事情。

【小蜜蜂戰鬥隊】運作模式
由自發性成為小蜜蜂的熱心群眾，初步是以發送傳單的方式在居家附近的信箱、車道、餐廳留下關於國家政策、公共議題等訊息。未來，我們會佐以官方網站、粉絲團、Line等網路管道交叉傳播。期盼能用這樣的方式喚起非網路使用者、不了解國家政策、公共議題之民眾的公民意識，主動關心國家政策、公共議題。"


根據觀察, 小蜜蜂們目前回報"哪些地區已經拜訪/發放過文宣"時, 目前還是使用google表單一項項回報, 並不好查閱
[https://docs.google.com/forms/d/1haMMHB6WuxHA72q5mbFHN0QcP-Nsntg-XhtPLJzMK3Y/viewform](https://docs.google.com/forms/d/1haMMHB6WuxHA72q5mbFHN0QcP-Nsntg-XhtPLJzMK3Y/viewform)
[https://docs.google.com/spreadsheet/ccc?key=0Ah_x9MED27xydFhHb056RjVfWTN3cHFQTGNWWDlfbEE#gid=0](https://docs.google.com/spreadsheet/ccc?key=0Ah_x9MED27xydFhHb056RjVfWTN3cHFQTGNWWDlfbEE#gid=0)
因此想要做出一個地圖視覺化顯示出已覆蓋(已經拜訪/發放傳單)的地區或路段, 還有條列出未覆蓋地區或路段的工具給小蜜蜂們使用.

## 專案介紹

專案說明
主要是想要開發能夠讓小蜜蜂戰鬥隊在回報已覆蓋路段和查閱未覆蓋路段時更方便的工具,
首次詢問蜂群們的迴響:
[https://www.facebook.com/groups/739964776043615/742570099116416/](https://www.facebook.com/groups/739964776043615/742570099116416/)

- **發起人/拋磚人：**[Kirsten Liu](https://g0v.hackpad.tw/ep/profile/thCnZv8r9eY)
- **現有類似專案：**
    - github: ben196888
    - google map應該有許多api可以用?
        目前有蜂群這樣使用:
        [https://mapsengine.google.com/map/viewer?mid=zqMBX3h4TySw.kv4VRLilReoo](https://mapsengine.google.com/map/viewer?mid=zqMBX3h4TySw.kv4VRLilReoo)
    - [http://ddio.github.io/MuscidaeFlash/](http://ddio.github.io/MuscidaeFlash/)

by 貓橘毛:"各區可以一個代表在 [http://mapsengine.google.com/map/](http://mapsengine.google.com/map/) 建立就可以了
但為防滲透的情況請盡量備份 kml 檔 & 設定權限....
(((mapsengine內建沒有備份功能"

- **授權方式**
MIT

- **使用資料**

目前回報表單:
[http://goo.gl/NvJOWx](http://goo.gl/NvJOWx)

目前覆蓋地區/路名回報:
[https://docs.google.com/spreadsheet/ccc?key=0Ah_x9MED27xydFhHb056RjVfWTN3cHFQTGNWWDlfbEE#gid=0](https://docs.google.com/spreadsheet/ccc?key=0Ah_x9MED27xydFhHb056RjVfWTN3cHFQTGNWWDlfbEE#gid=0)

社團定時整理所有回報:
[https://docs.google.com/spreadsheet/ccc?key=0AtOMoRZvQH9ZdFE2ZE8yanFJWnFqMU9vVFdhcDFPOEE&usp=sharing#gid=0](https://docs.google.com/spreadsheet/ccc?key=0AtOMoRZvQH9ZdFE2ZE8yanFJWnFqMU9vVFdhcDFPOEE&usp=sharing#gid=0)

各地蜂巢和蜂巢覆蓋率:
[https://docs.google.com/spreadsheet/ccc?key=0AtOMoRZvQH9ZdGZkalZicDNNZDA4MURwQXJqbTA1NVE&usp=sharing#gid=0](https://docs.google.com/spreadsheet/ccc?key=0AtOMoRZvQH9ZdGZkalZicDNNZDA4MURwQXJqbTA1NVE&usp=sharing#gid=0)

## 目標與功能（要如何解決）

專案目前狀態
- **進度狀態：第一版陽春型地圖回報工具測試中, 還差許多功能(強力徵人拜託Q__Q)**
- **預定功能：**
- [ ] 地圖視覺化顯示出已覆蓋(已經發放傳單)的地區或路段, 發放路段以點對點線條表現
    - [x] 自己成立另一個填寫表單
    輸入區域
    [https://docs.google.com/forms/d/1w2Im7uc-Gpv5T_YL1-Aa6FnFQRQxxRVPJ0mj-u1kdjY/viewform](https://docs.google.com/forms/d/1w2Im7uc-Gpv5T_YL1-Aa6FnFQRQxxRVPJ0mj-u1kdjY/viewform)
    結果表單
    [https://docs.google.com/spreadsheet/ccc?key=0Ah-9opsSMy6LdENYTDZQVWtfYmV3eXRtUFlSV094S1E&usp=sharing](https://docs.google.com/spreadsheet/ccc?key=0Ah-9opsSMy6LdENYTDZQVWtfYmV3eXRtUFlSV094S1E&usp=sharing)

    可用工具:
    [https://github.com/burnash/gspread](https://github.com/burnash/gspread)

    Beti提案：
    - [ ] 希望將顏色用於傳單發放數量, 而非傳單種類，因為若表單數量增加，顏色也會不斷增加，相對辨識度降低
    - [ ] 若要看出每種傳單發放總量,  可以將所有傳單表單列在網頁側欄, 以radio button方式點選項目之後, 出現單ㄧ表單發放總數量與路段線條
    - [ ] 可點擊路段, 出現bubble window, 觀看此路段每種傳單的發放數量
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8efdd3d941b767d04032421513d8a13a)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2896d9584c1b8a0e627937c4b56cbcac)

    - [ ] 定時去抓取新增的row
    - [ ] 模糊地址警示(地址填無法辨識者跳出警告對話框, 不給送出)

- [ ] 條列出未覆蓋地區或路段
- [ ] 能夠使小蜜蜂在輸入回報路名或區域時整合到已覆蓋地圖視覺化中

- **工作目標：**
    - **近程計畫（淺坑）：**地圖視覺化顯示出已覆蓋(已經發放傳單)的地區或路段
    最緊急(測試蜂有問, 有催):
        - [ ] 文宣選擇可擴充
        - [ ] 以地址匯入後user可以更動/修改自己輸入的資訊
        - [ ] 匯入歷史資料
    次緊急(測試蜂有問):
        - [ ] 在submit頁面增加畫地圖回報or填地址回報(目前蜂群google form style)二選一
        - [ ] 畫線自動mapping到路段上, 如果路有轉彎不用分段畫
        - [ ] 提供能夠使用google資料庫裡的地標功能
        [https://developers.google.com/places/documentation/supported_types](https://developers.google.com/places/documentation/supported_types)

    緊急(自由心證)
        - [ ] README.md
        - [ ] progress bar
        - [ ] Q&A單點回報流程
        - [ ] Feedback page

    暫緩(有最好, 但前面做完再填):
        - [ ] 文宣除了拉檔案進來可以選擇從資料夾上傳檔案
        - [ ] 文宣擴充分權限增加(有權限者可增加文宣版本)
        - [x] 提供在編輯時能修改先前畫的資訊, 而非只能clear重來
        - [x] 單點輸入發放份數 ex在捷運站門口發400份傳單
        - [ ] impress the color of info window close tag
- [ ]  加入我要印文宣，讓小蜜蜂還可以下載文宣加印
    - **中程計畫（中坑）：**
        - [ ] 防範惡搞/惡意灌水
            例如:增加登入驗證, 雙重驗證, 或是一筆筆回報資料由各地蜂后審核(?) or網站設計成可回複或有防禦機制
        - [ ] 把google map上有人去過的地方就上半透明的顏色，而且不同種類的傳單可以對應到不同的圖層(可以 filter 不同版本的文宣.)
        - [ ] 能夠使小蜜蜂在輸入回報路名或區域時整合到已覆蓋地圖視覺化中, 結合報表與地圖, 報表上有的自動畫在地圖上
        - [ ] 對模糊或不合法的地址回報做處理或警示(或用郵局中翻英格式規避)
            ----------------------------------------(以下kirsten認領地址NLP orz)
            - [x] 整理歷史地址
                - [ ] 制定合法地址(目前想法: 單一路名中包含"路"和"號", 裡面沒有'，' '、' '~')
                    - [x] xxxxxxxx號 : save as road_singleNum\[\]
                    - [ ]
                - [ ] 把逗點狀況分出來分析
                - [ ] 把頓點狀況分出來分析
                - [x] 把xxxx ~ xxx的抓取出來 分別在array中存成兩筆子地址
                - [ ] 處理xxxx ~ ooo 中, ooo只為號碼, 需要補前綴的狀況
                - [ ] 把無法處理的丟到人工辨識區(如有可能, 建立一個人工辨識頁面)
    - **遠程計畫（深坑）：**
        - [ ] 希望有選項可以以"傳單名稱"來勾選顯示發過的區域，這樣想找哪個版本在某區有無發過比較方便(目前預計以不同圖層來呈現)
        - [ ] *條列出未覆蓋地區或路段(最好是能有個check list之類?)  =>做出另一個類似模板, 讓版工可以標示出需要拜訪的區域(如果可以分priority圖層更好)
        - [ ] *投信箱戰術避免重複的工具，map無法顧及大樓戶數(增加精細度)
        - [ ] 整合 list 呈現方式 (refer: ng-grid)
    - **終極目標（無底洞）：**完善整個平台工具以及蜂群們的需求
        - 延伸坑: [https://www.facebook.com/groups/g0v.general/permalink/607850852624658/](https://www.facebook.com/groups/g0v.general/permalink/607850852624658/)

    - **以下開放蜂群許願（但是請高抬貴手工程師不是神阿）：**
        - 一位小蜜蜂建議:
            1.  先把達到民意需要割的闌尾。地圖上出現他的選區
            2.  約定時候後，大家路過掃街或是投單時可以用打卡的方式
            3.  掃街時定位打卡這樣。 做成路徑圖，這樣小蜜蜂才不會重覆投單。
            4.  當經過感招的民眾填寫加入割闌尾時，地圖上會顯示出人數的增加
        - 可以在旁邊有備註嗎?怕顏色多太亂的話，如果旁邊有欄位備註發了那種的型的傳單，或者是多數是那種類型的人的話應該可以提供更多人參考跟統計!(跟beti提案內容類似)
        - {遍地開花}行事曆的願，可以在登入時提醒今天登入區域周邊是否有活動。
        - 文宣攻略都可以一同存取，就是點進去看發了那種類型傳單時，可以順手點開查看文宣內容跟版本。
        - 區域類型人口可以分年齡層按鈕，例如70歲~80歲、30歲~50歲。或是職業選擇紐，如@商@服務@家管@工等等；以後方便做成統計年齡跟職業。
        - 或是可標記為商業大樓及店面型商店，小吃店家或是大樓住宅區，國宅、透天住宅、別墅區等。(因為可發便選擇對應發放的文宣類別)

- **預定使用者**
    各地蜂巢的小蜜蜂戰鬥隊


## 徵求協作者(強力徵人阿阿阿阿阿Q___Q)


分工與成員
- [x] NeedsDesigner:   [beti chiang](https://g0v.hackpad.tw/ep/profile/DA0yMFmOBFG)
- [ ] NeedsData: 需要資料（擷取、清理）from "小蜜蜂戰鬥隊"現有的回報資料需要merge進來  [Chewy Hsu](https://g0v.hackpad.tw/ep/profile/uMz1xr48sAf)
- [ ] NeedsTech: 需要技術支援（程式、架站 etc)  [Chuan-Heng Hsiao](https://g0v.hackpad.tw/ep/profile/rfP5bbcHah6)  [sherry lin](https://g0v.hackpad.tw/ep/profile/x7Hh4B7mUzZ)  [Kirsten Liu](https://g0v.hackpad.tw/ep/profile/thCnZv8r9eY)  [Chewy Hsu](https://g0v.hackpad.tw/ep/profile/uMz1xr48sAf)
- [ ] NeedsProcess: 需要幫忙設計作業流程
- [x] NeedsTalkingToRealPerson: [Kirsten Liu](https://g0v.hackpad.tw/ep/profile/thCnZv8r9eY) (跟各地蜂群詢問功能需要)
> 設定成 project registry 中的 tags，需要幫忙的會自動 promote 到 g0v project hub
> [name=ET B]



## 實作細節（非技術背景可跳填）

協作工具
- github repo：[https://github.com/](https://github.com/g0v/LittleBeeGeo)[g0v](https://github.com/g0v/LittleBeeGeo)[/LittleBeeGeo](https://github.com/g0v/LittleBeeGeo)
- hackfoldr 工作資料夾網址：
- google drive 共用資料夾網址：
- Dropbox shared folder for graphical design: [https://www.dropbox.com/sh/x2zck86kz60mirl/n1LCEwN3Oj](https://www.dropbox.com/sh/x2zck86kz60mirl/n1LCEwN3Oj)


## 記錄

- 建立蜂群
- 在地圖上標出蜂群街道發送點到點的"線"

資料格式:
\[{
save_time: 時間戳記 (timestamp: 123456890)
 agenda: 檔案版本 (文宣) (text)
 user_name: 暱稱 (text)
 county: 縣市 (text)
 town: 鄉鎮市區 (text)
 address: 路段 (text)
 start_number: 起始號碼 (text)
 end_number: 結束號碼 (text)
 count: 數量 (int)
 deliver_time: 派送時間 (timestamp)
 deliver_status: 發送狀況 (text)
 memo: 備註 (text)
 geo: geo 資訊 (list of geojson (polygon only))
extension: 其他 (json)
}\]


test server:
192.168.1.16:6437/post/json

curl -X POST -d '\[{"save\_time": 1234567890, "agenda": "test", "user\_name": "test\_user\_name", "county": "Taipei City", "address": "test\_adr", "start\_number": 1,  "end\_number": 2, "count": 100, "deliver\_time": 1234567890, "deliver\_status": "complete", "memo": "test\_memo", "geo": \[{"type": "LineString", "coordinates": \[\[121.5, 21.5\],\[121.5, 21.6\]\]}\], "extension": {}}\]' '192.168.1.16:6437/post/json'

192.168.1.16:6437/get/json

curl '192.168.1.16:6437/get/json'


## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）


dev 版: [http://106.187.101.193:6789/#/map](http://106.187.101.193:6789/#/map)

TODO:
1\. finish submit form part.
2\. discuss production machines.
3\. If the lines overlap, user can’t click the line and read the information.


Untitled

This pad text is synchronized as you type, so that everyone viewing this page sees the same text.  This allows you to collaborate seamlessly on documents!



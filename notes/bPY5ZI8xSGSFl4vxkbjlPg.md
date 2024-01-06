# 增加課程類別程序

### 建立中研院課程類別管理（以增加：學術研究倫理教育時數 為例）
E+ 類別：研究誠信 519

#### 新增課程類別步驟
* 新增類別：
![本院課程類別管理](https://i.imgur.com/28bdbMX.png)

* 設定角色：
![課程類別角色基本資料管理](https://i.imgur.com/U430ZMm.png)

* 中研院課程類別列表
```
[
   {
      "scategoryID":"1",
      "cname":"環境教育時數",
      "inUse":"0",
      "serialz":"1"
   },
   {
      "scategoryID":"2",
      "cname":"資通安全課程",
      "inUse":"1",
      "serialz":"2"
   },
   {
      "scategoryID":"3",
      "cname":"學術研究倫理教育時數",
      "inUse":"1",
      "serialz":"3"
   }
]
```

先找出中研院課程類代碼：scategoryID
查詢E+使用的類別：category，找到要增加的類別，ex: 研究誠信
```
   {
      "categoryID":"1599",
      "categoryNo":"10014118",
      "category":"研究誠信",
      "instCode":"0",
      "preClassify":"終身課程類別>政策能力訓練>政策宣導訓練>學術倫理",
      "sinicaType":"0"
   },
```

將sinicaType 設為中研院類別 scategoryID: 3
```
https://learnrecord.its.sinica.edu.tw/cronjob.php?dosqlcmx=Y&xxoo=Y&ipRangex=Y&sql=update category set sinicaType=3 where categoryID=1599
```

### 問題查找
* 首頁清單類別沒計算到時數，但個人學習紀錄有資料，且分類正確
![個人學習紀錄有資料](https://i.imgur.com/40HP1I5.png)
![首頁沒出現應有的學習時數](https://i.imgur.com/l4BhDUj.png)

```
[
   {
      "excelID":"13811",
      "usrNo":"1",
      "name":"",
      "department":"",
      "depID":"24",
      "title":"",
      "email":"",
      "tel":"",
      "courseID":"4637",
      "course":"學術紅線的五個模糊地帶",
      "datez":"",
      "datex":"2020-05-15",
      "hours":"2",
      "mm":"0",
      "lastupdate":"2020-05-16 01:31:37",
      "insTime":"2020-05-16 01:31:37",
      "ID":"1"
   }
]
```
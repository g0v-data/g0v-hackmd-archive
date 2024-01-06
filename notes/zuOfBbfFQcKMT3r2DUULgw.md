# 20190530_Meeting Summary

## OutLine

* 前情提要
* 本週進度

    * Data collection
        * 使用PyMySQl連接,控制資料庫
        * 爬蟲實作
        
        
    * Linebot
        * 解決兩個以上Js file互相呼叫的問題
        * Node.js+LineBot語法
        
    * Olami NLI
        * Olami 語法實作


    * 比賽企劃書
        * 副檔案直接說明

* 下週進度

---

#### 前情提要
---

* 實作的細節不夠清楚 -> <span style="color:red">詳細記錄、整理實作情形</span>
* 某些特定網站的資料無法抓下來 -> <span style="color:red">使用其他的方法嘗試</span>
* 比賽企劃書 -> <span style="color:red">參考學長姐的企劃書、開始撰寫</span>


---

#### 本週進度
---

### Data collection

<span style="color:red">使用**PyMySQL**進行**python**對**MySQL**資料庫的操作</span>


* Python中操作MySQL的模組

* 用在Python3.x中(Python2用mysqldb)

* 完全使用python編寫，避免mysqldb跨系統安裝的麻煩

---

安裝指令如下:

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_090b756a9514c74580a231408b0e6f6a)

---

**MySQL**

> 建立一個叫member的資料庫，裡面有一個table叫people(測試用)

|member|people
| -------- | -------- | 
|![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c250143a063fbae644cb7b15bb635740) |![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5d9df6b8ac596085a5928c13705a4f0c)	
    

**Python**

* 引入模組
``` python
import pymysql 
```
--
* 與資料庫建立連結
``` =python
pymysql.connect(…)
```
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7fe0c7c059cd3314166ea1e6ccc3cf38)

>  host:資料庫服務器地址
>  user:用戶名
>  password:登錄密碼
>  db:參數database別名
>  pymysql.connect()其他參數
>  ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_08b39a352b7d840bc3e9829d702357a1)


--


* 建立游標
> 指標的概念
```=python
cursor = connection.cursor()
```
--

* 創建新資料庫
```=python
cursor.execute(“CREATE DATABASE 資料庫名”)
```
--
* 創建新的表格
```=python
cursor.execute(“CREATE TABLE tablr名(欄位 資料型態)”)
```
--
* 新增資料
> INSERT INTO people(欄位名) VALUES():選擇目標table.欄位和插入的資料
>  records:用來放入要新增的資料
>  cursor.executemany(sql,records):批量執行SQL
(cursor.execute(sql,record):執行單條SQL
>  connection.commit():完成對數據的提交
>  INSERT.update.DELETE等要修改數據的語句要手動執行connection.commit()
```=python
sql = "INSERT INTO people(name,type,phone) VALUES(%s,%s,%s)"
records = [("Steve","cell","0922245672"),("Max","company","0978965345"),("Chang","cell","0958628713")]

cursor.executemany(sql,records)

connection.commit()
```


| 原來的people |刪除後的people |
  | -------- | -------- |
  | ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0e343fcb77135ab28ef42d680256a578)|![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b87c6cbbd41b900434ae25fd3867e440)|

--

* 刪除資料
> DELETE FROM people WHERE MemberID=4:選擇要刪除的目標table跟範圍
> cursor.execute():因為只有一條SQL指令，所以用execute就可以了
```=python
delete_users = "DELETE FROM people WHERE MemberID = 4"
cursor.execute(delete_users)

connection.commit()
```

| 原來的people |刪除後的people |
  | -------- | -------- |
  | ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0e343fcb77135ab28ef42d680256a578)|![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b87c6cbbd41b900434ae25fd3867e440)|

--

* 讀取資料
> SELECT * FROM ‘people’:選擇people table
> cursor.fetchall():獲取所有數據
> cursor.fetchone():獲取單條數據
> cursor.fetchmany(n):獲取前n條數據
> 用for迴圈將數據印出來

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8354ff643339e149f4c9936f0d0622a5)

---

**爬蟲實作**

<span style="color:green">**其他爬蟲資訊還在嘗試，如之前爬不出來的富邦、台新**</span>

(1)嘗試轉換成JSON檔
```python=
from bs4 import BeautifulSoup
import urllib.request as request
import json

src="https://data.taipei/opendata/datalist/apiAccess?scope=resourceAquire&rid=296acfa2-5d93-4706-ad58-e83cc951863c"
with request.urlopen(src) as response:
    data=json.load(response)
    print(data)
  ```
  

(2) 嘗試將轉換出來的JSON轉換成.txt檔案
```python=
import urllib.request as request
import json

src="https://data.taipei/opendata/datalist/apiAccess?scope=resourceAquire&rid=296acfa2-5d93-4706-ad58-e83cc951863c"
with request.urlopen(src) as response:
    data=json.load(response)
#印出公司名稱
clist=data["result"]["results"]
#with open("data.txt", "w", "encoding="utf-8") as file
#若要建立成data.txt檔案
for company in clist:
    print(company["公司名稱"])
    
#file.write(company["公司名稱"]+"\n")
```

(3)嘗試將爬蟲內容回傳LINEBOT
```python=
if event.message.text == "最新電影":
        a=movie()
        line_bot_api.reply_message(event.reply_token,TextSendMessage(text=a))

```
        
(4)嘗試將爬蟲內容回傳LINEBOT(圖文兼備的資訊)
```python=
 news_group=[]    #創一個List
    #將剛剛的三個List加進來
    news_group.append(news_title)
    news_group.append(news_link)
    news_group.append(news_photo)
    #要做為key值的List
    x=['title','link','link2']
    #把兩個做成dictionary
    dictionary = dict(zip(x,news_group))
```


---

### Linebot

* 專案LineBot主程式架構

1. **app.js**為主要的Linebot程式
2. **config.js**為儲存API KEY的程式
3. **nlp.js**為串接olami API的程式(目前還在看官方的document，還沒實作出來)
4. **package.json , package-lock.json** 為套件總覽(可以從裡面看到專案裝了哪些套件)
5. **node_modules/** 是node.js套件的資料夾
6. **.gitignore**是系統檔案，git在更新的時候會忽略ignore檔裡面紀錄的檔案


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_70c8ea7913b5e6d4bd168d81c883f003)

---


#### 解決兩個以上js file互相呼叫的問題

config.js
1. 產生config.js檔，define變數config並將lineBot的API KEY寫進來
    > <span style="color:red">重點是最後的module.exports部分，沒有寫的話會無法從別的地方呼叫</span>
```javascript=
var config = {
	
	channelId: bot的channelID,
	channelSecret: bot的channelSecret,
	channelAccessToken: bot的channelAcessToken 
	checkId: "checked" //檢查用
}
module.exports.config = config;
```
-- 

app.js
1. 把config.js require進來
```javascript=
var getKey = require('./config.js'); 
```

2. 測試是否能呼叫
```javascript=
console.log("config key:"+getKey.config.checkId);
```

3. 產生bot並且在裡面呼叫config.js裡面的金鑰
```javascript=
var bot = linebot({
  channelId: getKey.config.channelId,
  channelSecret: getKey.config.channelSecret,
  channelAccessToken: getKey.config.channelAccessToken 
});
```
--

Terminal
> 看到config key:checked 代表checkID呼叫成功
```shell=
➜  lineBot_test git:(master) ✗ npm start

> bhitter_bot@1.0.0 start /Users/ghjyjjj/Bhitter/lineBot_test
> node .

config key:checked
App now running on port 8080
```


--

Heroku
> 重新部署到heroku上也成功

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a0eec711c169f77d33eacce7be24b606)

---

#### Node.js - lineBot API

**LineBot Object**

以下介紹幾個常用的linebot js語法

* Linebot(config)

    > 創建一個基本的linebot

```javascript=
var bot = linebot({
  channelId: CHANNEL_ID,
  channelSecret: CHANNEL_SECRET,
  channelAccessToken: CHANNEL_ACCESS_TOKEN,
  verify: true // Verify 'X-Line-Signature' header (default=true)
});
```
--

* LineBot.on(eventType, eventHandler)

    > 接收不同的weebhook event

```javascript=
bot.on('message',  function (event) { });
bot.on('follow',   function (event) { });
bot.on('unfollow', function (event) { });
bot.on('join',     function (event) { });
bot.on('leave',    function (event) { });
bot.on('postback', function (event) { });
bot.on('beacon',   function (event) { });
```

---

**Event Object**

* Event.reply(message)
    > message 可以是string, string[], send message object..
    > 並且會從node-fetch module return 一個promise object
 
```javascript=
//reply text message
event.reply('Hello, world').then(function (data) {
  // success
}).catch(function (error) {
  // error
});
```

```javascript=
//return message object
event.reply({ type: 'text', text: 'Hello, world' });
```

```javascript=
//location example
event.reply({
  type: 'location',
  title: 'my location',
  address: '〒150-0002 東京都渋谷区渋谷２丁目２１−１',
  latitude: 35.65910807942215,
  longitude: 139.70372892916203
});
```

* Event.source.Member()
    > 可以直接拿到聊天室所有member的userID
    
* Event.message.content()
    > 可以透過buffer object拿到影音、圖片等等的data
---

### OLAMI NLI

* OSL 通用符號說明:

    ##### 1. “< >”
    >  呼叫/引用 rule、slot、template、grammar 等對象，例如：<rule_you_used>

    ##### 2. “( )”
    > 匹配區域/組（group），例如：我要看(電視|小說) ，將 電視|小說 視為一個組。

    ##### 3. “[ ]”
    > 表示其所包覆內容是可選的（意即可忽略），例如：[幫我]開門，可匹配幫我開門或開門兩種說法。

    ##### 4. “|”
    > 邏輯符號 “或（OR）”，例如：電視|小說 表示電視或小說。

---

* 四大元素：
    ##### Grammar
    > 即語法（說法），是OSL描述的目的對象，同時也是構成語意理解支持的主要元素。
    ##### Rule
    > 用於定義語句片段的匹配規則，語句片段可以是同義詞集合或短語等。
    ##### Slot
    > 可以理解為語意中的變數，用於傳遞、提取訊息。


        擁有五種類型：
        internal 自定義的字串集合，用於描述可列舉的內容，如燈光、亮光
        number 數字型態，如1、2、3
        float 浮點數和分數型態，如1.5、90%
        datetime 時間點型態，如明天下午三點、七月三號
        ext 自定義的字串集合，用於描述不可列舉的內容，如一家公司的所有商品，數量很多且有很多種說法，無法一一列舉。這時需要以驗證來協助建立slot。例如olami中有可以直接使用的驗證“山”，則此slot就可以匹配任何真實存在的山，如阿里山、玉山。驗證也可以自行定義。暪個slot可與四個驗證做連結。
    ##### Template
    > 模板，用於定義可復用的參數化語法片段，經由不同的參數來支持結構相同的不同說法。

        例如一些動詞 “看”、“說”、“想” 都有相同的短語說法：“看看”、“看一看”、“想一想” 等動詞疊式說法。
        例如我們建立如下範例中的template，並命名為“test”只要把 “看”，“想” 作為參數值傳遞進去：

    > [=動詞=]$(動詞)[一]$(動詞)
    > 最前方中括號內的內容為參數，而我們將此參數命名為“動詞”，而後方中括號內的“一”為可出現也可不出現的詞
    > 當我們引用此template時將要帶入的參數用小括號瓜在後方：
    > <test(看)>
    > 則此引用可以匹配：“看看”與“看一看”
    > 

---

另外還有以下兩種元素：

1. Context Grammar 使用於上下文處理
2. Ｍodifier 使用者意圖

--

以下是我們嘗試定義的一些元素：

*  Grammar
    1. 幫查卡
    內容：[<help_me_lookup>]<銀行名>[的][<信用卡>][卡][[的]優惠]
    2. 幫查卡2
內容：[<help_me_lookup>]<銀行名>[的][<信用卡2>][卡][[的]優惠]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b736267b2a658c073deec40d947d4ef6)

        其實這兩個Grammar是一樣的，只是因為每個slot只能與四個驗證做連結，因此只好分成兩個Grammar

--
*  Rule
    1. 銀行名
    內容：中國信託|中信|國泰世華|國泰|玉山銀行|玉山|中華郵政|中華|中郵|台新銀行|台新|花旗銀行|花旗|富邦銀行|富邦
    2. help_me_lookup
    內容：[[請]幫我|我想]查[詢]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_bd345074870ba02597fb8719d6c39713)

--
* Slot
    1. 銀行名
    類型：INTERNAL
    2. 信用卡
    類型：EXT 
    字數限制：1~15字
    驗證：中國信託卡、台新銀行卡、國泰世華卡、富邦銀行卡
    3. 信用卡2
    類型：EXT 
    字數限制：1~15字
    驗證：玉山銀行卡、花旗銀行卡

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ab91c6782e10f6fb81f26a68752f3731)

--

> 驗證內容：
中國信託卡：中國信託的所有卡種
台新銀行卡：台新銀行的所有卡種
國泰世華卡：國泰世華的所有卡種
富邦銀行卡：富邦銀行的所有卡種
玉山銀行卡：玉山銀行的所有卡種
花旗銀行卡：花旗銀行的所有卡種

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_44a0675af48594991db1bf8b104baedc)

--

* 我們的Grammar可以匹配的語句（以中國信託鼎級卡為例）
    附檔nli_test.txt說明

---

### 下週進度

* Data collection
    * 繼續抓取尚未抓取的資料
    * 了解將json寫入mysql
* LineBot
    * 串接Olami API
    * 了解Olami如何在linebot上運行與操作
* Olami
    * 增加grammar 
* 比賽企劃書
    * 繼續進行
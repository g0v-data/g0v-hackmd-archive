# Javascript 

* **直譯式語言**
* **靜態作用域**
* **單執行緒**
* **動態型別的語言**

# Object方法

* `Object.create` **繼承**
* `Object.defineProperty` **修改單一屬性**
* `Object.defineProperties` **修改多項屬性**
* `Object.preventExtensions`  **防止擴充**
* `Object.isExtensible`  **查看是否可擴充**
* `Object.getOwnPropertyDescriptor`  **查看單一屬性**
* `Object.getOwnPropertyDescriptors`  **查看多項屬性**
* `Object.seal`  **封裝**
* `Object.isSealed`  **是否被封裝**
* `Object.freeze`  **凍結**
* `Object.isFrozen`  **是否被凍結**

# Node.js 【Path】

* **抓目錄路徑**： `path.dirname('/xx/yy/zz.js')`  回傳 ==/xx/yy==
* **路徑合併**：`path.join(__dirname,'/xx')`  回傳 ==前後路徑合併==
* **抓檔名**： `path.basename('/xx/yy/zz.js')`  回傳 ==zz.js== 
* **抓副檔名**： `path.extname('/xx/yy/zz.js')`  回傳 ==js== 
* **分析路徑**： `path.parse('/xx/yy/zz.js')`  回傳 ==上述綜合物件==

# Node.js 【NPM】

* `npm -v` ：**觀看 NPM 版本**
* `npm init` ：**新增 package.json**
* `npm install [模組名稱][安裝位置]` ：**安裝 NPM 模組，安裝位置常用屬性如下**：
    1. `-g`  **全域安裝**
    2. `--save`  **安裝模組並寫入 package.json 的 "dependencies"**
    3. `--save-dev`  **安裝模組並寫入 package.json 的 "devDependencies"**
* `npm list` ：**顯示安裝的 NPM 列表**
* `npm uninstall [模組名稱]` ：**刪除專案裡的 NPM**

# Firebase

* **須先載入資料庫設定**
* **初始化**
```javascript
firebase.database() //firebase 全部物件格式，不能陣列內容
```
* **ref()  路徑**
```javascript
firebase.database().ref() //默認根目錄
```
* **set()  新增資料**
```javascript
firebase.database().ref().set()
```
* **once() 顯示**
```javascript
var myNameRef = firebase.database().ref("myName");
myNameRef.once("value", function(snapshot) {
    console.log(snapshot.val())
})
```
* **on()  隨時監聽**
```javascript
var myNameRef = firebase.database().ref("myName");
myNameRef.on("value", function(snapshot) {
    console.log(snapshot.val())
})
```
* **push()  新增資料【物件】**
```javascript
firebase.database().ref().push()
```
* **child()、remove()**
```javascript
var todosRef = firebase.database().ref("todos");
todosRef.child("-ldsjkfdofkdf").remove();
```
* **orderByChild()、forEach()**
```javascript
var peopleRef = firebase.database().ref("people");
peopleRef.orderByChild("old").once("value", function(snapshot) {
    snapshot.forEach(function(item) {
        console.log(item.key);
        console.log(item.val());
    })
})
```
> orderByChild 排序規則  ==null>false>true>數字>字串>物件==
* **startAt()、endAt()、equalTo()**
```javascript
var peopleRef = firebase.database().ref("people");
peopleRef.orderByChild("old").startAt(3500).endAt(4000).once("value", function(snapshot) {
    snapshot.forEach(function(item) {
        console.log(item.val());
    })
})
```
* **limitToFirst()、limitToLast()**
```javascript
var peopleRef = firebase.database().ref("people");
peopleRef.orderByChild("old").startAt(3500).limitToFirst(1).once("value", function(snapshot) {
    snapshot.forEach(function(item) {
        console.log(item.val());
    })
})
```
> limitToFirst  ==由前至後==   limitToLast  ==由後至前==

# Express

* **get() 開啟web**
```javascript
var express = require("express");
var app = express();
var port = 3000;
app.listen(port);
app.get("/", function(req, res) {
    res.send("hello!!");
});
```
* **params 取得指定路徑**
```javascript
app.get("/user/:name", function(req, res) {
    var myName = req.params.name;
    res.send(myName);
});
```
* **query 取得指定路徑**
```javascript
app.get("/user/:name", function(req, res) {
    var myName = req.params.name;
    var limit = req.query.limit; // ?limit
    res.send(myName + limit);
});
```

* **middleware 守門員**
```javascript
app.use(function(req, res, next) {
    switch(res.status()) {
        case 200:
            console.log(驗證過了);
            next();
            break;
        case 404:
            res.send("頁面找不到");
            break;
        case 500:
            res.send("程式碼錯誤");
            break;
        default:
            console.log(res);
    };
});

// 個別使用
var login = function(req, res, next) {
    if(res.status(200)) {
        next();
    } else {
        res.send("你的登入資料有錯");
    };
};
app.get("/", login, function(req,res) {
    res.send("資料對了才進這");
});
```
* **static 增加檔案路徑**
```javascript
app.use(express.static("public"));
app.get("/", function(req, res) {
    res.send('<img src="/images/logo.png">');
});
```




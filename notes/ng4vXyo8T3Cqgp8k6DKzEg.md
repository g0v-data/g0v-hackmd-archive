# JavaScript 練習


項目
- [JSP](#JSP)
  - [1-1] 範例 - 網頁結構概念
  - [1-2] 範例 - script的位子

- [HTML](#HTML)
  - [2-1] 範例-標題標籤
  - [2-2] 範例-無序有序列表
  - [2-3] 範例-超連結
  - [2-4] 範例-表格
  - [2-5] 範例-提交表單
  - [2-6] 範例-div物件

- [CSS](#CSS)
  - [3-1] 範例 - 顏色、背景色、大小
  - [3-2] 範例 - 全物件、註冊CSS

- [script](#script)
  - [4-1] 範例-字串處理
  - [4-2] 範例-FOR迴圈
  - [4-3] 範例-加減乘除


- [公司JSP框架](#公司JSP框架)
  - [5-1] 範例 - 主程式
  - [5-2] 範例 - JSP
  - [5-3] 範例 - XML



# JSP
JavaScript通常以三個區塊為主
HTML : 純網頁物件，常見的輸入欄位、下拉選單、
Css: : 通常是文字顏色、背景等等樣態
script: 處理程式邏輯、基本上就是JAVA搬來這邊寫，公司常見就是doQuery...

請先開啟任一W3 school的網站 整張修改
https://www.w3schools.com/html/tryit.asp?filename=tryhtml_default

## 1-1 範例 - 網頁結構概念
```javascript=
<!DOCTYPE html>  //第一行 既定形式 通常處理編碼
<html>  //對應25行 包起整個網頁
 
<head>   //對應19行 是放與網頁相關的東西 如CSS 或是引用外部連結 想像JAVA的IMPORT或是一些預設的參數，內部會包含script的話會於網頁載入時優先執行
公司常見會把script放在這裡觸發initApp

<link rel="stylesheet" href="https://www.w3schools.com/w3css/4/w3.css">
   <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f0f0f0;
      margin: 0;
      padding: 0;
    }
    </style>
    <script>
    	var currentTime = new Date().toLocaleTimeString();
        alert(currentTime);
    </script>
</head>

<body> //處理純粹網頁物件的部分，如果無誤 實際上可以存成HTML用CHROME開啟
 
    <p id="demo">這是原始文字</p>
</body>
</html>

```

結構如下

```javascript=
<!DOCTYPE html>  
<html>  /
<head> 
    //擺設定
    <style>
        顏色設定
    </style>
    <script>
        JAVA方法
    </script>
</head>

<body> 
     網頁物件
</body>
</html>
```

## 1-2 範例 - script的位子
script執行的位子很重要
如果放在head裡面 則是一開始就會執行如前面例子 他一開始會去拿時間並跳出ALERT

但最常遇到的問題是 如果還沒有產生下方HTML物件就去執行會錯

下面是一個點一下就可以改文字的範例 可以正常執行 等等請把10~16行搬到第五5行執行
會發現直接噴錯，原因是根本還沒有changeText 為ID的物件產生


```javascript=
<!DOCTYPE html>
<html>
<head>
    <title>JavaScript Event Example</title>
</head>
<body>
    <button id="changeText">點我改變文字</button>
    <p id="demo">這是原始文字</p>

    <script>
        // JavaScript 部分
        document.getElementById("changeText").addEventListener("click", function() {
            var demoElement = document.getElementById("demo");
            demoElement.textContent = "文字已變更！";
        });
    </script>
</body>
</html>

```
硬要用的話就要多個等待LOAD完的事件 先參考就好 目的知道順序性
```javascript=
<!DOCTYPE html>
<html>
<head>
    <title>JavaScript Event Example</title>
    <script>
        // 等待 DOMContentLoaded 事件
        document.addEventListener("DOMContentLoaded", function() {
            // 在這裡可以安全地使用 document.getElementById
            document.getElementById("changeText").addEventListener("click", function() {
                var demoElement = document.getElementById("demo");
                demoElement.textContent = "文字已變更！";
            });
        });
    </script>
</head>
<body>
    <button id="changeText">點我改變文字</button>
    <p id="demo">這是原始文字</p>
</body>
</html>

```

# HTML
## 2-1 範例-標題標籤
```javascript= 
<h1>這是一個大標題</h1>
<h2>這是一個中標題</h2>
<h3>這是一個小標題</h3>
```
## 2-2 範例-無序有序列表
無序列表 (Unordered List)，另一個是有序列表 (Ordered List)。
```javascript= 
User
<h3>無序列表</h3>
<ul>
    <li>項目一</li>
    <li>項目二</li>
    <li>項目三</li>
</ul>

<h3>有序列表</h3>
<ol>
    <li>第一個項目</li>
    <li>第二個項目</li>
    <li>第三個項目</li>
</ol>
```
## 2-3 範例-超連結
```javascript= 
<a href="https://www.example.com">前往示範網站</a>

```
## 2-4 範例-表格
```javascript= 
<table border="1">
    <tr>
        <th>姓名</th>
        <th>年齡</th>
    </tr>
    <tr>
        <td>小明</td>
        <td>25</td>
    </tr>
    <tr>
        <td>小華</td>
        <td>30</td>
    </tr>
</table>
```
## 2-5 範例-提交表單
```javascript= 
<form action="/submit" method="post">
    <label for="name">姓名：</label>
    <input type="text" id="name" name="name" required><br>
    
    <label for="email">電子郵件：</label>
    <input type="email" id="email" name="email" required><br>
    
    <button type="submit">提交</button>
</form>
```
## 2-6 範例-div物件
通常是用來幫網頁做格分段 舉例來說 有三個區塊想要紅燈黃燈綠燈

```javascript= 
<!DOCTYPE html>
<html>
<head>
    <style>
        .red {
            background-color: red;
        }
        
        .yellow {
            background-color: yellow;
        }
        
        .green {
            background-color: green;
        }
        
        .box {
            width: 100px;
            height: 100px;
            margin: 10px;
            padding: 10px;
            border: 1px solid black;
        }
    </style>
</head>
<body>
    <div class="box red">紅色的區塊</div>
    <div class="box yellow">黃色的區塊</div>
    <div class="box green">綠色的區塊</div>
</body>
</html>
```


# CSS
屬性太多了 真的沒有背 舉例常用的
## 3-1 範例 - 顏色、背景色、大小

```java 
/* 使用 px 單位指定文字大小 */
font-size: 16px;

/* 使用顏色名稱 */
color: red;

/* 使用十六進位色碼 */
color: #007bff;

/* 使用 RGB 值 */
color: rgb(0, 123, 255);

/* 使用顏色名稱 */
background-color: lightgray;

/* 使用十六進位色碼 */
background-color: #f0f0f0;

/* 使用 RGBA 值，帶有透明度 */
background-color: rgba(255, 0, 0, 0.5);

/* 設定文字粗細 */
font-weight: bold;

/* 設定文字斜體 */
font-style: italic;

/* 設定文字底線 */
text-decoration: underline;

/* 設定文字對齊方式 */
text-align: center;

/* 設定元素邊框 */
border: 1px solid black;

/* 設定元素寬度和高度 */
width: 200px;
height: 100px;

```


## 3-2 範例-註冊CSS
可以去掉button { 拿到一般的button

```javascript=
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" type="text/css" href="styles.css">
  
  <style>
   
  	button { 
  		padding: 10px 20px;
  		background-color: #333;
  		color: #fff;
  		border: none;
  		cursor: pointer;
  		margin: 5px;
	}
	.special-button {
  		background-color: #ff9900;
  		color: #fff;
  		font-weight: bold;
	}

  </style>
</head>
<body>
  <button>普通按鈕</button>
  <button class="special-button">特別按鈕</button>
  <button>普通按鈕2</button>
</body>
</html>
```



# script
script 內可以處理Java部分
目前無法DEMO doQuery 帶看一些常見的處理
## 4-1 範例-字串處理
```javascript= 
<!DOCTYPE html>
<html>
<head>
    <title>JavaScript String Example</title>
    <script>
        // 宣告一個字串變數
        var message = "Hello, World!";

        // 在 DOMContentLoaded 事件中處理字串並顯示結果
        document.addEventListener("DOMContentLoaded", function() {
            var resultElement = document.getElementById("result");
            resultElement.textContent = "原始字串：" + message + "\n轉大寫：" + message.toUpperCase();
        });
    </script>
</head>
<body>
    <p id="result">等待 JavaScript 載入...</p>
</body>
</html>
```
## 4-2 範例-FOR迴圈
```javascript= 
<!DOCTYPE html>
<html>
<head>
    <title>JavaScript For Loop Example</title>
    <script>
        // 在 DOMContentLoaded 事件中使用 for 迴圈計算 1 到 10 的總和
        document.addEventListener("DOMContentLoaded", function() {
            var sum = 0;
            for (var i = 1; i <= 10; i++) {
                sum = sum + i;
            }

            var resultElement = document.getElementById("result");
            resultElement.textContent = "1 到 10 的總和：" + sum;
        });
    </script>
</head>
<body>
    <p id="result">等待 JavaScript 載入...</p>
</body>
</html>
```
## 4-3 範例-加減乘除
```javascript= 
<!DOCTYPE html>
<html>
<head>
    <title>JavaScript Math Operations Example</title>
    <script>
        // 宣告兩個數值變數
        var num1 = 10;
        var num2 = 5;

        // 在 DOMContentLoaded 事件中進行加減乘除操作並顯示結果
        document.addEventListener("DOMContentLoaded", function() {
            var addResult = num1 + num2;
            var subtractResult = num1 - num2;
            var multiplyResult = num1 * num2;
            var divideResult = num1 / num2;

            var resultElement = document.getElementById("result");
            resultElement.textContent = "加法：" + addResult + "\n減法：" + subtractResult + "\n乘法：" + multiplyResult + "\n除法：" + divideResult;
        });
    </script>
</head>
<body>
    <p id="result">等待 JavaScript 載入...</p>
</body>
</html>
```




# 公司JSP框架
為了避免外洩公司資料 以下範例就先不貼圖 之後有空貼去公司gitbook
請到飛來飛去 我的資料夾 FOR IVY 有個jsp的資料夾
裡面有三個檔案 主程式 JSP 和XML 依序放到指定路徑
這三個檔案都是最基本的空殼檔 之後要開發可以拿這個當基底 改掉一些主程式代號即可

## 5-1 範例 - 主程式
公司通常需要start進行權限檢核
initApp 用來抓一些基礎資訊 會叫initApp也是JSP有寫一個對應的FUNCTION
之後請用 右鍵 主程式開發工具 幫你完成所有的主程式規則
## 5-2 範例- JSP
前面為Import 基本上 你如果開發哪個系統 就完全貼其他檔案的前面部分
每個專案有不同的樣態 跟需要Import的東西 所以每個系統的Import都略有不同

一樣可以看見同上 分成style script body三個區塊
可以將程式片段貼在這邊一直練習
請注意 JSP不用重啟SERVER 但要等個一分鐘才會生效
## 5-3 範例-XML
MVC架構 用來跟當JAVA和JSP的溝通橋樑
很難 基本上照抄寫死 路徑不要搞錯即可

```javascript= 
<label for="username">使用者名稱：</label>
<input type="text" id="username" name="username">



<input type="text" id="username" name="username">
```
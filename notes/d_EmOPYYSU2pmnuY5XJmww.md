# SummerCamp2019

**作業放置於workshop**

## 2019 / 06 / 24

### 筆記

SQL大致上版本會落在2008 - 2012

#### Introduction To T-SQL Querying

執行順序會影響別名或設定上的差異

Data Manimpulationg Language(DML)
Data Defintion Language(DDL)
Data Control Language(DCL)

---
**執行 SELECT 查詢順序**
5：SELECT < select list >
1：FROM < table source >
2：WHERE < search condition >
3：GROUP BY < group by list >
4：HAVING < search condition > //Group by裡面的什麼條件
6：ORDER BY < order by list >

**如果是雲端資料庫，一定要建立index**



抓取系統時間可用函數
1. GetDate()
2. SYSDATETIME()
---
---
==04.SQL-3 Select查詢==


不建議直接利用*
SELECT *
FROM Sales.Customers;
1. 必要把所有欄位倒回來
2. 當有join table時，會有相同的欄位名稱，若使用 * 回傳資料會發生問題
---
***DISTINCT：用來消除重複的資料，識別於後面有哪些欄位所決定***

SELECT DISTINCT < column list >
FROM < table or view >

例子：
SELECT DISTINCT country
FROM Sales.Customers
Where country='Mexico';

---

***別名***
- 欄位別名
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6d7c2a6ccfac2630c269a5e0b7cb60eb)

- Table別名 利用AS
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f1d1996706d12264108f48d8c4879c86)

建議：使用第三種，當在SELECT的時候，Table有別名就換上別名。好處為在未來MA的時候，SELECT可能同時join了好幾個Table，如果又突然join了其他Table進入，名稱相同的時候會掛掉。

SELECT SO.cusid, SO.orderdate
FROM Sales.Orders AS SO;


---

***CASE...WHEN...END





---

==SQL-4-Querying Multiple Tables==

***Cartesian Product(笛卡爾乘機)***
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6661abb2b01dd0d301770763d63579d6)


***Join Types***
- Cross
- Inner 取兩個table的交集
- Left(以左邊table為主) / Right / Full(取兩個table聯集的結果)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1dcbdafdaf4159957618ebe24ef47536)

語法：
```sql=
SELECT ...
FROM Table1 INNER JOIN Table2
    ON <on_predicate>
    WHERE <條件>
/* 
join key通常放在on上
篩選的條件才放在Where裡面
*/
```

做join的時候有可能是單一條件，也有可能是多重條件
```sql=
/*Single matching attribute*/

SELECT ...
FROM　Production.Categories AS C
    JOIN Production.Products AS P
        ON C.categoryid = P.categoryid;
        
/*Multiple matching attributes
-> 用AND串接*/

SELECT DISTINCT e.city, e.country
FROM Sales.Customers AS c
JOIN HR.Employees AS e
    ON c.city = e.city AND
    c.country = e.country;
```
---
***Self Joins***
```sql=
SELECT ...
FROM T1 AS t1 JOIN T1 AS t2
ON t1.Col1 = t2.Col2;
```

***實際例子比較***
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3dcd365ca8b0716b8b29b20a61de89c7)



---

==SQL-5 排序即篩選資料==

- **排序 ORDER BY**
```sql=
SELECT orderid, cutid, YEAR(orderdate) AS orderyear
FROM Sales.Orders
ORDER BY orderyear
/*預設的order是由小到大，也可以增加DESC，使得由小到大*/
```

- **篩選 WHERE條件**
```sql=
SELECT orderid, cutid, orderdate
FROM Sales.Orders
WHERE orderdate >= '20170101' && orderdate < '20180101'
```

- **可以利用TOP，來限定只要show出前幾筆資料**

```sql=
SELECT TOP(1) cutid, orderid
FROM Sales.Orders;
```

- **若TOP再外加ＷITH TIES，跟與TOP()某個回傳回來的值相同的，也會一並回傳回來**
```sql=
SELECT TOP(!) WITH TIES cutid, orderid
FROM Sales.Orders
ORDER BY custid;
```
- **可以利用百分比persent來決定，要回傳總共筆數的百分之多少筆的資料**
```sql=
SELECT TOP (10) PERCENT OrderID, CustomerID, OrderDate
FROM Sales.Orders
ORDER BY OrderDate DESC;
```


- **操作NULL：利用IS**
```sql=
SELECT cutid, city, region, country
FROM Sales.Customers
WHERE region IS NOT NULL;

```
- **Sample Code 5-1**
```sql=
SELECT HireDate, FirstName, LastName
FROM HR.Employees
ORDER BY HireDate DESC, LastName ASC;
/*7&8 當HireDate相同施，針對LastName做ASC排序*/
```
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b098997f74a018a9b7287d6042c98774)

- **NEWID()：runtime的時候排序，但不知道依照什麼。每一次結果都不同**

```sql=
SELECT HireDate, FirstName, LastName
FROM HR.Employees
ORDER BY NEWID();

```
- **IN() & NOT IN()**
```sql=
-- Step 6: 找出在 香港或是在西班牙 的客戶
SELECT CustomerID, CompanyName, Country
FROM Sales.Customers
WHERE Country = 'UK' 
	OR Country = 'Spain';
    
    
    
-- Step 7:找出在 香港或是在西班牙 的客戶
SELECT CustomerID, CompanyName, Country
FROM Sales.Customers
WHERE Country IN (N'UK',N'Spain');
/*此方法與單純用OR的結果相同，推薦使用IN*/



-- Step 8: 找出「不在」( 香港及西班牙) 的客戶
-- Use NOT operator with IN to provide an exclusion list
SELECT CustomerID, CompanyName, Country
FROM Sales.Customers
WHERE Country NOT IN (N'UK',N'Spain');
```

- **BETWEEN：做>= <= & < >**
```sql=
-- Step 9: Use WHERE to filter results
--取出2007年的資料
SELECT OrderID, CustomerID, OrderDate
FROM Sales.Orders
WHERE OrderDate > '2006/12/31' AND OrderDate < '2008-01-01';

-- Step 10: Use WHERE to filter results
-- Use BETWEEN operator to search within a range of dates
-- 包含2006/12/31 到 2008/1/1
SELECT OrderID, CustomerID, OrderDate
FROM Sales.Orders
WHERE OrderDate BETWEEN '20061231' AND '20080101';
```
- **SET ROWCOUNT**-
```sql=
SET ROWCOUNT 10
/*一旦設定之後，就都輸出10筆資料*/

/*若要回復的話，就把ROWCOUNT設成0*/
SET ROWCOUNT 0
```

- **回傳是否要包含NULL**
```sql=
--  Step 2: Region including NULL
SELECT CustomerID, City, Region, Country
FROM Sales.Customers
ORDER BY Region;

--  Step 3: Handling NULLs
-- 不包含Region為NULL的資料
SELECT CustomerID, City, Region, Country
FROM Sales.Customers
WHERE Region <> N'SP';

/*要判斷是否為NULL，也可以利用以下寫法*/

SELECT CustomerID, City, Region, Country
FROM Sales.Customers
WHERE ISNull(Region, '') = '';
```

### Workshop


- 在Visual Studio安裝
    - Newtonsoft.Json
    截圖：![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_caca6c668d3c7eb9ef86d517f9e56561)

    - Sonarlint
    截圖：![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6c32f686894bd1245702f50be8604fed)

- SSMS安裝
    - Sqlcomplete
    - https://www.devart.com/dbforge/sql/sqlcomplete/download.html
- 





---

## 2019 / 06 / 25

==SQL-6 Grouping and Aggregating Data==

- **Aggregate functions 計算平均值**
沒有特別指定的話，NULL都會被避掉，除了COUNT( * )





==SQL-7 子查詢==

依據回傳值是一個還是多個，寫法不同。
```sql=
SELECT orderid, productid, unitprice, qty
FROM Sales.OrderDetails
WHERE orderid = (
    SELECT MAX(orderid) AS lastorder FROM Sales.Orders);
```







==SQL-10 Window Ranking, Offset==

- OVER關鍵字

- Defining Window Function
    - Rank()
```sql=
SELECT productid, productname,unitprice,
    RANK() OVER(ORDER BY unitprice DESC)
    /*針對unitprice遞減做排名)
```

- OFFSET
- 



## 2019 / 06 / 26

==Course 2 / SQL-9 / SET==

- UNION Operator：慢 - 去除重複
- UNION ALL Operator：快 - 保留重複
```sql=
SELECT query_1
SET operator
SELECT query_2
ORDER BY <sort_list>
--ORDER BY 不能把它放在兩個SELECT之間
```




==Course3 / FrontEnd / jQuery==

以操縱網頁物件DOM為核心，沒有對JavaScript原本語言進行修改


```htmlmixed=
<head>

</head>
<body>
    <h1 class="demo-text">
    </h1>
    
</body>
```


- **This的用法**
```javascript=
$(".demo-input").on("input", function(){
    $(".demo-text").text(($this).val())
})
```


==Course3 / FrontEnd / KendoUI==
為一個UI的Framework物件，裡面有很多現成的小元件，可以提供我們直接存取使用

要先引入兩個CSS檔案，以及一個Script檔案(注意要放在<body></body>的下方

```htmlmixed=

<!DOCTYPE html>
<html>
<head>
    <link real="stylesheet" href="css/kendo.common-material.min.css">
    <linke real="stylesheet" href="css/kendo.material.min.css">
</head>

<body>
</body>

<script src="js/kendo.all.min.js"></script>
</html>




```



## 2019 / 06 / 27

### kendo
```javascript=
grid.getItem($(option.currentTarget).closest("tr"));
```

```javascript=
function deleteBook(options){
  
    var grid = $("#book_grid").data("kendoGrid"); 
    var dataItem = grid.dataItem($(options.currentTarget).closest("tr"));
    console.log(dataItem.BookId);
    
    var localData = JSON.parse(localStorage["bookData"]);
    console.log("ready delete");
    for(var i = 0 ; i < localData.length ; i++)
    {
        console.log(options.BookId);
        if(localData[i].BookId == dataItem.BookId)
        {
            console.log("find!");
            localData.splice(i, 1);
            break;
        }
    }

    localStorage["bookData"] = JSON.stringify(localData);
    location.reload();
    
};
```
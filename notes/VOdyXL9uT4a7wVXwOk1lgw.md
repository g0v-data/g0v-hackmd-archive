# MySQL

4/24 資料表/資料庫 增刪改查

> `mysql -uroot -p`
> 

用 `root` 帳號，連接到 MySQL 資料庫伺服器，並要求輸入密碼

![](https://g0v.hackmd.io/_uploads/BkeuekMxxg.png)


> `create database db1 charset utf8;`
> 

`CREATE DATABASE db1`：建立一個名字叫 `db1` 的資料庫。

`(DEFAULT) CHARSET utf8`：設定這個資料庫預設使用 `utf8` 編碼（支援中文及多國語言）

![](https://g0v.hackmd.io/_uploads/S1M9gkzlee.png)

> `show databases;`
> 

列出目前伺服器上所有資料庫

![](https://g0v.hackmd.io/_uploads/HJOjgJGlgl.png)

> `drop database db1;`
> 

**刪除** 資料庫 `db1`，包含裡面**所有的資料表和資料，一併全部清除**

![](https://g0v.hackmd.io/_uploads/Sye0ybkMxgl.png)

> `show databases;`
> 

**列出**目前伺服器上所有資料庫(資料庫`db1`剛剛被刪掉了)

![](https://g0v.hackmd.io/_uploads/rkJ--kzxlx.png)

> `create database db1 charset utf8;`
> 

再**建立**一次資料庫`db1`

![](https://g0v.hackmd.io/_uploads/ryEMZJzeee.png)



> `use db1;`
> 

**「切換」到名為 `db1` 的資料庫來操作。**
![](https://g0v.hackmd.io/_uploads/B1lNbJGxge.png)

> `create table student_t(
id int not null,
name varchar(10) not null,
age tinyint
);`
> 

建立一張名為 `student_t` 的資料表，表格有三個欄位。

| 欄位名 | 資料型別 | 限制 | 說明 |
| --- | --- | --- | --- |
| `id` | `INT` | `NOT NULL` | 學生編號，必填 |
| `name` | `VARCHAR(10)` | `NOT NULL` | 學生姓名，最多 10 字元，必填 |
| `age` | `TINYINT` | *(可為空)* | 年齡，0–255 |

![](https://g0v.hackmd.io/_uploads/rJxO1EJMllx.png)

> `show tables;`
> 


**列出目前所使用的資料庫（Database）裡的所有資料表（Tables）**

![](https://g0v.hackmd.io/_uploads/Skl4VyMgeg.png)

> `desc student_t;`
> 

顯示這張表 `student_t` 的欄位定義與資料型別

![](https://g0v.hackmd.io/_uploads/r1PEV1Melg.png)

> `show create table student_t;`
> 

顯示建立 `student_t` 資料表時，MySQL 實際使用的完整 `CREATE TABLE` 語法。

![](https://g0v.hackmd.io/_uploads/B1nNEJMlgl.png)

> `alter table student_t rename t1;`
> 

**把資料表 `student_t` 改名為 `t1`**

![](https://g0v.hackmd.io/_uploads/BkRuEkfxxx.png)

> `show tables;`
> 

列出**目前使用中的資料庫**裡的**所有資料表名稱**

![](https://g0v.hackmd.io/_uploads/SJ_KN1Gxgx.png)

> `select * from t1;`
> 

查詢 `t1` 資料表中的所有**資料列與欄位**

![](https://g0v.hackmd.io/_uploads/SyJ5Eyfgll.png)

> `desc t1;`
> 

顯示資料表 `t1` 的**欄位結構**

![](https://g0v.hackmd.io/_uploads/rJD5Nyzlee.png)

> `select database();`
> 

顯示目前「正在使用」的資料庫名稱

![](https://g0v.hackmd.io/_uploads/By09E1felg.png)

5/1

> 
>
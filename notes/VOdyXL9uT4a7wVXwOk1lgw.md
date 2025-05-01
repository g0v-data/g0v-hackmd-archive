# MySQL

4/24 資料表/資料庫 增刪改查

> `mysql -uroot -p`
> 

用 `root` 帳號，連接到 MySQL 資料庫伺服器，並要求輸入密碼

![image.png](attachment:397a82bb-7663-40b7-8606-e11f3528469a:61d96fae-f2a2-426e-9883-02d013440e6f.png)
> `create database db1 charset utf8;`
> 

`CREATE DATABASE db1`：建立一個名字叫 `db1` 的資料庫。

`(DEFAULT) CHARSET utf8`：設定這個資料庫預設使用 `utf8` 編碼（支援中文及多國語言）

![image.png](attachment:046c4953-548d-483b-9f07-dfeb01c418de:5e4f7de3-9f3f-4ab9-a69a-4be4a298315e.png)

> `show databases;`
> 

列出目前伺服器上所有資料庫

![image.png](attachment:6654ba77-d7cc-4536-a1f0-e00af9fbca96:c6fd0c44-1348-4d75-962b-1f53c288c2d7.png)

> `drop database db1;`
> 

**刪除** 資料庫 `db1`，包含裡面**所有的資料表和資料，一併全部清除**

![image.png](attachment:2a621656-068e-445c-beaf-5b313d929e4c:0e2ed753-950f-46a2-a596-b982deb92f86.png)

> `show databases;`
> 

**列出**目前伺服器上所有資料庫(資料庫`db1`剛剛被刪掉了)

![image.png](attachment:2d0de8d5-8ba7-4f7b-b262-d03cc939ce21:28ee1348-e9a9-4749-afd2-5e69f1ee970b.png)

> `create database db1 charset utf8;`
> 

再**建立**一次資料庫`db1`

![image.png](attachment:038c9a9b-d2a4-407a-9189-1f45e6d69d7d:4062ce98-03cc-4641-81f8-7bf5ed481827.png)

> `use db1;`
> 

**「切換」到名為 `db1` 的資料庫來操作。**

![image.png](attachment:1eb835c9-924c-414d-b9ae-af7b9446f249:92b734e6-df0b-4baf-b486-f74d767e9f3c.png)

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

![image.png](attachment:ad0ff3df-0ed3-4532-a0bd-a2676d5f6669:2f2e42bb-4b7d-4138-977a-f9641dfed9e1.png)

> `show tables;`
> 

**列出目前所使用的資料庫（Database）裡的所有資料表（Tables）**

![image.png](attachment:8cd5fb73-19c0-4a00-8463-15f3eaa1ff68:6e8ad45e-4b1b-4a9b-81b3-b02e1078916c.png)

> `desc student_t;`
> 

顯示這張表 `student_t` 的欄位定義與資料型別

![image.png](attachment:cfa56159-1bea-492b-979f-0be56d5d05b4:ec9a9c58-0b95-420c-bbac-47d089e69956.png)

> `show create table student_t;`
> 

顯示建立 `student_t` 資料表時，MySQL 實際使用的完整 `CREATE TABLE` 語法。

![image.png](attachment:0d99fdbe-7e03-41c4-96ed-4f648f3fb9e3:b5adf4fa-2612-4e0b-aa1a-ae8f2d950818.png)

> `alter table student_t rename t1;`
> 

**把資料表 `student_t` 改名為 `t1`**

![image.png](attachment:46824c60-e2c8-41c6-8ee1-5ca959f003bf:3bf89dbe-a2f4-4d93-80de-86318193ff10.png)

> `show tables;`
> 

列出**目前使用中的資料庫**裡的**所有資料表名稱**

![image.png](attachment:d01f16a2-2f54-429f-9931-5c03636fe38a:be0d3768-d668-4427-978a-9d994df21e70.png)

> `select * from t1;`
> 

查詢 `t1` 資料表中的所有**資料列與欄位**

![image.png](attachment:33b207a4-b394-442e-bf77-41b8ebebf666:0d5b3564-5e21-4ff7-bc2b-a9a469fd5844.png)

> `desc t1;`
> 

顯示資料表 `t1` 的**欄位結構**

![image.png](attachment:72cce7c1-54e2-460c-8592-5aaac92d5b59:93e349ff-0cfb-4a15-84d1-891e243e0140.png)

> `select database();`
> 

顯示目前「正在使用」的資料庫名稱

![image.png](attachment:0a9e96ff-c5a3-46b4-be43-14922eeddb95:7da6a00f-600a-4050-a8cc-103cfc9b9760.png)

5/1

> 
>
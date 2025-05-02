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

---


## 5/1 表之間的關係(一對一、一對多、多對多)

### 如果移除外鍵約束是否會造成兩張表的查詢差異?為什麼?

不會，外鍵的約束只是為了保留資料的完整性而已

### 如果沒有外鍵的約束會怎麼樣?

他會讓我刪任何我想刪的資料，即使其他資料表中仍有依賴它的資料

然後那個資料會變**孤兒資料**

> `CREATE TABLE customer (
id INT PRIMARY KEY auto_increment,
name VARCHAR(20),
phone char(10) not null
);`
> 

> `CREATE TABLE student (
id INT PRIMARY KEY auto_increment,
class_name VARCHAR(20) not null,
customer_id int unique,
foreign key(customer_id) references customer(id)
on delete cascade
on update cascade
);`
> 
![](https://g0v.hackmd.io/_uploads/SJ_YObGxge.png)

> `show tables;`
> 

![](https://g0v.hackmd.io/_uploads/SJr9dbzexx.png)


> - 插入 customer 表的四筆資料
`INSERT INTO customer (name, phone) VALUES
('張小明', '0912345678'),
('李小華', '0923456789'),
('王大雄', '0934567890'),
('林美玲', '0945678901');`
> 

> - 插入 student 表的四筆資料
`INSERT INTO student (class_name, customer_id) VALUES
('資訊工程系', 1),
('電機工程系', 2),
('企業管理系', 3),
('外國語文系', 4);`
> 

![](https://g0v.hackmd.io/_uploads/rklksd-fgee.png)


> select * from customer;
>
 

> select * from student;
> 
![](https://g0v.hackmd.io/_uploads/B1FodZfegx.png)



> select a.name, a.phone, b.class_name from customer a, student b where a.id=b.customer_id;
> 

![](https://g0v.hackmd.io/_uploads/Skegh_WMele.png)


> `CREATE TABLE Publishers (
publisher_id INT PRIMARY KEY,
publisher_name VARCHAR(100)
);`
> 

> `CREATE TABLE Books (
book_id INT PRIMARY KEY,
publisher_id INT,
FOREIGN KEY (publisher_id) REFERENCES Publishers(publisher_id)
on delete cascade
on update cascade
);`
> 

![image.png](attachment:578bf132-b330-4e76-a84a-93020bffa70b:c89ca6d2-f499-4177-b8a8-8e30bb3542c6.png)

> - 插入 Publishers 表的兩筆資料
`INSERT INTO Publishers (publisher_id, publisher_name) VALUES
(1, '天下文化'),
(2, '遠流出版');`
> 

> - 插入 Books 表的四筆資料
`INSERT INTO Books (book_id, publisher_id) VALUES
(101, 1),
(102, 1),
(103, 2),
(104, 2);`
> 

![image.png](attachment:fef912bc-fb84-43ea-bf08-2345b722b9d3:7fb869fb-deb4-4226-b53f-d44b1085624e.png)


    
> `CREATE TABLE author (
    id INT PRIMARY KEY auto_increment,
    name VARCHAR(20)
    );`
    
    
> `CREATE TABLE book (
    id INT PRIMARY KEY auto_increment,
    name VARCHAR(20)
    );`

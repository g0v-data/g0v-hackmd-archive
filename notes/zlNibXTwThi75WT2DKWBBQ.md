# MySQL
## 基礎語法
```
#創建Table
CREATE DATABASE `database`;
#展示有哪些Table
SHOW DATABASE;
#刪除Table
DROP DATABASE `database`;
#使用Table
USE `database`;
```
## 資料結構
```
INT  --整數
DECIMAL(m, n)  --有小數點的數 m是位數 n其中小數點佔幾位
CHAR  --字節
VARCHAR(n)  --字串
BLOB  --(Binary Large Object)圖片 影片 檔案
DATE   --'YYYY-MM-DD'日期
TIMESTAMP  --'YYYY-MM-DD'紀錄時間
```
## 表格創建
```
CREATE TABLE `database`(
    `id` INT PRIMARY KEY,
    `name` CHAR(15)
);

#展示表格
DESCRIBE `student`;
#刪除表格
DROP TBLE `student`;
#新增欄位，DECIMAL是位數的設定
ALTER TABLE `student` ADD `gpa` DECIMAL(3,2);
#刪除欄位
ALTER TABLE `student` DROP COLUMN `gpa`;

```
## 資料輸入與查詢
```
INSERT INTO `student` VALUE(1, `roy`, 2.3);

#搜尋表格內所有的資料
SELECT * FROM `student;

#依照特定順序填入資料
INSERT INTO `student`(`gpa`, `id`, `name`) VALUE(2.3, 1, `roy`);
```
## Constraints(限制)
```
NOT NULL 不能為空值
UNIQUE 唯一值
DEFAULT 預設值
AUTO_INCREMENT 自動生成流水號
```
## 修改資料
```
#修改資料 => 更新student表單，讓name欄位=Roy，在name欄位是roy的情況下
UPDATE `student`
SET `name` = `Roy`
WHERE name` = `roy`;
*可以用AND和OR來增加多條件的判斷

#刪除資料
DELETE FROM `student`
WHERE `id` = `2`;
*也運用>,<,>=,<=,=,<>(不等於) 設立條件
```
## 取得資料
```
#選取name和id 2個欄位，從student表單中，並依照先id再score來排序，按照降階(ASC)或升階(DESC)，僅限制3筆
SELECT `name`, `id` 
FROM `student`
ORDER BY `id`,`score` DESC(ASC)
LIMIT 3;
*也可以運用WHERE增加篩選條件，WHERE `name` IN(`ben`,`ken`)代表篩選名字是ben和ken的資料
```
## 公司資料庫的創建
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_75dd03b427c92eed5eb73b95234fce08.png)
```
*在創建上，會由於其他表還沒創立，Foreign Key會需要再補上
#Employee
CREATE TABLE `employee`(
    `emp_id` INT PRIMARY KEY,
    `name` VARCHAR(20),
    `birth_date` DATE,
    `sex` VARCHAR(1),
    `salary` INT,
    `branch` INT,
    `sup_id` INT
);

#Branch
CREATE TABLE `branch`(
    `branch_id` INT PRIMARY KEY,
    `branch_name` VARCHAR(20),
    `manager_id` INT,
    FOREIGN KEY (`manager_id`) REFERENCES `employee`(`emp_id`) ON DELETE SET NULL
);

#補上Employee的FOREIGN KEY 
ALTER TABLE `employee`
ADD FOREIGN KEY (`branch_id`) 
REFERENCES `branch`(`branch_id`) 
ON DELETE SET NULL;

ALTER TABLE `employee`
ADD FOREIGN KEY (`sup_id`) 
REFERENCES `employee`(`emp_id`) 
ON DELETE SET NULL;

#Clint
CREATE TABLE `clint`(
    `clint_id` INT PRIMARY KEY,
    `clint_name` VARCHAR(20),
    `phone` VARCHAR(20)
);

#Works_With
CREATE TABLE `works_with`(
    `emp_id` INT,
    `clint_id` INT,
    `total_sales` INT,
    PRIMARY KEY(`emp_id`, `clint_id`),
    FOREIGN KEY (`emp_id`) REFERENCES `employee`(`emp_id`) ON DELETE SET NULL,
    PRIMARY KEY(`emp_id`, `clint_id`),
    FOREIGN KEY (`client_id`) REFERENCES `client`(`client_id`) ON DELETE SET NULL
);

#insert data
*如果有用FOREIGN KEY連起來的值為空，則可能無法建立

#insert branch data
INSERT INTO `branch` VALUE (1, '研發', NULL);
INSERT INTO `branch` VALUE (2, '行政', NULL);
INSERT INTO `branch` VALUE (3, '資訊', NULL);

#insert employee data
INSERT INTO `employee`
(emp_id, name, birth_date, sex, salary, branch, sup_id)
VALUES
(206,'小黃','1998-10-08','F',50000,1,NULL),
(207,'小綠','1923-11-20','M',29000,2,206),
(206,'小黑','1987-03-06','F',35000,3,206),
(206,'小白','1945-04-06','M',39000,3,207),
(206,'小藍','1999-01-01','F',84000,1,207);

#將branch原本因為FOREIGN KEY而輸入NULL的值，改回來
UPDATE `branch`
SET `manager_id` = CASE id
    WHEN 1 THEN `206`
    WHEN 2 THEN `207`
    WHEN 3 THEN `208`
END
WHERE id IN(1,2,3);

#insert client data
INSERT INTO `client`
(client_id, client_name, phone)
VALUES
(400, '阿狗', '254354335'),
(401, '阿貓', '903857294'),
(402, '旺來', '239874917'),
(403, '露西', '109380391'),
(404, '艾瑞克', '134081084');

#insert sales data
INSERT INTO `work_withs`
(emp_id, client_id, total_sales)
VALUES
(206, '400', '70000'),
(207, '401', '24000'),
(208, '402', '9800'),
(208, '403', '24000'),
(210, '404', '87940');
```
## 取得公司資料
```
1.取得所有員工資料
SELECT * FROM `employee`;
2.取得所有客戶資料
SELECT * FROM `client`;
3.按薪水低到高取得員工資料
SELECT * FROM `employee`
ORDER BY `salary` ASC;
4.取得薪水前3高的員工
SELECT * FROM `employee`
ORDER BY `salary` DESC
LIMIT 3;
5.取得所有員工的名字
SELECT name FROM `employee`;
*若在SELECT後加上DISTINCT可以輸出非重複項
```
## Aggregate Function(聚合函數)
```
1.取得員工人數
2.取得所有生於1930年後的女性員工
3.取得所有員工薪水的總和
4.取得薪水最高的員工
5.取得薪水最低的員工
```

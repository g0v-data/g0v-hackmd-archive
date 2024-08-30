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
    `branch` INT,
    `sup_id` INT
);

```


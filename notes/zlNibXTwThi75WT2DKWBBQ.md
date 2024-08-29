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
#新增欄位
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
INSERT INTO `student`(`gpa`. `id`, `name`) VALUE(2.3, 1, `roy`);
```
## Constraints
```
NOT NULL 不能為空值
UNIQUE 唯一值
DEFAULT 預設值
AUTO_INCREMENT 自動生成流水號
```
## 修改資料
```
UPDATE `student`
SET `name` = `Roy`
WHERE name` = `roy`;

```



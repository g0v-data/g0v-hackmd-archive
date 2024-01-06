# postgresql
## 1. trigger
    在執行insert、update、delete語法之前(後)before(after)時觸動
    建立範例 :    
``` postgresql
CREATE TRIGGER <<trigger_name>>
{BEFORE | AFTER} {UPDATE | INSERT | DELETE}
ON <<table_name>>
FOR EACH ROW
WHEN <<條件>>
EXECUTE {FUNCTION | PROCEDURE} <<procedure_function>>();
```
* UPDATE 可以增加欄位條件 OF <<column_name>> 於特定欄位異動的時候, 進行相關處理

---
## 2. stored procedure 

``` postgresql

```

#### 相關參數:
- NEW : 於insert/update時, 傳遞近來的資料, 於delete時會是null
- OLD : 於update/delete時, 原始資料, 於insert時會是null
- TG_NAME : 
- TG_WHEN : 判斷是觸發到'before','after'
- TG_LEVEL : 判斷是觸發到'STATEMENT'還是'ROW'
- TG_OP : 判斷是觸發到'insert','update','delete'
- TG_RELID :
- TB_TABLE_NAME : 被觸發的資料表
- TG_TABLE_SCHEMA :
- TG_NARGS :
- TG_ARGV :

---
## 3. foregin key

---
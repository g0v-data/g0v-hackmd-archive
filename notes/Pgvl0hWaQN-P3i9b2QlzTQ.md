# 資料庫系統 Database Systems
## Database Systems(Database Server)
### 1.由DBMS+Database(Datas)組成
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_45c724c133ce03ddaa0b98408ddc6ba6.png)
### 2.透過DBMS進行Database的控管
使用 **SQL(結構化查詢語言)** 
ex:
外部使用者存取資料，藉由DBMS向DataBase進行搜索，找到對應資料後以二維表格形式進行呈現

**優點:**
1. 控制重複性
2. 限制未受權的存取
3. 提供程式物件永久的儲存空間


### 資料庫(Database;DB)
1. 相關資料之集合
2. 以系統化方式儲存，減少資料重複性
3. 由DBMS來管理

### 資料庫管理系統(Database Management System;DBMS)
1. 為一群程式之集合
2. 進行資料庫系統的定義(Defining)、建構(Constructing)、操作(Manipulating)與共享(Sharing)

### Database Users
* 資料庫管理師(Database Administrators ;DBA) 
1. 負責實作部分
2. 定義、建立、維護DB
* 資料庫設計師 (Database Designers;DBD) 
1.  負責分析、設計部分
2.  根據需求產生View
* 終端使用者(End Users)
* 軟體工程師(Software Engineers;SE)
### 觀點 View
為實際存在的資料庫表格，應使用者需求，而生成之關聯表格，為一虛擬表格
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8d322ba42f39e3d7ceb5cb5dbac1749b.png)
### 中繼資料 Meta-data
用來**描述資料**的資料
* 表頭資料
* 資料型態、儲存格式
* 資料間的關係、限制
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0ac31ebdbd1fb289372dc0b27c8f347d.png)
--->資料庫系統具有自我描述性


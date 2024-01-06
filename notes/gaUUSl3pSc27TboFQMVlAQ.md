# MS SQL資料異動擷取CDC
```
--對資料庫
sys.sp_cdc_enable_db
--對表
exec sp_cdc_enable_table
	@source_schema = 'dbo',
	@source_name = 'TableName',
	@role_name = 'cdc_admin'
```
查詢CT異動表
```
select * from [cdc].[dbo_Shippers_CT]　where __$start_lsn >= 0x0000002A00000610000B
```
服務需要開啟才有異動擷取功能
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_49cf3ee85cad035dae8c2eeabae253a4.png)

```

USE AGVC_ASE_K21  
GO
--DB啟動CDC
EXECUTE sys.sp_cdc_enable_db;
DB停用CDC
EXECUTE sys.sp_cdc_disable_db;
GO

--Table啟動CDC
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'ACMD', 
@role_name     = N'cdc_admin'
--Table停用CDC
EXEC sys.sp_cdc_disable_table  
@source_schema = N'dbo',  
@source_name   = N'ACMD',  
@capture_instance = N'dbo_ACMD'  
GO  
--查看占用容量
dbcc sqlperf(logspace)

SELECT name,is_tracked_by_cdc FROM sys.tables WHERE is_tracked_by_cdc = 1
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_78e7e46b97fb5960f131211c62dd905e.png)

```
EXECUTE sys.sp_cdc_enable_db;
select is_cdc_enabled from sys.databases where name = 'AGVC_ASE_K21'
SELECT name,is_tracked_by_cdc FROM sys.tables WHERE is_tracked_by_cdc = 1
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_96d42a04685864a766e5b022eec12bec.png)

修改CDC紀錄時間 預設3天 24*60*3 單位分鐘
```
execute sys.sp_cdc_change_job
	@job_type = N'cleanup',
	@retention = 86400;
exec sys.sp_cdc_help_jobs;

dbcc sqlperf(logspace);
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2d9875703b861ee127d33fd3ed22fa0d.png)




sys.sp_cdc_help_jobs
報告目前資料庫中所有異動資料擷取清除或擷取作業的相關資訊。
https://docs.microsoft.com/zh-tw/sql/relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql?view=sql-server-ver15
cdc.fn_cdc_get_all_changes_ < capture_instance >
針對在指定之記錄序號 (LSN) 範圍內套用至來源資料表的每個變更，各傳回一個資料列。
https://docs.microsoft.com/zh-tw/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql?view=sql-server-ver15
dbo.cdc_jobs
儲存擷取和清除作業的異動資料擷取組態參數。 此資料表儲存在 msdb 中。
https://docs.microsoft.com/zh-tw/sql/relational-databases/system-tables/dbo-cdc-jobs-transact-sql?view=sql-server-ver15
sys.sp_cdc_change_job
修改目前資料庫中異動資料擷取清除或擷取作業的組態。 若要查看目前的作業設定，請查詢 dbo.cdc_jobs 資料表，或使用 sp_cdc_help_jobs。
https://docs.microsoft.com/zh-tw/sql/relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql?view=sql-server-ver15
DBCC SQLPERF
為所有資料庫提供交易記錄空間使用量的統計資料。
https://docs.microsoft.com/zh-tw/sql/t-sql/database-console-commands/dbcc-sqlperf-transact-sql?view=sql-server-ver15
追蹤資料變更2016
https://docs.microsoft.com/zh-tw/sql/relational-databases/track-changes/track-data-changes-sql-server?view=sql-server-ver15
啟用和停用異動資料擷取2019
https://docs.microsoft.com/zh-tw/sql/relational-databases/track-changes/enable-and-disable-change-data-capture-sql-server?view=sql-server-ver15
關於異動資料擷取2019
https://docs.microsoft.com/zh-tw/sql/relational-databases/track-changes/about-change-data-capture-sql-server?view=sql-server-ver15

版本注意事項
2008開始才支援CDC
https://blog.yowko.com/sql-server-cdc-change-data-capture/
https://zh.wikipedia.org/wiki/Microsoft_SQL_Server
https://zh.wikipedia.org/wiki/SQL_Server_Express



參考
https://docs.microsoft.com/zh-tw/sql/relational-databases/track-changes/enable-and-disable-change-data-capture-sql-server?view=sql-server-ver15
https://dotblogs.com.tw/jamesfu/2016/01/05/CDC
http://vito-note.blogspot.com/2013/12/data-flow-3-cdc.html

https://blog.csdn.net/kk185800961/article/details/45749333
https://blog.yowko.com/sql-server-cdc-change-data-capture/
# MS SQL CDC函數

```
USE AGVC_ASE_K21  
GO
----DB啟動CDC
EXECUTE sys.sp_cdc_enable_db;
----DB停用CDC
--EXECUTE sys.sp_cdc_disable_db;
GO
```
```
----Table啟動CDC
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',
@source_name   = N'ACMD',--TableName
@role_name     = N'cdc_admin'
----Table停用CDC
--EXEC sys.sp_cdc_disable_table  
--@source_schema = N'dbo',
--@source_name   = N'ACMD',--TableName
--@capture_instance = N'dbo_ACMD'  
--GO  
```
```
--顯示所有資料庫的記錄檔空間資訊
DBCC SQLPERF(LOGSPACE);
GO
```
```
--查看那些表啟動CDC功能
SELECT name,is_tracked_by_cdc FROM sys.tables WHERE is_tracked_by_cdc = 1
```
```
取得第一筆進CTC的資料
declare @from binary(10) ;
declare @end binary(10);
declare @next binary(10);

set @from = sys.fn_cdc_get_min_lsn('dbo_ACMD')
set @end = sys.fn_cdc_get_max_lsn()
set @next = sys.fn_cdc_increment_lsn(from)--根據指定的記錄序號 (LSN)，傳回序列中的下一個 LSN。

select @from,@end

select TOP 1*
from [cdc].[fn_cdc_get_all_changes_dbo_ACMD]( @from , @end ,'all' )

```
```
使用時間區段找CDC
--DECLARE @from binary(10), @end binary(10);
--DECLARE @begin_time datetime2(7),@end_time datetime2(7);
--SET @begin_time = convert(datetime2, '2021-05-13 06:02:21.1762718');--
--SET @end_time = convert(datetime2, '2021-05-13 12:02:21.1762718');--
--SET @from = sys.fn_cdc_map_time_to_lsn('smallest greater than or equal', @begin_time);
--SET @end = sys.fn_cdc_map_time_to_lsn('largest less than or equal', @end_time);
--SELECT * FROM cdc.fn_cdc_get_all_changes_dbo_ACMD (@from, @end, 'all')
--SELECT * FROM cdc.fn_cdc_get_all_changes_dbo_ACMD (@from, @end, 'all update old');
```
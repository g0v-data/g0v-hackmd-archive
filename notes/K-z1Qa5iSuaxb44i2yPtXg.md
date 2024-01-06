# MSSQL資料庫從Express版升級至Developer時開啟CDC時SQL Server Agent無法開啟

1. 
SQL Server Agent旁多了已停用Agent XPs字樣，且無法啟動
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c782868778384693aeaeb3faedbd0e14.png)

使用以下T-SQL CMD設定:

EXECUTE sp_configure 'show advanced options', 1
RECONFIGURE WITH OVERRIDE
GO

EXECUTE sp_configure 'Agent XPs', 1
RECONFIGURE WITH OVERRIDE
GO

EXECUTE sp_configure 'show advanced options', 0
RECONFIGURE WITH OVERRIDE
GO

2. 
登入SQL Server Configuration Manager，在SQL Server Aagent屬性裡面，登入選項選擇“本賬戶”，輸入系統管理員的使用者名稱和密碼。儲存配置。
重新啟動


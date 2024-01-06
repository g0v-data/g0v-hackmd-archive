# MSSQL 紀錄: 關於已停用Agent XPs
參考:https://hub.docker.com/r/microsoft/mssql-server-windows-developer/
在docker容器內測試ms-sql時發現問題:
發現SQL Server Agent旁多了已停用Agent XPs字樣，且無法啟動，參考大神後:https://dotblogs.com.tw/darren.net/2010/07/22/16710



用以下T-SQL CMD設定:

EXECUTE sp_configure 'show advanced options', 1
RECONFIGURE WITH OVERRIDE
GO

EXECUTE sp_configure 'Agent XPs', 1
RECONFIGURE WITH OVERRIDE
GO

EXECUTE sp_configure 'show advanced options', 0
RECONFIGURE WITH OVERRIDE
GO
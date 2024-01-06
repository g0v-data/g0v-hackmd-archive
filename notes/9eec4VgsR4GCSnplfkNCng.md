# 2021_11_05 AT&S備机設定CDC問題解決

[sys].[sp_cdc_add_job] @job_type = N Capture'' 时失败。返回的错误为 22836:
安装sql server 后计算机改名了,导致当先运行的实例不是默认实例

修改SQL Server名称
1.檢查当前数据库的服务器名與傳回有關伺服器執行個體的屬性資訊
```
select @@SERVERNAME 
select SERVERPROPERTY('servername')
```
以上兩個要相同才能進行CDC
2.查看当前的所有服务器名
`     select * From Sys.SysServers`
3.删除服务器名
`     sp_dropserver  'servername'`
4.将本地服务器重新添加到服务器表中
`     erver  'new servername', 'LOCAL'`
5.检查核对
`    select * From Sys.SysServers`
6.修改完成后，重启数据库服务即可(IP上右鍵)
  
  以下為當時設定修改的指令
```
--select @@SERVERNAME
--select SERVERPROPERTY('servername')
--exec sp_dropserver 'WIN-R3OP69NTP4P\SQLEXPRESS';
--exec sp_addserver 'BACKUP02\SQLEXPRESS','LOCAL'
```
1.SQL Server Agent
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3cb12fdb62d1d52292ebdd9e2cee3a8d.png)
紅框處登入身分要改為相同

從SQL AGENT無法登入的話 改從工作管理員>service進入服務 從服務更改登入帳號後登入

select * from msdb.dbo.MSdistpublishers;
delete from msdb.dbo.MSdistpublishers;
exec sp_droplinkedsrvlogin 'old server name',null;
exec sp_dropserver 'old server name','droplogins';
exec sp_addserver 'new server name','LOCAL';
執行後
重啟SERVER
如果出現連接問題
使用 exec sp_helpserver
发现name为repl_distributor的服务器的network_name还是old name
解决处理
執行
exec sp_setnetname 'repl_distributor','MSSQLSERVER';
# 执行命令 '[sys].[sp_cdc_add_job] @job_type = N Capture'' 时失败。返回的错误为 22836

原因：SqlServer安装后修改了主机名，导致以下两个语句结果不一致
```
SELECT * FROM master.dbo.sysservers;
SELECT SERVERPROPERTY('ServerName')
```
修复方法：
```
IF serverproperty('servername')<>@@servername    

  BEGIN  

  DECLARE  @server SYSNAME  

  SET   @server=@@servername      

  EXEC  sp_dropserver @server=@server    

  SET   @server=cast(serverproperty('servername') AS SYSNAME)   

  EXEC  sp_addserver @server=@server,@local='LOCAL'     

  END  

  ELSE  

    PRINT '实例名与主机名一致，无需修改！' 
```
# SQL小筆記

列出欄位重複大於1的
```
select TRANSFER_ID,count(*) from AGVC_ASE_K21.dbo.HCMD
group by TRANSFER_ID
HAVING count(*)>1
```
# MS SQL查詢資料庫與其Table佔用空間

DB:
```
USE AGVC_Hsinchu_2F_Demoline;  
GO  
EXEC sp_spaceused;  
GO  
```
Table
```
SELECT
  t.object_id,
  OBJECT_NAME(t.object_id) ObjectName,
  sum(u.total_pages) * 8/1024 as Total_Reserved_MB,
  sum(u.used_pages) * 8/1024 as Used_Space_MB,
  u.type_desc,
  max(p.rows) RowsCount
FROM
  sys.allocation_units u
  JOIN sys.partitions p on u.container_id = p.hobt_id

  JOIN sys.tables t on p.object_id = t.object_id

GROUP BY
  t.object_id,
  OBJECT_NAME(t.object_id),
  u.type_desc
ORDER BY
  Used_Space_MB desc,
  ObjectName;
```
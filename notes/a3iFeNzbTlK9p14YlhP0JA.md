# Trend Micro Redshift Immersion Day

Lab URL : https://reurl.cc/Oja463 
Access Code : 840a-0c09f6-f8

Lab Document : https://catalog.us-east-1.prod.workshops.aws/workshops/9f29cdba-66c0-445e-8cbb-28a092cb5ba7/en-US 

Sample Stored Procedure :
```
drop table if exists demo.fact_sales_quantity;
create table demo.fact_sales_quantity
as 
  select r_name as Region, n_name as Nation, s_name as Supplier, l_shipmode as Ship_Mode, SUM(L_QUANTITY) Total_Qty
  from demo.lineitem
  join demo.supplier on l_suppkey = s_suppkey
  join demo.nation on s_nationkey = n_nationkey
  join demo.region on n_regionkey = r_regionkey
  where datepart(year, L_SHIPDATE) > 1997
  group by 1,2,3,4
;

CREATE OR REPLACE PROCEDURE sp_refresh_sales_quantity()
AS $$
BEGIN
  truncate table demo.fact_sales_quantity;
  insert into demo.fact_sales_quantity
  select r_name as Region, n_name as Nation, s_name as Supplier, l_shipmode as Ship_Mode, SUM(L_QUANTITY) Total_Qty
  from demo.lineitem
  join demo.supplier on l_suppkey = s_suppkey
  join demo.nation on s_nationkey = n_nationkey
  join demo.region on n_regionkey = r_regionkey
  where datepart(year, L_SHIPDATE) > 1997
  group by 1,2,3,4
  ;
END;
$$ LANGUAGE plpgsql
;

CALL sp_refresh_sales_quantity();
```

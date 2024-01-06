# Oracle語法小筆記
使用YYYY-MM-DD HH24:MI:SS對datetime(DD-MON-RR)做查詢
```
select * from tbname where starttime between to_date('2021-07-01 09:06:24','YYYY-MM-DD HH24:MI:SS') and to_date('2021-07-01 09:06:25','YYYY-MM-DD HH24:MI:SS') order by starttime;
```
--時間加減法
```
select sysdate,add_months(sysdate, 12) from dual; --加1年
select sysdate,add_months(sysdate, 1) from dual; --加1月
select sysdate,to_char(sysdate+ 7,'yyyy-mm-dd HH24:MI:SS' ) from dual ; --加1星期
select sysdate,to_char(sysdate+ 1,'yyyy-mm-dd HH24:MI:SS' ) from dual ; --加1天
select sysdate,to_char(sysdate+ 1/24 ,'yyyy-mm-dd HH24:MI:SS') from dual; --加1小時
select sysdate,to_char(sysdate+ 1/24 /60, 'yyyy-mm-dd HH24:MI:SS') from dual; --加1分鐘
select sysdate,to_char(sysdate+ 1/24 /60/ 60,'yyyy-mm-dd HH24:MI:SS' ) from dual; --加1秒
```

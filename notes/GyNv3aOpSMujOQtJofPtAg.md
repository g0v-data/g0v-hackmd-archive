报表建置参考文件.md
---
# 报表建置参考文件
以下內容目前會隨著報表作業而有所變動。
## 報表歸屬時間(today 08:00 AM ~ tomorrow 07:59 AM)
依據HISTORYMAINLINE資料產生時間當依據(TXNDATE)
:::warning
不能用在MV，雖然SQL內沒有Clob型別的欄位但仍發生以下錯誤。
錯誤訊息:ORA-22992: 無法使用自遠端表格選取的 LOB 定位器
:::
```sql=
 TXNDATE + INTERVAL '-8' HOUR as rptdate, 
 TXNDATEGMT + INTERVAL '-8' HOUR as rptdategmt,
```

## 分組
用來篩選當天同批LOT同站點重複MOVE IN/ MOVE OUT的資料，
只取最新一筆。
:::warning
必須在統計時依照ODSName與日期條件納入，
如果在第二階做會以當時的條件來分組。
例如取得某天進站資料或出站資料
:::
```sql=
 row_number() over (partition BY c.CONTAINERID, hml.WORKFLOWSTEPID order by TXNDATE desc) rownumber,
```

## 只呈現前7天資料
key word: temporal validity

## rptdate filter 
```sql=
to_char(hml.TXNDATE + INTERVAL '-8' HOUR, 'yyyyMMdd') = '20190909'
```

## CONTAINER STATUS 定義
```
状态 0 = Deletedn   1 = Activen   2 = Closedn   3 = In Transit (shipped) n   4 = Issued (component) 
```
## CONTAINER(CONTAINER_MV)
```sql=
CREATE MATERIALIZED VIEW LOG ON CONTAINER
  WITH ROWID, PRIMARY KEY
  INCLUDING NEW VALUES;
```
```sql=
CREATE MATERIALIZED VIEW CONTAINER_MV
    REFRESH FORCE
    START WITH (sysdate) NEXT (sysdate + 1 / 1440) WITH ROWID
AS
SELECT * FROM CONTAINER@todslink;
```

## PRODUCT(PRODUCT_MV)
```sql=
CREATE MATERIALIZED VIEW LOG ON PRODUCT
  WITH ROWID, PRIMARY KEY
  INCLUDING NEW VALUES;
```
```sql=
CREATE MATERIALIZED VIEW PRODUCT_MV
    REFRESH FORCE
    START WITH (sysdate) NEXT (sysdate + 1 / 1440) WITH ROWID
AS
SELECT * FROM PRODUCT@todslink;
```

## HISTORYMAINLINE(HISTORYMAINLINE_MV)
```sql=
CREATE MATERIALIZED VIEW LOG ON HISTORYMAINLINE
  WITH ROWID, PRIMARY KEY
  INCLUDING NEW VALUES;
```
```sql=
CREATE MATERIALIZED VIEW HISTORYMAINLINE_MV
    REFRESH FORCE
    START WITH (sysdate) NEXT (sysdate + 1 / 1440) WITH ROWID
AS
SELECT * FROM HISTORYMAINLINE@todslink;
```

## RESOURCEDEF(RESOURCEDEF_MV)
```sql=
CREATE MATERIALIZED VIEW LOG ON RESOURCEDEF
  WITH ROWID, PRIMARY KEY
  INCLUDING NEW VALUES;
```
```sql=
CREATE MATERIALIZED VIEW RESOURCEDEF_MV
    REFRESH FORCE
    START WITH (sysdate) NEXT (sysdate + 1 / 1440) WITH ROWID
AS
SELECT * FROM RESOURCEDEF@todslink;
```
## A_LOTWAFERS(A_LOTWAFERS)
```sql=
CREATE MATERIALIZED VIEW LOG ON A_LOTWAFERS
  WITH ROWID, PRIMARY KEY
  INCLUDING NEW VALUES;
```
```sql=
CREATE MATERIALIZED VIEW A_LOTWAFERS_MV
    REFRESH FORCE
    START WITH (sysdate) NEXT (sysdate + 1 / 1440) WITH ROWID
AS
SELECT distinct CONTAINERID, SLPLAINTSUBSTRATEVENDOR FROM A_LOTWAFERS@todslink;
```
## 線上基版供應商表(V_SUBSTRATEVENDOR)
```sql=
create view V_SUBSTRATEVENDOR as
SELECT * FROM A_LOTWAFERS_MV;
```
## 產品明細表(PRODUCTINFO_MV)
```sql=
CREATE MATERIALIZED VIEW PRODUCTINFO_MV
    REFRESH FORCE
    START WITH (sysdate) NEXT (sysdate + 1 / 1440) WITH ROWID
AS
SELECT p.isavailable,
       pb.productname,
       p.productrevision,
       p.fabplantarea,
       p.gdpw,
       p.masksetid,
       p.lotsize,
       p.objectcategory,
       p.objecttype,
       p.opn,
       p.opnrevision,
       p.productbaseid,
       p.productfamilyid,
       pf.description,
       pf.productfamilyname,
       p.producttypeid,
       pt.producttypename,
       p.productid,
       p.productlineid,
       pl.productlinename,
       p.stdstartqty,
       p.stdstartqty2,
       p.stdstartuomid,
       p.stdstartuom2id,
       p.wafersize,
       p.workflowbaseid,
       p.workflowid,
       p.slqtyperbag,
       p.slsubstrategraphicid,
       p.slsubstratetypeid,
       p.bomid,
       p.bombaseid
FROM product@todslink p
         INNER JOIN productbase@todslink pb ON pb.productbaseid = p.productbaseid
         LEFT JOIN productfamily@todslink pf ON pf.productfamilyid = p.productfamilyid
         LEFT JOIN producttype@todslink pt ON pt.producttypeid = p.producttypeid
         LEFT JOIN a_productline@todslink pl ON pl.productlineid = p.productlineid;
```
## 產品製程明細表(PRODUCTSTEPINFO_MV)
```sql=
CREATE MATERIALIZED VIEW PRODUCTSTEPINFO_MV
    REFRESH FORCE
    START WITH (sysdate) NEXT (sysdate + 1 / 1440) WITH ROWID
AS
select pb.productname,
       p.productid,
       p.productrevision as version,
       psb.displaysequence,
       psb.processspecbaseid,
       aps.processspecname,
       ap.processspecrevision,
       psb.processspecid,
       ap.cycletime,
       ap.description,
       ap.processspecstatusid,
       apss.isavailable,
       apss.processspecstatusname,
       ap.status,
       ap.workflowbaseid,
       wfb.workflowname,
       ap.workflowid,
       ap.slpnstageid,
       wf.objectcategory,
       wf.objecttype,
       wf.workflowrevision
from a_productprocessspeclist@todslink psb
         inner join product@todslink p on p.productid = psb.productid
         inner join productbase@todslink pb on pb.productbaseid = p.productbaseid
         inner join a_processspecbase@todslink aps on aps.processspecbaseid = psb.processspecbaseid
         inner join a_processspec@todslink ap on ap.processspecbaseid = aps.processspecbaseid
         inner join a_ProcessSpecStatus@todslink apss on apss.processspecstatusid = ap.processspecstatusid
         left join workflow@todslink wf on wf.workflowid = ap.workflowid
         inner join workflowbase@todslink wfb on wfb.workflowbaseid = wf.workflowbaseid;
```

## WORKFLOWSPECINFO(WORKFLOWSPECINFO_MV)
```sql=
CREATE MATERIALIZED VIEW WORKFLOWSPECINFO_MV
    REFRESH FORCE
    START WITH (sysdate) NEXT (sysdate + 1 / 1440) WITH ROWID
AS
select ws.specbaseid,
       ws.workflowstepname,
       ws.workflowid,
       wfb.workflowname,
       ws.slstage,
       ws.slstagesequence,
       ws.slstepcode,
       apsd.masklayerid,
       apsd.wipdatasetupid,
       apsd.toolplanid,
       wd.wipdatasetupname,
       ws.SEQUENCE,
       aps.processspecrevision
from workflowstep@todslink ws
         inner join workflow@todslink wf on wf.workflowid = ws.workflowid
         left join a_processspecdetails@todslink apsd on apsd.ss_stepid = ws.workflowstepid
         inner join a_processspec@todslink aps on aps.processspecid = apsd.processspecid
         left join a_wipdatasetup@todslink wd on wd.wipdatasetupid = apsd.wipdatasetupid
         inner join workflowbase@todslink wfb on wfb.workflowbaseid = wf.workflowbaseid
```

## WIP歷程明細表 (WIPSTEPINFO_MV)
```sql=
CREATE MATERIALIZED VIEW WIPSTEPINFO_MV
    REFRESH FORCE
    START WITH (sysdate) NEXT (sysdate + 1 / 1440) WITH ROWID
AS
select
    c.CONTAINERID,
    c.CONTAINERNAME,
    hml.CDONAME,
    hml.FACTORYID,
    c.FACTORYSTARTDATE,
    c.FACTORYSTARTDATEGMT,
    c.FACTORYSTARTQTY,
    c.FACTORYSTARTQTY2,
    c.FACTORYSTARTUOMID,
    c.FACTORYSTARTUOM2ID,
    c.OBJECTTYPE,
    c.PRODUCTID,
    hml.PRODUCTNAME,
    wfs.WORKFLOWID,
    hml.WORKFLOWNAME,
    wfs.SLSTAGE,
    wfs.SLSTAGESEQUENCE,
    hml.WORKFLOWSTEPID,
    wfs.WORKFLOWSTEPNAME,
    wfs.SEQUENCE as STEPSEQUENCE,
    hml.SPECID,
    hml.SPECNAME,
    hml.SPECPASS,
    c.PROCESSSPECID,
    ps.SLPNSTAGEID,
    sps.SLPNSTAGENAME,
    p.GDPW,
    c.QTY,
    c.QTY2,
    c.MOVEINQTY,
    c.MOVEINQTY2,
    c.MOVEINTIMESTAMP,
    c.MOVEINUSERNAME,
    hml.EMPLOYEEID,
    hml.EMPLOYEENAME,
    hml.MFGDATE,
    hml.OPERATIONID,
    hml.RESOURCEID,
    hml.RESOURCENAME,
    hml.FROMCONTAINERID,
    hml.FROMCONTAINERNAME,
    hml.FROMQTY,
    hml.FROMQTY2,
    hml.FROMSPECID,
    hml.FROMSPECNAME,
    hml.FROMSPECPASS,
    hml.FROMSTATUS,
    hml.FROMUOM2NAME,
    hml.FROMUOMNAME,
    hml.FROMWORKFLOWNAME,
    hml.HISTORYID,
    hml.HISTORYMAINLINEID,
    hml.INREWORK,
    c.LASTMOVEOUTTIMESTAMP,
    c.LASTMOVEOUTUSERNAME,
    c.SCSLASTMOVEOUTTIMESTAMPGMT,
    c.SCSMOVEINTIMESTAMPGMT,
    c.STATUS,
    hml.SYSTEMDATE,
    hml.SYSTEMDATEGMT,
    hml.TXNDATE,
    hml.TXNDATEGMT,
    hml.TXNID,
    hml.TXNTYPE,
    hml.UOM2NAME,
    hml.UOMNAME,
    c.CURRENTHOLDCOUNT,
    c.CURRENTREWORKCOUNT,
    c.CURRENTSTATUSID,
    c.CURRENTWIPLOTID,
    c.CUSTOMERID,
    c.DETAILID,
    c.ISESHIP,
    c.LASTACTIVITYDATE,
    c.LASTACTIVITYDATEGMT,
    c.LASTCOMPLETIONDATE,
    c.LASTCOMPLETIONDATEGMT,
    c.LASTSCHEDULEDATAID,
    c.LASTSTEPID,
    c.LOANCOUNT,
    c.LOANSEQUENCE,
    c.MFGORDERID,
    c.ONHOLDDATE,
    c.ORIGINALCONTAINERID,
    c.ORIGINALFACTORYID,
    c.ORIGINALQTY,
    c.ORIGINALQTY2,
    c.ORIGINALSTARTDATE,
    c.ORIGINALSTARTDATEGMT,
    c.ORIGINALUOM2ID,
    c.ORIGINALUOMID,
    c.PRIORITYCODEID,
    c.QTYSCHEDULED,
    c.SCHEDULEDATAID,
    c.SCHEDULERESIDUEQTY,
    c.SCSONHOLDDATEGMT,
    c.SPLITCOUNT,
    c.UNITCOUNT,
    c.UOM2ID,
    c.UOMID
from HISTORYMAINLINE@todslink hml
         inner join Container@todslink c on hml.CONTAINERID = c.CONTAINERID
         inner join WORKFLOWSTEP@todslink wfs on hml.WORKFLOWSTEPID = wfs.WORKFLOWSTEPID
         inner join PRODUCT@todslink p on p.PRODUCTID = hml.PRODUCTID
         inner join A_processspec@todslink ps on ps.PROCESSSPECID = c.PROCESSSPECID
         inner join SLPNSTAGE@todslink sps on sps.SLPNSTAGEID = ps.SLPNSTAGEID;
```
## H_EQP_RUNTIME
```sql=
-- auto-generated definition
create table H_EQP_RUNTIME
(
    RESOURCEID         CHAR(16),
    RESOURCENAME       VARCHAR2(40),
    RESOURCEFAMILYID   CHAR(16),
    RESOURCEFAMILYNAME VARCHAR2(30),
    STATUSCODEID       CHAR(16),
    STATUSNAME         VARCHAR2(40),
    NOTES              VARCHAR2(2000),
    DURATION_H         NUMBER,
    RPTDATE            DATE,
    TOTAL_QTY          NUMBER,
    TOTAL_QTY2         NUMBER,
    LM_TIME            DATE
)
/


```
## H_EQP_RUNTIME_SUM
```sql=
-- auto-generated definition
create table H_EQP_RUNTIME_SUM
(
    RESOURCEID           CHAR(16),
    RESOURCENAME         VARCHAR2(40),
    RESOURCEFAMILYID     CHAR(16),
    RESOURCEFAMILYNAME   VARCHAR2(30),
    RPTDATE              DATE,
    TOTAL_QTY2           NUMBER,
    TOTAL_DURATION_H     NUMBER,
    IDLE_DURATION_H      NUMBER,
    PM_DURATION_H        NUMBER,
    DOWN_DURATION_H      NUMBER,
    OFFLINE_DURATION_H   NUMBER,
    LM_TIME              DATE,
    TOTAL_TRACKREJECTQTY NUMBER,
    CHMT_DURATION_H      NUMBER,
    UPTIME               NUMBER,
    RUNTIME              NUMBER,
    YIELD                NUMBER,
    UPRATE               NUMBER,
    RUNRATE              NUMBER,
    OEE                  NUMBER
)
/


```
## H_UTH_REPORT
```sql=
-- auto-generated definition
create table H_UTH_REPORT
(
    WORKFLOWID       CHAR(16),
    WORKFLOWNAME     VARCHAR2(40),
    WORKFLOWREVISION VARCHAR2(15),
    SLSTAGE          VARCHAR2(40),
    SLSTAGESEQUENCE  VARCHAR2(40),
    WORKFLOWSTEPID   CHAR(16) not null,
    WORKFLOWSTEPNAME VARCHAR2(40),
    STEPSEQUENCE     NUMBER(10),
    GRADE_A          NUMBER,
    GRADE_B          NUMBER,
    GRADE_C          NUMBER,
    REJECT_QTY       NUMBER,
    SCRAP_QTY        NUMBER,
    REWORK_QTY       NUMBER,
    YIELD            NUMBER,
    RPTDATE          DATE,
    LM_TIME          DATE,
    MOVEIN_QTY       NUMBER default null
)
/


```
## R_WIP_INFO
```sql=
-- auto-generated definition
create table R_WIP_INFO
(
    CONTAINERID             CHAR(16) not null,
    CONTAINERNAME           VARCHAR2(30),
    STATUS                  NUMBER(10),
    SLLOTTYPEID             CHAR(16),
    SLLOTTYPENAME           VARCHAR2(40),
    PRIORITYCODEID          CHAR(16),
    PRIORITYCODENAME        VARCHAR2(40),
    ORIGINALFACTORYID       CHAR(16),
    FACTORYNAME             VARCHAR2(30),
    WORKCENTERID            CHAR(16),
    WORKCENTERNAME          VARCHAR2(30),
    LOCATIONID              CHAR(16),
    LOCATIONNAME            VARCHAR2(40),
    PRODUCTFAMILYID         CHAR(16),
    PRODUCTFAMILYNAME       VARCHAR2(30),
    PRODUCTLINEID           CHAR(16),
    PRODUCTLINENAME         VARCHAR2(40),
    PRODUCTID               CHAR(16),
    PRODUCTNAME             VARCHAR2(40),
    WORKFLOWBASEID          CHAR(16),
    WORKFLOWID              CHAR(16),
    WORKFLOWNAME            VARCHAR2(40),
    WORKFLOWREVISION        VARCHAR2(15),
    SLSTAGE                 VARCHAR2(40),
    SLSTAGESEQUENCE         VARCHAR2(40),
    WORKFLOWSTEPID          CHAR(16),
    WORKFLOWSTEPNAME        VARCHAR2(40),
    STEPSEQUENCE            NUMBER(10),
    OBJECTCATEGORY          VARCHAR2(40),
    SPECBASEID              CHAR(16),
    SPECID                  CHAR(16),
    SPECNAME                VARCHAR2(40),
    PROCESSSPECID           CHAR(16),
    OPERATIONGROUPID        CHAR(16),
    OPERATIONGROUPNAME      VARCHAR2(40),
    OPERATIONID             CHAR(16),
    OPERATIONNAME           VARCHAR2(30),
    SLPLAINTSUBSTRATEVENDOR VARCHAR2(40),
    UOMID                   CHAR(16),
    UOMNAME                 VARCHAR2(40),
    OWNERID                 CHAR(16),
    HOLDREASONID            CHAR(16),
    HOLDREASONNAME          VARCHAR2(40),
    GDPW                    NUMBER,
    MOVEINQTY               NUMBER,
    MOVEINQTY2              NUMBER,
    MOVEINTIMESTAMP         DATE,
    QTY                     NUMBER,
    QTY2                    NUMBER,
    REWORKTOTALCOUNT        NUMBER(10),
    INPROCESS               NUMBER(10),
    INREWORK                NUMBER(10),
    PROCESSDIFF_H           NUMBER,
    REAL_H                  NUMBER,
    CONTAINERCOMMENTS       VARCHAR2(2000),
    SCHEDULEDATE            DATE,
    SALESORDERNUMBER        VARCHAR2(40),
    EXPECTEDSTARTDATE       DATE,
    EXPECTEDENDDATE         DATE,
    EXPECTEDENDWEEK         VARCHAR2(2),
    FACTORYSTARTDATE        DATE,
    FACTORYSTARTDATEGMT     DATE,
    DUEDATE                 DATE,
    DUEDATEGMT              DATE,
    ORIGINALSTARTDATE       DATE,
    ORIGINALSTARTDATEGMT    DATE,
    PLANNEDSTARTDATE        DATE,
    PLANNEDSTARTDATEGMT     DATE,
    MASKLAYERID             CHAR(16),
    MASKLAYERNAME           VARCHAR2(40),
    DESCRIPTION             VARCHAR2(255),
    C3                      NUMBER default 0,
    C4                      NUMBER default 0,
    C5                      NUMBER default 0,
    STDCT_H                 NUMBER default 0,
    ORIGINAL_NORMALCT_H     NUMBER default 0,
    ORIGINAL_FASTCT_H       NUMBER default 0,
    PRODUCTREVISION         VARCHAR2(15),
    WAITTIME_H              NUMBER,
    LASTMOVEOUTTIMESTAMP    DATE,
    ACTUALOUTPUTWEEK        NUMBER,
    RPTDATE                 DATE   default sysdate - (8 / 24),
    RPTDATEGMT              DATE   default sysdate,
    ACTUALOUTPUTTIMESTAMP   DATE
)
/


```
## R_WIP_MOVE
```sql=
-- auto-generated definition
create table R_WIP_MOVE
(
    PRODUCTID                  CHAR(16),
    PRODUCTNAME                VARCHAR2(40),
    PRODUCTREVISION            VARCHAR2(15),
    PRODUCTBASEID              CHAR(16),
    PRODUCTLINEID              CHAR(16),
    PRODUCTLINENAME            VARCHAR2(40),
    PRODUCTFAMILYID            CHAR(16),
    PRODUCTFAMILYNAME          VARCHAR2(30),
    GDPW                       NUMBER,
    WORKFLOWBASEID             CHAR(16),
    WORKFLOWID                 CHAR(16),
    WORKFLOWNAME               VARCHAR2(40),
    WORKFLOWREVISION           VARCHAR2(15),
    SLSTAGE                    VARCHAR2(40),
    SLSTAGESEQUENCE            VARCHAR2(40),
    WORKFLOWSTEPID             CHAR(16),
    WORKFLOWSTEPNAME           VARCHAR2(40),
    STEPSEQUENCE               NUMBER(10),
    WAFERSCRIBENUMBER          VARCHAR2(40),
    CONTAINERID                CHAR(16),
    CONTAINERNAME              VARCHAR2(30),
    STATUS                     NUMBER(10),
    QTY                        NUMBER,
    QTY2                       NUMBER,
    UOMID                      CHAR(16),
    MOVEINTIMESTAMP            DATE,
    LASTMOVEOUTTIMESTAMP       DATE,
    SCSLASTMOVEOUTTIMESTAMPGMT DATE,
    MOVEINQTY                  NUMBER,
    MOVEINQTY2                 NUMBER,
    PRIORITYCODEID             CHAR(16),
    FACTORYSTARTDATE           DATE,
    FACTORYSTARTDATEGMT        DATE,
    DUEDATE                    DATE,
    DUEDATEGMT                 DATE,
    ORIGINALSTARTDATE          DATE,
    ORIGINALSTARTDATEGMT       DATE,
    PLANNEDSTARTDATE           DATE,
    PLANNEDSTARTDATEGMT        DATE,
    DIESIZE                    NUMBER,
    GRADE                      VARCHAR2(40),
    NDPW                       NUMBER,
    ORIGINALNDPW               NUMBER,
    PRODUCTIONGRADE            VARCHAR2(40),
    PSSGRADE                   VARCHAR2(40),
    TXNTIMESTAMP               DATE,
    VENDORNAME                 VARCHAR2(40),
    VENDORLOTNUMBER            VARCHAR2(40),
    WAFERSIZE                  NUMBER,
    LOTWAFERSID                CHAR(16) not null,
    RUNNUMBER                  VARCHAR2(40),
    RUNNUMBERSETUPID           CHAR(16),
    RUNNUMBERSETUPNAME         VARCHAR2(40),
    EQUIPMENTNAME              VARCHAR2(40),
    SCHEDULEDATE               DATE,
    SALESORDERNUMBER           VARCHAR2(40),
    EXPECTEDSTARTDATE          DATE,
    EXPECTEDENDDATE            DATE,
    ORDERSTARTDATE             DATE,
    ORDERSTARTDATEGMT          DATE,
    OTD                        NUMBER,
    ITO                        VARCHAR2(40),
    METAL                      VARCHAR2(40),
    METALTOOLING               VARCHAR2(40),
    FURANCE                    VARCHAR2(40),
    FURANCEBATCH               VARCHAR2(40),
    RPTDATE                    DATE,
    RPTDATEGMT                 DATE,
    DATE_DIFF                  NUMBER,
    SPECNAME                   VARCHAR2(40),
    SPECID                     CHAR(16),
    PROCESSSPECOBJECTTYPE      VARCHAR2(40),
    PROCESSSPECREVISION        VARCHAR2(40),
    PROCESSSPECNAME            VARCHAR2(40),
    PROCESSSPECID              CHAR(16),
    WIPTYPE                    VARCHAR2(40),
    WIPSTATUS                  VARCHAR2(40),
    MOVEOUTTIMESTAMP           DATE,
    MOVEOUTQTY2                NUMBER,
    MOVEOUTQTY                 NUMBER,
    EPIWAFER                   VARCHAR2(40),
    EPIREACTOR                 VARCHAR2(40),
    UOMNAME                    VARCHAR2(30),
    NORMALCYCLETIME            NUMBER,
    FASTCYCLETIME              NUMBER,
    OTD_RANGE                  NUMBER,
    OVERPROCESSTIME_H          NUMBER
)
/


```
## R_WIP_REPORT_DETAIL
```sql=
-- auto-generated definition
create table R_WIP_REPORT_DETAIL
(
    RPTDATE              DATE,
    RPTDATEGMT           DATE,
    INHISTORYMAINLINEID  CHAR(16),
    OUTHISTORYMAINLINEID CHAR(16),
    CONTAINERID          VARCHAR2(16),
    CONTAINERNAME        VARCHAR2(30),
    PRODUCTID            CHAR(16),
    PRODUCTNAME          VARCHAR2(40),
    WORKFLOWID           CHAR(16),
    WORKFLOWNAME         VARCHAR2(40),
    SLSTAGE              VARCHAR2(40),
    SLSTAGESEQUENCE      VARCHAR2(40),
    WORKFLOWSTEPID       CHAR(16),
    WORKFLOWSTEPNAME     VARCHAR2(40),
    STEPSEQUENCE         VARCHAR2(40),
    PROCESSSPECID        CHAR(16),
    SLPNSTAGEID          CHAR(16),
    SLPNSTAGENAME        VARCHAR2(40),
    FACTORYSTARTQTY      NUMBER,
    FACTORYSTARTQTY2     NUMBER,
    GDPW                 NUMBER,
    MOVEIN_QTY           NUMBER,
    MOVEIN_QTY2          NUMBER,
    MOVEOUT_QTY          NUMBER,
    MOVEOUT_QTY2         NUMBER,
    LM_TIME              DATE
)
/


```
## TMP_EQP_RUNTIME_SUM
```sql=
-- auto-generated definition
create table TMP_EQP_RUNTIME_SUM
(
    RESOURCEID           CHAR(16),
    RESOURCENAME         VARCHAR2(40),
    RESOURCEFAMILYID     CHAR(16),
    RESOURCEFAMILYNAME   VARCHAR2(30),
    RPTDATE              DATE,
    TOTAL_QTY2           NUMBER,
    TOTAL_DURATION_H     NUMBER,
    IDLE_DURATION_H      NUMBER,
    PM_DURATION_H        NUMBER,
    DOWN_DURATION_H      NUMBER,
    OFFLINE_DURATION_H   NUMBER,
    LM_TIME              DATE,
    TOTAL_TRACKREJECTQTY NUMBER,
    CHMT_DURATION_H      NUMBER,
    YIELD                NUMBER,
    UPRATE               NUMBER,
    RUNRATE              NUMBER,
    OEE                  NUMBER
)
/


```
## TMP_MOVEIN_LIST
```sql=
-- auto-generated definition
create table TMP_MOVEIN_LIST
(
    ROWNUMBER         NUMBER,
    RPTDATE           DATE,
    RPTDATEGMT        DATE,
    HISTORYMAINLINEID CHAR(16) not null,
    CONTAINERID       CHAR(16) not null,
    CONTAINERNAME     VARCHAR2(30),
    CDONAME           VARCHAR2(40),
    FACTORYID         CHAR(16),
    FACTORYSTARTQTY   NUMBER,
    FACTORYSTARTQTY2  NUMBER,
    PRODUCTID         CHAR(16),
    PRODUCTNAME       VARCHAR2(40),
    WORKFLOWID        CHAR(16),
    WORKFLOWNAME      VARCHAR2(40),
    SLSTAGE           VARCHAR2(40),
    SLSTAGESEQUENCE   VARCHAR2(40),
    WORKFLOWSTEPID    CHAR(16),
    WORKFLOWSTEPNAME  VARCHAR2(40),
    SPECID            CHAR(16),
    SPECNAME          VARCHAR2(40),
    SPECPASS          NUMBER(10),
    PROCESSSPECID     CHAR(16),
    SLPNSTAGEID       CHAR(16),
    SLPNSTAGENAME     VARCHAR2(40),
    GDPW              NUMBER,
    QTY               NUMBER,
    QTY2              NUMBER
)
/


```
## TMP_MOVEOUT_LIST
```sql=
-- auto-generated definition
create table TMP_MOVEOUT_LIST
(
    ROWNUMBER         NUMBER,
    RPTDATE           DATE,
    RPTDATEGMT        DATE,
    HISTORYMAINLINEID CHAR(16) not null,
    CONTAINERID       CHAR(16) not null,
    CONTAINERNAME     VARCHAR2(30),
    CDONAME           VARCHAR2(40),
    FACTORYID         CHAR(16),
    FACTORYSTARTQTY   NUMBER,
    FACTORYSTARTQTY2  NUMBER,
    PRODUCTID         CHAR(16),
    PRODUCTNAME       VARCHAR2(40),
    WORKFLOWID        CHAR(16),
    WORKFLOWNAME      VARCHAR2(40),
    SLSTAGE           VARCHAR2(40),
    SLSTAGESEQUENCE   VARCHAR2(40),
    WORKFLOWSTEPID    CHAR(16),
    WORKFLOWSTEPNAME  VARCHAR2(40),
    SPECID            CHAR(16),
    SPECNAME          VARCHAR2(40),
    SPECPASS          NUMBER(10),
    PROCESSSPECID     CHAR(16),
    SLPNSTAGEID       CHAR(16),
    SLPNSTAGENAME     VARCHAR2(40),
    GDPW              NUMBER,
    QTY               NUMBER,
    QTY2              NUMBER
)
/


```
## TMP_STEPCT_DETAIL
```sql=
-- auto-generated definition
create table TMP_STEPCT_DETAIL
(
    CONTAINERID     CHAR(16),
    WORKFLOWID      CHAR(16),
    WORKFLOWSTEPID  CHAR(16),
    STEPSEQUENCE    NUMBER(10),
    NORMALCYCLETIME NUMBER,
    FASTCYCLETIME   NUMBER
)
/


```
## TMP_WIP_INFO
```sql=
-- auto-generated definition
create table TMP_WIP_INFO
(
    CONTAINERID             CHAR(16) not null,
    CONTAINERNAME           VARCHAR2(30),
    STATUS                  NUMBER(10),
    SLLOTTYPEID             CHAR(16),
    SLLOTTYPENAME           VARCHAR2(40),
    PRIORITYCODEID          CHAR(16),
    PRIORITYCODENAME        VARCHAR2(40),
    ORIGINALFACTORYID       CHAR(16),
    FACTORYNAME             VARCHAR2(30),
    WORKCENTERID            CHAR(16),
    WORKCENTERNAME          VARCHAR2(30),
    LOCATIONID              CHAR(16),
    LOCATIONNAME            VARCHAR2(40),
    PRODUCTFAMILYID         CHAR(16),
    PRODUCTFAMILYNAME       VARCHAR2(30),
    PRODUCTLINEID           CHAR(16),
    PRODUCTLINENAME         VARCHAR2(40),
    PRODUCTID               CHAR(16),
    PRODUCTNAME             VARCHAR2(40),
    WORKFLOWBASEID          CHAR(16),
    WORKFLOWID              CHAR(16),
    WORKFLOWNAME            VARCHAR2(40),
    WORKFLOWREVISION        VARCHAR2(15),
    SLSTAGE                 VARCHAR2(40),
    SLSTAGESEQUENCE         VARCHAR2(40),
    WORKFLOWSTEPID          CHAR(16),
    WORKFLOWSTEPNAME        VARCHAR2(40),
    STEPSEQUENCE            NUMBER(10),
    OBJECTCATEGORY          VARCHAR2(40),
    SPECBASEID              CHAR(16),
    SPECID                  CHAR(16),
    SPECNAME                VARCHAR2(40),
    PROCESSSPECID           CHAR(16),
    OPERATIONGROUPID        CHAR(16),
    OPERATIONGROUPNAME      VARCHAR2(40),
    OPERATIONID             CHAR(16),
    OPERATIONNAME           VARCHAR2(30),
    SLPLAINTSUBSTRATEVENDOR VARCHAR2(40),
    UOMID                   CHAR(16),
    UOMNAME                 VARCHAR2(40),
    OWNERID                 CHAR(16),
    HOLDREASONID            CHAR(16),
    HOLDREASONNAME          VARCHAR2(40),
    GDPW                    NUMBER,
    MOVEINQTY               NUMBER,
    MOVEINQTY2              NUMBER,
    MOVEINTIMESTAMP         DATE,
    QTY                     NUMBER,
    QTY2                    NUMBER,
    REWORKTOTALCOUNT        NUMBER(10),
    INPROCESS               NUMBER(10),
    INREWORK                NUMBER(10),
    PROCESSDIFF_H           NUMBER,
    REAL_H                  NUMBER,
    CONTAINERCOMMENTS       VARCHAR2(2000),
    SCHEDULEDATE            DATE,
    SALESORDERNUMBER        VARCHAR2(40),
    EXPECTEDSTARTDATE       DATE,
    EXPECTEDENDDATE         DATE,
    EXPECTEDENDWEEK         VARCHAR2(2),
    FACTORYSTARTDATE        DATE,
    FACTORYSTARTDATEGMT     DATE,
    DUEDATE                 DATE,
    DUEDATEGMT              DATE,
    ORIGINALSTARTDATE       DATE,
    ORIGINALSTARTDATEGMT    DATE,
    PLANNEDSTARTDATE        DATE,
    PLANNEDSTARTDATEGMT     DATE,
    MASKLAYERID             CHAR(16),
    MASKLAYERNAME           VARCHAR2(40),
    DESCRIPTION             VARCHAR2(255),
    C3                      NUMBER default 0,
    C4                      NUMBER default 0,
    C5                      NUMBER default 0,
    STDCT_H                 NUMBER default 0,
    ORIGINAL_NORMALCT_H     NUMBER default 0,
    ORIGINAL_FASTCT_H       NUMBER default 0,
    PRODUCTREVISION         VARCHAR2(15),
    WAITTIME_H              NUMBER,
    LASTMOVEOUTTIMESTAMP    DATE,
    ACTUALOUTPUTWEEK        NUMBER
)
/


```
## TMP_WIPREPORT_STEP
```sql=
create table TMP_WIPREPORT_STEP
(
    CONTAINERID      CHAR(16) not null,
    CONTAINERNAME    VARCHAR2(30),
    PRODUCTID        CHAR(16),
    PRODUCTNAME      VARCHAR2(40),
    WORKFLOWID       CHAR(16),
    WORKFLOWNAME     VARCHAR2(40),
    SLSTAGE          VARCHAR2(40),
    SLSTAGESEQUENCE  VARCHAR2(40),
    WORKFLOWSTEPID   CHAR(16),
    WORKFLOWSTEPNAME VARCHAR2(40),
    STEPSEQUENCE     VARCHAR2(40),
    PROCESSSPECID    CHAR(16),
    SLPNSTAGEID      CHAR(16),
    SLPNSTAGENAME    VARCHAR2(40)
)
```
## TMP_WIP_MOVE
```sql=
-- auto-generated definition
create table TMP_WIP_MOVE
(
    PRODUCTID                  CHAR(16),
    PRODUCTNAME                VARCHAR2(40),
    PRODUCTREVISION            VARCHAR2(15),
    PRODUCTBASEID              CHAR(16),
    PRODUCTLINEID              CHAR(16),
    PRODUCTLINENAME            VARCHAR2(40),
    PRODUCTFAMILYID            CHAR(16),
    PRODUCTFAMILYNAME          VARCHAR2(30),
    GDPW                       NUMBER,
    WORKFLOWBASEID             CHAR(16),
    WORKFLOWID                 CHAR(16),
    WORKFLOWNAME               VARCHAR2(40),
    WORKFLOWREVISION           VARCHAR2(15),
    SLSTAGE                    VARCHAR2(40),
    SLSTAGESEQUENCE            VARCHAR2(40),
    WORKFLOWSTEPID             CHAR(16),
    WORKFLOWSTEPNAME           VARCHAR2(40),
    STEPSEQUENCE               NUMBER(10),
    WAFERSCRIBENUMBER          VARCHAR2(40),
    CONTAINERID                CHAR(16),
    CONTAINERNAME              VARCHAR2(30),
    STATUS                     NUMBER(10),
    QTY                        NUMBER,
    QTY2                       NUMBER,
    UOMID                      CHAR(16),
    MOVEINTIMESTAMP            DATE,
    LASTMOVEOUTTIMESTAMP       DATE,
    SCSLASTMOVEOUTTIMESTAMPGMT DATE,
    MOVEINQTY                  NUMBER,
    MOVEINQTY2                 NUMBER,
    PRIORITYCODEID             CHAR(16),
    FACTORYSTARTDATE           DATE,
    FACTORYSTARTDATEGMT        DATE,
    DUEDATE                    DATE,
    DUEDATEGMT                 DATE,
    ORIGINALSTARTDATE          DATE,
    ORIGINALSTARTDATEGMT       DATE,
    PLANNEDSTARTDATE           DATE,
    PLANNEDSTARTDATEGMT        DATE,
    DIESIZE                    NUMBER,
    GRADE                      VARCHAR2(40),
    NDPW                       NUMBER,
    ORIGINALNDPW               NUMBER,
    PRODUCTIONGRADE            VARCHAR2(40),
    PSSGRADE                   VARCHAR2(40),
    TXNTIMESTAMP               DATE,
    VENDORNAME                 VARCHAR2(40),
    VENDORLOTNUMBER            VARCHAR2(40),
    WAFERSIZE                  NUMBER,
    LOTWAFERSID                CHAR(16) not null,
    RUNNUMBER                  VARCHAR2(40),
    RUNNUMBERSETUPID           CHAR(16),
    RUNNUMBERSETUPNAME         VARCHAR2(40),
    EQUIPMENTNAME              VARCHAR2(40),
    SCHEDULEDATE               DATE,
    SALESORDERNUMBER           VARCHAR2(40),
    EXPECTEDSTARTDATE          DATE,
    EXPECTEDENDDATE            DATE,
    ORDERSTARTDATE             DATE,
    ORDERSTARTDATEGMT          DATE,
    OTD                        NUMBER,
    ITO                        VARCHAR2(40),
    METAL                      VARCHAR2(40),
    METALTOOLING               VARCHAR2(40),
    FURANCE                    VARCHAR2(40),
    FURANCEBATCH               VARCHAR2(40),
    RPTDATE                    DATE,
    RPTDATEGMT                 DATE,
    DATE_DIFF                  NUMBER,
    SPECNAME                   VARCHAR2(40),
    SPECID                     CHAR(16),
    PROCESSSPECOBJECTTYPE      VARCHAR2(40),
    PROCESSSPECREVISION        VARCHAR2(40),
    PROCESSSPECNAME            VARCHAR2(40),
    PROCESSSPECID              CHAR(16),
    WIPTYPE                    VARCHAR2(40),
    WIPSTATUS                  VARCHAR2(40),
    MOVEOUTTIMESTAMP           DATE,
    MOVEOUTQTY2                NUMBER,
    MOVEOUTQTY                 NUMBER,
    EPIWAFER                   VARCHAR2(40),
    EPIREACTOR                 VARCHAR2(40),
    UOMNAME                    VARCHAR2(30),
    NORMALCYCLETIME            NUMBER,
    FASTCYCLETIME              NUMBER,
    OTD_RANGE                  NUMBER,
    OVERPROCESSTIME_H          NUMBER
)
/


```
## TMP_MOVEIN_LIST
```sql=
create table TMP_MOVEIN_LIST
(
    ROWNUMBER        NUMBER,
    RPTDATE          DATE,
    RPTDATEGMT       DATE,
    HISTORYMAINLINEID CHAR(16) not null,
    CONTAINERID      CHAR(16) not null,
    CONTAINERNAME    VARCHAR2(30),
    CDONAME          VARCHAR2(40),
    FACTORYID        CHAR(16),
    FACTORYSTARTQTY  NUMBER,
    FACTORYSTARTQTY2 NUMBER,
    PRODUCTID        CHAR(16),
    PRODUCTNAME      VARCHAR2(40),
    WORKFLOWID       CHAR(16),
    WORKFLOWNAME     VARCHAR2(40),
    SLSTAGE          VARCHAR2(40),
    SLSTAGESEQUENCE  VARCHAR2(40),
    WORKFLOWSTEPID   CHAR(16),
    WORKFLOWSTEPNAME VARCHAR2(40),
    SPECID           CHAR(16),
    SPECNAME         VARCHAR2(40),
    SPECPASS         NUMBER(10),
    PROCESSSPECID    CHAR(16),
    SLPNSTAGEID      CHAR(16),
    SLPNSTAGENAME   VARCHAR2(40),
    GDPW             NUMBER,
    QTY              NUMBER,
    QTY2             NUMBER
)
```
## TMP_MOVEOUT_LIST
```sql=
create table TMP_MOVEOUT_LIST
(
    ROWNUMBER        NUMBER,
    RPTDATE          DATE,
    RPTDATEGMT       DATE,
    HISTORYMAINLINEID CHAR(16) not null,
    CONTAINERID      CHAR(16) not null,
    CONTAINERNAME    VARCHAR2(30),
    CDONAME          VARCHAR2(40),
    FACTORYID        CHAR(16),
    FACTORYSTARTQTY  NUMBER,
    FACTORYSTARTQTY2 NUMBER,
    PRODUCTID        CHAR(16),
    PRODUCTNAME      VARCHAR2(40),
    WORKFLOWID       CHAR(16),
    WORKFLOWNAME     VARCHAR2(40),
    SLSTAGE          VARCHAR2(40),
    SLSTAGESEQUENCE  VARCHAR2(40),
    WORKFLOWSTEPID   CHAR(16),
    WORKFLOWSTEPNAME VARCHAR2(40),
    SPECID           CHAR(16),
    SPECNAME         VARCHAR2(40),
    SPECPASS         NUMBER(10),
    PROCESSSPECID    CHAR(16),
    SLPNSTAGEID      CHAR(16),
    SLPNSTAGENAME   VARCHAR2(40),
    GDPW             NUMBER,
    QTY              NUMBER,
    QTY2             NUMBER
)
```
## TMP_WIPREPORT_STEP
```sql=
create table TMP_WIPREPORT_STEP
(
    CONTAINERID      CHAR(16) not null,
    CONTAINERNAME    VARCHAR2(30),
    PRODUCTID        CHAR(16),
    PRODUCTNAME      VARCHAR2(40),
    WORKFLOWID       CHAR(16),
    WORKFLOWNAME     VARCHAR2(40),
    SLSTAGE          VARCHAR2(40),
    SLSTAGESEQUENCE  VARCHAR2(40),
    WORKFLOWSTEPID   CHAR(16),
    WORKFLOWSTEPNAME VARCHAR2(40),
    STEPSEQUENCE     VARCHAR2(40),
    PROCESSSPECID    CHAR(16),
    SLPNSTAGEID      CHAR(16),
    SLPNSTAGENAME   VARCHAR2(40)
)
```
## V_CONTAINER
```sql=
create view V_CONTAINER as
select c.CONTAINERID,
       c.CONTAINERNAME,
       c.STATUS,
       c.SLLOTTYPEID,
       slt.SLLOTTYPENAME,
       c.PRIORITYCODEID,
       pc.PRIORITYCODENAME,
       c.ORIGINALFACTORYID,
       f.FACTORYNAME,
       cs.LOCATIONID,
       p.PRODUCTFAMILYID,
       pf.PRODUCTFAMILYNAME,
       p.PRODUCTLINEID,
       pl.PRODUCTLINENAME,
       c.PRODUCTID,
       pb.PRODUCTNAME,
       p.PRODUCTREVISION,
       c.PROCESSSPECID,
       c.UOMID,
       u.UOMNAME,
       c.OWNERID,
       c.HOLDREASONID,
       hs.HOLDREASONNAME,
       lf.SLPLAINTSUBSTRATEVENDOR,
       p.GDPW,
       c.MOVEINQTY,
       c.MOVEINQTY2,
       c.MOVEINTIMESTAMP,
       c.QTY,
       c.QTY2,
       cs.REWORKTOTALCOUNT,
       cs.INPROCESS,
       cs.INREWORK,
       c.CONTAINERCOMMENTS,
       sd.SCHEDULEDATE,
       sd.SALESORDERNUMBER,
       sd.EXPECTEDSTARTDATE,
       sd.EXPECTEDENDDATE,
       TO_CHAR(sd.EXPECTEDENDDATE,'IW') AS EXPECTEDENDWEEK,
       c.FACTORYSTARTDATE,
       c.FACTORYSTARTDATEGMT,
       c.DUEDATE,
       c.DUEDATEGMT,
       c.ORIGINALSTARTDATE,
       c.ORIGINALSTARTDATEGMT,
       c.PLANNEDSTARTDATE,
       c.PLANNEDSTARTDATEGMT,
       psd.masklayerid,
       am.masklayername,
       p.OBJECTCATEGORY
from Container@meslink c
         left join (
    select distinct CONTAINERID, SLPLAINTSUBSTRATEVENDOR from A_LOTWAFERS@meslink where SLPLAINTSUBSTRATEVENDOR is not null
) lf on lf.CONTAINERID = c.CONTAINERID
         left join SLLOTTYPE@meslink slt on slt.SLLOTTYPEID = c.SLLOTTYPEID
         inner join PRIORITYCODE@meslink pc on pc.PRIORITYCODEID = c.PRIORITYCODEID
         inner join FACTORY@meslink f on f.FACTORYID = c.ORIGINALFACTORYID
         inner join PRODUCT@meslink p on p.PRODUCTID = c.PRODUCTID
         inner join PRODUCTBASE@meslink pb on pb.PRODUCTBASEID = p.PRODUCTBASEID
         left join PRODUCTFAMILY@meslink pf on pf.PRODUCTFAMILYID = p.PRODUCTFAMILYID
         left join A_PRODUCTLINE@meslink pl on pl.PRODUCTLINEID = p.PRODUCTLINEID
         inner join UOM@meslink u on u.UOMID = c.UOMID
         inner join CURRENTSTATUS@meslink cs on cs.CURRENTSTATUSID = c.CURRENTSTATUSID
         left join A_SCHEDULEDATA@meslink sd on sd.CONTAINERID = c.CONTAINERID
         left join HOLDREASON@meslink hs on hs.HOLDREASONID = c.HOLDREASONID
         left join LOCATION@meslink l on (l.FACTORYID = f.FACTORYID AND l.LOCATIONID = cs.LOCATIONID)
         left join A_PROCESSSPECDETAILS@meslink psd
                   on c.processspecid = psd.processspecid and cs.workflowstepid = psd.ss_stepid
         left join a_masklayer@meslink am on am.masklayerid = psd.masklayerid
/


```
## V_DIRECTTHROUGHOUT_DETAIL
```sql=
create or replace view V_DIRECTTHROUGHOUT_DETAIL as
SELECT DISTINCT HML.CONTAINERID,
                HML.CONTAINERNAME,
                HML.CDONAME,
                HML.QTY,
                HML.QTY2,
                WFS.WORKFLOWID,
                HML.WORKFLOWNAME,
                HML.WORKFLOWSTEPID,
                TRUNC(HML.SYSTEMDATE) AS RPTDATE
FROM HISTORYMAINLINE@MESLINK HML
         LEFT JOIN WORKFLOWSTEP@MESLINK WFS ON WFS.WORKFLOWSTEPID = HML.WORKFLOWSTEPID
WHERE UPPER(CDONAME) IN ('MOVEINLOT', 'REJECTLOT', 'REWORKLOT', 'SCRAPLOT')
ORDER BY CONTAINERID
```
## V_DIRECTTHROUGHOUT_SUM
```sql=
CREATE OR REPLACE VIEW V_DIRECTTHROUGHOUT_SUM AS
SELECT WORKFLOWID, WORKFLOWNAME, WORKFLOWSTEPID, SUM(QTY2) AS TOTAL_QTY2, CDONAME, RPTDATE
FROM V_DIRECTTHROUGHOUT_DETAIL
GROUP BY WORKFLOWID, WORKFLOWNAME, WORKFLOWSTEPID, CDONAME, RPTDATE
ORDER BY RPTDATE, WORKFLOWNAME, WORKFLOWSTEPID
```
## V_EQP_LOTS_DETAIL
```sql=
create OR REPLACE view V_EQP_LOTS_DETAIL as
SELECT
       WE.TRACKINTIMESTAMP + INTERVAL '-8' HOUR as rptdate
     , WE.TRACKINTIMESTAMP + INTERVAL '-8' HOUR as rptdategmt
     , R.RESOURCEID
     , R.RESOURCENAME
     , C.CONTAINERID
     , C.CONTAINERNAME
     , CASE WHEN C.CURRENTHOLDCOUNT = 0 THEN 'NO' ELSE 'YES' END          AS LOTONHOLD
     , C.QTY
     , C.QTY2
     , WE.TRACKSTATUS
     , WE.INSERTIONNUMBER
     , WE.PROCESSTYPENAME
     , WE.BATCHID
     , R.OBJECTCATEGORY
     , R.OBJECTTYPE
     , WE.TRACKINTIMESTAMP
     , WE.TRACKINUSERNAME
     , WE.TRACKINEMPLOYEENAME
     , WE.ORIGINALTRACKINQTY
     , WE.TRACKINQTY
     , WE.TRACKREJECTQTY
     , WE.TRACKDEFECTQTY
     , WE.TRACKREWORKABLEREJECTQTY
     , WE.TRACKUNIDENTIFIABLEREJECTQTY
     , WE.TRACKACCEPTABLEBINSQTY
     , WE.TRACKNOTREQUIREDBINSQTY
     , WE.TRACKREJECTBINSQTY
     , WE.TRACKDUMMYQTY
     , WE.TRACKINPROCESSCOMBINEDQTY
     , WE.TRACKINPROCESSSPLITQTY
     , WE.TRACKCONSUMEDOUTQTY
     , WE.TRACKSCRAPREJECTQTY
     , WE.TRACKOUTTIMESTAMP
     , WE.TRACKOUTUSERNAME
     , WE.TRACKOUTEMPLOYEENAME
     , WE.TRACKOUTQTY
     , WE.TRACKSEQUENCE
     , WE.TRACKSEQUENCEBYEQUIPMENT
     , WE.TRACKSEQUENCECLONED
     , WE.TRACKSEQUENCECLONEDDATE
     , WE.MASKNAME
     , CASE WHEN WE.RECIPENAME IS NULL AND WE.RECIPEREVISION IS NULL THEN '' ELSE WE.RECIPENAME || ':' || WE.RECIPEREVISION END  AS RECIPE
     , WE.TESTPROGRAMNAME
     , WE.TESTPROGRAMMAJORREVISION
     , WE.TESTPROGRAMMINORREVISION
     , WE.TESTCODE
     , WE.TESTTEMPERATURE
FROM CONTAINER@meslink C
         INNER JOIN A_WIPEQUIPMENTHISTORY@meslink WE ON C.CONTAINERID = WE.CONTAINERID
         INNER JOIN RESOURCEDEF@meslink R ON R.RESOURCEID = WE.EQUIPMENTID
         LEFT JOIN RESOURCEFAMILY@meslink ET ON R.RESOURCEFAMILYID = ET.RESOURCEFAMILYID
ORDER BY R.RESOURCEID, TRACKINTIMESTAMP
/


```
## V_EQP_STATUS_DAILY_HISTORY
```sql=
create view V_EQP_STATUS_DAILY_HISTORY as
SELECT T.RPTDATE,
       T.RPTDATEGMT,
       OLDAVAILABILITY,
       RESOURCEID,
       RESOURCENAME,
       RESOURCEFAMILYID,
       RESOURCEFAMILYNAME,
       OLDRESOURCESTATUSCODEID,
       OLDSTATUSNAME,
       OLDNOTES,
       TOTAL_DURATION_H,
       (CASE
           -- 如果只有LASTSTATUSCHANGEDATE有資料，OLDLASTSTATUSCHANGEDATE沒資料表示該狀態仍持續中，要用sysdate - LASTSTATUSCHANGEDATE換算持續時間.
           --          WHEN N != 1 AND TRUNC(T.RPTDATE + N - 1) = TRUNC(T.LASTSTATUSCHANGEDATE_SHIFT) AND
--                  T.LASTSTATUSCHANGEDATE_SHIFT - T.RPTDATE <= 1
           -- 跨天，且時間差不足一天(只有兩天)
--                 THEN TRUNC(24 * ((T.RPTDATE+N-1) - (TRUNC(T.RPTDATE))), 2)
            WHEN N = 1 AND TRUNC(T.RPTDATE + N - 1) = TRUNC(T.LASTSTATUSCHANGEDATE_SHIFT) AND
                 T.LASTSTATUSCHANGEDATE_SHIFT - T.RPTDATE <= 1
                -- 1.同一天，且只有一天 2.跨天，且時間差不足一天(只有兩天)
                THEN TRUNC(24 * (T.LASTSTATUSCHANGEDATE_SHIFT - (T.RPTDATE + N - 1)), 4)
            WHEN TRUNC(T.RPTDATE + N - 1) != TRUNC(T.LASTSTATUSCHANGEDATE_SHIFT) AND
                 T.LASTSTATUSCHANGEDATE_SHIFT - T.RPTDATE < 1
                -- 連續天數的第一天(不同天，但兩者時間差不超過一天)
                THEN TRUNC(24 * (TRUNC(T.RPTDATE + N) - T.RPTDATE), 4)
            WHEN N = 1 AND T.LASTSTATUSCHANGEDATE_SHIFT - T.RPTDATE > 1
                -- 連續天數的第一天(不同天，但兩者時間差超過一天)
                THEN TRUNC(24 * (TRUNC(T.RPTDATE + N) - T.RPTDATE), 4)
            WHEN TRUNC(T.RPTDATE + N - 1) = TRUNC(T.LASTSTATUSCHANGEDATE_SHIFT) AND
                 T.LASTSTATUSCHANGEDATE_SHIFT - (T.RPTDATE + N - 1) < 1
                -- 連續天數的最後一天 , TRUNC(T.RPTDATE + N - 1) = Last Date 0時0分,去掉小時以免超過Last的時間
                THEN TRUNC(24 * (T.LASTSTATUSCHANGEDATE_SHIFT - TRUNC(T.RPTDATE + N - 1)), 4)
           -- 連續天數的中間天數(滿一天)
            ELSE TRUNC(24 * (T.RPTDATE + N - (T.RPTDATE + N - 1)), 4)
           END) AS DURATION_H,
       (CASE
            WHEN N = 1 THEN T.RPTDATE
            ELSE TRUNC(T.RPTDATE + N - 1)
           END) AS STARTDATE,
       (CASE
            WHEN TRUNC(T.RPTDATE + N - 1) = TRUNC(T.LASTSTATUSCHANGEDATE_SHIFT)
                THEN T.LASTSTATUSCHANGEDATE_SHIFT -- 同一天
            ELSE TRUNC(T.RPTDATE + N) - 1 / (24 * 60 * 60) -- 中間天數
           END) AS ENDDATE,
       (CASE
           --          WHEN N != 1 AND TRUNC(T.OLDLASTSTATUSCHANGEDATE + N - 1) = TRUNC(T.LASTSTATUSCHANGEDATE) AND
--                  T.LASTSTATUSCHANGEDATE - T.OLDLASTSTATUSCHANGEDATE <= 1
           -- 跨天，且時間差不足一天(只有兩天)
--                 THEN TRUNC(24 * ((T.OLDLASTSTATUSCHANGEDATE+N-1) - (TRUNC(T.OLDLASTSTATUSCHANGEDATE))), 2)
            WHEN N = 1 AND TRUNC(T.OLDLASTSTATUSCHANGEDATE + N - 1) = TRUNC(T.LASTSTATUSCHANGEDATE) AND
                 T.LASTSTATUSCHANGEDATE - T.OLDLASTSTATUSCHANGEDATE <= 1
                -- 1.同一天，且只有一天 2.跨天，且時間差不足一天(只有兩天)
                THEN TRUNC(24 * (T.LASTSTATUSCHANGEDATE - (T.OLDLASTSTATUSCHANGEDATE + N - 1)), 4)
            WHEN TRUNC(T.OLDLASTSTATUSCHANGEDATE + N - 1) != TRUNC(T.LASTSTATUSCHANGEDATE) AND
                 T.LASTSTATUSCHANGEDATE - T.OLDLASTSTATUSCHANGEDATE < 1
                -- 連續天數的第一天(不同天，但兩者時間差不超過一天)
                THEN TRUNC(24 * (TRUNC(T.OLDLASTSTATUSCHANGEDATE + N) - T.OLDLASTSTATUSCHANGEDATE), 4)
            WHEN N = 1 AND T.LASTSTATUSCHANGEDATE - T.OLDLASTSTATUSCHANGEDATE > 1
                -- 連續天數的第一天(不同天，但兩者時間差超過一天)
                THEN TRUNC(24 * (TRUNC(T.OLDLASTSTATUSCHANGEDATE + N) - T.OLDLASTSTATUSCHANGEDATE), 4)
            WHEN TRUNC(T.OLDLASTSTATUSCHANGEDATE + N - 1) = TRUNC(T.LASTSTATUSCHANGEDATE) AND
                 T.LASTSTATUSCHANGEDATE - (T.OLDLASTSTATUSCHANGEDATE + N - 1) < 1
                -- 連續天數的最後一天 , TRUNC(T.OLDLASTSTATUSCHANGEDATE + N - 1) = Last Date 0時0分,去掉小時以免超過Last的時間
                THEN TRUNC(24 * (T.LASTSTATUSCHANGEDATE - TRUNC(T.OLDLASTSTATUSCHANGEDATE + N - 1)), 4)
           -- 連續天數的中間天數(滿一天)
            ELSE TRUNC(24 * (T.OLDLASTSTATUSCHANGEDATE + N - (T.OLDLASTSTATUSCHANGEDATE + N - 1)), 4)
           END) AS ORIGINAL_DURATION_H,
       (CASE
            WHEN N = 1 THEN T.OLDLASTSTATUSCHANGEDATE
            ELSE TRUNC(T.OLDLASTSTATUSCHANGEDATE + N - 1)
           END) AS ORIGINAL_STARTDATE,
       (CASE
            WHEN TRUNC(T.OLDLASTSTATUSCHANGEDATE + N - 1) = TRUNC(T.LASTSTATUSCHANGEDATE)
                THEN T.LASTSTATUSCHANGEDATE -- 同一天
            ELSE TRUNC(T.OLDLASTSTATUSCHANGEDATE + N) - 1 / (24 * 60 * 60) -- 中間天數
           END) AS ORIGINAL_ENDDATE,
       LASTSTATUSCHANGEDATE,
       LASTSTATUSCHANGEDATEGMT,
       OLDLASTSTATUSCHANGEDATE,
       OLDLASTSTATUSCHANGEDATEGMT
FROM V_EQP_STATUS_SUM T
         JOIN
     (SELECT LEVEL N
      FROM DUAL
      CONNECT BY LEVEL <= 20) N
     ON TRUNC(T.OLDLASTSTATUSCHANGEDATE + N - 1) <= TRUNC(T.LASTSTATUSCHANGEDATE)
ORDER BY T.RESOURCEID, STARTDATE
/


```
## V_EQP_STATUS_HISTORY
```sql=
create view V_EQP_STATUS_HISTORY as
SELECT RSH.AVAILABILITY,
       RF.RESOURCEFAMILYID,
       RF.RESOURCEFAMILYNAME,
       HML.RESOURCEID,
       HML.RESOURCENAME,
       RSH.HISTORYMAINLINEID,
       RSH.LASTSTATUSCHANGEDATE,
       RSH.LASTSTATUSCHANGEDATEGMT,
       RSH.NEWREASONNAME,
       RSH.NEWSTATUSNAME,
       RSC.NOTES  AS NEWNOTES,
       RSH.OLDAVAILABILITY,
       RSH.OLDLASTACTIVITYDATE,
       RSH.OLDLASTACTIVITYDATEGMT,
       RSH.OLDLASTSTATUSCHANGEDATE,
       RSH.OLDLASTSTATUSCHANGEDATEGMT,
       RSH.OLDPRODUCTID,
       RSH.OLDREASONNAME,
       RSH.OLDRESOURCESTATE,
       RSH.OLDRESOURCESTATUSCODEID,
       RSH.OLDRESOURCESTATUSREASONCODEID,
       RSH.OLDRUN,
       RSH.OLDSETUPID,
       RSH.OLDSTATUSNAME,
       RSC2.NOTES AS OLDNOTES,
       RSH.OLDUPDATELASTSTATUSCHANGEDATE,
       RSH.PRODUCTID,
       RSH.RESOURCESTATE,
       RSH.RESOURCESTATUSCODEID,
       RSH.RESOURCESTATUSHISTORYID,
       RSH.RESOURCESTATUSREASONCODEID,
       RSH.RUN,
       RSH.SETUPID,
       F.FACTORYID,
       F.FACTORYNAME
FROM RESOURCESTATUSHISTORY@MESLINK RSH
         LEFT JOIN HISTORYMAINLINE@MESLINK HML ON HML.HISTORYMAINLINEID = RSH.HISTORYMAINLINEID
         LEFT JOIN RESOURCEDEF@MESLINK RD ON RD.RESOURCEID = HML.RESOURCEID
         LEFT JOIN RESOURCESTATUSCODE@MESLINK RSC ON RSC.RESOURCESTATUSCODEID = RSH.RESOURCESTATUSCODEID
         LEFT JOIN RESOURCESTATUSCODE@MESLINK RSC2 ON RSC2.RESOURCESTATUSCODEID = RSH.OLDRESOURCESTATUSCODEID
         LEFT JOIN RESOURCEFAMILY@MESLINK RF ON RF.RESOURCEFAMILYID = RD.RESOURCEFAMILYID
         LEFT JOIN FACTORY@MESLINK F ON RD.FACTORYID = F.FACTORYID
/


```
## V_EQP_STATUS_SUM
```sql=
create view V_EQP_STATUS_SUM as
select OLDLASTSTATUSCHANGEDATE + INTERVAL '-8' HOUR                            as RPTDATE,
       OLDLASTSTATUSCHANGEDATEGMT + INTERVAL '-8' HOUR                         as RPTDATEGMT,
       LASTSTATUSCHANGEDATE + INTERVAL '-8' HOUR                            as LASTSTATUSCHANGEDATE_SHIFT,
       LASTSTATUSCHANGEDATEGMT + INTERVAL '-8' HOUR                         as LASTSTATUSCHANGEDATEGMT_SHIFT,
       OLDAVAILABILITY,
       RESOURCEID,
       RESOURCENAME,
       RESOURCEFAMILYID,
       RESOURCEFAMILYNAME,
       OLDRESOURCESTATUSCODEID,
       OLDSTATUSNAME,
       OLDNOTES,
       (CASE WHEN OLDLASTSTATUSCHANGEDATE IS NULL THEN   NVL(TRUNC(24 * (SYSDATE - LASTSTATUSCHANGEDATE), 4), 0)
           ELSE NVL(TRUNC(24 * (LASTSTATUSCHANGEDATE - OLDLASTSTATUSCHANGEDATE), 4), 0) END ) as TOTAL_DURATION_H,
       LASTSTATUSCHANGEDATE,
       LASTSTATUSCHANGEDATEGMT,
       OLDLASTSTATUSCHANGEDATE,
       OLDLASTSTATUSCHANGEDATEGMT
from V_EQP_STATUS_HISTORY
order by RESOURCEID, LASTSTATUSCHANGEDATE desc
```
## V_MOVEIN
```sql=
create or replace view V_MOVEIN as
select
        TXNDATE + INTERVAL '-8' HOUR as rptdate,
        TXNDATEGMT + INTERVAL '-8' HOUR as rptdategmt,
        CONTAINERID,
        CONTAINERNAME,
        CDONAME,
        FACTORYID,
        FACTORYSTARTDATE,
        FACTORYSTARTDATEGMT,
        FACTORYSTARTQTY,
        FACTORYSTARTQTY2,
        FACTORYSTARTUOMID,
        FACTORYSTARTUOM2ID,
        OBJECTTYPE,
        PRODUCTID,
        PRODUCTNAME,
        WORKFLOWID,
        WORKFLOWNAME,
        SLSTAGE,
        SLSTAGESEQUENCE,
        WORKFLOWSTEPID,
        WORKFLOWSTEPNAME,
        STEPSEQUENCE,
        SPECID,
        SPECNAME,
        SPECPASS,
        PROCESSSPECID,
        SLPNSTAGEID,
        SLPNSTAGENAME,
        GDPW,
        QTY,
        QTY2,
        MOVEINQTY,
        MOVEINQTY2,
        MOVEINTIMESTAMP,
        MOVEINUSERNAME,
        EMPLOYEEID,
        EMPLOYEENAME,
        MFGDATE,
        OPERATIONID,
        RESOURCEID,
        RESOURCENAME,
        FROMCONTAINERID,
        FROMCONTAINERNAME,
        FROMQTY,
        FROMQTY2,
        FROMSPECID,
        FROMSPECNAME,
        FROMSPECPASS,
        FROMSTATUS,
        FROMUOM2NAME,
        FROMUOMNAME,
        FROMWORKFLOWNAME,
        HISTORYID,
        HISTORYMAINLINEID,
        INREWORK,
        LASTMOVEOUTTIMESTAMP,
        LASTMOVEOUTUSERNAME,
        SCSLASTMOVEOUTTIMESTAMPGMT,
        SCSMOVEINTIMESTAMPGMT,
        STATUS,
        SYSTEMDATE,
        SYSTEMDATEGMT,
        TXNDATE,
        TXNDATEGMT,
        TXNID,
        TXNTYPE,
        UOM2NAME,
        UOMNAME,
        CURRENTHOLDCOUNT,
        CURRENTREWORKCOUNT,
        CURRENTSTATUSID,
        CURRENTWIPLOTID,
        CUSTOMERID,
        DETAILID,
        ISESHIP,
        LASTACTIVITYDATE,
        LASTACTIVITYDATEGMT,
        LASTCOMPLETIONDATE,
        LASTCOMPLETIONDATEGMT,
        LASTSCHEDULEDATAID,
        LASTSTEPID,
        LOANCOUNT,
        LOANSEQUENCE,
        MFGORDERID,
        ONHOLDDATE,
        ORIGINALCONTAINERID,
        ORIGINALFACTORYID,
        ORIGINALQTY,
        ORIGINALQTY2,
        ORIGINALSTARTDATE,
        ORIGINALSTARTDATEGMT,
        ORIGINALUOM2ID,
        ORIGINALUOMID,
        PRIORITYCODEID,
        QTYSCHEDULED,
        SCHEDULEDATAID,
        SCHEDULERESIDUEQTY,
        SCSONHOLDDATEGMT,
        SPLITCOUNT,
        UNITCOUNT,
        UOM2ID,
        UOMID
from V_WIPSTEP
where CDONAME = 'MoveInLot'
```
## V_MOVEOUT
```sql=
create or replace view V_MOVEOUT as
select
        TXNDATE + INTERVAL '-8' HOUR as rptdate,
        TXNDATEGMT + INTERVAL '-8' HOUR as rptdategmt,
        CONTAINERID,
        CONTAINERNAME,
        CDONAME,
        FACTORYID,
        FACTORYSTARTDATE,
        FACTORYSTARTDATEGMT,
        FACTORYSTARTQTY,
        FACTORYSTARTQTY2,
        FACTORYSTARTUOMID,
        FACTORYSTARTUOM2ID,
        OBJECTTYPE,
        PRODUCTID,
        PRODUCTNAME,
        WORKFLOWID,
        WORKFLOWNAME,
        SLSTAGE,
        SLSTAGESEQUENCE,
        WORKFLOWSTEPID,
        WORKFLOWSTEPNAME,
        STEPSEQUENCE,
        SPECID,
        SPECNAME,
        SPECPASS,
        PROCESSSPECID,
        GDPW,
        QTY,
        QTY2,
        MOVEINQTY,
        MOVEINQTY2,
        MOVEINTIMESTAMP,
        MOVEINUSERNAME,
        EMPLOYEEID,
        EMPLOYEENAME,
        MFGDATE,
        OPERATIONID,
        RESOURCEID,
        RESOURCENAME,
        FROMCONTAINERID,
        FROMCONTAINERNAME,
        FROMQTY,
        FROMQTY2,
        FROMSPECID,
        FROMSPECNAME,
        FROMSPECPASS,
        FROMSTATUS,
        FROMUOM2NAME,
        FROMUOMNAME,
        FROMWORKFLOWNAME,
        HISTORYID,
        HISTORYMAINLINEID,
        INREWORK,
        LASTMOVEOUTTIMESTAMP,
        LASTMOVEOUTUSERNAME,
        SCSLASTMOVEOUTTIMESTAMPGMT,
        SCSMOVEINTIMESTAMPGMT,
        STATUS,
        SYSTEMDATE,
        SYSTEMDATEGMT,
        TXNDATE,
        TXNDATEGMT,
        TXNID,
        TXNTYPE,
        UOM2NAME,
        UOMNAME,
        CURRENTHOLDCOUNT,
        CURRENTREWORKCOUNT,
        CURRENTSTATUSID,
        CURRENTWIPLOTID,
        CUSTOMERID,
        DETAILID,
        ISESHIP,
        LASTACTIVITYDATE,
        LASTACTIVITYDATEGMT,
        LASTCOMPLETIONDATE,
        LASTCOMPLETIONDATEGMT,
        LASTSCHEDULEDATAID,
        LASTSTEPID,
        LOANCOUNT,
        LOANSEQUENCE,
        MFGORDERID,
        ONHOLDDATE,
        ORIGINALCONTAINERID,
        ORIGINALFACTORYID,
        ORIGINALQTY,
        ORIGINALQTY2,
        ORIGINALSTARTDATE,
        ORIGINALSTARTDATEGMT,
        ORIGINALUOM2ID,
        ORIGINALUOMID,
        PRIORITYCODEID,
        QTYSCHEDULED,
        SCHEDULEDATAID,
        SCHEDULERESIDUEQTY,
        SCSONHOLDDATEGMT,
        SPLITCOUNT,
        UNITCOUNT,
        UOM2ID,
        UOMID,
        SLPNSTAGEID,
        SLPNSTAGENAME
from V_WIPSTEP
where CDONAME = 'MoveLot'
```
## V_LATESTSTEPOFCON
```sql=
create view V_LATESTSTEPOFCON as
select
    row_number() over (partition BY CONTAINERID order by TXNDATE desc) rownumber,
    CONTAINERID,
    WORKFLOWSTEPID,
    TXNDATE
    from HISTORYMAINLINE@meslink
         where CONTAINERID is not null
```
## V_SUBSTRATEVENDOR
```sql=
create view V_SUBSTRATEVENDOR as
SELECT distinct CONTAINERID, SLPLAINTSUBSTRATEVENDOR FROM A_LOTWAFERS@meslink
```
## V_UTH_BASE
```sql=
create or replace view V_UTH_BASE as
SELECT WORKFLOWID,
       WORKFLOWNAME,
       WORKFLOWREVISION,
       SLSTAGE,
       SLSTAGESEQUENCE,
       WORKFLOWSTEPID,
       WORKFLOWSTEPNAME,
       STEPSEQUENCE,
       SYSDATE        AS LM_TIME
FROM V_STEP
WHERE UPPER(SUBSTR(WORKFLOWNAME, 1, 4)) = 'GAAS'
   OR UPPER(SUBSTR(WORKFLOWNAME, 1, 3)) = 'GAN'
ORDER BY WORKFLOWNAME, WORKFLOWREVISION, SLSTAGESEQUENCE, WORKFLOWSTEPID, STEPSEQUENCE
```
## V_WAFER
```sql=
CREATE OR REPLACE VIEW V_WAFER AS
SELECT C.PRODUCTID,
       PB.PRODUCTNAME,
       P.PRODUCTREVISION,
       P.PRODUCTBASEID,
       P.PRODUCTLINEID,
       PL.PRODUCTLINENAME,
       P.PRODUCTFAMILYID,
       PF.PRODUCTFAMILYNAME,
       P.GDPW,
       W.WAFERSCRIBENUMBER,
       W.CONTAINERID,
       C.CONTAINERNAME,
       C.STATUS,
       C.QTY,
       C.QTY2,
       C.UOMID,
       U.UOMNAME,
       C.MOVEINTIMESTAMP,
       C.LASTMOVEOUTTIMESTAMP,
       C.SCSLASTMOVEOUTTIMESTAMPGMT,
       C.MOVEINQTY,
       C.MOVEINQTY2,
       C.PRIORITYCODEID,
       C.FACTORYSTARTDATE,
       C.FACTORYSTARTDATEGMT,
       C.DUEDATE,
       C.DUEDATEGMT,
       C.ORIGINALSTARTDATE,
       C.ORIGINALSTARTDATEGMT,
       C.PLANNEDSTARTDATE,
       C.PLANNEDSTARTDATEGMT,
       W.DIESIZE,
       W.GRADE,
       W.NDPW,
       W.ORIGINALNDPW,
       W.PRODUCTIONGRADE,
       W.PSSGRADE,
       W.TXNTIMESTAMP,
       W.VENDORNAME,
       W.VENDORLOTNUMBER,
       W.WAFERSIZE,
       W.LOTWAFERSID,
       LWR.RUNNUMBER,
       LWR.RUNNUMBERSETUPID,
       LWR.RUNNUMBERSETUPNAME,
       LWR.EQUIPMENTNAME,
       SD.SCHEDULEDATE,
       SD.SALESORDERNUMBER,
       SD.EXPECTEDSTARTDATE,
       SD.EXPECTEDENDDATE,
       MO.ORDERSTARTDATE,
       MO.ORDERSTARTDATEGMT,
--        SYSDATE AS PROCESSTIME,
--        SYSDATE AS STDPROCESSTIME,
--        SYSDATE AS OVERPROCCESSTIME,
--        1 AS OTD,
       LWR.RUNNUMBER AS ITO,
       LWR.RUNNUMBER AS METAL,
       LWR.RUNNUMBER AS EPIReactor,
       SWD.WAFERSCRIBENUMBER AS EPIWafer
FROM A_LOTWAFERS@MESLINK W
         LEFT JOIN CONTAINER@MESLINK C ON W.CONTAINERID = C.CONTAINERID
         LEFT JOIN UOM@MESLINK U ON U.UOMID = C.UOMID
         LEFT JOIN A_SPLITWAFERSHISTORYDETAILS@MESLINK SWD ON W.WAFERSCRIBENUMBER = SWD.TOWAFERSCRIBENUMBER AND W.WAFERNUMBER = SWD.WAFERNUMBER
         LEFT JOIN (SELECT * FROM A_LOTWAFERSRUNS@MESLINK WHERE ISLATEST = 1) LWR ON W.LOTWAFERSID = LWR.LOTWAFERSID
         LEFT JOIN PRODUCT@MESLINK P ON P.PRODUCTID = C.PRODUCTID
         LEFT JOIN PRODUCTBASE@MESLINK PB ON P.PRODUCTBASEID = PB.PRODUCTBASEID
         LEFT JOIN PRODUCTFAMILY@MESLINK PF ON PF.PRODUCTFAMILYID = P.PRODUCTFAMILYID
         LEFT JOIN A_PRODUCTLINE@MESLINK PL ON PL.PRODUCTLINEID = P.PRODUCTLINEID
         LEFT JOIN MFGORDER@MESLINK MO ON MO.MFGORDERID = C.MFGORDERID
         LEFT JOIN A_SCHEDULEDATA@MESLINK SD ON SD.CONTAINERID = C.CONTAINERID

```
## V_WIPLOT
```sql=
create view V_WIPLOT as
    SELECT DISTINCT CONTAINERID,
                    WORKFLOWNAME,
                    WORKFLOWSTEPID,
                    WORKFLOWSTEPNAME,
                    MOVEINQTY,
                    MOVEINQTY2,
                    MOVEINTIMESTAMP,
                    MOVEOUTQTY,
                    MOVEOUTQTY2,
                    MOVEOUTTIMESTAMP,
                    WIPSTATUS,
                    WIPTYPE,
                    PROCESSSPECID,
                    PROCESSSPECNAME,
                    PROCESSSPECREVISION,
                    PROCESSSPECOBJECTTYPE,
                    SPECID,
                    SPECNAME,
                    MOVEINTIMESTAMP + INTERVAL '-16' HOUR as RPTDATE,
                    MOVEINTIMESTAMP + INTERVAL '-8' HOUR as RPTDATEGMT,
                    (MOVEOUTTIMESTAMP - MOVEINTIMESTAMP) AS DATE_DIFF
    FROM A_WIPLOTHISTORY@MESLINK
    UNION
    SELECT DISTINCT CONTAINERID,
                    WORKFLOWNAME,
                    WORKFLOWSTEPID,
                    WORKFLOWSTEPNAME,
                    MOVEINQTY,
                    MOVEINQTY2,
                    MOVEINTIMESTAMP,
                    MOVEOUTQTY,
                    MOVEOUTQTY2,
                    MOVEOUTTIMESTAMP,
                    WIPSTATUS,
                    WIPTYPE,
                    PROCESSSPECID,
                    PROCESSSPECNAME,
                    PROCESSSPECREVISION,
                    PROCESSSPECOBJECTTYPE,
                    SPECID,
                    SPECNAME,
                    MOVEINTIMESTAMP + INTERVAL '-16' HOUR as RPTDATE,
                    MOVEINTIMESTAMP + INTERVAL '-8' HOUR as RPTDATEGMT,
                    (MOVEOUTTIMESTAMP - MOVEINTIMESTAMP) AS DATE_DIFF
    FROM A_WIPLOT@MESLINK
```
## V_WIPSTEP
```sql=
create or replace view V_WIPSTEP as
select
    c.CONTAINERID,
    c.CONTAINERNAME,
    hml.CDONAME,
    hml.FACTORYID,
    c.FACTORYSTARTDATE,
    c.FACTORYSTARTDATEGMT,
    c.FACTORYSTARTQTY,
    c.FACTORYSTARTQTY2,
    c.FACTORYSTARTUOMID,
    c.FACTORYSTARTUOM2ID,
    c.OBJECTTYPE,
    c.PRODUCTID,
    hml.PRODUCTNAME,
    wfs.WORKFLOWID,
    hml.WORKFLOWNAME,
    wfs.SLSTAGE,
    wfs.SLSTAGESEQUENCE,
    hml.WORKFLOWSTEPID,
    wfs.WORKFLOWSTEPNAME,
    wfs.SEQUENCE as STEPSEQUENCE,
    hml.SPECID,
    hml.SPECNAME,
    hml.SPECPASS,
    c.PROCESSSPECID,
    ps.SLPNSTAGEID,
    sps.SLPNSTAGENAME,
    p.GDPW,
    c.QTY,
    c.QTY2,
    c.MOVEINQTY,
    c.MOVEINQTY2,
    c.MOVEINTIMESTAMP,
    c.MOVEINUSERNAME,
    hml.EMPLOYEEID,
    hml.EMPLOYEENAME,
    hml.MFGDATE,
    hml.OPERATIONID,
    hml.RESOURCEID,
    hml.RESOURCENAME,
    hml.FROMCONTAINERID,
    hml.FROMCONTAINERNAME,
    hml.FROMQTY,
    hml.FROMQTY2,
    hml.FROMSPECID,
    hml.FROMSPECNAME,
    hml.FROMSPECPASS,
    hml.FROMSTATUS,
    hml.FROMUOM2NAME,
    hml.FROMUOMNAME,
    hml.FROMWORKFLOWNAME,
    hml.HISTORYID,
    hml.HISTORYMAINLINEID,
    hml.INREWORK,
    c.LASTMOVEOUTTIMESTAMP,
    c.LASTMOVEOUTUSERNAME,
    c.SCSLASTMOVEOUTTIMESTAMPGMT,
    c.SCSMOVEINTIMESTAMPGMT,
    c.STATUS,
    hml.SYSTEMDATE,
    hml.SYSTEMDATEGMT,
    hml.TXNDATE,
    hml.TXNDATEGMT,
    hml.TXNID,
    hml.TXNTYPE,
    hml.UOM2NAME,
    hml.UOMNAME,
    c.CURRENTHOLDCOUNT,
    c.CURRENTREWORKCOUNT,
    c.CURRENTSTATUSID,
    c.CURRENTWIPLOTID,
    c.CUSTOMERID,
    c.DETAILID,
    c.ISESHIP,
    c.LASTACTIVITYDATE,
    c.LASTACTIVITYDATEGMT,
    c.LASTCOMPLETIONDATE,
    c.LASTCOMPLETIONDATEGMT,
    c.LASTSCHEDULEDATAID,
    c.LASTSTEPID,
    c.LOANCOUNT,
    c.LOANSEQUENCE,
    c.MFGORDERID,
    c.ONHOLDDATE,
    c.ORIGINALCONTAINERID,
    c.ORIGINALFACTORYID,
    c.ORIGINALQTY,
    c.ORIGINALQTY2,
    c.ORIGINALSTARTDATE,
    c.ORIGINALSTARTDATEGMT,
    c.ORIGINALUOM2ID,
    c.ORIGINALUOMID,
    c.PRIORITYCODEID,
    c.QTYSCHEDULED,
    c.SCHEDULEDATAID,
    c.SCHEDULERESIDUEQTY,
    c.SCSONHOLDDATEGMT,
    c.SPLITCOUNT,
    c.UNITCOUNT,
    c.UOM2ID,
    c.UOMID
from HISTORYMAINLINE@MESLINK hml
         inner join Container@MESLINK c on hml.CONTAINERID = c.CONTAINERID
         inner join WORKFLOWSTEP@MESLINK wfs on hml.WORKFLOWSTEPID = wfs.WORKFLOWSTEPID
         inner join PRODUCT@MESLINK p on p.PRODUCTID = hml.PRODUCTID
         inner join A_processspec@MESLINK ps on ps.PROCESSSPECID = c.PROCESSSPECID
         inner join SLPNSTAGE@MESLINK sps on sps.SLPNSTAGEID = ps.SLPNSTAGEID
/


```  
## R_WIP_REPORT (預留)
  ```sql=
create table R_WIP_REPORT
(
    RPTDATEGMT         DATE,
    PRODUCTID          CHAR(16),
    PRODUCTNAME        VARCHAR2(40),
    WORKFLOWID         CHAR(16),
    WORKFLOWNAME       VARCHAR2(40),
    SLSTAGE            VARCHAR2(40),
    SLSTAGESEQUENCE    VARCHAR2(40),
    WORKFLOWSTEPID     CHAR(16),
    WORKFLOWSTEPNAME   VARCHAR2(40),
    STEPSEQUENCE       VARCHAR2(40),
    FACTORYSTARTQTY    NUMBER,
    FACTORYSTARTQTY2   NUMBER,
    GDPW               NUMBER,
    MOVEIN_TOTAL_QTY   NUMBER,
    MOVEIN_TOTAL_QTY2  NUMBER,
    MOVEOUT_TOTAL_QTY  NUMBER,
    MOVEOUT_TOTAL_QTY2 NUMBER,
    SYSTEMDATE           DATE,
    SYSTEMDATEGMT        DATE
)
```
## R_WIP_REPORT_DETAIL 
```sql=
create table R_WIP_REPORT_DETAIL
(
    RPTDATE              DATE,
    RPTDATEGMT           DATE,
    INHISTORYMAINLINEID  CHAR(16),
    OUTHISTORYMAINLINEID CHAR(16),
    CONTAINERID          VARCHAR2(16),
    CONTAINERNAME        VARCHAR2(30),
    PRODUCTID            CHAR(16),
    PRODUCTNAME          VARCHAR2(40),
    WORKFLOWID           CHAR(16),
    WORKFLOWNAME         VARCHAR2(40),
    SLSTAGE              VARCHAR2(40),
    SLSTAGESEQUENCE      VARCHAR2(40),
    WORKFLOWSTEPID       CHAR(16),
    WORKFLOWSTEPNAME     VARCHAR2(40),
    STEPSEQUENCE         VARCHAR2(40),
    PROCESSSPECID        CHAR(16),
    SLPNSTAGEID          CHAR(16),
    SLPNSTAGENAME        VARCHAR2(40),
    FACTORYSTARTQTY      NUMBER,
    FACTORYSTARTQTY2     NUMBER,
    GDPW                 NUMBER,
    MOVEIN_QTY           NUMBER,
    MOVEIN_QTY2          NUMBER,
    MOVEOUT_QTY          NUMBER,
    MOVEOUT_QTY2         NUMBER,
    SYSTEMDATE           DATE,
    SYSTEMDATEGMT        DATE
)
```
## R_WIP_INFO (在製品明細表)
```sql=
create table R_WIP_INFO
(
    CONTAINERID          CHAR(16) not null,
    CONTAINERNAME        VARCHAR2(30),
    STATUS               NUMBER(10),
    SLLOTTYPEID          CHAR(16),
    SLLOTTYPENAME        VARCHAR2(40),
    PRIORITYCODEID       CHAR(16),
    PRIORITYCODENAME     VARCHAR2(40),
    ORIGINALFACTORYID    CHAR(16),
    FACTORYNAME          VARCHAR2(30),
    WORKCENTERID         CHAR(16),
    WORKCENTERNAME       VARCHAR2(30),
    LOCATIONID           CHAR(16),
    LOCATIONNAME         VARCHAR2(40),
    PRODUCTFAMILYID      CHAR(16),
    PRODUCTFAMILYNAME    VARCHAR2(30),
    PRODUCTLINEID        CHAR(16),
    PRODUCTLINENAME      VARCHAR2(40),
    PRODUCTID            CHAR(16),
    PRODUCTNAME          VARCHAR2(40),
    PRODUCTREVISION      VARCHAR2(15),
    WORKFLOWBASEID       CHAR(16),
    WORKFLOWID           CHAR(16),
    WORKFLOWNAME         VARCHAR2(40),
    WORKFLOWREVISION     VARCHAR2(15),
    SLSTAGE              VARCHAR2(40),
    SLSTAGESEQUENCE      VARCHAR2(40),
    WORKFLOWSTEPID       CHAR(16),
    WORKFLOWSTEPNAME     VARCHAR2(40),
    STEPSEQUENCE         NUMBER(10),
    OBJECTCATEGORY       VARCHAR2(40),
    SPECBASEID           CHAR(16),
    SPECID               CHAR(16),
    SPECNAME             VARCHAR2(40),
    PROCESSSPECID        CHAR(16),
    OPERATIONGROUPID     CHAR(16),
    OPERATIONGROUPNAME   VARCHAR2(40),
    OPERATIONID          CHAR(16),
    OPERATIONNAME        VARCHAR2(30),
    SLPLAINTSUBSTRATEVENDOR       VARCHAR2(40),
    UOMID                CHAR(16),
    UOMNAME              VARCHAR2(40),
    OWNERID              CHAR(16),
    HOLDREASONID         CHAR(16),
    HOLDREASONNAME       VARCHAR2(40),
    GDPW                 NUMBER,
    MOVEINQTY            NUMBER,
    MOVEINQTY2           NUMBER,
    MOVEINTIMESTAMP      DATE,
    QTY                  NUMBER,
    QTY2                 NUMBER,
    REWORKTOTALCOUNT     NUMBER(10),
    INPROCESS            NUMBER(10),
    INREWORK             NUMBER(10),
    FASTCYCLETIME        NUMBER,
    NORMALCYCLETIME      NUMBER,
    CONTAINERCOMMENTS    VARCHAR2(2000),
    SCHEDULEDATE         DATE,
    SALESORDERNUMBER     VARCHAR2(40),
    EXPECTEDSTARTDATE    DATE,
    EXPECTEDENDDATE      DATE,
    EXPECTEDENDWEEK      VARCHAR2(2),
    FACTORYSTARTDATE     DATE,
    FACTORYSTARTDATEGMT  DATE,
    DUEDATE              DATE,
    DUEDATEGMT           DATE,
    ORIGINALSTARTDATE    DATE,
    ORIGINALSTARTDATEGMT DATE,
    PLANNEDSTARTDATE     DATE,
    PLANNEDSTARTDATEGMT  DATE,
    MASKLAYERID          CHAR(16) ,
    MASKLAYERNAME        VARCHAR2(40),
    DESCRIPTION          VARCHAR2(255),
    C3                   NUMBER default 0,
    C4                   NUMBER default 0,
    C5                   NUMBER default 0,
    STDCT_H              NUMBER default 0,
    REAL_H               NUMBER default 0,
    PROCESSDIFF_H        NUMBER default 0,
    ORIGINAL_NORMALCT_H NUMBER default 0,
    ORIGINAL_FASTCT_H NUMBER default 0
)
```
## TMP_WIP_INFO
```sql=
create table TMP_WIP_INFO
(
    CONTAINERID          CHAR(16) not null,
    CONTAINERNAME        VARCHAR2(30),
    STATUS               NUMBER(10),
    SLLOTTYPEID          CHAR(16),
    SLLOTTYPENAME        VARCHAR2(40),
    PRIORITYCODEID       CHAR(16),
    PRIORITYCODENAME     VARCHAR2(40),
    ORIGINALFACTORYID    CHAR(16),
    FACTORYNAME          VARCHAR2(30),
    WORKCENTERID         CHAR(16),
    WORKCENTERNAME       VARCHAR2(30),
    LOCATIONID           CHAR(16),
    LOCATIONNAME         VARCHAR2(40),
    PRODUCTFAMILYID      CHAR(16),
    PRODUCTFAMILYNAME    VARCHAR2(30),
    PRODUCTLINEID        CHAR(16),
    PRODUCTLINENAME      VARCHAR2(40),
    PRODUCTID            CHAR(16),
    PRODUCTNAME          VARCHAR2(40),
    PRODUCTREVISION      VARCHAR2(15),
    WORKFLOWBASEID       CHAR(16),
    WORKFLOWID           CHAR(16),
    WORKFLOWNAME         VARCHAR2(40),
    WORKFLOWREVISION     VARCHAR2(15),
    SLSTAGE              VARCHAR2(40),
    SLSTAGESEQUENCE      VARCHAR2(40),
    WORKFLOWSTEPID       CHAR(16),
    WORKFLOWSTEPNAME     VARCHAR2(40),
    STEPSEQUENCE         NUMBER(10),
    OBJECTCATEGORY       VARCHAR2(40),
    SPECBASEID           CHAR(16),
    SPECID               CHAR(16),
    SPECNAME             VARCHAR2(40),
    PROCESSSPECID        CHAR(16),
    OPERATIONGROUPID     CHAR(16),
    OPERATIONGROUPNAME   VARCHAR2(40),
    OPERATIONID          CHAR(16),
    OPERATIONNAME        VARCHAR2(30),
    SLPLAINTSUBSTRATEVENDOR       VARCHAR2(40),
    UOMID                CHAR(16),
    UOMNAME              VARCHAR2(40),
    OWNERID              CHAR(16),
    HOLDREASONID         CHAR(16),
    HOLDREASONNAME       VARCHAR2(40),
    GDPW                 NUMBER,
    MOVEINQTY            NUMBER,
    MOVEINQTY2           NUMBER,
    MOVEINTIMESTAMP      DATE,
    QTY                  NUMBER,
    QTY2                 NUMBER,
    REWORKTOTALCOUNT     NUMBER(10),
    INPROCESS            NUMBER(10),
    INREWORK             NUMBER(10),
    FASTCYCLETIME        NUMBER,
    NORMALCYCLETIME      NUMBER,
    CONTAINERCOMMENTS    VARCHAR2(2000),
    SCHEDULEDATE         DATE,
    SALESORDERNUMBER     VARCHAR2(40),
    EXPECTEDSTARTDATE    DATE,
    EXPECTEDENDDATE      DATE,
    EXPECTEDENDWEEK      VARCHAR2(2),
    FACTORYSTARTDATE     DATE,
    FACTORYSTARTDATEGMT  DATE,
    DUEDATE              DATE,
    DUEDATEGMT           DATE,
    ORIGINALSTARTDATE    DATE,
    ORIGINALSTARTDATEGMT DATE,
    PLANNEDSTARTDATE     DATE,
    PLANNEDSTARTDATEGMT  DATE,
    MASKLAYERID          CHAR(16) ,
    MASKLAYERNAME        VARCHAR2(40),
    DESCRIPTION          VARCHAR2(255),
    C3                   NUMBER,
    C4                   NUMBER,
    C5                   NUMBER,
    STDCT_H              NUMBER,
    REAL_H               NUMBER,
    PROCESSDIFF_H        NUMBER,
    ORIGINAL_NORMALCT_H NUMBER default 0,
    ORIGINAL_FASTCT_H NUMBER default 0
)
```
## R_WIP_MOVE (投入產出明細表)
```sql=
create table R_WIP_MOVE
(
    PRODUCTID                  CHAR(16),
    PRODUCTNAME                VARCHAR2(40),
    PRODUCTREVISION            VARCHAR2(15),
    PRODUCTBASEID              CHAR(16),
    PRODUCTLINEID              CHAR(16),
    PRODUCTLINENAME            VARCHAR2(40),
    PRODUCTFAMILYID            CHAR(16),
    PRODUCTFAMILYNAME          VARCHAR2(30),
    GDPW                       NUMBER,
    WORKFLOWBASEID             CHAR(16),
    WORKFLOWID                 CHAR(16),
    WORKFLOWNAME               VARCHAR2(40),
    WORKFLOWREVISION           VARCHAR2(15),
    SLSTAGE                    VARCHAR2(40),
    SLSTAGESEQUENCE            VARCHAR2(40),
    WORKFLOWSTEPID             CHAR(16),
    WORKFLOWSTEPNAME           VARCHAR2(40),
    STEPSEQUENCE               NUMBER(10),
    WAFERSCRIBENUMBER          VARCHAR2(40),
    CONTAINERID                CHAR(16),
    CONTAINERNAME              VARCHAR2(30),
    STATUS                     NUMBER(10),
    QTY                        NUMBER,
    QTY2                       NUMBER,
    UOMID                      CHAR(16),
    MOVEINTIMESTAMP            DATE,
    LASTMOVEOUTTIMESTAMP       DATE,
    SCSLASTMOVEOUTTIMESTAMPGMT DATE,
    MOVEINQTY                  NUMBER,
    MOVEINQTY2                 NUMBER,
    PRIORITYCODEID             CHAR(16),
    FACTORYSTARTDATE           DATE,
    FACTORYSTARTDATEGMT        DATE,
    DUEDATE                    DATE,
    DUEDATEGMT                 DATE,
    ORIGINALSTARTDATE          DATE,
    ORIGINALSTARTDATEGMT       DATE,
    PLANNEDSTARTDATE           DATE,
    PLANNEDSTARTDATEGMT        DATE,
    DIESIZE                    NUMBER,
    GRADE                      VARCHAR2(40),
    NDPW                       NUMBER,
    ORIGINALNDPW               NUMBER,
    PRODUCTIONGRADE            VARCHAR2(40),
    PSSGRADE                   VARCHAR2(40),
    TXNTIMESTAMP               DATE,
    VENDORNAME                 VARCHAR2(40),
    VENDORLOTNUMBER            VARCHAR2(40),
    WAFERSIZE                  NUMBER,
    LOTWAFERSID                CHAR(16) not null,
    RUNNUMBER                  VARCHAR2(40),
    RUNNUMBERSETUPID           CHAR(16),
    RUNNUMBERSETUPNAME         VARCHAR2(40),
    EQUIPMENTNAME              VARCHAR2(40),
    SCHEDULEDATE               DATE,
    SALESORDERNUMBER           VARCHAR2(40),
    EXPECTEDSTARTDATE          DATE,
    EXPECTEDENDDATE            DATE,
    ORDERSTARTDATE             DATE,
    ORDERSTARTDATEGMT          DATE,
    OTD                        NUMBER,
    ITO                        VARCHAR2(40),
    METAL                      VARCHAR2(40),
    METALTOOLING               VARCHAR2(40),
    FURANCE                    VARCHAR2(40),
    FURANCEBATCH               VARCHAR2(40),
    PROCESSTIME                DATE,
    STDPROCESSTIME             DATE,
    OVERPROCESSTIME            DATE
)
```

## 測試!同LOT同站點有多筆資料，如何透過rownum抓最後一筆
```sql=
select row_number() over (partition BY c.CONTAINERID, hml.WORKFLOWSTEPID order by TXNDATE desc) rownumber,
       hml.TXNDATE + INTERVAL '-8' HOUR    as                                              rptdate,
       hml.TXNDATEGMT + INTERVAL '-8' HOUR as                                              rptdategmt,
       c.CONTAINERID,
       c.CONTAINERNAME
from HISTORYMAINLINE@meslink hml
         inner join Container@meslink c on hml.CONTAINERID = c.CONTAINERID
         inner join WORKFLOWSTEP@meslink wfs on hml.WORKFLOWSTEPID = wfs.WORKFLOWSTEPID
         inner join PRODUCT@meslink p on p.PRODUCTID = hml.PRODUCTID
where hml.CDONAME = 'MoveInLot'
  and c.containerid = '48810380000003d5'
  and hml.workflowstepid = '00074e80000004d2'
  and to_char(hml.TXNDATE + INTERVAL '-8' HOUR, 'yyyyMMdd') = '20190909';
  ```
  ## V_PRODSTEP
```sql=
  create view V_PRODSTEP as
select
        TXNDATE + INTERVAL '-8' HOUR as rptdate,
        TXNDATEGMT + INTERVAL '-8' HOUR as rptdategmt,
        CONTAINERID,
        CONTAINERNAME,
        CDONAME,
        OBJECTTYPE,
        PRODUCTID,
        PRODUCTNAME,
        WORKFLOWID,
        WORKFLOWNAME,
        SLSTAGE,
        SLSTAGESEQUENCE,
        WORKFLOWSTEPID,
        WORKFLOWSTEPNAME,
        STEPSEQUENCE,
        PROCESSSPECID,
        SLPNSTAGEID,
        SLPNSTAGENAME
from V_WIPSTEP
```
  ## V_STEP
  ```sql=
create or replace view V_STEP as
select WFS.WORKFLOWID,
       WFB.WORKFLOWNAME,
       WF.WORKFLOWREVISION,
       WFS.SLSTAGE,
       WFS.SLSTAGESEQUENCE,
       WFS.WORKFLOWSTEPID,
       WFS.WORKFLOWSTEPNAME,
       WFS.SEQUENCE as STEPSEQUENCE
from WORKFLOWSTEP@MESLINK WFS
         LEFT JOIN WORKFLOW@MESLINK WF ON WF.WORKFLOWID = WFS.WORKFLOWID
         INNER JOIN WORKFLOWBASE@MESLINK WFB ON WFB.WORKFLOWBASEID = WF.WORKFLOWBASEID
  ```
  ## V_STEPSPEC
  此VIEW解決WORKFLOWSTEP SPECID為0的情況
  ```sql=
create view V_STEPSPEC as
    select b.SPECBASEID, b.SPECID, WORKFLOWID, WORKFLOWSTEPID, SEQUENCE as STEPSEQUENCE
    from WORKFLOWSTEP@meslink a
             inner join SPEC@meslink b on a.SPECBASEID = b.SPECBASEID
    union
    select b.SPECBASEID, b.SPECID, WORKFLOWID, WORKFLOWSTEPID, SEQUENCE as STEPSEQUENCE
    from WORKFLOWSTEP@meslink a
    inner join SPEC@meslink b on a.SPECID = b.SPECID
  ```
 ## V_STEPCT
 ```sql=
create or replace view V_STEPCT as
select distinct WORKFLOWID, WORKFLOWSTEPID ,STEPSEQUENCE,
                sp.SPECID,
                NVL(FASTCYCLETIME, 0)   as FASTCYCLETIME,
                NVL(NORMALCYCLETIME, 0) as NORMALCYCLETIME
from V_STEPSPEC@meslink sp
         left join (
    SELECT SPECID,
           FASTCYCLETIME,
           NORMALCYCLETIME
    FROM SPECSCHEDULINGDETAIL@meslink
) ct on ct.SPECID = sp.SPECID
order by sp.WORKFLOWID
 ```
 ## TMP_STEPCT_DETAIL 
 ```sql=
 create table TMP_STEPCT_DETAIL
(
    CONTAINERID     CHAR(16),
    WORKFLOWID      CHAR(16),
    WORKFLOWSTEPID  CHAR(16),
    STEPSEQUENCE    NUMBER(10),
    NORMALCYCLETIME NUMBER,
    FASTCYCLETIME   NUMBER
)
 ```
 # Function 
 ## 計算等待時間

 ```sql=
 CREATE OR REPLACE FUNCTION CALCULATE_WATITIME(IS_INPROCESS NUMBER, IS_INREWORK NUMBER, MOVEINTIMESTAMP DATE)
    RETURN CHAR
AS
BEGIN
    IF NVL(IS_INPROCESS, 0) = 1 AND NVL(IS_INREWORK, 0) = 0 THEN
        RETURN TO_CHAR(SYSDATE - NVL(MOVEINTIMESTAMP, SYSDATE), '99990.999');
    ELSE
        RETURN NULL;
    END IF;
END CALCULATE_WATITIME;
 ```
 ## CALCULATE_ACTUAL_DATE
```sql
create FUNCTION CALCULATE_ACTUAL_DATE(OBJECTCATEGORY VARCHAR2, PROCESSSPECID VARCHAR2, MOVEOUTTIMESTAMP DATE)
    RETURN DATE
AS
BEGIN
    IF (OBJECTCATEGORY = 'INVENTORY' AND PROCESSSPECID IS NOT NULL) THEN
        RETURN MOVEOUTTIMESTAMP;
    ELSE
        RETURN NULL;
    end if;
END CALCULATE_ACTUAL_DATE;
/

```
## package
```sql=
create package stepmap
as
    type cursorType is ref cursor;
end;
```
 # Store Procedure
 ## getstepmap
 必須加上參數kettle才抓的到
 ```sql=
 create or replace procedure getstepmap(nouse IN STRING)
as
BEGIN
    DELETE TMP_STEPCT_DETAIL;
    FOR container IN ( SELECT CONTAINERID, WORKFLOWID, WORKFLOWSTEPID, STEPSEQUENCE FROM TMP_WIP_INFO )
        LOOP
            --             dbms_output.put_line(container.CONTAINERID || ' : ' || container.WORKFLOWSTEPID);
            INSERT INTO TMP_STEPCT_DETAIL
            (CONTAINERID, WORKFLOWID, WORKFLOWSTEPID, STEPSEQUENCE, NORMALCYCLETIME, FASTCYCLETIME)
            SELECT container.CONTAINERID, WORKFLOWID, WORKFLOWSTEPID, STEPSEQUENCE, NORMALCYCLETIME, FASTCYCLETIME
            from V_STEPCT
            WHERE WORKFLOWID = container.WORKFLOWID
              AND STEPSEQUENCE <= container.STEPSEQUENCE;
        END LOOP;
END;
 ```


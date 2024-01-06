---
tags: 預算
---

中央政府總預算改
==============

已整理各單位預算資料：https://govmoney.g0v.ronny.tw/
進度介紹影片：https://youtu.be/6iQYXlIHHI8

data.gov.tw 內現況
-----------------
- 以下資料是 2021-06-23 抓取
- 總共有 49851 資料集，其中有 8871 筆包含「預算」、「決算」、「會計」關鍵字
- 8871 個資料集一共有 33238 個資料資源
- 檔案格式如下：
```
      4 application/vnd.openxmlformats-officedocument.spreadsheetml.sheet
      5 application/vnd.openxmlformats-officedocument.wordprocessingml.document
      6 message/news
      7 application/msword
     21 application/vnd.ms-excel
     36 application/x-dosexec
    169 application/vnd.oasis.opendocument.spreadsheet
    536 application/x-rar
    539 application/pdf
    804 application/x-7z-compressed
    991 text/xml
   5411 text/plain
   7493 text/html
  16694 application/zip
  ```
- XML 格式統計如下：
```
{"nullbean":9,
"Root-Row-科目名稱":35,
"url-link-trash":355,
"Root-Row-職能別分類經濟性分類":1097,
"unknown":1246,
"Root-Row-款":1313,
"dw_agrm":5911,
"bcme":8313,
"unknown-notxml":8340,
"GenericData-報表":11118,
"BCT":13889,
"CGBA":116956}
```

## XML 格式
### CGBA 會計月報
```
<?xml version="1.0" encoding="UTF-8" ?>
<CGBA0551C_會計月報_平衡表>
    <CGBA0551C_會計月報_平衡表_row>
        <會計年度>106</會計年度>
        <月份>01</月份>
        <基金別>1</基金別>
        <會計分類>1</會計分類>
        <使用機關別>2</使用機關別>
        <科目分類>1</科目分類>
        <會計科目編號>110103</會計科目編號>
        <會計科目名稱>專戶存款</會計科目名稱>
        <金額>621248829</金額>
    </CGBA0551C_會計月報_平衡表_row>
```

### dw_agrm
```
<?xml version="1.0" encoding="big5" standalone="no"?>

<dw_agrm1040_report><dw_agrm1040_report_row><dw_agrm1040_report_group1><budgetyear>103</budgetyear><dw_agrm1040_report_g
roup2><go_ordinary>3</go_ordinary><sort1>1</sort1><expid></expid><budgetno7>04000000000</budgetno7><samt9>10000.00</samt
9><samt10>0</samt10><samt11>0</samt11><samt12>0</samt12><samt15>2265.00</samt15><samt16>0</samt16><samt17>2265.00</samt1
7><samt18>0</samt18><samt19>0</samt19><samt20>0</samt20><samt23>2265.00</samt23><samt24>2265.00</samt24><useno></useno><
subp1></subp1><subp2></subp2><agenitemserialno1>02</agenitemserialno1><agenitemserialno2>00</agenitemserialno2><agenitem
serialno3>00</agenitemserialno3><agenitemserialno4>00</agenitemserialno4><budgetnochk>2</budgetnochk><budgetname>�@�ڤ ν��
v���J</budgetname><objectname></objectname><subprojectname></subprojectname><subp2_name></subp2_name><go_level>2</go_lev
el><go_word></go_word><go_no></go_no></dw_agrm1040_report_group2><dw_agrm1040_report_group2><go_ordinar
```

### BCME3410
```
<?xml version="1.0" encoding="UTF-8"?>
<tables>
    <BCME3410_row>
        <mh_itemserialno1/>
        <mh_itemserialno2/>
        <mh_itemserialno3/>
        <mh_itemserialno4/>
        <budgetno/>
        <mh_budgetname>合         計</mh_budgetname>
        <budgetno_conver/>
        <tyear_amt>67783.000000</tyear_amt>
        <lyear_amt>65472.000000</lyear_amt>
        <byear_amt>68652.000000</byear_amt>
        <b_amt>2311.000000</b_amt>
        <bc_content/>
        <blevel>9</blevel>
        <ordinaryid>1</ordinaryid>
    </BCME3410_row>
```

### BCTDBUDGETDETAIL
```
<?xml version="1.0" encoding="UTF-8"?>
<tables>
    <BCTDBUDGETDETAIL>
        <BCTDBUDGETDETAIL_row>
            <ba_fiscalyear>110</ba_fiscalyear>
            <ba_fundkind>1</ba_fundkind>
            <ba_budgetkind>1</ba_budgetkind>
            <ba_specialbudgetno/>
            <ba_agenno>05051</ba_agenno>
            <ba_agentype>C</ba_agentype>
            <ba_budgetstate>2</ba_budgetstate>
            <ba_versiondate/>
            <ba_budgetyear>110</ba_budgetyear>
            <ba_budgetno>04050510101</ba_budgetno>
            <ba_subprojectno>xxxx</ba_subprojectno>
            <mj_subprojectname/>
            <ba_departno>07</ba_departno>
            <ba_objectno>xxxxxxxx</ba_objectno>
            <ba_budgettype>R</ba_budgettype>
            <ba_budgetsource>1</ba_budgetsource>
            <ba_mergetype>1</ba_mergetype>
            <ba_budgetamt>10000.00</ba_budgetamt>
            <ba_flowflag/>
            <ba_signflag/>
            <ba_signno/>
            <ba_key>11  </ba_key>
```

Root/Row
```
<?xml version="1.0" encoding="UTF-8"?>
<Root>
    <Row>
        <款>4</款>
        <項/>
        <目/>
        <節/>
        <科目名稱>司法院主管</科目名稱>
        <預算科目編號>00050000000</預算科目編號>
    </Row>
    <Row>
        <款/>
        <項>22</項>
        <目/>
        <節/>
        <科目名稱>臺灣南投地方法院</科目名稱>
        <預算科目編號>00050510000</預算科目編號>
        <人事費>284145</人事費>
        <業務費_經>54283</業務費_經>
        <奬補助費_經>54</奬補助費_經>
        <債務費>0</債務費>
        <預備金_經>513</預備金_經>
        <經常支出小計>338995</經常支出小計>
        <業務費_資>0</業務費_資>
        <設備及投資>4369</設備及投資>
        <奬補助費_資>0</奬補助費_資>
```

### GenericData

```
<?xml version="1.0" encoding="UTF-8"?>
<GenericData>
　　<Header>
　　　　<Table Id="FNWFWORKR" Name="收支餘絀決算表" Domain="SFUND" />
　　　　<Program Id="FNWGRB0040" />
　　　　<Sender Name="國立高級中等學校校務基金" />
　　　　<報表名稱>收支餘絀決算表</報表名稱>
　　　　<年度>109</年度>
　　　　<基金>國立高級中等學校校務基金</基金>
　　　　<階段>自編決算</階段>
　　　　<版本>1</版本>
　　　　<單位>新臺幣元</單位>
　　</Header>
　　<DataSet>
　　　　<ROW>
　　　　　　<SEQNO>1</SEQNO>
　　　　　　<LEVEL>02</LEVEL>
　　　　　　<BOLD>1</BOLD>
　　　　　　<科目>業務收入</科目>
　　　　　　<本年度預算數-金額>29535891000</本年度預算數-金額>
　　　　　　<本年度預算數-百分比>100.00</本年度預算數-百分比>
　　　　　　<本年度決算數-金額>30744877125</本年度決算數-金額>
　　　　　　<本年度決算數-百分比>100.00</本年度決算數-百分比>
　　　　　　<比較增減-金額>1208986125</比較增減-金額>
　　　　　　<比較增減-百分比>4.09</比較增減-百分比>
```

### nullBean
```
<?xml version="1.0" encoding="UTF-8"?>
<tables>
    <nullBean>
        <nullBean_row>
            <be_fiscalyear>104</be_fiscalyear>
            <be_fundkind>1</be_fundkind>
            <be_budgetkind>1</be_budgetkind>
            <be_specialbudgetno/>
            <be_agenno>51005</be_agenno>
            <be_agentype>B</be_agentype>
            <be_budgetstate>2</be_budgetstate>
            <be_budgetsource>1</be_budgetsource>
            <be_budgetno/>
            <be_ordinaryid/>
            <be_budgettype/>
            <be_caseno>01</be_caseno>
            <be_exectype/>
            <be_applyid>0</be_applyid>
            <be_versiondate/>
            <oeme>null
null</oeme>
            <reme>null
null</reme>
            <list1>
                <list1_row>
                    <be_fiscalyear>104</be_fiscalyear>
                    <be_fundkind>1</be_fundkind>
```
```
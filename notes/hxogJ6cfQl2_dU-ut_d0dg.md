---
title: "長期照顧"
tags: hackpad
---

# 長期照顧

> [點此觀看原始內容](https://g0v.hackpad.tw/eX7IO2HhUZW)


Q:服務提供者有的是醫療背景, 有的是社服背景 ; 經費部分有的是NGO/NPO, 有的是拿政府預算;  但是這些服務提供者分散各地, 民眾無法一覽到底所在的地區有多少服務提供者, 有多少不同的服務形態, 聯絡方式為何?

A: 預計產出:
1.  盤點資料 (公部門 opendata 將來資料一個月update一次) + 其他NGO (如羅慧夫)
2.  做到g0v地圖layer 上 (含基本資料, 床位, 人力 etc)
3.  不同service 點選不同layer , 方便民眾就近選擇
4.  提供social network 供大家評分 ( 因為目前並無第三方公評機構)
5.  提供使用者于網頁輸入部分資料(避免完整個資), 透過查詢機制, 產生
    1.  可利用的資源
    2.  可提供服務的機構清單
    3.  申請該項服務需要準備之文件

P:
1.  公部門不見得會將 "非政府出資" 的服務提供單位資料一起呈現

Reference :
1.  公部門 : [護理及健康照護司首頁](http://www.mohw.gov.tw/cht/DONAHC/Index.aspx)
2.  法源 : [長期照護保險法草案](https://ly.g0v.tw/bills/1619L13287)

Data:  data.gov.tw
Origin : [安養機構名冊](http://data.gov.tw/iisi/logaccess?dataUrl=http%3A%2F%2Fwww.sfaa.gov.tw%2FSFAA%2FPages%2Fashx%2FFile.ashx%3FFilePath%3D%7E%2FFile%2FAttach%2F2630%2FFile_3754.xls&type=CSV&nid=8577) , excel file
> **收容對象** 和 **核定收容人數** 不太好 parse， (這兩個欄位應該是動態更新?)
> [name=lanfon]

> 8/26 新檔案, 不知多久 update 一次. 不過內部消息, 大盤點中
> [name=Tom S]

JSON 格式: [https://gist.github.com/lanfon72/52b849b834dfd73a8738](https://gist.github.com/lanfon72/52b849b834dfd73a8738)
csv: [https://gist.github.com/lanfon72/390970e3235d73602a7d](https://gist.github.com/lanfon72/390970e3235d73602a7d)
> 缺 **核定收容人數** 和 **收容對象** 兩個欄位，json內容主要是機構基本資料
> [name=lanfon]

> 可能會需要 re-parse，部份電話有多筆(且格式不完全相同，有些中間會有「- 」)
> [name=lanfon]

> btw, 記得用 utf8 + 開...
> [name=lanfon]



( 以下待盤點
### 各縣市長照管理中心


### 機構式

亞急性慢性病機構
!護理之家
!長期照護機構
!安養機構
!養護機構
榮民之家
!老人公寓
!身心障礙機構


### 居家式

居家護理
居家營養/復健
居家服務
送餐服務
緊急救援通報系統
居家無障礙設施改善
喘息服務
!輔具購買租借
> 衛生福利部社會及家庭署多功能輔具資源整合推廣中 [http://repat.sfaa.gov.tw/catr/page/](http://repat.sfaa.gov.tw/catr/page/)
> [name=Clement T]

> 衛生福利部社會及家庭署多功能輔具資源整合推廣中心（國立陽明大學ICF暨輔助科技研究中心）[http://repat.sfaa.gov.tw/](http://repat.sfaa.gov.tw/)
> [name=Clement T]

> [行無礙資源推廣協會](http://www.sunable.net/node/513)
> [name=che l]

> 財團法人第一社會福利基金會附設第一輔具資源中心
> [name=che l]

> 新北市輔具資源中心
> [name=che l]

> 台中市肢體傷殘關懷協會
> [name=che l]

> [桃園縣輔具資源中心](http://www.tyad.org.tw/tyatc/)
> [name=che l]


### 社區式

!日間照顧
!送餐服務
!關懷據點
!喘息服務

日托
照顧住宅
老人住宅
家庭託顧
社區定點用餐

### 其他

交通服務
聯結式服務
呼吸器照護
安寧照護
失智症/植物人照護

潛在服務提供者: 但服務提供項目不確定
1.  醫院 [https://gist.github.com/clkao/760f162de2bb7e832224](https://gist.github.com/clkao/760f162de2bb7e832224)
2.  NGO [https://github.com/pm5/npo-data/blob/master/data/npolist.json](https://github.com/pm5/npo-data/blob/master/data/npolist.json)
3.  其他私人機構

範例
桃園縣[喘息服務地圖 ](http://www.care.tychb.gov.tw/gmap2/index.asp?Parser=99,5,93,92)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2eee3b56b17e5193e9e339553631e545)


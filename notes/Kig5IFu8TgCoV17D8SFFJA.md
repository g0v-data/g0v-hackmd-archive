---
title: "中研院「社會變遷全記錄」半自動化計畫"
tags: hackpad
---

# 中研院「社會變遷全記錄」半自動化計畫

> [點此觀看原始內容](https://g0v.hackpad.tw/UssOWtAVda9)


## 專案簡介


### 緣由


中研院[台灣社會變遷全紀錄](http://www.ios.sinica.edu.tw/TSCpedia/index.php/%E5%8F%B0%E7%81%A3%E7%A4%BE%E6%9C%83%E8%AE%8A%E9%81%B7%E5%85%A8%E8%A8%98%E9%8C%84)，記載各大主題及面向的社會變遷，主要內容來自[社會變遷調查](http://survey.sinica.edu.tw/srda/TSCS_topic.htm)  （自 1985 年起），以及其他各種政府統計。

但是因為全記錄涵蓋的面向廣、更新不易，希望能建立一個簡便的機制，連結各個議題所使用的「調查問卷題號」與「政府統計」，讓每個議題可以自動化更新所連結的相關數字，並且鼓勵關心不同面向的社群，就這些基礎資料來進行研究或書寫。

推廣使用方面，希望提供三種層次的資料，讓有興趣的人，可以逐步理解如何使用調查資料：
1.  第一步是讓有興趣的人，可以先快速瀏覽資料，不用 excel 或太多資料處理，就能˙進行簡單分析，以了解資料特性。例如列出歷年快不快樂指數在性別上的差異。
2.  第二步是如果覺得資料有趣，那可以開始看一些既有的資料整理，此部份可參見[台灣社會變遷全記錄i](http://www.ios.sinica.edu.tw/TSCpedia/index.php/%E5%8F%B0%E7%81%A3%E7%A4%BE%E6%9C%83%E8%AE%8A%E9%81%B7%E5%85%A8%E8%A8%98%E9%8C%84) ）
3.  第三步則是拿逐年的原始資料來使用，需要建立起撿變得機制，連結跨年份不同問卷的題目。


### 要解決的問題


說明問題的 \[ [PPT](https://docs.google.com/presentation/d/1o7KEM-7As7zeA4-6pbSYjrWrPycr8TmHKGhKiM-I2JI/edit#slide=id.p3)\] ( [https://goo.gl/WRELny](https://goo.gl/WRELny) )

1.  第一步：建立可供人簡易查詢的界面
2.  第三步：半自動化連結跨年份的不同問卷 \+ 連結主計處
    1.  [http://www.ios.sinica.edu.tw/sc/cht/5.php](http://www.ios.sinica.edu.tw/sc/cht/5.php) 每期的問卷的題號不同，需要有「題目」對應「各期題號」的 master table
    2.  「題目」對應已有相關研究與論文（社會所有資料，待整理）
    3.  自動抓取主計總處列管統計

#### 舉例來說：

1.  婆媳關係研究，
> 教育程度 vs 婆婆吵架 by 年份
> [name=ddio J]

> 性別 vs 婆婆吵架 by 年份
> [name=ddio J]


### 使用統計資料：


希望有一個工具，每次有新的問卷資料或者統計資料，就能自動更新這篇文章的圖表。

資料下載位置：
- 資料： \[[sheethub](https://sheethub.com/ronnywang/%E5%8F%B0%E7%81%A3%E7%A4%BE%E6%9C%83%E8%AE%8A%E9%81%B720%E5%B9%B4)\]
- 欄位定義（有些欄位有缺字，請參見樓下 spreadsheet ）： \[[sheethub](https://sheethub.com/ronnywang/%E5%8F%B0%E7%81%A3%E7%A4%BE%E6%9C%83%E8%AE%8A%E9%81%B720%E5%B9%B4_%E6%AC%84%E4%BD%8D%E5%AE%9A%E7%BE%A9)\]
- Google Spreadsheet: [（內含各欄位數值解釋）](https://docs.google.com/spreadsheets/d/1oWDJfCdIPFt3SvcVHDV57zVzCrp1AgrRqGmNwWNIfls/edit?usp=sharing)


### 資料特性

- 欄位大多數是離散的，如性別、（和婆婆吵架是不好、有點不好、好），
    - 教育程度、收入相對連續，但也是切成區間，收入使用區間中位數當作值
- 是隨機抽樣，所以有反應當時的人口狀況，跨年份比較時，不用再平均

### 預定使用者

給想要了解台灣社會狀況，願意拿資料來作初步分析的人

### 預定功能

1.  可以透過簡單的操作，針對整理過的統計資料，產生兩個變量（或再加上時間）的圖表。
2.  [#needpeople](https://g0v.hackpad.tw/ep/search/?q=%23needpeople&via=UssOWtAVda9) 需要有人協助半自動化～

### 現有類似專案

（現成的是否可以直接使用？或者有什麼不足之處？國外專案可參考？）

### 相關專案

（衍生自某專案/衍生出某專案/API串接自某專案.）

台灣發展經驗實證資料庫 有更多其他
[https://www.most.gov.tw/hum/ch/list?menu_id=27c85f1c-c983-4f2f-8191-7183a1ac6778](https://www.most.gov.tw/hum/ch/list?menu_id=27c85f1c-c983-4f2f-8191-7183a1ac6778)

中研院調查研究專題研究中心有提供線上分析，但是一樣未串接跨期的資料，需要手動選用；且需註冊
[http://140.109.171.222/webview/index.jsp?object=http://140.109.171.222:80/obj/fStudy/C00221_1](http://140.109.171.222/webview/index.jsp?object=http://140.109.171.222:80/obj/fStudy/C00221_1)

貧富差距 [https://g0v.hackpad.com/Ko9q8O2Y1rr](https://g0v.hackpad.com/Ko9q8O2Y1rr)

世銀統計與我國統計對照 (ronnywang 有一次提的, 連結待補)

### 授權方式


Code: MIT
Document: CC-BY

### 使用資料


中研院社會變遷調查原始資料 \- 目前為學術用，正與計畫主持人溝通轉為開放授權

### 專案目前狀態


規劃

### 利益揭露


提供 use case 的的中研院社會所研究員與其研究領域相關，


## 徵求協作者


發起人/拋磚人：
- [ ] NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
- [ ] NeedsDesigner: 需要介面設計
- [ ] NeedsData: 需要資料（擷取、清理）
- [ ] NeedsTech: 需要技術支援（程式、架站 etc)
- [ ] NeedsProcess: 需要幫忙設計作業流程
- [ ] NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡


## 實作細節（非技術背景可跳填）


### 協作工具

- hackfoldr: [http://beta.hackfoldr.org/tscs](http://beta.hackfoldr.org/tscs)
- github repo：[https://github.com/g0v/automate.tscs](https://github.com/g0v/automate.tscs)

### 進度與 to-do

- [ ] 第一步 \- 簡易查詢界面
    - [x] 建立堪用的網站，讓路人可以自己編輯/試用圖表
    - [ ] 確認資料授權
    - [ ] 編輯說明文件
    - [ ] 自動對應編碼與問題，以及各數值代表的意義，顯示在網頁上
- [ ] 第三步 \- 半自動化資料連結


## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）


### 如果有做出成果可以往這邊丟丟看

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8f36a1c9eb7783e8f8713d8063118b9c)
不同年齡對於離婚是否有錯看法(1=非常錯;  2=相當錯;  3=有點錯;  4=沒有錯)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_56bd7a440731d72e3dd5b50d15936aac)
不同調查年份對於離婚是否有錯看法變化(1=非常錯;  2=相當錯;  3=有點錯;  4=沒有錯)

### 用 Grafana + InfluxDB 來作簡易版視覺化工具


[http://](http://140.109.240.72/dashboard/db/po-xi-chao-jia-20-nian-bian-hua-tu)[140.109.240.72](http://140.109.240.72/dashboard/db/po-xi-chao-jia-20-nian-bian-hua-tu)[/dashboard/db/po-xi-chao-jia-20-nian-bian-hua-tu](http://140.109.240.72/dashboard/db/po-xi-chao-jia-20-nian-bian-hua-tu)

所有欄位同時是 field 也是 tag ，所以可以同時使用，匿名可編輯不可存檔。

婆媳吵架 20 年變化：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ddc891f8b59d9d2eac6ec5706224d6b7)
編輯界面：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b684b2d6d3561967f6c098928248f338)
1.  先點 FROM，選 basic_88
2.  再點 SELECT ，選擇想要的欄位
3.  再點 GROUP BY 的 + 號，選想要的第二象限

> 目前跑在弱弱的aws  t2.medium 上，==好像很容易被玩壞== XD 想玩的請自架用上面的 git 架，全都自動化惹～～
> [name=ddio J]

> 看起來蠻好用的...下一步可能應該用議題來推這樣的應用...感謝!
> [name=Lin T]



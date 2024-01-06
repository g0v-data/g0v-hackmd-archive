---
title: "開放政治獻金 - 資料說明"
tags: CY 零時監察院,hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/cnmUlDwCooX)



### 監察院政治獻金專戶

監察院一共有 6000 多個政治獻金專戶，專戶名稱會是「第16屆苗栗縣竹南鎮鎮長補選擬參選人陳碧華政治獻金專戶」這種格式
同一個人可能會有多個獻金專戶，Ex: 丁守中有 「第8屆立法委員擬參選人丁守中政治獻金專戶」「第7屆立法委員擬參選人丁守中政治獻金專戶」「第6屆立法委員擬參選人丁守中政治獻金專戶」三個專戶。
查詢網址: [http://sunshine.cy.gov.tw/GipOpenWeb/wSite/sp?xdUrl=/wSite/PoliticAccount/PAQuery.jsp&ctNode=353](http://sunshine.cy.gov.tw/GipOpenWeb/wSite/sp?xdUrl=/wSite/PoliticAccount/PAQuery.jsp&ctNode=353)
資料打包: [https://github.com/ronnywang/sunshine.cy.gov.tw/blob/master/list.csv](https://github.com/ronnywang/sunshine.cy.gov.tw/blob/master/list.csv) \[資料更新時間: 2014/4/20\]

### 監察院政治獻金專戶會計總表

[http://sunshine.cy.gov.tw](http://sunshine.cy.gov.tw) 有提供會計總表功能，只包含各項目總合不包含細項，在上面的查詢網址進去就可以下載到 PDF 版本，而也有 [Finjon Kiang](https://g0v.hackpad.tw/ep/profile/G4yGGowBe3x) 幫忙將資料匯出在 [https://github.com/kiang/sunshine.cy.gov.tw/tree/master/report2txt](https://github.com/kiang/sunshine.cy.gov.tw/tree/master/report2txt)
如有需要較好用資料可以至上面網址下載

### 調查兵團原始圖檔資料

這邊是靠人力衝進監察院中取出的文件掃描的圖檔
[http://bit.ly/ScanPoliticalContribution](http://bit.ly/ScanPoliticalContribution)

### 表格框線位置資料

拿到原始圖檔後， Ronny Wang 會把他全部傳到 PIXNET 相簿去，並且依照處理日期生出一個 listMMDD.csv 的檔案，Ex: [list0610.csv](https://github.com/ronnywang/tw-campaign-finance/blob/master/list0610.csv) 裡面的資訊就只有 1\. 調查兵團上傳的原始檔名 2. 頁碼 3. 上傳到 PIXNET 後的網址

接下來，會用 [search-all-line2.php](https://github.com/ronnywang/tw-campaign-finance/blob/master/scripts/search-all-lines2.php) 這隻程式將 list0610.csv 的每一張圖檔都偵測一次表格線段，找出所有的水平線位置和垂直線位置，並且會生出一個 [output0610.csv](https://github.com/ronnywang/tw-campaign-finance/blob/master/output0610.csv) ，每一張圖片會多出一個 id 欄位，id 會對應到 output0610/{id}.json 放這圖所找到的所有垂直線和水平線的資料，以及這兩種線交會的所有交點座標 Ex: [output0610/10.json](https://github.com/ronnywang/tw-campaign-finance/blob/master/output0610/10.json)

為了校對，也有生出一個 edit0610.html \[[程式碼](https://github.com/ronnywang/tw-campaign-finance/blob/master/edit0610.html)\]\[[瀏覽](http://ronnywang.github.io/tw-campaign-finance/edit0610.html)\] ，Ronny Wang 會用這工具看看是否切豆腐程式有漏抓的框線，再人工加上漏抓的線並把更新的 json 換掉 (這部份求坑，希望有更方便的校對頁面)

最後會將 output0610.csv 裡面的檔名統一改成「{帳戶名}-{收支科目}-{資料開始日期}-{資料結束日期}」 「第11屆臺北市議員擬參選人厲耿桂芳政治獻金專戶-收入-099/05/24-099/12/21」，表格框線動作就完成了。
以上的程式都放在 [https://github.com/ronnywang/tw-campaign-finance](https://github.com/ronnywang/tw-campaign-finance)

### 豆腐資料 API

產生出來的 output0610.csv ，會透過 [https://github.com/ronnywang/campaign-finance.g0v.ronny.tw/blob/master/webdata/scripts/import.php](https://github.com/ronnywang/campaign-finance.g0v.ronny.tw/blob/master/webdata/scripts/import.php)  這隻 script上傳到 [http://campaign-finance.g0v.ronny.tw/](http://campaign-finance.g0v.ronny.tw/) 並且得到一個 page id，接下來可以透過 [http://campaign-finance.g0v.ronny.tw/table/show/](http://campaign-finance.g0v.ronny.tw/table/show/){id} 這個網址取得該 page 相關的所有 API ，包含
1.  [http://campaign-finance.g0v.ronny.tw/api/tables/](http://campaign-finance.g0v.ronny.tw/api/tables/){id} 取得該頁相關資訊，包含他有幾行有幾列，他的檔名和頁碼是什麼
2.  [http://campaign-finance.g0v.ronny.tw/api/getcellimage/](http://campaign-finance.g0v.ronny.tw/api/getcellimage/)[{](http://campaign-finance.g0v.ronny.tw/api/getcellimage//第幾行/第幾列.png)id}/第幾行/第幾列.png 可以取得第幾格的圖檔

另外也可以透過 [http://campaign-finance.g0v.ronny.tw/api/gettables](http://campaign-finance.g0v.ronny.tw/api/gettables) 這個 API 取得到所有的頁面的資訊 (內容大小約 2MB)

以上功能都是放在 [http://campaign-finance.g0v.ronny.tw/](http://campaign-finance.g0v.ronny.tw/) 這邊只管圖的切豆腐供其他應用使用，不管圖的內容判斷以及 OCR 的部份。

### 鄉民 OCR API

有了每一格豆腐之後，會在 [Timothy Lee](https://g0v.hackpad.tw/ep/profile/Caoe3JBMnxk) 寫的 [http://campaign-finance.g0v.ctiml.tw/](http://campaign-finance.g0v.ctiml.tw/) 把他同步過來，透過 PageInfo::addPage($id) 就會將上面的豆腐資料 API 的新頁同步過來並且開啟新關卡

因為鄉民已經開始輸入資訊了，所以每一格就會開始累積鄉民的輸入資料，鄉民 OCR API 提供以下 API
1.  [http://campaign-finance.g0v.ctiml.tw/api/getcells/345](http://campaign-finance.g0v.ctiml.tw/api/getcells/345) 取得某一頁內每一格的最新一筆資料 (這邊只顯示最新一筆，因此有可能最新一筆錯的資料蓋掉前面舊的) ，這邊的 page id 與上面豆腐資料 API 是一樣的
2.  [http://campaign-finance.g0v.ctiml.tw/api/getcellvalue/345/6/7](http://campaign-finance.g0v.ctiml.tw/api/getcellvalue/345/6/7) 取得某一頁內某一格的所有鄉民輸入記錄，裡面包含每一筆的輸入時間、輸入的值以及他的 IP (這個 IP 是加密過的，無法反推回原 IP ，但是同 IP 都會是同一人)

另外更完整的資料可以透過 [dump-history.php](https://github.com/ctiml/campaign-finance.g0v.ctiml.tw/blob/master/webdata/scripts/dump-history.php) 匯出，2014年5月有一次匯出檔放在 [http://ronnywang-public.s3](http://ronnywang-public.s3.amazonaws.com/opendata/campaign-finance/ans.csv)[.amazonaws.com/opendata/campaign-finance/ans.csv](http://ronnywang-public.s3.amazonaws.com/opendata/campaign-finance/ans.csv) 約 300 萬行 100MB (IP 的部份也有加密過) ，已經可以用這些資料分析出正確答案了

### 最終結果

有了鄉民 OCR 結果，每一格都有三到五人輸入過，接下來透過 [Cheng-Yu Lin](https://g0v.hackpad.tw/ep/profile/nXAx9dGG8ZR) 的幫忙，他將上面 鄉民OCR API 產生的 ans.csv 計算出每一格最可能的正確答案，程式和結果放在 [https://github.com/ntuaha/GovCash](https://github.com/ntuaha/GovCash)

> 該專案位置[README](https://github.com/ntuaha/GovCash/blob/master/README.md)已經放入**處理資料**的流程說明
> [name=Cheng-Yu L]

> 此外，資料裡面有很多
> [name=Cheng-Yu L]


每一行的猜測答案放在 [https://github.com/ntuaha/GovCash/blob/master/data/govcash.csv](https://github.com/ntuaha/GovCash/blob/master/data/govcash.csv)
這邊包含每一行是屬於哪一頁(來自 豆腐 API 的 page id )、第幾行、那一行的值以及信心度

另外也有結合豆腐 API 的 gettables 的內容，將每一個專戶分出來的檔案，放在 [https://github.com/ronnywang/GovCash/tree/master/accounts](https://github.com/ronnywang/GovCash/tree/master/accounts)
這邊就已經是最終目標還原回來的 CSV 了


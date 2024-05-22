# Introduction to Database Systems

**資料階層:**
資料（Data）
「資料」（Data）是指收集但是沒有經過整理和分析的原始數值、文字或符號，它是資訊的原始型態。本身沒有意義，需要經過處理後，才會成為資訊（Information）。

資訊（Information）
「資訊」（Information）是經過處理的資料，在經過整理和分析後，就可以成為有用或可供決策的資訊。

「資料處理」（Data Processing）是使用特定方法將資料轉換成資訊的過程，我們需要將資料進行搜尋、排序、分類、計算、收集、選取或結合等操作，以便產生所需的資訊。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_67d40fcc296e6b1b0bf2b37f93e72379.png)

資料階層
資料一共分成六個階層：位元、位元組、欄位、記錄、檔案和資料庫。
 
欄位(Field、Column或Attribute)是由1或多個位元組或字元組成，屬於相同性質資料組成的資料項目，以欄位名稱來識別。

EX: 一組字元組成的字串"Joe"和"Chen"，可以使用欄位名稱"姓名"來識別，或數值33、29，可以使用欄位名稱"年齡"來識別等。

記錄(Record、Row或Tuple)是相關欄位的集合，記 錄 的 欄 位 是 儲 存 「 實 體 」 （ Entity）的一些「屬性」（Attributes）值，實體是用來描述真實世界的東西。
EX：記錄為學生的詳細資料。
-> 姓名、年齡、地址等欄位的值。

檔案(File、Table或Relation)就是相關聯記錄的集合，檔案是以檔案名稱儲存在電腦磁碟。程式設計者可以撰寫電腦程式使用檔案名稱來開啟和存取檔案內容的記錄，其相關操作如下所示：
-> 讀取記錄。
-> 更新記錄。
-> 新增記錄。
-> 刪除記錄。

**資料庫的演進**
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_05a6acc1946ad0fc4d65450dff03d99a.png)



**資料庫系統優點**
資料庫管理系統擁有多種程式模組：查詢處理模組、交易管理和回復處理等，可以進行資料庫的資料管理，將實際資料庫結構和存取都隱藏在資料庫管理系統之後，如此可以達到：
* 多人使用，資料共享。
* 資料一致和最少的資料重複─資料不重覆出現於多個檔案。
* 資料獨立─與程式無關。
* 改進資料完整性問題─如：不可為負值的銀行帳戶。
* 更佳的資料安全管理─權限控管。
* 同步與交易管理─資料正確性確保。
* 資料備份與回復。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0c536dae8d483594490085bd78ad6b60.png)



# Batch練習



項目
- [批次分類](#批次分類)
  - [1-1] 範例 - 共用extends、execute、try-catch
  - [1-1] 觀念 - 假批次
  - [1-2] 觀念 - 真批次

- [假批次](#假批次)
  - [2-1] 範例-傳入參數
  - [2-1] 範例-假批次

- [真批次](#真批次)
  - [3-1] 範例 - 執行順序
  - [3-2] 範例 - firstProcess
  - [3-3] 範例 - searchProcess
  - [3-4] 範例 - forEachProcess
  - [3-5] 範例 - executeBatchProcess
  - [3-6] 範例 - lastProcess
  - [3-7] 範例 - finallyProcess
  - [3-8] 範例 - 計數型別 



# 批次分類

真批次通常拿來處理資料，常用的有收資料、統計，倒檔之類，需覆寫底層的既定方法，且有既定的流程，沒有滿足(回傳False或是查無資料)，就不會執行<font color="red">不會執行</font>。
也因為要有覆寫方法和既定流程，自由度沒有假批次高，但在做資料批量處理很方便，因為底層都幫你處理好了，舉例要處理9500筆資料，因為一次commit 9500筆會造成資料庫太忙，通常會做批次處理，如果一次處理1000，那會需要在那數1~1000,1001~2000...,9001~9500其實很麻煩的，所以底層針對資料處理完成很多方法只需要覆寫。

假批次通常是以前的舊寫法，或是處理其他的事情，譬如常用的迴歸批次、寄信批次、監控批次如QRT1_B100 300，700等等，寫法上很自由只要從execute進去後可以隨意呼叫，程式就是由上到下執行，沒有流程控制，其實也可以用來處理資料倒檔，但就要自己處理會比較麻煩。


## 1-1 範例 - 共用extends、execute、try-catch-finally
一定要Extends BatchBean
```java 
public class XXTP_B998 extends XX_BatchBean { // 繼承BatchBean
```
這邊跟新舊無關，批次通常透過CTM控制，我們需要回傳一個碼給CTM，才會顯示紅燈、黃燈、綠燈，再加上本來就要做例外處理，一定會用
```java 
public class XXTP_B998 extends XX_BatchBean { 

    private static final Logger log = Logger.getLogger(XXTP_B998.class);

    public void execute(String args[]) throws Exception { //從這開始
        try {

        } catch (Exception e) {
            setExitCode(ERROR); // 設定預定回傳給Control_M的訊息 , 請依需求調整
            log.fatal("執行時發生錯誤", e);
        } finally {
            printExitCode(getExitCode()); // 回傳給 Control_M 的訊息代碼 , 程式終止
		}
	}
}

```
這樣就是一個基本框架，從extends BatchBean然後execute開始到try-catch-finally


## 1-2 觀念 - 假批次
這邊不會有範例CODE，大概提個觀念，假批次很像在白紙上隨意作畫，同上面程式範例框架
如果要做FT的批次，我們假設情境
1. 要先確定傳入參數是否有sysgp,syscd或caseid
2. 查詢是否有回歸案例
3. 迴圈開啟瀏覽器進行測試
4. 統一寫入結果
5. 發送信件跟報表
6. 關閉測試機瀏覽器

```java 
public class XXTP_B998 extends XX_BatchBean { 

    private static final Logger log = Logger.getLogger(XXTP_B998.class);

    public void execute(String args[]) throws Exception { //從這開始
        try {
            1. 要先確定傳入參數是否有sysgp,syscd或caseid
            2. 查詢是否有回歸案例
            3. 迴圈開啟瀏覽器進行測試
            4. 統一寫入結果
            5. 發送信件跟報表
            6. 關閉測試機瀏覽器

        } catch (Exception e) {
            setExitCode(ERROR); // 設定預定回傳給Control_M的訊息 , 請依需求調整
            log.fatal("執行時發生錯誤", e);
        } finally {
            printExitCode(getExitCode()); // 回傳給 Control_M 的訊息代碼 , 程式終止
		}
	}
}

```
1.的部分會先檢核參數
2.的部分會去查詢
3.逐筆跑案例，將結果保存
4.將結果保存後統一
5.最後發送報表
6.最後關閉瀏覽器

我們可以把這邊所有步驟通通寫到裡面去，當然也可以在裡面try-catch知道是誰錯
```java 
public class XXTP_B998 extends XX_BatchBean { 

    private static final Logger log = Logger.getLogger(XXTP_B998.class);

    public void execute(String args[]) throws Exception { //從這開始
        try {
            1. 要先確定傳入參數是否有sysgp,syscd或caseid
            try {
                2. 查詢是否有回歸案例
             } catch (Exception e) {
                 log.fatal(查無資料)
             }
            try {
                 3. 迴圈開啟瀏覽器進行測試
             } catch (Exception e) {
                 log.fatal(執行案例失敗)
             }
           
            4. 統一寫入結果
            5. 發送信件跟報表
            6. 關閉測試機瀏覽器

        } catch (Exception e) {
            setExitCode(ERROR); // 設定預定回傳給Control_M的訊息 , 請依需求調整
            log.fatal("執行時發生錯誤", e);
        } finally {
            printExitCode(getExitCode()); // 回傳給 Control_M 的訊息代碼 , 程式終止
		}
	}
}

```


## 1-2 觀念 - 真批次
如果以上的範例要用真批次來做呢
```java 
public class XXTP_B998 extends XX_BatchBean { 

    private static final Logger log = Logger.getLogger(XXTP_B998.class);

    public void execute(String args[]) throws Exception { //從這開始
        try {
           同樣的空殼需要execute try-catch-finally

        } catch (Exception e) {
            setExitCode(ERROR); // 設定預定回傳給Control_M的訊息 , 請依需求調整
            log.fatal("執行時發生錯誤", e);
        } finally {
            printExitCode(getExitCode()); // 回傳給 Control_M 的訊息代碼 , 程式終止
		}
	}
}
```

```java 
public class XXTP_B998 extends XX_BatchBean { 

    private static final Logger log = Logger.getLogger(XXTP_B998.class);

    public void execute(String args[]) throws Exception { //從這開始
        try {
             覆寫firstProcess方法做檢核
             覆寫searchProcess方法去查案例
             覆寫forEachProcess方法去執行案例並準備測試結果
             覆寫executeBatchProcess方法批次寫入測試結果
             覆寫lastProcess方法發信
             覆寫finallyProcess關瀏覽器

        } catch (Exception e) {
            setExitCode(ERROR); // 設定預定回傳給Control_M的訊息 , 請依需求調整
            log.fatal("執行時發生錯誤", e);
        } finally {
            printExitCode(getExitCode()); // 回傳給 Control_M 的訊息代碼 , 程式終止
		}
	}
}
```
變成要使用覆寫的方法將假批次的CODE放入覆寫方法，底層會依序執行。


# 假批次

## 2-1 範例-傳入參數
執行批次需使用空殼必須要extends CathayJUnit

```java 
String[] param = {};
BatchController.executeBean("com.cathay.xx.tp.batch.XXTP_B998", param);

```
可以只有一個空殼，改裡面的參數即可執行其他批次，如果沒打錯，游標移動到batch.後面的那隻，會有超連結
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_54993e528857689f56e64d8188bafe94.png)

這時候是沒有傳入參數的寫法，同理我們再呼叫QRT1_B100會傳入caseid=XXXX syscd=AA
在部署系統執行時是用空白區隔，但在空殼執行不是
```java 
String[] param = { "HELLO", "WORLD" };
BatchController.executeBean("com.cathay.xx.tp.batch.XXTP_B998", param);
```
```java 
String[] param = { "caseid=XXXX", "syscd=AA" };
BatchController.executeBean("com.cathay.xx.tp.batch.XXTP_B998", param);
```
這樣會把字串整個傳入，那個=是批次有處理，有興趣可以看QRT1_B100有針對傳入參數做處理
```java 
 decideArgs(String[] args) throws Exception {
String[] arg = s.split("="); //基本上這個大家現在應該會就是用=區隔
```


## 2-2 範例-假批次
前面提到假批次很自由，各位寫過的JUNIT，把它搬過來一起執行
1.先刪除
2.新增
3.查詢看結果
4.更新
5.查詢看結果

直接參考各位寫的JUNIT照貼

```java=
// 1.刪除
try {
	String EMP_ID = "A00006";
	theXX_ZX0100.delete(EMP_ID);
} catch (Exception e) {
	log.fatal("刪無資料視為正常");
}
// 2.新增
UserObject user = new AuthUtil().getUserObjByID("B24531717N");
Map reqMap = new HashMap();
reqMap.put("EMP_ID", "A00006");
reqMap.put("DIV_NO", "9100100");
reqMap.put("EMP_NAME", "MOO");
reqMap.put("BIRTHDAY", "2023-08-09");
reqMap.put("POSITION", "20");
theXX_ZX0100.insert(reqMap, user);
 // 3.新增後重查
Map reqMap2 = new HashMap();
reqMap2.put("EMP_ID", "A00006");
reqMap2.put("DIV_NO", "9100100");
List<Map> rtnList = theXX_ZX0100.query(reqMap2);
log.fatal("新增後重查 rtnList" + rtnList);
 // 4.修改
Map reqMap3 = new HashMap();
reqMap3.put("EMP_ID", "A00006");
reqMap3.put("BIRTHDAY", "2023-08-10");
reqMap3.put("EMP_NAME", "MIKEY");
reqMap3.put("POSITION", "30");
theXX_ZX0100.update(reqMap3, user);
//5.修改後重查
log.fatal(" 修改後重查 rtnList" +  theXX_ZX0100.query(reqMap2));
```
這樣就完成一個批次了，可以練習第9行USER ID 或是EMP_ID讓使用者傳入。


# 真批次

## 3-1 範例 - 執行順序
覆寫批次請參考空殼檔案
我們先逐步解說，這些覆寫的方法

<font color="red">不必呼叫</font>
寫的順序可以亂寫，底層會依照順序自己呼叫


first(false)->finally
first(true)->search(false)->finally
first(true)->search(true)->沒資料->last->finally
first(true)->search(true)->有資料->forEach->executeBatch->last->finally


```java=
@Override
protected boolean firstProcess() {
	log.fatal("@@@@@@我在firstProcess@@@@@@");
	return true;
}

@Override
protected boolean searchProcess(BatchQueryDataSet bqds) throws DBException, ModuleException {
	log.fatal("@@@c@@我在searchProcess@@@@@@"); // 550
	return true;
}

```
和下面的寫法一樣，不會因為寫的行數先後造成執行問題。
```java=
@Override
protected boolean searchProcess(BatchQueryDataSet bqds) throws DBException, ModuleException {
	log.fatal("@@@c@@我在searchProcess@@@@@@"); // 550
	return true;
}

@Override
protected boolean firstProcess() {
	log.fatal("@@@@@@我在firstProcess@@@@@@");
	return true;
}

```
建議: 3、9行初期練習都先保留，你才知道怎麼跑的，那些怎麼執行的


如果你直接執行我給的範例會發現
只有印出
```java=
[XXTP_B997$1.firstProcess()(32)] - @@@@@@我在firstProcess@@@@@@
[XXTP_B997$1.searchProcess()(38)] - @@@c@@我在searchProcess@@@@@@
[XXTP_B997$1.lastProcess()(63)] - @@@@@@我在lastProcess@@@@@@
[XXTP_B997$1.finallyProcess()(69)] - @@@@@@我在finallyProcess@@@@@@ //要注意這行在很下面
```
這是因為流程圖寫的，
我滿足我在firstProcess回true
searchProcess回true，但是資料不存在，因為我根本沒去查
按照流程圖資料不存在會跑我在lastProcess

這邊先知道他怎麼跑


練習改一下跑的路徑 我們把firstProcess直接改false
```java=
@Override
protected boolean firstProcess() {
	log.fatal("@@@@@@我在firstProcess@@@@@@");
	return false; <---
}
```
```java=
[XXTP_B997$1.firstProcess()(32)] - @@@@@@我在firstProcess@@@@@@
[XXTP_B997$1.finallyProcess()(69)] - @@@@@@我在finallyProcess@@@@@@ //要注意這行在很下面
```
發現只剩下這兩行了，也很合理流程圖跟你說firstProcess為false直接進入我在finallyProcess

再多練習改
```java=
@Override
protected boolean firstProcess() {
	log.fatal("@@@@@@我在firstProcess@@@@@@");
	return true;
}

@Override
protected boolean searchProcess(BatchQueryDataSet bqds) throws DBException, ModuleException {
	log.fatal("@@@c@@我在searchProcess@@@@@@");
	return false;  <---
}

```
```java=
[XXTP_B997$1.firstProcess()(32)] - @@@@@@我在firstProcess@@@@@@
[XXTP_B997$1.searchProcess()(38)] - @@@c@@我在searchProcess@@@@@@
[XXTP_B997$1.finallyProcess()(69)] - @@@@@@我在finallyProcess@@@@@@ //要注意這行在很下面
```
沒有lastProcess，因為searchProcess為False直接進入finallyProcess


以上可以發現，只要沒有查到資料，永遠不會進去forEachProcess和executeBatchProcess
這邊的觀念很重要，很常不知道為什麼程式寫得沒跑，通常都是這個原因。

所以我們要讓searchProcess回傳true且有東西，把註解打開後
SQL請自己用主程式開發工具寫，一個SELECT *的SQL先簡單寫讓你的查尋有東西

```java=
[XXTP_B997$1.forEachProcess()(52)] - @@@@@@我在forEachProcess@@@@@@
[XXTP_B997$1.executeBatchProcess()(58)] - @@@@@@我在executeBatchProcess@@@@@@
[XXTP_B997$1.finallyProcess()(69)] - @@@@@@我在finallyProcess@@@@@@ //要注意這行在很下面
```
把整個LOG貼到NotePad++　使用Ctrl+F看找到多少次
你會發現@@@@@@我在forEachProcess@@@@@@出現的八百多次，那就是因為SELECT＊會把所有資料讀取後逐筆處理
@@@@@@我在executeBatchProcess@@@@@@ 會出現9次，因為一次處理100，一共9次

知道怎麼跑以後 我們就可以把程式擺到正確的位子
我們拿前面的範例來說
1.清空_BAK
2.查詢TP01
3.開檔案寫入CSV
4.逐筆倒檔
5.關閉file



這題目因為要求很少，所以firstProcess lastProcess都不需要(沒要求開頭跟結尾要做事)
```java=
public class XXTP_B998 extends XX_BatchBean { 

    private static final Logger log = Logger.getLogger(XXTP_B998.class);

    public void execute(String args[]) throws Exception { //從這開始
        try {
      
             覆寫firstProcess方法清空_BAK
      
             覆寫searchProcess方法去查TP01
             
             覆寫forEachProcess方法
              a. 逐筆update語法
              b. 逐筆寫入csv檔案
             覆寫executeBatchProcess方法批次寫入測試結果
         
             覆寫finallyProcess關file

        } catch (Exception e) {
            setExitCode(ERROR); // 設定預定回傳給Control_M的訊息 , 請依需求調整
            log.fatal("執行時發生錯誤", e);
        } finally {
            printExitCode(getExitCode()); // 回傳給 Control_M 的訊息代碼 , 程式終止
		}
	}
}
```


因為這次SPEC的範例比較簡單，無法使用到所有的覆寫方法，我先把題目改一下
```java=
1.1 請確認傳入參數必定要有DIV_NO，只處理該DIV_NO的資料
1.2 清空_BAK
2.查詢該SQL
3.逐筆處理，若非傳入的DIV_NO則不處理
3.1 如果是傳入的DIV_NO寫入檔案，檔名為ORI_DATA.txt
3.2 如果是傳入的DIV_NO寫入，隨機產生兩位數的OP_STATUS寫入_BAK 
4.全部做完寫一行LOG，"已完成，讚嘆指揮官 維持系統穩定"
5.確認寫入檔案有關閉
```

## 3-2 範例 - firstProcess
須回傳boolean 如果有錯就回傳False讓它結束
```java=
if (args.length == 0) {
	log.fatal("請傳入參數單位代號 沒有傳入 批次結束");
	return false;
}

if (!"DIV_NO".equals(args[0])) {
	log.fatal("請傳入參數單位代號 否則 批次結束");
} else {
	DIV_NO = (args[1]);
}

DataSet ds = Transaction.getDataSet();
EmptyTableHelper eth = new EmptyTableHelper();
eth.alterWithEmptyTable("DBXX", "DTXXTP01_BAK", ds);
```                 
      
## 3-3 範例 - searchProcess
sql請自行用sql工具產生
```java=
bqds.searchAndRetrieve(SQL_QUERY_ALL_001);
```

## 3-4 範例 - forEachProcess
先做資料寫入
buds要先在上面先寫好
```java=
BatchUpdateDataSet buds = bc.getBatchUpdateDataSet(SQL_INSERT_ALL_001, ErrorHandler.DATA_NOT_FOUND_FAIL_DUPLICATE_FAIL);
```
從bqds <--q
拿出來放入buds
```java=
if(DIV_NO.equals(bqds.getField("DIV_NO"))) {
	int a = (int) (Math.random()*90+10);
    buds.setField("EMP_ID", bqds.getField("EMP_ID"));
    buds.setField("EMP_NAME", bqds.getField("EMP_NAME"));
    buds.setField("DIV_NO", bqds.getField("DIV_NO"));
    buds.setField("BIRTHDAY", bqds.getField("BIRTHDAY"));
    buds.setField("POSITION", bqds.getField("POSITION"));
    buds.setField("UPDT_ID", bqds.getField("UPDT_ID"));
    buds.setField("UPDT_DATE", bqds.getField("UPDT_DATE"));
    buds.setField("OP_STATUS", a);
    buds.setField("FLOW_NO", bqds.getField("FLOW_NO"));

    addBatchAndJoinGroup(buds);
}
```
可以發現寫入成功了
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7b315bd58a5ec9286d69455a4a8c3245.png)

再來做備份
我們要備份 原本的EMP_ID的OP_STATUS是多少

```java
bufferedWriter.write("EMP_ID: " + bqds.getField("EMP_ID") + "原本的OP_STATUS: " + bqds.getField("OP_STATUS"));

bufferedWriter.newLine();           
```
當然上面要先把檔案開好，忘記請複習參考教學JAVA3
```java=
String filePath = "D:\\XXTP.txt";
FileWriter fileWriter = new FileWriter(filePath, true); // 使用 true 表示附加到檔案末尾
BufferedWriter bufferedWriter = new BufferedWriter(fileWriter) ;
```      
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5d5538e3b5f400d94b7a677e4c0c659d.png)

      
## 3-5 範例 - executeBatchProcess
```java=
通常不用幹嘛，除非要做特殊處理
```

## 3-6 範例 - lastProcess
題目要求印LOG
```java=
log.fatal("完成，讚嘆指揮官 維持系統穩定"); 
```

## 3-7 範例 - finallyProcess
```java=
bufferedWriter.close();
```
## 3-8 範例 - 計數型別 
在一開始的bc宣告createCountType
```java=
bc.createCountType("XX_BAK的INPUT件數");
```
在想要計數的地方，通常是forEachProcess
加上計數器看要加多少
```java=

addBatchAndJoinGroup(buds);
bc.addCountNumber("XX_BAK的INPUT件數", 1);
```
通常放在addbatch後才+1

  
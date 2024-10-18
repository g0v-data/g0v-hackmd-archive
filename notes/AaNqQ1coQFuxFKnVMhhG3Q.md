# 常用網站
https://quip.com/browse
https://miro.com/app/board/uXjVKZzX5b0=/
流程圖：https://mermaid.live/edit

# 9/26禮拜四****
主管開會會議內容
- 高鐵搶票預防（有效流量），偽造登入
- 如何偵測在短時間內會有大量買票行為，並加以阻擋
- 簡單來說就是要針對過往資料去分析，並偵測目前行為是否怪怪的
- 如果怪怪的，就要阻擋當前行為
- 猜測密碼
- 論文題目和內容要有吸引性、有價值
- 如何防止機器人搶票？

---
# 初步解決想法

## 基於熵的異常網路流量偵測方法之研究

通過對惡意攻擊的分析可以知道，當攻擊出現時，會有大量不完整的連 接請求，packets、bytes、flows 這些特徵會異常的增加。而 Entropy 可用於計 算一條或是數條 Flows 中來源 IP 或是目的地 IP 分佈的隨機性；一條 Flow 含 有許多的訊息，當訊息越多，Entropy 就會越高，也代表這個訊息越隨機，所 以一條 Flow 的訊息量多寡會與隨機性有直接的關係。。例如，在某個時間點 偵測到了 1000 個封包，接著計算這 1000 個封包中每個不同 IP 地址的頻 率；當 IP 分布越隨機，Entropy 就越高，也就是說，計算這些隨機性高的 IP 所產生的流量(bytes、packets、flows…)，在一定的程度上能夠區分惡意流量與否。


## 基於熵與機器學習之SDN多層DDoS緩解系統

SDN 網路具有網路的可視性與集中控 制的功能，更能應對雜亂無序的 DDoS 攻擊。軟體定義網路將控制層與 資料層分開，利用 Openflow 協議讓控制層管理資料層，就能自訂規則生 成 DDoS 攻擊防禦策略。

## 混合KNN及時間序列於軟體定義網路中對DDoS之攻擊進行偵測和預測





## 雙因子認證 / 多因子認證機制 
加強身分驗證之安全性


## informix的專案介紹
說明目前專案要把informix的架構利用AI整理出
以及了解informix的語法跟目前專案的進度
利用quip和miro






# 結論
> ### 禮拜四：業界研發學習
> ### 禮拜五：論文產出發想


# 9/27禮拜五****

與團隊開會內容

* 12306是一個架構練習專案
* 目前架構並不完整
* 但有基本流程

主要模擬中國訂票系統



redis

目標根據使用者歷程去分析
最後結果可以需求預測
數據分析統計

策略中的替代方案需要考慮後續
替代方案的難易度定義
替代方案是否可行性定義

系統架構師更有價值
薪水很高
要有遠見


# 10/4禮拜五****

介紹了如何在 Spring Boot 中實現 AOP（面向切面程式設計），以日誌記錄為範例，達到在不修改原有方法程式碼的情況下，監聽 API 呼叫時執行的方法名稱、成功與否及詳細資訊。

**AOP 簡介：**

- **目的：** 將多個方法的共同行為抽離出來，無需顯式呼叫，也可在指定時間點自動觸發，實現共通工作的附加。

**相關術語：**

- **Advice（通知）：** 定義「什麼時候」執行「什麼事」。
- **Join Point（連接點）：** 程式執行過程中可應用 Advice 的所有點。
- **Pointcut（切點）：** 定義「在哪些地方」進行切入，哪些 Join Point 會接收到 Advice。
- **Aspect（切面）：** Advice 和 Pointcut 的結合，完整定義了「什麼時候、在哪裡、做什麼事」。
- **Introduction（引入）：** 允許向現有的 Class 添加新的方法或屬性。
- **Weaving（織入）：** 將 Pointcut 應用到目標物件並創建新代理對象的過程。

**在 Spring Boot 中實作 AOP 的步驟：**

1. **加入依賴：**
   在 `pom.xml` 中添加 AOP 的依賴項目：
   ```xml
   <dependency>
       <groupId>org.springframework.boot</groupId>
       <artifactId>spring-boot-starter-aop</artifactId>
   </dependency>
   ```

2. **建立切面（Aspect）：**
   - 創建一個名為 `LogAspect` 的類。
   - 使用 `@Component` 注解，讓 Spring Boot 在啟動時檢測並實例化該類。
   - 使用 `@Aspect` 注解，標識此類為一個切面。
   ```java
   @Component
   @Aspect
   public class LogAspect {
   }
   ```

3. **定義切點（Pointcut）：**
   - 在 `LogAspect` 中創建一個空的方法，使用 `@Pointcut` 注解定義切點。
   - 在注解中添加表達式，指定攔截的範圍，例如攔截 `com.school.learning.service` 包下的所有方法。
   ```java
   @Pointcut("execution(* com.school.learning.service..*(..))")
   public void serviceMethods() {}
   ```

4. **建立通知（Advice）：**
   - 介紹五種 Advice 類型：
     - `@Before`：在目標方法執行前執行。
     - `@After`：在目標方法執行後執行。
     - `@Around`：在目標方法執行前後執行。
     - `@AfterReturning`：在目標方法成功返回後執行。
     - `@AfterThrowing`：在目標方法拋出異常後執行。
   - 範例：使用 `@Before` 在方法執行前記錄日誌。
   ```java
   @Before("serviceMethods()")
   public void beforeAdvice(JoinPoint joinPoint) {
       // 實現日誌記錄
   }
   ```

5. **加入日誌機制：**
   - 在 Advice 中使用 `JoinPoint` 獲取被監聽的方法資訊。
   - 將所需資訊（如時間、方法名稱）寫入日誌文件。

透過以上步驟，成功實現了在 Spring Boot 中使用 AOP 進行日誌記錄的功能，達到在指定時間點自動觸發共同行為的目的，而無需修改原有的業務邏輯程式碼。

# 10/17禮拜四****

**摘要：**

介紹了 Informix 語法知識，重點講解了 `.per` 檔案和 `4gl` 檔案，這些是 Informix 4GL 程式設計的核心組件。

**一、`.per` 檔案：**

- **用途：** `.per` 檔案是用於定義 Informix 4GL 應用程式中使用者介面的螢幕檔案。

- **組成部分：**

  - **SCREEN SECTION（螢幕部分）：** 定義使用者介面的佈局，指定欄位和標籤在螢幕上的顯示方式。欄位通常用 `[]` 表示，內部的文字作為欄位的臨時名稱。

  - **ATTRIBUTES SECTION（屬性部分）：** 將 SCREEN SECTION 中的臨時欄位名稱映射到實際的變數或資料庫欄位。它定義了資料類型、格式、輸入限制和行為（如 `AUTONEXT`、`NOENTRY`）等屬性。

- **範例分析：**

  - **臨時欄位名稱與實際變數的映射：** 透過在 ATTRIBUTES SECTION 中查看臨時名稱，可以找到對應的實際變數或資料庫欄位。

  - **輸入限制：** 使用 `INCLUDE` 限制欄位的可輸入值範圍，例如 `INCLUDE = (1 TO 5)`。

  - **必填欄位：** 使用 `NOT NULL` 指定欄位為必填項。

**二、`4gl` 檔案：**

- **控制結構：**

  - **WHILE 迴圈：** 用於迭代處理，以 `END WHILE` 結束。

  - **DEFER INTERRUPT：** 暫時禁用使用者中斷（如 `Ctrl+C`），以防止在關鍵代碼段期間意外終止程式，保護資料完整性。

- **使用者互動：**

  - **PROMPT 語句：** 用於顯示提示資訊並捕獲使用者輸入，將其存儲到指定的變數中。

  - **範例：**

    ```4gl
    MAIN
      DEFINE user_input CHAR(20)
      PROMPT "請輸入您的姓名: " FOR user_input
      DISPLAY "您輸入的姓名是: ", user_input
    END MAIN
    ```

**三、Informix SQL 知識：**

- **基本 SQL 語法：**

  - 資料查詢與操作：`SELECT`、`INSERT`、`UPDATE`、`DELETE`

  - 資料定義與結構修改：`CREATE TABLE`、`DROP TABLE`、`ALTER TABLE`

- **控制流程語法：**

  - 條件判斷：`IF...THEN...ELSE`

  - 迴圈結構：`FOR...END FOR`、`WHILE...END WHILE`

  - 多條件選擇：`CASE`

- **錯誤處理語法：**

  - 交易控制：`BEGIN WORK`、`COMMIT WORK`、`ROLLBACK WORK`

  - 異常處理：`WHENEVER SQLERROR CONTINUE`、`WHENEVER SQLERROR STOP`

- **資料操作與變數處理：**

  - **DEFINE：** 定義變數

  - **LET：** 變數賦值

**四、動態 SQL 與游標：**

- **動態 SQL：**

  - **PREPARE：** 準備動態 SQL 語句

  - **EXECUTE：** 執行已準備的語句

  - **DEALLOCATE：** 釋放語句

- **游標（Cursors）：**

  - **用途：** 處理複雜查詢，逐行遍歷結果集

  - **使用步驟：**

    1. **DECLARE CURSOR：** 宣告游標並指定查詢語句

    2. **OPEN CURSOR：** 開啟游標，執行查詢

    3. **FETCH：** 從游標提取一行資料

    4. **CLOSE CURSOR：** 關閉游標，釋放資源

  - **範例：**

    ```4gl
    DECLARE cust_cursor CURSOR FOR
        SELECT customer_id, order_date FROM customers
        WHERE customer_id >= 'CUST001' AND order_date >= '2023-01-01'
        ORDER BY customer_id, order_date;

    OPEN cust_cursor;

    FETCH cust_cursor INTO var1, var2;
    WHILE (SQLCODE = 0)
        DISPLAY var1, var2;
        FETCH cust_cursor INTO var1, var2;
    END WHILE;

    CLOSE cust_cursor;
    ```

**五、其他重要概念：**

- **CONSTRUCT 動態查詢條件：**

  - 用於根據使用者輸入動態構建 `WHERE` 子句

  - **BY NAME：** 使用欄位名稱映射使用者輸入條件

  - **範例：**

    ```4gl
    CONSTRUCT BY NAME WK_QUERY ON BKERMWST.EDYEAR, BKERMWST.EDSEQ
    ```

- **系統內置變數：**

  - **STATUS：** 最近一次 SQL 操作的結果碼（0 表示成功）

  - **INT_FLAG：** 指示使用者是否按下中斷鍵（如 `Ctrl+C`）

  - **SQLCA：** 包含最近執行的 SQL 語句的詳細資訊

    - **SQLCA.SQLCODE：** SQL 返回碼

    - **SQLCA.SQLERRM：** 錯誤資訊描述

    - **SQLCA.SQLERRD[2]：** 影響的行數

  - **NOTFOUND：** 指示最近的資料庫查詢是否未返回任何記錄

**總結：**

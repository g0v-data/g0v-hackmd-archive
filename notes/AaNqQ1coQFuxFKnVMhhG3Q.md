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

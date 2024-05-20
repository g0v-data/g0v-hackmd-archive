
## Spring Transaction 的 Propagation

前言
在處理Mantis維修單時，遇到了一個與Transaction(交易)有關的錯誤。發生錯誤的原因是：要即刻Update(更新)資料至資料庫表格的行為，被"延後"至Transaction(交易)結束時才真正執行。導致系統執行的結果與預期完全不同。

上述功能的情境是「允許多人同時搶買商品，而商品有數量上限，商品賣完就停止交易」。此情境下，準確扣減商品數量最為重要。

當商品數量記錄在資料庫表格，「扣減商品數量」需要先從資料庫表格讀出商品數量；扣減後再將商品數量更新至資料庫表格。此時若是使用了Spring @Transaction(交易)機制，又對Spring @Transaction的Propagation(傳播)特性不瞭解，就會造成不預期的錯誤，導致商品數量沒及時更新或是出現Exception(例外)導致失敗。

基於上述類似的問題很容易出現在各種商業領域的情境中，所以全面地詳細測試Spring @Transaction的各種Propagation(傳播)特性是有必要的。藉著此次機會將測試結果記錄下來，做為日後查閱之用。

提高Transaction傳播特性的瞭解後，期許能夠在編寫交易類程式時更得心應手，更穩健踏實地開發出穩定的系統。

 


---

# Propagation Types 傳播類型
甚麼是Propagation(傳播)呢？當一個Transaction方法(method)碰到另一個Transaction方法(method)時的處理行為。

Propagation Types(傳播類型)一共有八種，說明如下:




第五個傳播類型 REQUIRED 和第六個傳播類型 REQUIRES_NEW 這二種傳播類型是最常用的，可以多留意以下範例的測試結果，可有效避免再次踏入陷阱。

 

傳播的情境
當一個交易方法(method)碰到另一個交易方法(method)時，調用者與被調用者是否有事務(Transaction)？是否發生異常(Exception)？都會影響到 Transaction 是否回滾(Rollback)？以下列出互相影響的八種情境。

| 序號 | 傳播類型與說明                       | 說明                                                                                                                                                      | Spring                                                              | Transaction                 |
| ---- | ------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- | -------------------- |
| 1    | TransactionDefinition.PROPAGATION_MANDATORY | Supports a current transaction; throws an exception if no current transaction exists. (支持當前 Transaction；如果當前 Transaction 不存在，則引發異常。) | org.springframework.transaction.annotation.Propagation.MANDATORY | PROPAGATION_MANDATORY |
| 2    | TransactionDefinition.PROPAGATION_NESTED    | Executes within a nested transaction if a current transaction exists. (如果當前 Transaction 存在，則在嵌套 Transaction 中執行。)                                    | org.springframework.transaction.annotation.Propagation.NESTED    | PROPAGATION_NESTED    |
| 3    | TransactionDefinition.PROPAGATION_NEVER     | Does not support a current transaction; throws an exception if a current transaction exists. (不支持當前 Transaction；如果當前 Transaction 存在，則引發異常。)    | org.springframework.transaction.annotation.Propagation.NEVER     | PROPAGATION_NEVER     |
| 4    | TransactionDefinition.PROPAGATION_NOT_SUPPORTED | Does not support a current transaction; rather always execute nontransactionally. (不支持當前 Transaction；而是始終以非 Transaction 方式執行。)                    | org.springframework.transaction.annotation.Propagation.NOT_SUPPORTED | PROPAGATION_NOT_SUPPORTED |
| 5    | TransactionDefinition.PROPAGATION_REQUIRED   | Supports a current transaction; creates a new one if none exists. (支持當前 Transaction；如果不存在，則創建一個新的。)                                        | org.springframework.transaction.annotation.Propagation.REQUIRED   | PROPAGATION_REQUIRED   |
| 6    | TransactionDefinition.PROPAGATION_REQUIRES_NEW | Creates a new transaction, suspending the current transaction if one exists. (創建一個新 Transaction，如果 Transaction 存在則暫停當前 Transaction 。)                  | org.springframework.transaction.annotation.Propagation.REQUIRES_NEW | PROPAGATION_REQUIRES_NEW |
| 7    | TransactionDefinition.PROPAGATION_SUPPORTS  | Supports a current transaction; executes non-transactionally if none exists. (支持當前 Transaction；如果不存在，則以非 Transaction 方式執行。)                             | org.springframework.transaction.annotation.Propagation.SUPPORTS  | PROPAGATION_SUPPORTS  |
| 8    | TransactionDefinition.TIMEOUT_DEFAULT       | Uses the default timeout of the underlying transaction system, or none if timeouts are not supported. (使用基礎 Transaction 系統的默認超時；如果不支持超時，則不使用默認超時。) | 不支援                                                               | TIMEOUT_DEFAULT       |


第五個傳播類型 REQUIRED 和第六個傳播類型 REQUIRES_NEW 這二種傳播類型是最常用的，可以多留意以下範例的測試結果，可有效避免再次踏入陷阱。

---

# 傳播的情境

當一個交易方法(method)碰到另一個交易方法(method)時，調用者與被調用者是否有事務(Transaction)？是否發生異常(Exception)？都會影響到 Transaction 是否回滾(Rollback)？以下列出互相影響的八種情境。

| 序號 | 調用者有交易？ | 調用者有異常？ | 被調用者有交易？                                           | 被調用者有異常？ |
| ---- | -------------- | -------------- | -------------------------------------------------------- | -------------- |
| 1    | 有             | 有             | 被調用者是否有 Transaction，取決於 @Transaction Propagation 屬性的屬性值 | 有             |
| 2    | <font color="#000093">**有**</font> |<font color="#000093">**有**</font>          | 被調用者是否有 Transaction，取決於 @Transaction Propagation 屬性的屬性值 |<font color="#000093">**沒有**</font>        |
| 3    | <font color="#000093">**有**</font>             | <font color="#000093">**沒有**</font>        | 被調用者是否有 Transaction，取決於 @Transaction Propagation 屬性的屬性值 |<font color="#000093">**有**</font>             |
| 4    | 有             | 沒有           | 被調用者是否有 Transaction，取決於 @Transaction Propagation 屬性的屬性值 | 沒有           |
| 5    | 沒有           | 有             | 被調用者是否有 Transaction，取決於 @Transaction Propagation 屬性的屬性值 | 有             |
| 6    | 沒有           | 有             | 被調用者是否有 Transaction，取決於 @Transaction Propagation 屬性的屬性值 | 沒有           |
| 7    | <font color="#000093">**沒有**</font>      | <font color="#000093">**沒有**</font>       | 被調用者是否有 Transaction，取決於 @Transaction Propagation 屬性的屬性值 | <font color="#000093">**有**</font>         |
| 8    | 沒有           | 沒有           | 被調用者是否有 Transaction，取決於 @Transaction Propagation 屬性的屬性值 | 沒有           |



表格中標示<font color="#000093">**藍色字體**</font> 的情境共有三種，這三種情境最具代表性，也會在下述傳播類型與情境案例說明中，搭配Transaction傳播類型逐一說明。

 

---


# 傳播類型與情境案例說明
以下案例說明，調用者函式與被調用者函式皆是使用註解式Transaction。
在傳播類型案例的情境上，被調用者函式一定會使用@Transactional(propagation=Propagation.xxx)，而 xxx 意指傳播類型。
 

<h4>1. PROPAGATION_MANDATORY (支持當前 Transaction；如果當前 Transaction 不存在，則引發異常)</h4>

※在此傳播屬性下，調用者有 Transaction，則被調用者使用該 Transaction，否則引發異常。
<br>
當被調用者函式使用 PROPAGATION_MANDATORY 此傳播類型時，用以下的情境進行說明 Transaction 是否會回滾(Rollback)：

| 調用者有事務 | 調用者拋出異常 | 被調用者有事務    | 被調用者拋出異常 |
| ------------ | -------------- | --------------- | -------------- |
|        | 有           | 無             | **有，開啟事務** | 有             |


調用者有事務，被調用者開啟事務。
被調用者拋出異常，被調用者回滾。
調用者沒有捕獲異常，則調用者回滾。
調用者捕獲異常並正常提交事務，則會發生 Transaction silently rolled back because it has been marked as rollback-only 的異常。
Case2-a:

<調用者>

@Transactional()
public void hasTransactional() {
    insertData();
    callee.hasTransactional();
}
 

<被調用者(callee)>

@Transactional(propagation = Propagation.MANDATORY)
public void hasTransactional() {
    insertData();
    throw new RuntimeException();
}
 

Case2-b:

<調用者>

@Transactional()
public void hasTransactional() {
    try{
        insertData();
        callee.hasTransactional();
    } catch(Exception e) {
    }
}
<被調用者(callee)>

@Transactional(propagation = Propagation.MANDATORY)
public void hasTransactional() {
    insertData();
    throw new RuntimeException();
}
情境二

調用者有事務

調用者拋出異常

被調用者有事務

被調用者拋出異常

有

有

有，開啟事務

無

調用者有事務，被調用者開啟事務。
調用者拋出異常，因被調用者的事務與調用者是同一個，所以調用者與被調用者皆會回滾。

<調用者>

@Transactional()
public void hasTransactional() {
    insertData();
    callee.hasTransactional();
    throw new RuntimeException();
}

<被調用者(callee)>

@Transactional(propagation = Propagation.MANDATORY)
public void hasTransactional() {
    insertData();
}
情境三

調用者有事務

調用者拋出異常

被調用者有事務

被調用者拋出異常

無

無

無

有

調用者無事務，因被調用者的傳播類型為 MANDATORY；調用者呼叫被調用者函式時，發生Exception:No existing transaction found for transaction marked with propagation 'mandatory'。

<調用者>

public void noTransactional() {
    insertData();
    callee.hasTransactional();
}
 

<被調用者(callee)>

@Transactional(propagation = Propagation.MANDATORY)
public void hasTransactional() {
    insertData();
    throw new RuntimeException();
}
 
2. PROPAGATION_NESTED (如果當前 Transaction 存在，則在嵌套事務中執行)
※在此傳播屬性下，被調用者 Transaction 與調用者 Transaction 有嵌套關係。嵌套事務的本質就是外層會影響內層，內層不影響外層。
我們重點說一下 NESTED 傳播類型的特性：

調用者是否有事務

說明

有

被調用者會新起一個 Transaction ，此 Transaction 和調用者 Transaction 是一個嵌套的關係

無

被調用者會自己新起一個 Transaction 

 

當被調用者函式使用 PROPAGATION_NESTED 此傳播類型時，用以下的情境進行說明 Transaction 是否會回滾(Rollback)：

情境一

調用者有事務

調用者拋出異常

被調用者有事務

被調用者拋出異常

有

無

有，新建事務

有

調用者有事務，被調用者新建事務。
被調用者拋出異常，被調用者回滾。
調用者沒有捕獲異常，則調用者和被調用者回滾。
調用者捕獲異常，則調用者不回滾；被調用者回滾。
觀察程式執行結果，被調用者拋出異常，調用者不回滾；被調用者回滾。
調用者有事務，被調用者新建事務，二者事務成為嵌套關係，調用者事務不受被調用者事務影響。
結論:Propagation.NESTED傳播類型，外層事務不受內層事務影響。

Case2-a:

<調用者>

@Transactional()
public void hasTransactional() {
    insertData();
    callee.hasTransactional();
}
 

<被調用者(callee)>

@Transactional(propagation = Propagation.NESTED)
public void hasTransactional() {
    insertData();
    throw new RuntimeException();
}
 

Case2-b:

<調用者>

@Transactional()
public void hasTransactional() {
    try{
        insertData();
        callee.hasTransactional();
    } catch(Exception e) {
    }
}
<被調用者(callee)>

@Transactional(propagation = Propagation.NESTED)
public void hasTransactional() {
    insertData();
    throw new RuntimeException();
}
情境二

調用者有事務

調用者拋出異常

被調用者有事務

被調用者拋出異常

有

有

有，新建事務

無

調用者有事務，被調用者新建事務。
調用者拋出異常，調用者與被調用者皆會回滾。

調用者有事務，被調用者新建事務，二者事務成為嵌套關係。
調用者拋出異常，因調用者與被調用者的事務不是同一個，理論上被調用者事務不會回滾才對，但是最終結果被調用者事務回滾了。
結論:Propagation.NESTED傳播類型，外層事務會影響內層事務。

<調用者>

@Transactional()
public void hasTransactional() {
    insertData();
    callee.hasTransactional();
    throw new RuntimeException();
}
 

<被調用者(callee)>

@Transactional(propagation = Propagation.NESTED)
public void hasTransactional() {
    insertData();
}
情境三

調用者有事務

調用者拋出異常

被調用者有事務

被調用者拋出異常

無

無

有，新建事務

有

調用者無事務，被調用者新建事務。
被調用者拋出異常，調用者不回滾；被調用者回滾。

<調用者>

public void hasTransactional() {
    insertData();
    callee.hasTransactional();
}

<被調用者(callee)>

@Transactional(propagation = Propagation.NESTED)
public void hasTransactional() {
    insertData();
    throw new RuntimeException();
}
 
3. PROPAGATION_NEVER(不支持當前 Transaction；如果當前 Transaction 存在，則引發異常)
※在此傳播屬性下，調用者有 Transaction，被調用者就會拋出異常。

 

當被調用者函式使用 PROPAGATION_NEVER 此傳播類型時，用以下的情境進行說明 Transaction 是否會回滾(Rollback)：

情境一/情境二

調用者有事務

調用者拋出異常

被調用者有事務

被調用者拋出異常

有

無/有

無，Never

無/引發異常
調用者有事務，被調用者則會出現 Existingtransaction found for transaction marked with propagation 'never' 異常。

<調用者>

@Transactional()
public void hasTransactional() {
    insertData();
    callee.hasTransactional();
}
 

<被調用者(callee)>

@Transactional(propagation = Propagation.NEVER)
public void hasTransactional() {
    insertData();
}
情境三

調用者有事務

調用者拋出異常

被調用者有事務

被調用者拋出異常

無

無

無

有

調用者無事務，被調用者無事務。
被調用者拋出異常，因調用者與被調用者皆無事務，所以調用者與被調用者皆不會回滾。
 

<調用者>

public void hasTransactional() {
    insertData();
    callee.hasTransactional();
}
 

<被調用者(callee)>

@Transactional(propagation = Propagation.NEVER)
public void hasTransactional() {
    insertData();
    throw new RuntimeException();
}
 
4. PROPAGATION_NOT_SUPPORTED (不支持當前 Transaction；而是始終以非 Transaction 方式執行)
※在此傳播屬性下，無論調用者是否有 Transaction，被調用者都不以 Transaction 的方式運行。

 

當被調用者函式使用 PROPAGATION_NOT_SUPPORTED 此傳播類型時，用以下的情境進行說明 Transaction 是否會回滾(Rollback)：

情境一

調用者有事務

調用者拋出異常

被調用者有事務

被調用者拋出異常

有

無

無，Not Support

有

調用者有事務，被調用者無(Not Support)事務。
被調用者拋出異常，被調用者丟擲異常前的資料操作不受影響。
調用者沒有捕獲異常，則調用者回滾。
調用者捕獲異常，則調用者不受影響，不回滾。

Case2-a:

<調用者>

@Transactional()
public void hasTransactional() {
    insertData();
    callee.hasTransactional();
}

<被調用者(callee)>

@Transactional(propagation = Propagation.NOT_SUPPORTED)
public void hasTransactional() {
    insertData();
    throw new RuntimeException();
}
 

Case2-b:

<調用者>

@Transactional()
public void hasTransactional() {
    try{
        insertData();
        callee.hasTransactional();
    } catch(Exception e) {
    }
}
 

<被調用者(callee)>

@Transactional(propagation = Propagation.NOT_SUPPORTED)
public void hasTransactional() {
    insertData();
    throw new RuntimeException();
}
情境二

調用者有事務

調用者拋出異常

被調用者有事務

被調用者拋出異常

有

有

無，Not Support

無

調用者有事務，被調用者無(Not Support)事務。
調用者拋出異常，調用者回滾；被調用者無事務，不受影響，不回滾。

<調用者>

@Transactional()
public void hasTransactional() {
    insertData();
    callee.hasTransactional();
    throw new RuntimeException();
}
 

<被調用者(callee)>

@Transactional(propagation = Propagation.NOT_SUPPORTED)
public void hasTransactional()
{
    insertData();
}
情境三

調用者有事務

調用者拋出異常

被調用者有事務

被調用者拋出異常

無

無

無，Not Support

有

調用者無事務，被調用者無(Not Support)事務。
被調用者拋出異常，因調用者與被調用者皆無事務，所以調用者與被調用者皆不會回滾。

<調用者>

public void hasTransactional() {
    insertData();
    callee.hasTransactional();
}
 

<被調用者(callee)>

@Transactional(propagation = Propagation.NOT_SUPPORTED)
public void hasTransactional() {
    insertData();
    throw new RuntimeException();
}
 

5. PROPAGATION_REQUIRED (支持當前 Transaction；如果不存在，則創建一個新的)

※在此傳播屬性下，被調用者是否新建 Transaction 取決於調用者是否帶著 Transaction 。

 

當被調用者函式使用 PROPAGATION_REQUIRED 此傳播類型時，用以下的情境進行說明 Transaction 是否會回滾(Rollback)：

情境一

調用者有事務

調用者拋出異常

被調用者有事務

被調用者拋出異常

有

無

有，開啟事務

有

調用者有事務，被調用者開啟事務。
被調用者拋出異常，被調用者回滾。
調用者沒有捕獲異常，則調用者回滾。
調用者捕獲異常並正常提交事務，則會發生Transaction silently rolled back because it has been marked as rollback-only的異常。
Case2-a:

<調用者>

@Transactional()
public void hasTransactional() {
    insertData();
    callee.hasTransactional();
}
 

<被調用者(callee)>

@Transactional(propagation = Propagation.REQUIRED)
public void hasTransactional() {
    insertData();
    throw new RuntimeException();
}
 

Case2-b:

<調用者>

@Transactional()
public void hasTransactional() {
    try{
        insertData();
        callee.hasTransactional();
    } catch(Exception e) {
    }
}
 

<被調用者(callee)>

@Transactional(propagation = Propagation.REQUIRED)
public void hasTransactional() {
    insertData();
    throw new RuntimeException();
}
情境二

調用者有事務

調用者拋出異常

被調用者有事務

被調用者拋出異常

有

有

有，開啟事務

無

調用者有事務，被調用者開啟事務。
調用者拋出異常，因被調用者的事務與調用者是同一個，所以調用者與被調用者皆會回滾。

<調用者>

@Transactional()
public void hasTransactional() {
    insertData();
    callee.hasTransactional();
    throw new RuntimeException();
}
 

<被調用者(callee)>

@Transactional(propagation = Propagation.REQUIRED)
public void hasTransactional() {
    insertData();
}
情境三

調用者有事務

調用者拋出異常

被調用者有事務

被調用者拋出異常

無

無

有，新建事務

有

調用者無事務，被調用者新建事務。
被調用者拋出異常，因調用者無事務，所以調用者不回滾；被調用者回滾。

<調用者>

public void hasTransactional() {
    insertData();
    callee.hasTransactional();
}
 

<被調用者(callee)>

@Transactional(propagation = Propagation.REQUIRED)
public void hasTransactional() {
    insertData();
    throw new RuntimeException();
}
 

6. PROPAGATION_REQUIRES_NEW (創建一個新 Transaction，如果 Transaction 存在，則暫停當前 Transaction)
※在此傳播屬性下，無論調用者是否有事務，被調用者都會新建一個事務。

 

當被調用者函式使用 PROPAGATION_REQUIRES_NEW 此傳播類型時，用以下的情境進行說明 Transaction 是否會回滾(Rollback)：

情境一

調用者有事務

調用者拋出異常

被調用者有事務

被調用者拋出異常

有

無

有，新建事務

有

調用者有事務，被調用者新建事務。
被調用者拋出異常，被調用者回滾。
調用者沒有捕獲異常，則調用者回滾。
調用者捕獲異常，調用者不受影響，不回滾。
Case2-a:

<調用者>

@Transactional()
public void hasTransactional() {
    insertData();
    callee.hasTransactional();
}
 

<被調用者(callee)>

@Transactional(propagation = Propagation.REQUIRES_NEW)
public void hasTransactional() {
    insertData();
    throw new RuntimeException();
}
 

Case2-b:

<調用者>

@Transactional()
public void hasTransactional() {
    try{
        insertData();
        callee.hasTransactional();
    } catch(Exception e) {
    }
}
 

<被調用者(callee)>

@Transactional(propagation = Propagation.REQUIRES_NEW)
public void hasTransactional() {
    insertData();
    throw new RuntimeException();
}
情境二

調用者有事務

調用者拋出異常

被調用者有事務

被調用者拋出異常

有

有

有，新建事務

無

調用者有事務，被調用者新建事務。
調用者拋出異常，因被調用者事務與調用者事務與不是同一個，所以調用者會回滾；被調用者不受影響，不回滾。

<調用者>

@Transactional()
public void hasTransactional() {
    insertData();
    callee.hasTransactional();
    throw new RuntimeException();
}
 

<被調用者(callee)>

@Transactional(propagation = Propagation.REQUIRES_NEW)
public void hasTransactional() {
    insertData();
}
情境三

調用者有事務

調用者拋出異常

被調用者有事務

被調用者拋出異常

無

無

有，新建事務

有

調用者無事務，被調用者新建事務。
被調用者拋出異常，因調用者無事務，所以調用者不回滾；被調用者回滾。

<調用者>

public void hasTransactional() {
    insertData();
    callee.hasTransactional();
}
 

<被調用者(callee)>

@Transactional(propagation = Propagation.REQUIRES_NEW)
public void hasTransactional() {
    insertData();
    throw new RuntimeException();
}
 

7. PROPAGATION_SUPPORTS (支持當前 Transaction；如果不存在，則以非 Transaction 方式執行)
※在此傳播屬性下，被調用者是否有 Transaction，完全依賴於調用者，調用者有 Transaction 則有 Transaction，調用者沒 Transaction 則沒 Transaction 。

 

當被調用者函式使用 PROPAGATION_SUPPORTS 此傳播類型時，用以下的情境進行說明 Transaction 是否會回滾(Rollback)：

情境一

調用者有事務

調用者拋出異常

被調用者有事務

被調用者拋出異常

有

無

有，開啟事務

有

調用者有事務，被調用者開啟事務。
被調用者拋出異常，被調用者回滾。
調用者沒有捕獲異常，則調用者回滾。
調用者捕獲異常並正常提交事務，則會發生 Transaction silently rolled back because it has been marked as rollback-only的異常。
Case2-a:

<調用者>

@Transactional()
public void hasTransactional() {
    insertData();
    callee.hasTransactional();
}
 

<被調用者(callee)>

@Transactional(propagation = Propagation.SUPPORTS)
public void hasTransactional() {
    insertData();
    throw new RuntimeException();
}
 

Case2-b:

<調用者>

@Transactional()
public void hasTransactional() {
    try{
        insertData();
        callee.hasTransactional();
    } catch(Exception e) {
    }
}
 

<被調用者(callee)>

@Transactional(propagation = Propagation.SUPPORTS)
public void hasTransactional() {
    insertData();
    throw new RuntimeException();
}
情境二

調用者有事務

調用者拋出異常

被調用者有事務

被調用者拋出異常

有

有

有，開啟事務

無

調用者有事務，被調用者開啟事務。
調用者拋出異常，因被調用者的事務與調用者是同一個，所以調用者與被調用者皆會回滾。

<調用者>

@Transactional()
public void hasTransactional() {
    insertData();
    callee.hasTransactional();
    throw new RuntimeException();
}

<被調用者(callee)>

@Transactional(propagation = Propagation.SUPPORTS)
public void hasTransactional() {
    insertData();
}
情境三

調用者有事務

調用者拋出異常

被調用者有事務

被調用者拋出異常

無

無

無

有

調用者無事務，被調用者無事務。
被調用者拋出異常，因調用者與被調用者皆無事務，所以調用者與被調用者皆不會回滾。

<調用者>

public void hasTransactional() {
    insertData();
    callee.hasTransactional();
}

<被調用者(callee)>

@Transactional(propagation = Propagation.SUPPORTS)
public void hasTransactional() {
    insertData();
    throw new RuntimeException();
}
 

//=======================================================
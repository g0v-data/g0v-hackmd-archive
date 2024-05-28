# 5/29
## ch 11
[toc]
## Basic Networked Application Concepts
- 應用層功能在電腦之間傳播以向使用者提供服務有以下三種模式
    1. Stand-alone operation(單機運作)
    2. Client/server operation(客戶端/伺服器操作)
    3. Peer-to-peer (P2P) operation(點對點操作)
## Application Security
- 如果應用程式有漏洞，很可能被入侵並濫用權限(xss,SQL Injection)
### xss
- 什麼是xss?
    - 跨網站指令碼(Cross-Site Scripting，通常簡稱為XSS)
    - 駭客在瀏覽器插入惡意 Javascript，一旦受害者的瀏覽器解析並執行，可能導致受害者cookie 被盜取、網頁導向惡意網站等
    - 簡單來說，就是讓使用者(駭客)「 輸入的資料」 變成「 程式的一部分 」，藉此攻擊其他的使用者
- 常見的 XSS 手法分為三種類型： (危害等級： 儲存型 > 反射型 > DOM 型)
    - 反射型 XSS ( Reflected )
        - 若後端程式會從 GET 參數取得資料，並將內容顯示在前端，如此一來便可在 GET 參數中植入 javascript。
       - e.g. 將攻擊的 script 藏在URL中，網頁透過 GET 參數傳遞
       ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_72d2b0d7d67c8b4cd861eba8ebdfd3ea.png)

    - 儲存型 XSS ( Stored )
        - 攻擊的方式是 Hacker 將 Javascript 儲存在伺服器的資料庫中，進而引起使 User 遭受攻擊。
        - e.g. 將攻擊的 script 透過留言板功能，儲存於 database 中，當下一位 User 瀏覽網頁時，網頁會載入留言板的 Javascript 進而使 User 受到攻擊
    - DOM 型 XSS
        - 前二型通常發生在網頁的後端程式，然而DOM XSS是基於客戶端的，並且其惡意腳本不會通過服務器端輸入輸出過程
       -  DOM XSS與反射型XSS的主要區別在於，DOM XSS是在客戶端透過JavaScript程式碼直接處理不受信任的數據，而反射型XSS涉及伺服器將惡意輸入反射回客戶端。

## SQL Injection
```
SELECT * FROM Users WHERE (UserName='” + strUN + “') AND (Password='” + strPW + “');”
```
攻擊手法:
```
SELECT * FROM Users WHERE (UserName='' OR '1'='1') AND  (Password='' OR '1'='1');

```
- 加 - -把後面註解調，根本不用CARE Password要輸入什麼
```
SELECT * FROM Users WHERE (UserName='' OR '1'='1'--) AND  (Password);

```

## email
- 是internet早期被發明出來的應用，到目前為止該標準都沒有被修改，但存在某些限制互聯網普遍服務
- 可以附加、傳送檔案，並算是最為妥當的傳送方式
- 但很多攻擊都經由email(釣魚、傳播病毒或蠕蟲)
- 寄信(SMTP)與收信(POP,IMAP)是不同標準
- 文件標準：RFC 822/2822 用於純文字訊息，用於格式化的 HTML 正文，UNICODE 可以表示任何語言的文本

## Simple Mail Transfer Protocol (SMTP)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_20e6d4596a211c85e8c9ec42e85a7684.png)
- 200多 正常
- 300多 正在處理中
- 400、500、600…錯誤
- Mail from:實際的寄信者
- RCPT to:實際上的收件人
- CRLF:換行符號

## Scanning Locations for E-Mail

- 在兩個或多個位置進行過濾可以提供深度防禦。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0c53b9cc0505ae2ee870159d39031e32.png)

## Encryption for Confidentiality
- SSL/TLS只有保護客戶端到MAIL HOST，那其他地方要由誰保護?
- MAIL HOST之間也可以使用SSL/TLS
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6d9a605f104f85806a7ab0cdc75bbc82.png)

- 端到端加密是可能的，傳送前用PGP加密，它是由兩個主機完成的，但是很少這樣做
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2b702c819583fab67a5cbfbbaf7581be.png)




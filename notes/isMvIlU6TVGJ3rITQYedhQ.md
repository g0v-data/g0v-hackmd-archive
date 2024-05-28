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
       -  e.g. 在 input 處輸入 DOM 語法，只能在前端發生，所以除非駭客在你電腦前幫受害者輸入，否則無法讓受害者輸入惡意程式，所以通常 DOM 型 XSS 要搭配反射型與儲存型製造出內容，讓 Javascript 動態產生 DOM 才能達成

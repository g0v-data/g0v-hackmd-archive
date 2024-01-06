# 前端工程師面試問答

## 常見問題
💡**說出三種能加快網頁讀取速度的方法（如何有效減低網頁 loding 太久？、如何降速？）**

網頁載入流程：
1. 解析HTML結構。
2.  載入外部指令碼和樣式表文件。
3. 解析並執行指令碼程式碼。// 部分指令碼會阻塞頁面的載入
4. DOM樹構建完成。//DOMContentLoaded 事件
5. 載入圖片等外部檔案。
6. 頁面載入完畢。//load 事件

一句話說明：請求HTML，然後順帶將HTML依賴的JS/CSS/iconfont等其他資源一併請求過來。
降速的最本質方法：**減少請求數量**、**減小請求大小**

* **減少請求數量**
    1. 將小圖示合併成 [sprite 圖](https://kknews.cc/zh-tw/code/2ellvm9.html)或者 iconfont 字型檔案
    2. 用 base64 減少不必要的網路請求
    3. [圖片延遲載入](https://www.jianshu.com/p/dc5fd46ff22c)
    4. JS/CSS按需打包
    5. 延遲載入ga統計

* **減小請求大小**
    1. JS/CSS/HTML壓縮
    2. gzip壓縮
    3. JS/CSS按需載入
    4. 圖片壓縮，jpg優化
    5. webp優化 & srcset優化

[◎參考1：如何讓你的網頁開啟速度降低到1s內](https://www.itread01.com/content/1548824798.html)

## HTML
💡**doctype 做什麼用的？**
document type (文件型別)的簡寫，用來說明用的XHTML或者HTML是什麼版本。

\
💡**standards mode 和 quirks mode 有什麼不同？**
在W3C標準制定之前，就已經有很多網站跑在 Netscape Navigator 和 Internet Explorer 上了，如果瀏覽器都按照W3C的標準去實現的話，以前的那些網站就會壞掉。為了**相容以前的網站**，所以產生了quirks mode（怪異模式），瀏覽器會按照 W3C 標準以前的簡析方式去工作。

\
💡**data- 屬性的好處在哪**
我們常常會添加一些自己需要用到的屬性名稱，以方便自己容易理解，為了避免在 HTML 結構中隨意的添加屬性，在 HTML5 中就多了 data-* attribte 這個屬性，其中的 * 就是一個可以**自定義**的名稱，且**可以被 js 操作**。

\
💡**請描述 cookies, sessionStorage 和 localStorage 的不同**

* **HTTP cookie（web cookie、browser cookie）**
    為伺服器傳送給使用者瀏覽器的一個小片段資料。瀏覽器可能儲存並在下一次請求回傳 cookie 至相同的伺服器。Cookie 通常被用來保持使用者的登入狀態 — — 如果兩次請求都來自相同的瀏覽器。有個數限制（各瀏覽器不同），一般不能超過20個。
    特性：儲存量小、不適用於大量資料本地儲存。
    應用場景：
    1. Session 管理
        帳號登入、購物車、遊戲分數，或任何伺服器應該記住的資訊。
    2. 個人化
        使用者設定、佈景主題，以及其他設定
    3. 追蹤
        記錄並分析使用者行為
    
* **LocalStorage / SessionStorage**
    HTML5提供兩種在客戶端儲存資料的方法，兩者可使用的API都相同。
    1. sessionStorage
        將資料儲存在 session 中，瀏覽器關閉也就沒了。
        應用場景：
        如果遇到一些**內容特別多的表單**，為了提升用戶體驗，可能要把表單頁面拆分成**多個子頁面**，然後**按照步驟**引導用戶。
    2. localStorage
        一直將資料儲存在客戶端本地。
        應用場景：
        代替 Cookie 管理購物車的工作。

**生命周期只存在瀏覽囂的單一分頁** ，也就是另開新分頁的話 ，又是一個新的 sessionStorage ，預設無逾期時間，除非關閉該分頁、關閉瀏覽器等，sessionStorage 就會消失。

![cookies, sessionStorage 和 localStorage 的差異](https://miro.medium.com/max/1400/1*JiT0KNuYIO8l5QBtpNtOHA.png)

\
💡**為什麼把 CSS `<link>` 放在 `<head></head>` 之間，與將 JS `<script>` 放在 `</body>` 之前是個較好的主意？有什麼例外情形嗎？**

程式碼是一行一行接著渲染，如果 Js若放在 `<head></head>` 中會延遲第一次渲染的速度，而放在 `</boby>` 內則可以減少載入時間。
若 js 當中需要調用 css 內的參數，css 要先載入才行。

*（缺例外情形）*


\
💡**描述下列之間的不同 `<script>`, `<script async> `& `<script defer>`。**

* **`<script defer>`**
    在解析 HTML 時不會停下來等 js 執行完，而是 等到 HTML 解析完成才執行，而且會**循著宣告的順序執行**。
    如果你將 `<script>` 放在 HTML 文檔的結尾，有沒有加 defer 的效果是一樣的。
    差別是當你將 `<script>` 放在 HTML 文檔中間，他並不會暫停 HTML 解析。
* **`<script async>`**
    async 也不會暫停 HTML 解析，但他很特別，他會在**下載完成**的那一刻馬上執行。
    如果有多個 `<script>` 使用 async，他們之間的執行順序一定不能保證，async 只適合用在需要**越早執行越好**，但是又**跟其他程式碼沒有依賴關係**的程式碼，像是偵測使用者行為的程式（例：**Google Analytics**）。


## CSS
💡**針對各瀏覽器制定的樣式表（browser-specific styling），你的做法是？（如何讓不同瀏覽器設定預設樣式？、兼容性問題）**
1. **Css 初始化（Reset.css）**
    不同的瀏覽器有不同的預設值，清除即可統一。
3. **瀏覽器私有屬性（前綴詞）**
    1. -moz: firefox
    2. -ms: IE
    3. -webkit: chrome, safari
    4. -o: opera
4. **Css Hack** 
    針對不同的瀏覽器或不同版本寫特定的 css。因無法通過 W3C 驗證， 若要使用 CSS Hack 來統一各瀏覽器之間的差異，把他當成是網頁設計時**最後的手段**。
[◎參考1：瀏覽器兼容性](https://jimmywei01.github.io/2019/05/23/%E7%80%8F%E8%A6%BD%E5%99%A8%E5%85%BC%E5%AE%B9%E6%80%A7%E7%B4%80%E9%8C%84-%E5%96%AE%E4%BD%8D%E3%80%81font%E3%80%81CSS-%E8%A8%AD%E5%AE%9A%E3%80%81RWD-media/)
[◎參考2：告別瀏覽器兼容問題](https://kknews.cc/zh-tw/code/3a5n2jo.html)

\
💡**display: none 跟 visibility: hidden 差別**
* visibility： hidden：隱藏元素，但在頁面上保留該元素的空間。
* display: none：元素實際上就從頁面中被移走，相當於消失。

\
💡**描述 “resetting” 和 “normalizing” 的差異性？**

* Reset.css
    優點：清除所有預設設定
    缺點：過於激烈的重置，不管是 h1 還是 h5 甚至是 span 標籤，大小都是一樣的，且**已經不再維護**。
* Normalize.css
    優點：保留不衝突的預設值、且持續在維護的專案。
    
一般的 CSS framework 已經初始化完，如 Bootstrap 、 materialize 和 ant-design 中，是使用 Normalize.css。


## Javascript
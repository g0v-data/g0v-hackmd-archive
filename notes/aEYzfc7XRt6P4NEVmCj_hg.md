## 透明來源行動 – 介紹跨平台內容來源（XPOC）框架

**前情提要**

Microsoft Research 進行了一個非營利開源行動，名為 XPOC。他們打造了一個簡單的憑證工具，可以視為跨平台、跨網頁使用者認證「藍勾勾」，將網路上的資訊，以發表單位進行自我認證，協助事實查核方進行審核業務。目前 Microsoft Research 正在台灣尋找合作夥伴歡迎與我們聯繫。

---

**參與者**
坑主：簡信昌 HC hcchien@gmail.com
張潔平 [az@matters.town](https://)
Jacky taipeicity.eth@gmail.com
黃豆泥 mashbean@gmail.com

---

[10/15 g0v hackthon 短講介紹簡報 by HC](https://docs.google.com/presentation/d/1uin7WFZhHLCovCL6Dw8NqxG8oH5g2GW5V1sC5Zpcssw/edit)
[1015 Hackthon Record](/VxleYzp1S4qJyV0rRquq4w)

MSR Christian 提供資料 10/15 Update
1. [Demo Video](https://www.youtube.com/watch?v=OVyOKU8qfQM)
2. [Sample Website](https://microsoft.github.io/xpoc-framework/)



* a new tutorial video demonstrating how to use the sample manifest creation tools
* a new resource website containing the relevant project information and the deployed sample tools (we’ve made some updates this week, so this page contains the latest version).

---

**招募夥伴**

1. **資訊發表方**：如媒體、非政府組織、公民團體，透過 XPOC 釋出的工具，簡單製作出一個純文字檔案，並且放在發布單位官網的目錄下（方式就像 robots.txt 以及 ads.txt），讓 XPOC 程式可以辨識網路內容來源。
2. **資訊查核方**：如事實查核組織、專家、社群，使用 XPOC 提供的工具，對於網路上有疑慮的內容進行內容溯源。

**開坑目標**

1. 尋求事實查核相關領域專家合作，瞭解目前的工作流程，研究既有流程如何應變 AI 帶來的影響。
2. 收集改進 XPOC 和解決錯誤資訊問題的技術方法，並且具體回饋。
3. 以台灣的協作經驗為基礎，在試行期間收集學習成果，建立通報和影響，將成果應用於全球範圍，以建立減少不實資訊的策略。

**我們目前有的資源**

參與者將能與 Microsoft Research 計劃開發者和研究人員接觸，得到技術支援與整合諮詢，以及共同參與議題與解法的回饋討論。我們希望儘快展開遠距合作，並在試行後，我們的團隊成員將直接在台灣一個月，與共同協作的成員們直接合作。

---

**Microsoft Research 簡介 XPOC**

生成人工智慧（Generative AI）最近快速發展，加劇了錯誤資訊（misinfomation）的影響。為了減少人工智慧的潛在有害干擾，我們打造了辨識媒體可信度的工具，使公民與公民團體更有意識地評估他們平常接觸的媒體內容，以提升公民數位素養。

此工具名為「透明來源行動—跨平台內容溯源計畫」（Cross Platform Origin of Content Project，簡稱 XPOC）。XPOC 讓個人或組織對他們所發佈的內容進行數位認證。我們建立XPOC 框架，規範了如何在「不同」新聞媒體、社群平台或個人網頁上，發佈內容清單，並託管在一個網站上，讓使用相關規範的工具能自動發現和驗證這些內容。

本計畫已經在 GitHub 上公開。我們的下一步是與媒體、非政府組織、公民團體以及事實核查社群合作，試行 XPOC。過去十年來，台灣的公民科技社群常常使用新興科技面對社會問題，並打造出世界級的問題解決能力，因此我們希望在台灣試行 XPOC。

MSR Rsearch: [About Microsoft Research](https://www.microsoft.com/en-us/research/about-microsoft-research/)
Special Projects: [Microsoft Research Special Projects](https://www.microsoft.com/en-us/research/group/microsoft-research-special-projects/)

---

計畫的開放原始碼與介紹影片連結如下：
GitHub：https://github.com/microsoft/xpoc-framework
部落格：https://christianpaquin.github.io/2023-09-08-xpoc-framework.html
Youtube 技術概要：https://www.youtube.com/watch?v=G9OGrOpNif8
Youtube demo：https://www.youtube.com/watch?v=PNn_ex_J-YA

如果您有興趣與我們合作，成為試行計劃的一員，請寄信至 xpoc@Microsoft.com。

---

下文譯自：[Introducing the Cross-Platform Origin of Content (XPOC) framework](https://christianpaquin.github.io/2023-09-08-xpoc-framework.html)
開坑頁面： [透明來源行動：開坑夥伴募集
](https://hackmd.io/IbH86vFfTDKgInDLx3j7Hw)

文：Christian Paquin 2023/09/08
譯：mashbean 2023/10/01

---

### 透明來源行動簡介

這個年頭要驗證網路內容的來源相當具有挑戰性。知名內容創作者（無論是個人或組織）在他們的官方網站中，通常會提供他們在社群媒體上的相關帳戶，如 YouTube、X/Twitter、Facebook、Instagram... 等，最常見的方式是放上這些社群平台的 Logo。

![社群網站的 logo ](https://hackmd.io/_uploads/HJzH6-ve6.png)

我們要自己驗證此類資訊是否來自真正的創作者本人，可能會很複雜，並且需要先知道創作者的網站網址。此外，許多內容可能來自多名創作者合作的結果，例如 Podcast、影片訪談、會議 Panel 等等，而內容可能由其中一位創作者或主持人的帳號發布。

尤其生成式 AI 不斷進化，可能加速虛假資訊的影響力。透過 AI 製作看似真實的假帳戶和內容，可能損害個人聲譽，也可能對整個社會產生影響，這將非常危險。 道高一尺，魔高一丈，AI 檢測工具正在與潛在惡質的 AI 使用者進行搏鬥，但處於劣勢。許多媒體托管平台都有帳戶和內容驗證流程，但品質各不相同，這些平台彼此脫鉤，無法藉由標準化的驗證機制進行資源共享。

為了解決這個問題，我們打造了[透明來源行動（XPOC）框架](https://github.com/microsoft/xpoc-framework)，允許內容創作者：
1. 在各個平台上公開其帳戶和批准內容的授權清單
2. 使用特殊的 XPOC URI 為這些帳戶和內容增加標籤，並與其清單相互關聯。

這使得驗證工具能夠自動確定受保護內容的來源。

![](https://hackmd.io/_uploads/Bk6OpWvxp.png)
christianpaquin.github.io的XPOC 清單

這個行動與框架對政治家、名人、公司、政府實體和許多其他利益相關者來說非常有用，可以為他們所控制的帳戶和內容，提供溯源的真實性。

XPOC 框架的設計目標是盡量能夠簡單操作，允許內容創作者發表清單並為受保護的內容添加標籤，而無需與特定社群平台合作；反過來說，實施該框架的平台將改善使用者體驗和內容來源驗證。

該 GitHub 專案包含框架規範、TypeScript 參考庫以及用於 XPOC 清單編輯工具和 XPOC URI 驗證工具的一些案例。

### 系統概述

我將以自己作為例子來說明 XPOC 框架。我的主要網站是 christianpaquin.github.io，這個網頁彰顯了我的專業，你可以在這裡找到我在其他平台上控制的一些社交帳戶連結（例如我的 X/Twitter 帳號和我的 GitHub 帳號）。我創建了一個 XPOC 清單，以標準化且易於發現的方式列出所有這些帳戶。此外，我還添加了連結到我創建或參與的，但不由我控制的帳戶發布的內容（例如，這個在微軟 YouTube 頻道上發布的有關[社會韌性的專題](https://www.youtube.com/watch?v=pzi76VdmD9g)或我在 DEF CON 27 上發表的[後量子加密演講](https://www.youtube.com/watch?v=IqCw19bKE6c)）。您可以查看托管在這個網站上的 xpoc-manifest.json 文件。

![](https://hackmd.io/_uploads/ry7-RZPga.jpg)
christianpaquin.github.io的 XPOC 清單

值得注意的是，此清單僅包含我與我的微軟形象相關聯的帳戶和內容；我還有其他個人帳戶和內容沒有在此列出（但可能存在於個人網頁的清單中）。

如果有人或某個系統想要找到與我相關聯的所有帳戶和內容，他們可以檢索並檢查此文件。人們更喜歡使用更友好的進行檢視，例如我們在 GitHub Repository中提供的示例 XPOC [檢視器](https://github.com/microsoft/xpoc-framework/tree/main/samples/client-side-html)。

![](https://hackmd.io/_uploads/ryVm0WPla.jpg)
XPOC清單檢視器

該框架的一個重要功能是能夠將這些帳戶和內容連結回我的主要網站，讓訪客知道是誰在我的社交媒體帳號和帳號名背後。我透過我的帳戶頁面和內容中增加 `xpoc://christianpaquin.github.io!` XPOC URI 來實現這一點。前綴 `xpoc://` 和終止字符 `!` 有助於解析工具在頁面的 HTML 中找到 URI；然後它們將提取基本 URL `christianpaquin.github.io` 並在 `https://christianpaquin.github.io/xpoc-manifest.json` 處提取相應的清單。

例如，我在我的 [X/Twitter 個人簡介](https://twitter.com/chpaquin) 中和[ YouTube 影片描述](https://www.youtube.com/watch?v=hDd3t7y1asU)  中放置了我的XPOC URI，這樣驗證工具就可以找到我的清單。

我們的 GitHub 存儲庫中包含一個案例 [瀏覽器擴充套件](https://github.com/microsoft/xpoc-framework/tree/main/samples/browser-extension)，可用於驗證這些URI，讓人們可以驗證這些帳戶和內容是否真的是我本人，而不是冒充者。

![](https://hackmd.io/_uploads/Hk5u0ZDlT.jpg)
驗證X/Twitter XPOC URI

![](https://hackmd.io/_uploads/SJyt0WDe6.jpg)
驗證X/Twitter XPOC URI
    
    
### 前方道路

打擊假訊息和虛假內容是一項具有挑戰性的任務，我們還在非常初始的階段。

XPOC 框架不會神奇地解決問題，但它可以幫助解決其中一部分問題。如果內容創作者（尤其是那些受到虛假內容攻擊的人）開始發布內容清單，那麼驗證者（事實核查人員、記者、託管平台）將能夠更好地確認其來源，這將減少惡意內容造成的損害機會。

若早期採用 XPOC 的人不幸成為攻擊目標，將可能有助於教育驗證者，讓他們知道他們應該檢測到虛假內容，因為它們沒有列在清單中。這些早期事件將有助於 XPOC 具有實際效果。

隨著採用的增加，攻擊將越來越難以針對使用 XPOC 框架的創作者，攻擊者可能會專注於那些不使用的人。就像在 HTTP 到 HTTPS 的轉換過程中發生的情況一樣，早期採用者受益於更強大的安全性，而那些遲到的人則會被標記為不安全甚至被封鎖。我可以想像，如果創作者開始使用 XPOC，相同的情況可能會發生：最後一小部分未受保護的帳戶看起來可疑，可能會在託管平台上經歷更嚴格的帳戶和內容審查過程。

告訴我們您對XPOC框架的看法，它如何使用和改進。

一起向前！

###連結

1. GitHub Repository：https://github.com/microsoft/xpoc-framework
2. 技術概述視頻：https://www.youtube.com/watch?v=G9OGrOpNif8
3. 示範影片：https://www.youtube.com/watch?v=PNn_ex_J-YA

---
title: '題目：ONTOLOGIES AND INTERACTIVE NETWORK VISUALIZATIONS 本體和交互式網絡可視化 '
---
:::success
[回 2021 NASA 黑客松挑戰中文翻譯 Challenge](https://g0v.hackmd.io/4DIbh5k4R-SNBq3FdGMIjQ?both)
:::

題目：ONTOLOGIES AND INTERACTIVE NETWORK VISUALIZATIONS 本體和交互式網絡可視化 
===
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e7892bb8e8c1b90a7464fc509e6a2fd6.png)

[官網原文](https://2021.spaceappschallenge.org/challenges/statements/ontologies-and-interactive-network-visualizations/details)

# Full Details 完整說明

## Summary 概述

> Tens of thousands of NASA datasets are publicly available online, but with so many files available, how can potential users determine those that will meet their needs? Your challenge is to (1) create an ontology to integrate descriptions of disparate NASA data sets, and (2) develop an interactive network visualization to depict relationships among those data sets.

數以萬計的美國國家航空暨太空總署(NASA)資料集在網路上皆是公開做使用的，但有這麼多檔案能夠使用，潛在用戶要如何確定哪些數據能夠滿足他們的需求？你的挑戰是（1）創建一個本體來整合各種不同的NASA資料集的描述、（2）開發一個可視化的交互式網路來描述這些資料集的關係。

## Details 詳細描述
### Background 背景說明
> The NASA Open Data Portal provides a catalog of 42,946 data sets and 555 code repositories, and links to open-innovation sites, NASA science archives, and code and data from numerous U.S. federal agencies. Many of the data set collections are described in JavaScript Object Notation (JSON) files.
> 
> Given burgeoning NASA data, users can have a hard time knowing where to start, or knowing which data set(s) might meet their needs. This issue is exacerbated by different data sets having varying internal organization / list mechanisms, further confusing the user. NASA is going through the process of creating an internal metadata catalog that would act in many ways like data.nasa.gov does publicly. Both catalogs are primarily catalogs of metadata, not data. For data.nasa.gov, its metadata follows the project open data standard and is available as a single JSON at data.nasa.gov/data.json. What types of data visualizations or user interfaces can you come up with that save users time and frustration by linking them with the right data sets in a faster, more accurate manner?
> 
> An ontology defines terminology, organizes classes of things into a taxonomy, describes types of relationships among things, and specifies the attributes of things. The relationships between these things can be depicted as a network consisting of shapes and lines that connect the shapes. Each shape represents a node (or thing) and the lines depict relationships between connected nodes (or things). Free open-source software is available for developing ontologies and network visualizations.
> 
美國太空總署資料開放平台提供包含 42,946 個資料集和 555 個代碼儲存庫的目錄，以及連接到開放式創意網站、美國太空總署科學檔案和眾多美國聯邦機構的代碼和數據的連結。許多資料集是用 JavaScript Object Notation (JSON) 文件描述的。

鑑於美國太空總署資料迅速增長，用戶可能很難知道從哪裡開始，或者知道哪些資料集可能滿足他們的需求。不同的資料集會有不同內部組織/排列技巧，加劇了這個問題，進一步混淆了用戶。美國太空總署正在創建一個內部詮釋資料目錄，該目錄很多方面將像 data.nasa.gov那樣公開運作。這兩個目錄主要是詮釋資料目錄，而不僅是資料目錄。至於data.nasa.gov，其詮釋資料依照項目開放資料為標準，並以單個JSON形式在data.nasa.gov/data.json 上供使用。你可以想出哪些類型的資料可視化或用戶界面可以以更快、更準確的方式將用戶與正確的資料集連結起來，節省用戶的時間和減少挫折感？

本體論定義了術語，將事物的類別組織成分類法，描述事物之間的關係類型，並且指定事物的屬性。這些事物之間的關係可以被描述為由形狀和連接形狀的線所組成的網絡。每個形狀代表一個節點（或事物），線條描繪了連接節點（或事物）之間的關係。免費的開源軟體可用於開發本體論和網絡可視化。

### Objectives 目標
> Your challenge is to (1) create an ontology to integrate descriptions of disparate, publicly available NASA data sets, and (2) develop an interactive network visualization to depict relationships among those data sets. Objectives of this challenge include specifying a taxonomy of data set classes, integrating terminology, defining relationships (also known as object properties), and identifying attributes (also known as data properties) of data sets in open data catalogs. You may then apply the ontology to define a network wherein data sets are nodes and the notional relationships among them are the links between nodes. The network should be visualized as an interactive diagram or 3D model embedded in a web page.
> 
> Specific activities associated with this challenge include:
> 1.	Exploring open data sets at NASA and other U.S. government agencies, as well as free and open datasets from other international space agencies.
> 2.	Identifying complementary data sets, e.g., Earth science data sets, population densities, demographics, pollution, etc.
> 3.	Obtaining the JSON description of those data sets. Viewing the source of a web page can reveal links to JSON data.
> 4.	Creating an ontology or a master JSON structure for integrating disparate data set descriptions.
> 5.	Visualizing the ontology or integrated JSON data as an interactive network. Examples of relationships could be locations, source, key words, etc.
> 
> An ideal network visualization will be interactive; e.g., the nodes will be linked to the web page that describes the data set. Your interactive network should be integrated into a web page.


你的挑戰是（1）創建一個本體來整合各種不同的NASA資料集的描述、（2）開發一個可視化的交互式網路來描述這些資料集的關係。此挑戰的目標包括指定資料集類的分類法、整合術語、定義關係（也稱為物體屬性）以及識別開放資料目錄中資料集的屬性（也稱為資料屬性）。然後，你可以應用本體論來定義網絡，其中資料集是節點，它們之間的概念關係是節點之間的連結。網絡應被可視化為一個交互式圖表或嵌入在網頁中的3D 模型。

與此挑戰相關的具體活動包括：
1. 探索美國太空總署和其他美國政府機構的開放資料集，以及其他國際太空機構的免費開放資料集。
2. 辨識補充資料集，例如地球科學數據集、人口密度、人口統計、污染等。
3. 獲取這些資料集的 JSON描述。查看網頁的來源可以顯示連接 JSON 數據的連結。
4. 創建一個本體或主要的JSON結構以整合不同的資料集描述。
5. 將本體或整合JSON 數據可視化為一個交互式網絡。關係的範例可以是位置、來源、關鍵詞等。

理想的網絡可視化將是交互式的；例如，節點將連接到描述資料集的網頁上。 你的交互式網絡應該整合到一個網頁中。

### Potential Considerations 潛在考量
> You may (but are not required to) consider the following when developing your ontology and visualization:
> - Popular code repositories offer free hosting of web pages that can include JavaScript, which can parse JSON data.
> - Your interactive network could be hierarchical; clicking on a node could open a lower-level detailed network. A web application could display a taxonomy in a navigation pane and another pane could present the interactive network of data sets that exist within a selected class. Nodes could be color-coded or various icons could be used as node shapes to indicate different categories. Scalable Vector Graphics (SVG) could depict a network and the shapes could have embedded Uniform Resource Locators (URL). The binary version of the Graphics Language Transfer Format (GLB) could be embedded in a web page and displayed via a viewer, which would enable the creation of an interactive 3D network.
> - This challenge requires knowledge in ontology development and skills in data visualization. When recruiting team members, consider seeking ontologists as well as web application developers who are familiar with data visualization code libraries. Research free and open-source applications and code libraries.
> - The Example Resources include links to a NASA Scientific and Technical Information (STI) thesaurus, a NASA Taxonomy at the Library of Congress, a Planetary Data Sciences (PDS) ontology expressed in the Resource Description Framework (RDF) format, and subjects from the NASA taxonomy specified in a Simple Knowledge Organization System (SKOS) ontology. This thesaurus, taxonomy, and the ontologies can serve as examples of the types of products that could be generated in this challenge. Research search terms may include “Label Property Graphs” (LPG), “Typed Property Graphs” (TPG), and RDF to LPG conversion.
> - Security policies and regulations prohibit NASA personnel and contractors from downloading executable code to their computers. Ontology documentation and a network diagram with embedded hyperlinks could be a Portable Document Format (PDF) file. Ontology editors can export web-based documentation and code libraries can produce interactive collapsible and expandable networks within a web application. Web-based documentation and web applications ought to be deployed on a web server. There are free web hosting services.
> - Key words in the text above can serve as a starting point for your research online; inclusion of those key words in this challenge description does not constitute an endorsement.

在開發本體和可視化時，你可以（但不是必須）考慮以下事項：
* 流行的代碼儲存庫提供免費網頁代管服務，其中包含可以解析JSON資料的JavaScript。
* 你的交互式網絡可以是階級制的；點一下節點可以打開一個較低級別的詳細網絡。一個網路應用程式可以在導航視窗中顯示分類法，而另一個視窗可以顯示所選類中存在的數據集的交互式網絡。節點可以用顏色編碼，也可以使用各種圖標作為節點形狀來辨認不同的類別。可縮放向量圖形 (SVG) 可以描繪網絡，並且形狀可以嵌入統一資源定位器 (URL)。圖形語言傳輸格式 (GLB) 的二進制版本可以嵌入到網頁中並通過瀏覽器顯示，這將能夠創建交互式 3D 網絡。
* 這個挑戰需要本體開發方面的知識和資料可視化方面的技能。在招募團隊成員時，請考慮尋找本體論者和熟悉資料可視化代碼庫的網路應用程式開發人員。研究免費和開放的應用程式和代碼庫。
* 範例資源包括美國太空總署科學和技術資訊(STI) 同義詞庫的連結、美國國會圖書館中的美國太空總署分類法、以資源描述框架 (RDF) 格式表示的行星數據科學 (PDS) 本體以及來自美國太空總署在簡單知識組織系統 (SKOS) 本體中指定的分類法。這個詞庫、分類法和本體可以作為在這個挑戰中可能產生的產品類型的例子。研究檢索詞可能包含“標籤屬性圖”(LPG)、“類型化屬性圖”(TPG) 和 RDF 到 LPG 的轉換。
* 安全政策和法規禁止美國太空總署人員和承包商將可執行代碼下載到他們的電腦上。本體文檔和帶有嵌入超連結的網絡圖可以是可攜式文件格式 (PDF) 的文件。本體編輯器可以匯出基於網路的文檔，代碼庫可以在網路應用程式中產生交互式的可折疊和可擴展的網絡。基於網路的文檔和網路應用程式應該部署在一個網路伺服器上。有免費的網頁代管服務。
* 上文中的關鍵詞可以作為你在線上研究的起點；將這些關鍵詞納入本挑戰描述中並不會有加分效果。

# Resources 相關資源
> <https://2021.spaceappschallenge.org/challenges/statements/ontologies-and-interactive-network-visualizations/resources>


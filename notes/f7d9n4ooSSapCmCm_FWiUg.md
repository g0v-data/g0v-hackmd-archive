---
title: '題目：VIRTUAL PLANETARY EXPLORATION V2.0 虛擬行星探索 V2.0 '
---

:::success
[回 2021 NASA 黑客松挑戰中文翻譯 Challenge](https://g0v.hackmd.io/4DIbh5k4R-SNBq3FdGMIjQ?both)
:::

題目：VIRTUAL PLANETARY EXPLORATION V2.0 虛擬行星探索 V2.0 
===
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d00d94c97bd7d9c46da96b00d347d899.jpeg)

[官網原文](https://2021.spaceappschallenge.org/challenges/statements/virtual-planetary-exploration-v20/details)

# Full Details 完整說明

## Summary 概述
> Future astronauts will conduct various activities in space and on or near celestial bodies to help us learn about their mission destinations, Earth, and our universe. Your challenge is to create interactive 3D models of equipment (e.g., planetary geology tools) that future space explorers might use for activities like exploring a planetary surface.

未來的太空人將會在太空和天體上或附近，進行各式各樣的活動，以幫助我們了解他們的任務目的地、地球和我們宇宙。你的挑戰是創建交互式的3D模型設備(例如，行星地質工具)，好讓未來的太空探索者可使用這些模型來進行探索行星表面之類的活動。

## Details 詳細描述
### Background 背景說明
> A half-century ago, NASA conducted the Apollo missions, which put the first men on the Moon. Artemis (the name of Apollo's twin sister in Greek myth) is NASA's planned lunar mission to put the first woman and the next man on the Moon. As future astronauts conduct a variety of upcoming robotic and human activities on the surface and in orbit around the Moon, we will better understand the universe and our home planet. Then, we will use what we learn on and around the Moon to take the next giant leap – sending astronauts to Mars.

半個世紀前，美國太空總署進行了阿波羅任務，將第一批人類送上月球。阿特米斯（希臘神話中阿波羅的雙胞胎妹妹）是美國太空總署計劃中的月球任務，預計將第一位女性和下一位男性太空人送上月球。隨著未來的太空人在月球表面和軌道上進行各種機器人和人類活動，我們將更深入了解宇宙和我們的星球。然後，我們將利用我們從月球所學到的知識，達成下一個巨大的目標---將太空人送往火星。

### Objectives 目標
> Your challenge is to create interactive 3D models of equipment that future space explorers might use for activities such as exploring a lunar or planetary surface and deploy these models on a web page.
> 
> Think about what kinds of experiments future explorers will want to perform, and what sort of tools could help with those experiments. For example, you could (but are not required to) design planetary geology tools for exploring bodies such as moons, planets, and asteroids. One historical reference, the Apollo 16 Press Kit (see Example Resources), has pictures of the tools that the Apollo 16 astronauts carried in their geology field kit.
> 
> Objectives of this challenge may be educational or creative or both. In pursuit of the educational objective, your team may choose to create interactive models of historical items, such as the handheld tools used during the Apollo missions or science instruments and systems used in Lunar missions conducted by the other space agencies participating in the International Space Apps Challenge. In pursuit of the creative objective, your team may choose to invent new tools or surface exploration systems. Inventions may derive and improve upon historical systems. If your team develops a new and improved version of a historical system, make sure to describe that heritage in your project's product description.
> 
> Participating teams should research planetary exploration tools, create interactive 3D models of the equipment, embed those models in a web page, and deploy the web page on a free hosting service. Products from this challenge ought to be relatively low polygon count models in the Graphics Language Transmission Format (GLTF). The model(s) should be embedded in a deployed web page.


你的挑戰是創建交互式的3D模型設備，好讓未來的太空探索者可使用這些模型來進行探索行星表面之類的活動，並將此模型架設於一個網頁中。

想一想未來的探索者會想要進行什麼樣的實驗，以及什麼樣的工具可以幫助這些實驗的進行。例如，你可以（但非必須）設計行星地質學工具，用於探索衛星、行星和小行星等天體。有一個關於阿波羅16號的歷史參考資料(詳見參考資源)，其中有阿波羅16號太空人在地質學野外工具箱中攜帶的工具圖片。

這項挑戰的目標可以是教育性的，也可以是創新性的，或者兩者兼有。為了實現教育目標，你的團隊可以選擇創建歷史物品的交互式模型，如阿波羅任務中使用的手持工具，或參加國際太空應用程式挑戰賽的其他團隊執行月球任務時使用的科學儀器和系統。為了追求創造性的目標，你的團隊可以選擇發明新的工具或地表探索系統。發明可以在歷史系統的基礎上加以做變化和改良。如果你的團隊開發了一個歷史系統的改良版，請務必在你的產品敘述中描述該歷史系統。

參賽團隊應研究行星探測工具，創建設備的交互式3D模型，將這些模型嵌入到網頁中，並將網頁部署到免費的託管服務。這項挑戰的產品應該是圖形語言傳輸格式（GLTF）中相對較少多邊形數量的模型。這些模型應該被嵌入於網頁中。

### Potential Considerations 潛在考量
> As you develop your project, you may (but are not required to) consider the following:
> - Beginners may create individual tools or devices such as a pick or a hammer. Intermediate teams may produce a kit containing multiple tools or devices; the kit itself may be a backpack or an interactive container. Advanced teams could create interactive models of analysis equipment that present real or simulated time-series data.
> - The model could be a historic or futuristic design of equipment such as hand tools, analysis equipment, or integrated kits comprised of several items.
> - Consider making the model interactive, including features such as a hinged lid, button(s), knob(s), switch(es), slider(s), etc. Alternatively, teams may identify multiple time-series data sets that could be presented as a static or dynamic 3D visualization in WebGL with widgets that enable starting, stopping, and zooming to manipulate the model.
> - Notional ideas for potential models that could be manipulated via HTML5 widgets or 3D widgets within the WebGL model include:
> - One or more robot hands with two or more fingers with actions to open, close, move (x,y,z), and rotate (pitch, yaw, roll)
> - A teleoperated robotic glove box or greenhouse that includes commands to pick up, move, place, push, pull, etc.
> - A subsystem, e.g., a battery, capacitor, bearings, or turbofan, with a plot of prognostic data from the Prognostics Data Repository
> - Virtual equipment that presents time-series Goddard Institute for Space Studies (GISS) Earth science data sets
> - Interactive 3D models of Lunar Geology Hand Tools as described and depicted in pages 79-85 of the Apollo 16 Press Kit
> - Building upon free open-source models is okay, provided that you comply with all proper requirements, including, as applicable, providing your team's project page and repository ReadMe file a credit to the original creators and an explanation of how your team added value to the model. An example of building upon an existing model could be to add a scientific instrument or tool to a robotic system. An interactive 3D model could include a user interface widget, such as a button that would cause that new part of the system to highlight or change color.
> - For security reasons, Space Apps judges cannot download executable files; therefore, the interactive 3D models ought to be embedded in a deployed web page. The example resources include suggested ideas for finding free web application hosting services.
> 

> Keywords for researching development applications and hosting services are as follows: 
> - Planetary science tools, 3D modeling formats, free open source 3D modeling tools, free JavaScript code libraries, how to embed WebGL in a web page, tutorials on how to add GLTF models to a web page. To learn how to deploy a web page, search for free web hosting services. (Consider where you are deploying your code repository; repository hosting services also offer web page hosting.)
> 
> For data and resources related to this challenge, refer to the Resources tab at the top of the page. More resources may be added before the hackathon begins. NASA does not endorse any non-U.S. Government entity and is not responsible for information contained on non-U.S. Government websites.

在開發你的作品時，你可以（但不是必須）考慮以下問題。
* 初學者可以製作單個工具或裝置，如鎬或錘子。中級團隊可以製作一個包含多種工具或設備的工具包；工具包本身可以是一個背包或一個交互式容器。高級團隊可以創造分析設備的交互式模型，呈現真實或模擬的時間序列資料。
* 該模型可以是歷史上或未來的設備設計，如手持工具、分析設備，或由多個項目組成的綜合工具包。
* 可以考慮使模型具有互動性，包括鉸鍊式蓋子、按鈕、旋鈕、開關、滑塊等功能。或者，團隊可以確定多個時間序列資料集，並且在WebGL中以靜態或動態形象化的方式呈現，並透過小部件執行啟動、停止和縮放等方式操縱模型。
* 可透過HTML5小部件或WebGL模型內的3D小部件操縱的潛在模型概念想法包括：
* 一隻或多隻有兩根或多根手指，且具有打開、關閉、移動（x、y、z）和旋轉（俯仰、偏擺、翻滾）等動作功能的機械手臂。
* 一個可以遠端操作，且具有拿起、移動、放置、推、拉等功能的機械手套箱或溫室。
* 一個子系統，帶有來自預知數據儲存庫的預知數據圖表，如電池、電容器、軸承或渦輪風扇等。
* 呈現時間序列的戈達德空間研究所（GISS）地球科學數據集的虛擬設備。
* 阿波羅16號新聞資料袋第79-85頁中描述和描繪的月球地質手持工具的交互式3D模型。
* 在免費開放模型的基礎上進行構建是可以的，但是作品須符合規範，包括在你的團隊的項目頁面和資源庫ReadMe文件中提供原始出處，並解釋你的團隊如何為該模型增加價值。一個例子是在現有模型的基礎上加以改良的方式，包含在機器人系統中增加一個科學儀器或工具等作品。交互式3D模型可以包括一個用戶界面小部件，如一個按鈕能使系統的新部分顯示或改變顏色的按鈕。
* 出於安全原因，太空應用程式挑戰賽評審不能下載可執行檔案；因此，交互式3D模型應嵌入於網頁中。範例資源已包含尋找免費網絡應用程式託管服務的建議方式。

研究開發應用和託管服務的關鍵詞如下: 
* 行星科學工具、3D建模格式、免費開放3D建模工具、免費JavaScript代碼庫、如何在網頁中嵌入WebGL、關於如何在網頁中添加GLTF模型的相關教學。若要學習如何架設一個網頁，請搜索免費的網路託管服務。 (先考慮你要在哪裡部署你的代碼庫；代碼庫託管服務也提供網頁託管)。

有關與這項挑戰相關的數據與資源，請參考頁面頂端的資源標籤（Resources）。在黑客松競賽開始前，會加入更多資源。美國太空總署並不會替任何非美國政府的機構背書，也不對非美國政府網站上的資訊負責。

# Resources 相關資源
> <https://2021.spaceappschallenge.org/challenges/statements/virtual-planetary-exploration-v20/resources>


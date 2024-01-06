---
title: '題目：GUI FOR MATERIALS SCIENCE 材料科學的圖形使用者介面'
---

:::success
[回 2021 NASA 黑客松挑戰中文翻譯 Challenge](https://g0v.hackmd.io/4DIbh5k4R-SNBq3FdGMIjQ?both)
:::

題目：GUI FOR MATERIALS SCIENCE 材料科學的圖形使用者介面
===
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a9165714bed36e2d5e0365dce61db13d.jpeg)


# Full Details 完整說明
## Summary 概述
> The design of novel alloys via predictive computational modeling is progressing by leaps and bounds, but the numerous open-source tools available for materials science modeling are often difficult to use and interpret. Your challenge is to develop a graphical user interface (GUI) that allows easy and seamless use of these tools.
>
透過預測性電腦建模所設計的新型合金正在突飛猛進，但在材料科學建模中可使用的眾多開放原始碼工具，通常很難使用及解釋。你的挑戰是要開發出一個圖形使用者介面 (GUI)，以輕易順利地使用這些工具。

## Details 詳細描述
### Background 背景說明
> NASA uses alloys to construct many of its mission elements, including space launch system (SLS) components, engines, and even nuclear thermal propulsion (NTP) and international space station (ISS) microgravity materials research. The large-scale structures that comprise space stations and habitats, spacecraft that use NTP, and other items ranging from engine nozzles to Hall ionic thrusters all depend on materials design and development as does advancing the state of the art. The success of each element depends on the characteristics of the alloy selected, the alloy’s performance in the intended environment, its printability and weldability, and the joining method used— e.g., a selective melting process (fusion welding and 3D selective laser melting [SLM] printing and the related direct energy deposition [DED] methods) or a solid-state joining process.
> 
> Materials science and predictive modeling of alloys are challenging topics. However, methods to design novel alloys via predictive computational modeling are progressing by leaps and bounds! Coupling computational alloy design with iterative synthesis and characterization/testing of alloys has reduced the time to produce a novel alloy to a year or two when it used to take over a decade! Many readers will recognize this as the integrated computational materials engineering (ICME) approach.
> 
> These rapid advancements depend on computational calculations regarding the thermodynamic and even the atomistic interactions of alloys and materials. Solutions are iterated to determine the optimal configurations and materials for additive manufacturing (3D printing) and for welding and joining on Earth and for in-space manufacturing of large on-orbit and Lunar structures.
> 
> Over the past decade, computational materials science modeling tools have been developed at national laboratories such as the U.S. National Institute of Standards and Technology (NIST) and Sandia National Laboratories, at NASA and by teams at world-class universities. These applications consist of quantum mechanical and molecular dynamics calculations tools, Monte Carlo and stochastic statistical methods, and thermodynamical calculation tools. Many of these tools are freeware and licensed under the General Public License (GPL) or open-source licensing schemes.
> 
> However, most of these open-source tools rely on complex command line interfaces and scripting languages and are very unique which limits their accessibility to the general community of materials engineers and scientists. To use these tools, one usually has to know several specialized programming languages, install special libraries, use third-party software tools or even specially built materials databases. Then, one has to execute massive parallel job queues—all to run a computationally simple model.
> 
> Use of these open-source tools could be increased if they could be used to run model after model, for material after material in a seamless, effortless way, and be able to switch the calculation method employed from one bundled resource (e.g., quantum) to another (e.g., Molecular Dynamics, Monte Carlo, Thermodynamics, etc.) to another at quite literally the push of a button. Furthermore, it may be helpful if such open source tools could be configured to be able to display and manipulate the various outputs just as effortlessly.
> 
> Here is where GUIs applications may be useful. An application with easy-to-install, bundled wrappers for required libraries and dependencies with a GUI (i.e., drop-down menus and push-button computing) could increase the use of existing open-source materials science modeling tools. The GUI can be for each individual approach and freeware or can incorporate several approaches. The application could also be for workflow between approaches.
>
美國太空總署使用合金來構建其許多任務元素，包括太空發射系統 (SLS) 零件、引擎，甚至核熱推進 (NTP) 和國際太空站 (ISS) 微重力材料研究。設有太空站和棲息地的大型結構、使用核熱推進的太空船以及從引擎噴嘴到霍爾離子推進器的其他項目都依賴於材料設計和開發，如同推進最先進的技術一樣。每個元素的成功取決於所選合金的特性、在預期環境中的性能、其可印刷性和可焊性以及所使用的連接方法——例如，選擇性熔化加工（熔焊和 3D 選擇性雷射熔化 [SLM] 印刷和相關的直接能量沉積 [DED] 方法）或固態連接加工。

合金的材料科學和預測建模是具有挑戰性的課題。然而，通過預測計算建模設計新型合金的方法正在突飛猛進！將計算合金設計與合金的重複融合與特徵/測試相結合，將生產新型合金的時間縮短到一兩年，這在過去可需要耗費十多年！許多讀者會視為這是集成計算材料工程 (ICME) 方法。

這些快速進步取決於關於合金和材料的熱力學甚至原子相互作用的電腦計算。解決方案不斷地重複計算，以決定積層製造（3D列印）、地球上的焊接和連接，以及大型軌道製造和月球結構的空間製造的最佳結構和材料。

在過去十年中，美國國家標準與技術研究院 (NIST) 和桑迪亞國家實驗室等國家實驗室、美國太空總署以及世界一流大學的團隊開發了計算材料科學的建模工具。這些應用程式包括量子力學和分子動力學計算工具、蒙特卡羅和隨機統計方法以及熱力學計算工具。其中許多工具是免費軟體，並根據通用公共許可協議 (GPL) 或開放授權機制獲得許可。

然而，多數的開放工具都依賴於複雜的命令列介面和指令語言，並且非常獨特，這往往使一般材料工程師和科學家卻步。要使用這些工具，通常需要了解幾種專門的程式語言、安裝專門的文庫、使用第三方軟體工具，或甚至使用專門構建的材料數據庫。 然後，必須執行大量並行的工件佇列——這些全部都是為了運行一個簡單的計算模型。

如果這些開放工具可用於運行一個接一個的模型，以連續、輕鬆的方式處理一個接一個的材料，並且能夠從一個捆綁資源（例如，量子）到另一個（例如，分子動力學、蒙特卡洛、熱力學等）甚至另一個，且實際上只需按一下按鈕切換使用的計算方法，那麼它們的使用率可能會增加。此外，如果可以將此類開放工具設定為能夠毫不費力地顯示和操作各種輸出結果，這會有所幫助。

這可能就是圖形使用者介面 (GUI)應用程式有用的地方。易於安裝、綑綁包裝所需的資料庫且依賴於圖形使用者介面（即下拉畫面和按鈕計算）的應用程式可能增加對現有開放材料科學建模工具的使用。圖形使用者介面可以用於每種方法和免費軟體，也可以包含多種方法。該應用程式還可以用於方法間的工作流程。

### Objectives 目標
> Your challenge is to develop an interactive GUI application, or multiple GUI applications, that enable easy, user-friendly utilization of existing, open-source, materials science and engineering modeling software suites. Your tool may seamlessly integrate all the elements required to use these software suites, including install packages with all dependencies, databases, and third-party resources/freeware.
>
你的挑戰是開發一個或多個交互式圖形使用者介面應用程式，以便輕鬆、易於使用地利用現有的開放材料科學和工程建模軟體套件。你的工具可以連續整合、使用這些軟體套件所需的所有元素，包括安裝包中所具有所有的依賴資料庫和第三方資源/免費軟體。

### Potential Considerations 潛在考量
> As you develop your GUI, you may (but are not required to) consider the following:
> 
> •	Your GUI could interface with the following materials science modeling computation packages:
    > - MUST alloys computational kit
    > - ATAT alloys theoretical automated toolbox (Brown University and Massachusetts Institute of Technology)
    > -	OpenCalphad freeware package (NIST), PyCalphad is also freeware.

> •	Your GUI could bundle together several approaches and packages with open-source fundamental atomistic packages, graphing and plotting utilities, and even Machine Learning/Artificial Intelligence (AI) packages. The GUI design and development burden for atomistic packages and even Machine Learning Packages and Plotting Packages is nearly identical to the above example packages.
    > -	Specific examples of atomistic packages: Your GUI could also seamlessly integrate with the above, freeware atomistic density functional theory (DFT) (e.g., atomistic quantum and classical molecular dynamics, etc.) applications such as SIESTA and LAMMPS and with graphing/plotting freeware such as ParaView (Los Alamos freeware) and gnuplot, etc. 
    > 
> •	Potential keywords you may search online: Integrated computational materials engineering (ICME), density functional theory, molecular dynamics, graphical user interface (GUI), application programming interface (API), phase field, micress, machine learning, tensor flow, computational materials discovery, alloys design

>
在開發圖形使用者介面時，你可以（但不是必須）考慮以下事項：
* 你的圖形使用者介面可以與下列材料科學建模計算套件相互作用：
    * MUST合金計算工具
    * ATAT 合金理論自動化工具箱（布朗大學和麻省理工學院）
    * OpenCalphad 免費軟體包 (NIST)，PyCalphad 也是免費軟體。
* 你的圖形使用者介面可以將多種方法和開放基本原子套組、繪圖和繪圖實用程序，甚至機器學習/人工智慧 (AI) 套組綁在一起。 原子封包甚至機器學習套組和繪圖封包的圖形使用者介面設計和開發負擔與上述列舉出的套組幾乎相同。
    * 原子封包的具體範例：你的圖形使用者介面還可以與上述的免費軟體原子密度泛函理論 (DFT)（例如，原子量子和經典分子動力學等）、像SIESTA和LAMMPS這種應用程式、ParaView（洛斯阿拉莫斯免費軟體）這種的免費圖形/繪圖軟體，以及gnuplot等連續地整合。
* 你可以在線上搜尋的潛在關鍵詞：整合計算材料工程 (ICME)、密度泛函理論、分子動力學、圖形使用者介面 (GUI)、應用程式介面 (API)、相位場、micress、機器學習、張量流、計算材料發現，合金設計。


# Resources 相關資源
> <https://2021.spaceappschallenge.org/challenges/statements/gui-for-materials-science/resources>


---
title: '題目：02 COVID-19: CALCULATE THE RISK 新冠肺炎：病毒風險的計算'
---

:::success
[回 2021 NASA 黑客松挑戰中文翻譯 Challenge](https://g0v.hackmd.io/4DIbh5k4R-SNBq3FdGMIjQ?both)
:::

題目：02 COVID-19: CALCULATE THE RISK 新冠肺炎：病毒風險的計算
===
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f77dd69076682f94beefa435b7b3e833.jpeg)

[TOC]

# Full Details 完整說明
## Summary 概述
> COVID-19 continues to be a global problem even though vaccination efforts are underway to control its propagation. Your challenge is to use environmental data and other information (such as epidemiological, social, policy, and economic data) to build a smartphone application that provides individualized, geolocated, COVID-19 risk warnings to guide social awareness, response, and health security.
> 
儘管藉由疫苗的接種來控制病毒的傳播，新冠肺炎仍然是全球性的問題。你的挑戰是藉由用環境的數據或其他的資訊 (像是流行病學、社會、政策和經濟的數據)來建立一個智慧型手機的應用程式，為提供個人化和地理位置的新冠肺炎風險警告，以引導社會的自覺、反應以及健康安全。

## Details 詳細描述
### BACKGROUND 背景資料


新冠肺炎從地區至全球快速地傳播。截至2021年8月，世界衛生組織通報了將近一億九千九百萬的確診個案，以及四百二十四萬的死亡個案。該病毒已經造成了幾兆美元的影響。儘管藉由持續的疫苗接種來控制病毒的傳播，這次的傳染病已經戰勝了兩個半球的年度季節性週期，並且仍然是個全球性的問題。

網路上提供了大量與冠狀病毒相關的開放研究結果。但其中許多研究都還沒下定論，必須收集和分析更多的數據。許多資訊豐富的開放網路門戶和儀表板提供了新冠肺炎致病率和死亡率的即時快照，有些還能顯示可能相關的環境變數。這個挑戰試圖使用多個開放冠狀病毒相關資訊，並將其整合到一個量化的計算框架中，該框架考慮到了物理位置、天氣/氣候條件，和社會行為，來提供個別的警告。

這個挑戰涉及使用開放環境觀察（遙測/原位/建模）來區分可能與新冠肺炎的傳染及傳播有關的環境因素（例如，溫度、相對或絕對濕度、風、壓力、PM2.5的污染、太陽輻射/紫外線等），以及由於政策（例如，封城、警戒等），社交習慣（戴口罩、保持社交距離等），人口統計（人口密度、國內生產毛額GDP、空調與通風空間等），和經濟活動（例如，開放/關閉企業、娛樂、旅遊等）而產生的共點力。

>SARS-CoV2/COVID-19 propagated rapidly from local to global scales. Almost 199 million COVID-19 cases and 4.24 million deaths were reported by the World Health Organization as of August 2021, and the virus has resulted in multi-trillion dollar impacts. The pandemic has prevailed over the annual seasonal cycles of both hemispheres and continues to be a global problem, even though vaccination efforts are underway to control its propagation.

>An abundance of open-source COVID-related research findings is available online. But many of these studies are inconclusive and require more data to be collected and analyzed. Many informative open-source web portals and dashboards provide real-time snapshots of COVID-19 case rates and mortality and some also display potentially associated environmental variables. This challenge is an attempt to consolidate open-source COVID-related information from multiple sources and integrate it in a quantified, computational framework that provides individualized risk warnings, taking into account physical location, weather/climate conditions, as well as social behavior.

>This challenge involves use of open-source environmental observations (remote sensing/in situ/modeled) to distinguish among environmental factors (e.g., Temperature, Relative or Specific Humidity, Winds, Pressure, Pollution PM2.5, Solar Radiation/UV etc.) possibly associated with SARS-CoV-2/COVID-19 infectiousness and propagation, and concurrent forcings due to policy (e.g., lockdowns, slow-downs..), social practice (wearing masks, social distancing…), demographics (population density, GDP, air conditioned vs. ventilated spaces, etc.), and economic activity (e.g., open/closed businesses, recreation/tourism, etc.).

### Objectives 目標

你的挑戰是藉由用環境的數據或其他的資訊 (像是流行病學、社會、政策和經濟的數據)來建立一個智慧型手機的應用程式，為提供個人化和地理位置的新冠肺炎風險警告，以引導社會的自覺、反應以及健康安全。

這個挑戰涉及使用風險預警模型/演算法作為智慧型手機的應用程式，來向用戶告知他們的冠狀病毒風險。例如，該應用程式可以提供用戶地理定位的新冠肺炎風險/易受影響的程度，並提供個性化的決定，像是要戴哪種的口罩，可能需要避免哪些地點（例如，購物、飲食、社交和運動聚會），社交距離的措施和其他的接觸控制措施。

>Your challenge is to use open-source environmental data and other open-source information (such as epidemiological, social, policy and economic data) as available to build and demonstrate a prototype smartphone application that can provide individualized, geolocated, COVID-19 risk warnings to guide social awareness, response, and health security.

>The challenge involves use of risk warning models/algorithms as smart phone applications to advise users of their COVID risk; e.g., the application might provide the user with geolocated COVID-19 risk/susceptibility levels, which could guide individual decisions regarding what to wear (type of mask), which locations to avoid if possible (e.g., shopping, dining, social and sports gatherings), social distancing measures, and other exposure control measures.
### Potential Considerations 潛在考量
在開發原型應用程式時，你可以（但不是必須）參考以下事項：
- 為了使典型的終端用戶應用程式能夠被廣泛接受，無論是研究還是應用程式的產品，版面和圖形應該保持簡單易懂。例如，用戶能夠輕鬆填寫當地所須的輸入資訊，並根據位置、個人社交選擇和該區域新冠肺炎的背景資訊，獲得新冠肺炎的風險因子以及預測。
- 在現有的新冠肺炎計算器的基礎上，增加有助於風險預警計算器的環境因素。如果能夠從公開資源獲取智能手機網路的鄰近資訊(從測試網站上通報的新冠肺炎個案)將會非常有用。
- 你可以在網路上搜尋的潛在關鍵字：19 and me、COVID calculator、case rates、death rates、earth engine、climate data store、monthly climate explorer。

>When developing your prototype application, you may (but are not required to) consider the following:
>- For the typical end-user application to be well received—be it a research or applications product—the templates and graphics should be kept simple and intuitive. I.e., a user should be able to easily fill in the required local input information and obtain a COVID-19 risk factor or prediction depending on location, personal social choices, and regional COVID-19 context.
>- It might be useful to build upon existing COVID-19 calculators and add environmental elements that help refine the risk-warning calculations. Proximity (to reported COVID-19 cases from testing sites) information from smart phone networks could be very useful if such information can be obtained from public sources.
>- Potential keywords you may search online: 19 and me, COVID calculator, case rates, death rates, earth engine, climate data store, monthly climate explorer.

# Resources 相關資源
> [https://2021.spaceappschallenge.org/challenges/statements/artfully-illuminated-asteroids/resources](https://2021.spaceappschallenge.org/challenges/statements/artfully-illuminated-asteroids/resources)


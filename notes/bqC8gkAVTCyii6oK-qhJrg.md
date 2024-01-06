---
title: '題目：04 DRONES AND SATELLITES FOR URBAN DEVELOPMENT 無人機和衛星對於都市的發展'
---

:::success
[回 2021 NASA 黑客松挑戰中文翻譯 Challenge](https://g0v.hackmd.io/4DIbh5k4R-SNBq3FdGMIjQ?both)
:::

題目：04 DRONES AND SATELLITES FOR URBAN DEVELOPMENT 無人機和衛星對於都市的發展
===
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6ffff24bed0b0ba0e78c0abf3e56f876.jpg)

[TOC]

# Full Details 完整說明
## Summary 概述
> Data from Earth-observing satellites, airborne science platforms, unmanned aerial vehicles (UAVs), and in situ platforms can be used to address development challenges around the world. Your challenge is to use this data to enable local stakeholders to develop more sustainable, disaster-risk resilient, and inclusive urban plans.
> 
來自觀測地球的衛星、機載科學平台、無人機（UAVs）和原位平台的數據，可以被用於解決世界各地發展所帶來的挑戰。你的挑戰是利用這些數據，使當地的利益相關者能夠擬定出更永續、災害應變以及有包容性的都市計畫。

## Details 詳細描述
### Background 背景說明
> To make urban spaces more inclusive, resilient, and sustainable, we need to leverage high-quality, timely, and reliable disaggregated data to inform the creation and management of inclusive urban development plans. These plans should include improvements to enable access to basic services (water, electricity, etc.) and public transportation, allow access to open spaces for public use by all, and incorporate slum improvement policies, among other elements.
> 
> Medium- (1 km-500m) to high-resolution (30m -10m) satellite imagery, coupled with methodological and computational advances, can be used to define and map urban areas and settlements in spatiotemporal dimensions, characterize their morphology, extract population estimates through statistical modeling techniques, and help authorities better plan and manage urban growth and spatial distribution. In addition, unmanned aerial vehicles (UAV), commonly known as drones, can capture images at very high spatial and temporal resolutions, and provide supplemental geospatial information that can support urban upgrading projects, when combined with local knowledge and advanced processing.
> 
> The United Nations (UN) developed its 2030 Agenda for Sustainable Development to provide a blueprint for peace and prosperity for people and the planet, now and into the future (https://sdgs.un.org/goals). That agenda includes 17 Sustainable Development Goals (SDGs), and SDG 11 (Sustainable Cities and Communities) directly pertains to this challenge. Relevant SDG 11 Targets include the following:
> 
> - Target 11.1: By 2030, ensure access for all to adequate, safe and affordable housing and basic services and upgrade slums.
> - Target 11.2: By 2030, provide access to safe, affordable, accessible and sustainable transport systems for all, improving road safety, notably by expanding public transport, with special attention to the needs of those in vulnerable situations, women, children, persons with disabilities and older persons.
> - Target 11.3: By 2030, enhance inclusive and sustainable urbanization and capacity for participatory, integrated and sustainable human settlement planning and management in all countries.
> - Target 11.6: By 2030, reduce the adverse per capita environmental impact of cities, including by paying special attention to air quality and municipal and other waste management.
> - Target 11.7: By 2030, provide universal access to safe, inclusive and accessible, green and public spaces, in particular for women and children, older persons and persons with disabilities.


>
為了使都市空間更具包容性、應變性以及永續性，我們需要利用高品質、即時且可靠的分類數據，為創建與管理包容性都市發展計畫的提供資訊。這些計畫應包含改進措施，使人們能夠使用基本服務（水、電力等），大眾運輸工具，開放給大眾所使用的開放空間，並納入將貧民窟改善政策等內容。

中解析度（500公尺至1公里）到高解析度（10公尺至30公尺）衛星影像，加上方法學和計算的進步，可用於定義和繪製都市區域和住宅區的時空維度，描述其型態特徵，通過統計建模技術提取人口估計數，並幫助當局更好的規劃和管理都市的成長以及空間分佈。此外，無人駕駛飛行器（UAV），又稱無人機，可以在非常高的空間和時間解析度來捕捉影像，並結合當地知識和先進的處理技術，以補充地理空間資訊，來輔助都市升級計畫。

聯合國（UN）制定了2030年永續發展的議程，為現在和未來的人類以及地球提供和平和繁榮的藍圖( https://sdgs.un.org/goals )。該議程包括與這項挑戰直接相關的17個永續發展目標 (SDGs) 和永續發展目標SDG 11（永續城市和社區）。以下是永續發展目標SDG 11相關內容：

* 目標11.1：在西元 2030 年前，確保所有的人都可取得適當的、安全的，以及負擔的起的住宅與基本服務，並改善貧民窟。
* 目標11.2：在西元 2030 年前，為所有的人提供安全的、負擔的起、可使用的，以及可永續發展的交通運輸系統，改善道路安全，尤其是擴大公共運輸，特別注意弱勢族群、婦女、兒童、身心障礙者以及老年人的需求。
* 目標11.3：在西元 2030 年前，提高融合的、包容的以及可永續發展的都市化與容積，以讓所有的國家落實參與性、一體性以及可永續發展的人類定居規劃與管理。
* 目標11.6：在西元 2030 年前，減少都市對環境的有害影響，其中包括特別注意空氣品質、都市管理與廢棄物管理。
* 目標11.7：在西元 2030 年前，為所有的人提供安全的、包容的、可使用的綠色公共空間，尤其是婦女、孩童、老年人以及身心障礙者。


### Objectives 目標
>Your challenge is to demonstrate how spaceborne, airborne, and ground-based remote sensing data can be combined with data collected by UAVs to improve the timeliness and quality of urban-related indicators, support sustainable urban development, and enable tangible improvements to the quality of people’s lives in cities and local communities.
>
>More specifically, your challenge is to use multiple data streams – including spaceborne remote sensing and Unmanned Aerial Systems (UAS) sensing data – to inform UN SDG 11 (Sustainable Cities and Communities) and address the relevant SDG 11 Targets for a city (or cities) of interest. Your overarching goal is to enable local stakeholders (urban planners, city authorities) to develop more sustainable, disaster-risk resilient and inclusive urban plans.

你的挑戰是要展示如何將衛星上的、太空的和地面遙測數據與無人機收集的數據結合，以提升都市相關指標的即時性和品質，輔助永續都市發展，並能夠確實改善人們在都市和當地社區的生活品質。

更明確地說，你的挑戰是要利用多重數據流，包括太空遙測和無人機（UAS）感測數據，來為聯合國永續發展目標SDG 11（永續城市和社區）提供資訊，並解決感興趣的城市（或多個城市）的相關永續發展目標SDG 11。你的首要目標是使當地的利益相關者（都市計畫者、城市當局），來制定更多具永續性、災害應變和包容性的都市計畫。

### Potential Considerations 潛在考量
> The following are example outputs that your project could (but is not required to) include:
> - a city-specific tool (or app) for computing an indicator
> - a digital story-telling product (e.g., story map, web portal)
> - a short video tutorial sharing your step-by-step method or providing a demonstration of your city-specific app or tool
>
你的計畫可以（但不是必須）包含以下範例：
* 用於計算指標的特定工具（或應用程式）
* 一個數位說故事產品（例如，故事地圖、網路門戶）
* 一個簡短的教學影片，分享你的方法的每個步驟，或是展示你城市的特定應用程式或工具的一個教學短片。

# Resources 相關資源
> [https://2021.spaceappschallenge.org/challenges/statements/drones-and-satellites-for-urban-development/resources](https://2021.spaceappschallenge.org/challenges/statements/drones-and-satellites-for-urban-development/resources)


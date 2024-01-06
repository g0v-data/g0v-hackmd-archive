---
title: '題目：MAPPING SPACE TRASH IN REAL TIME 即時定位太空垃圾 '
---

:::success
[回 2021 NASA 黑客松挑戰中文翻譯 Challenge](https://g0v.hackmd.io/4DIbh5k4R-SNBq3FdGMIjQ?both)
:::

題目：MAPPING SPACE TRASH IN REAL TIME 即時定位太空垃圾 
===
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e2320ca859597c884809505bfa7f98f1.jpg)

[官網原文](https://2021.spaceappschallenge.org/challenges/statements/mapping-space-trash-in-real-time/details)

# Full Details 完整說明

## Summary 概述

> The increasing amount of debris orbiting Earth could potentially limit our access to space, impacting not only exploration efforts, but routine aspects of our life on Earth. Your challenge is to develop an open-source geospatial application that displays and locates every known debris object orbiting Earth in real time.


圍繞地球運行的垃圾越來越多，將可能限制我們進入太空，這不僅影響探索工作，還會影響我們在地球上的日常生活。你的挑戰是開發一個利用開放原始碼寫成的地理空間應用程式，以即時顯示和定位圍繞地球運行的每個已知碎片物體。

## Details 詳細描述
### Background 背景說明
> Though artificial satellites are not usually regarded as natural resources, the increasingly crowded orbits that they utilize very much are. Orbits around Earth provide us with invaluable vantage points to deploy spacecraft that allow us to study our planet and the rest of the universe. They also allow us to set up global telecommunication networks and satellite navigation systems that are used for a wide assortment of things from managing global airline traffic to requesting a cab. Low Earth orbits are also essential for crewed space exploration missions even when the final mission destination lies further away. Space debris endangers space operations and could potentially limit our access to space if it's not addressed.
> 
> Today there are nearly 22,000 artificial objects in Earth orbit, including 6,444 spacecraft (active and defunct). However, these statistics include only the objects large enough to be tracked. More than 128 million pieces of debris smaller than 1 cm (0.4 in), about 900,000 pieces of debris 1–10 cm, and around 34,000 pieces larger than 10 cm (3.9 in) are estimated to be orbiting Earth.
> 
> Over the years, spent rockets, satellites, and other space trash have accumulated in orbit increasing the likelihood of collision with other debris. Unfortunately, collisions create more debris, creating a runaway chain reaction of collisions and more debris. This phenomenon is known as the Kessler Syndrome after the man who first proposed the issue, Donald Kessler, or collisional cascading.
> 
> This cascade of collisions first came to NASA’s attention in the 1970s when derelict Delta rockets left in orbit began to explode, creating shrapnel clouds. Kessler demonstrated that once the amount of debris in a particular orbit reaches critical mass, collisional cascading begins even if no additional objects are launched into the orbit. Once collisional cascading begins, the risk to satellites and spacecraft increases until the orbit is no longer usable.
> 
> Kessler proposed it would take 30 to 40 years for such a threshold to be reached and today some experts believe we are already at critical mass in low-Earth orbit at about 560 to 620 miles (900 to 1,000 kilometers).

僅管人造衛星並不被視為自然資源，但它們使用的日漸擁擠的軌道卻是。環繞地球的軌道為我們提供寶貴且有利的位置來部署太空船，使我們能夠研究我們的星球以及宇宙的其他地方。它們也讓我們建立全球電信網路以及衛星導航系統，用於從管理全球航線的交通到叫計程車等各種方面的事情。低軌道對於載人太空探索任務也是不可或缺的，即便任務最終目的地在更遠的地方。太空垃圾會危及太空行動，如果不加以解決，可能會限制我們進入太空。

現今，在地球的軌道上，有將近22000個人造物體，其中包括6444個太空船（現役或退役）。然而，這些統計僅包含能夠追蹤的大型物體。目前估計超過一億兩千八百萬塊小於1公分（0.4英吋）的垃圾碎片，大約九十萬塊介於1至10公分的垃圾碎片，且大約有三萬四千個大於10 公分（3.9英吋）的碎片圍繞在地球軌道中。

多年來，廢棄火箭、衛星，和其他太空垃圾持續累積在軌道上，增加了與其他垃圾碰撞的可能性。不幸的是，碰撞會造成更多的垃圾，造成碰撞和更多垃圾的失控連鎖反應。這種現象被稱為凱斯勒症候群，是以最早提出這個問題的唐納德·凱斯勒的名字命名，又稱為碰撞級聯效應。

1970年代，當留在軌道上的廢棄三角洲（Delta）火箭開始爆炸，產生榴霰雲，這一系列的碰撞級聯首次引起了美國太空總署的注意。凱斯勒證明，一旦軌道上的碎片達到臨界質量，即便沒有其他物體進入軌道，碰撞級聯效應也會開始。一旦碰撞級聯效應開始，就會增加衛星和太空船的風險，直到軌道不能再使用。

凱斯勒提出，大概只要花30到40年的時間就會達到臨界點。現今，有些科學家相信，我們在低軌道已經達到臨界點了，大概是560至620英里(900至1000公里)。

### Objectives 目標
> Your mission is to develop an open-source geospatial (i.e., map-based, or virtual globe-based) application that displays and locates every known debris object orbiting Earth, in real time.

你的挑戰是開發一個利用開放原始碼寫成的地理空間應用程式，以即時顯示和定位圍繞地球運行的每個已知碎片物體。

### Potential Considerations 潛在考量
> Your strategy might (but is not required to) include the following steps:
> 1.	Choose an open-source, geospatial virtual globe or mapping library (e.g., NASA WorldWind or OpenLayers).
> 2.	Obtain the orbital parameters for every currently tracked space debris object in Earth orbit (e.g., from Celestrak or Space-Track).
> 3.	From the orbital parameters of an object, obtain its geographical position (latitude, longitude, altitude) at the current time (a library such as SatelliteJS or Python's SGP4 can be used for this).
> 4.	Using its geographical position, locate the object in your geospatial library.
> 5.	Repeat from step 3 for all space debris objects in your chosen catalog.
> 6.	A fraction of a second afterwards, update the time, and repeat, providing a real-time animation of every space debris object in the catalog.
> 

> Your application could also include options for the following:
> 
> - Include debris clouds consisting of smaller objects for which we can only estimate the locations.
> - Incorporate a user interface (UI) timeline feature to allow the user to see the orbital environment at a different point in time.
> - Add satellite tracking capabilities. Predict when a particular object is going to pass over a user-selected location on Earth's surface.
> 

> Potential search keywords:
> 
> - Mapping/virtual globe libraries: openlayers examples, leaflet tutorials.
> - General orbital parameter information to map space debris: two line element sets, AIAA 2006-6753, sgp4 propagator, celestrak space debris tle, space-track documentation.
> - Software libraries to read orbital parameters in two-line element set (TLE) format: satellitejs library, nsat/jspredict library, pypi sgp4.
> - Examples of open-source satellite trackers: stuffinspace, jsattrak, worldwind spacebirds


你的策略可能需要（但不是必須）包含以下步驟：
1. 選擇一個開放、地理空間虛擬地球儀或地圖庫（例如，NASA WorldWind或是OpenLayers）
2. 獲取目前在地球軌道上所追蹤的每個太空垃圾物體的軌道參數。（例如，來自Celestrak或是SpaceTrack）。
3. 從每個物體的軌道參數中，獲取它目前的地理位置（緯度、經度、高度）（可以使用SatelliteJS或是Python的SGP4等庫）。
4. 利用它的地理位置，在你的地理空間庫中定位該物體。
5. 對你選擇的目錄單中所有的太空垃圾物體重複步驟三。
6. 在每一瞬間，更新時間，並且重複以提供在你目錄單中的每一個太空垃圾物體的即時動畫。

你的應用程式還可以包含以下的選項：
* 包含我們只能估計位置的較小型物體所組成的碎片雲。
* 包含一個用戶介面（UI）時間軸的功能，讓用戶能夠看到不同時間點的軌道環境。
* 增加衛星追蹤功能。預測特定物體何時會經過用戶所選擇的地球表面位置。

可能搜尋的關鍵字：
* 繪圖或虛擬地球庫：openlayers examples,、leaflet tutorials。
* 繪製太空垃圾的一般軌道參數資訊：兩行軌道要素形式，AIAA 2006-6753、sgp4傳播器、celestrak space debris tle、 space-track文件。
* 讀取兩行軌道要素形式（TLE）格式的軌道參數的軟體庫：satellitejs library、nsat/jspredict library、pypi sgp4。
* 開放衛星追蹤器的例子：stuffinspace、jsattrak、worldwind spacebirds。

# Resources 相關資源
> <https://2021.spaceappschallenge.org/challenges/statements/mapping-space-trash-in-real-time/resources>


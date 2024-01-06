---
title: '題目：LEVERAGING AI/ML FOR PLASTIC MARINE DEBRIS 利用人工智慧和機器學習來處理海洋塑膠垃圾'
---

:::success
[回 2021 NASA 黑客松挑戰中文翻譯 Challenge](https://g0v.hackmd.io/4DIbh5k4R-SNBq3FdGMIjQ?both)
:::

題目：LEVERAGING AI/ML FOR PLASTIC MARINE DEBRIS 利用人工智慧和機器學習來處理海洋塑膠垃圾
===
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f4dc93c9dc9c4a9ce411d57802f1fb33.jpg)

# Full Details 完整說明

## Summary 概述
> Marine debris is one of the most pervasive threats to the health of coastal areas, oceans, and waterways. Your challenge is to leverage Artificial Intelligence/Machine Learning to monitor, detect, and quantify plastic pollution and increase our understanding about using these techniques for this purpose.

海洋垃圾是沿海地區、海洋和水道健康最普遍的威脅之一。你的挑戰是要利用人工智能和機器學習來監控、探查和量化塑料汙染，並要讓我們理解使用這些技術的目的為何。

## Details 詳細描述
### Background 背景說明
> Marine debris is one of the most pervasive threats to the health of coastal areas, oceans, and waterways. It is an issue of local, regional, national, and international concern. Marine debris can injure or kill marine fauna, damage and degrade habitats, interfere with navigational safety, cause economic loss to fishing and maritime industries, degrade the quality of life in coastal communities, and threaten human health and safety. It is believed that at least eight million tons of plastic end up in our oceans every year and comprise 80% of all marine debris present—from surface waters down to deep-sea sediments.
> 
> The U.S. Marine Debris Research, Prevention, and Reduction Act defines marine debris as "any persistent solid material that is manufactured or processed and directly or indirectly, intentionally or unintentionally, disposed of or abandoned into the Marine environment or connecting systems" (https://www.epa.gov/trash-free-waters/toxicological-threats-plastic) . Marine debris of varying size—from microscopic particles to objects that are several meters long—is ubiquitous in the global ocean. However, it is difficult to track and quantify how much marine debris is currently in the ocean and determine where the highest concentrations are, how it is distributed, and how debris is interacting with the biological elements in the ocean. This information is critical to formulate and enact any type of mitigation strategy to address the marine debris problem.
> 
> While marine debris enters the ocean daily through atmospheric deposition (wind-blown trash), river discharge, and improper disposal of fishing and vessel waste, major debris events caused by disasters also contribute significantly. For example, hurricanes and landslides can carry large amounts of debris—ranging from toppled housing and infrastructure to small pieces of trash—into the ocean. Tracking where this debris is and what happens to it is fundamental to ensure a sustainable and healthy ocean.
> 
> The marine debris problem has been widely recognized; there are several initiatives, nationally and internationally, dedicated to devising strategies to address the debris issue.



海洋垃圾是沿海地區、海洋和水道健康最普遍的威脅之一。它是一個引起地方、地區、國家和國際關注的議題。海洋垃圾會傷害或殺害海洋生物、破壞並損害牠們的棲息地、干擾航行的安全，使漁業和航運業造成經濟的損失、降低沿海地區的生活品質，並威脅人類的健康以及安全。據了解，每年至少有八百萬頓的塑料最後會進入大海。從表層海水至深層沈積物中，那些塑料至少就佔了所有海洋垃圾的80%。

美國「研究、預防與減少海洋廢棄物法」將海洋垃圾定義為：「直接或間接，有意或無意的丟棄任何永久性固體材料於海洋環境或相關的環境中。」(https://www.epa.gov/trash-free-waters/toxicological-threats-plastic) 海洋垃圾有各式各樣的大小，從微粒到幾公尺長的物體，在全球海洋中無所不在。然而，我們很難去追蹤並量化目前海洋中的垃圾，也很難確認哪裡有最多垃圾、它們的分佈方式，以及海洋垃圾與海洋生物的交互作用。這個資訊對於制定並實施任何形式的緩和措施以處理海洋垃圾的問題至關重要。

雖然海洋垃圾每天都會藉由大氣循環（風吹垃圾）、河流排放以及漁業和船舶廢棄物不當的丟棄進入海洋，但災害造成的重大垃圾也有很大的影響。例如，颶風和土石流能夾帶大量的垃圾，從倒塌的房屋和基礎設施到小型垃圾，最後進入大海。追蹤垃圾的位置以及發生了什麼，對於確保海洋的永續性以及安全性是非常重要的。

海洋垃圾的問題已獲得廣泛關注，在國內外有許多提倡者正致力於設計處理垃圾問題的策略。

### Objectives 目標
> Your challenge is to leverage geospatial technology and apply Artificial Intelligence/Machine Learning (AI/ML) capabilities to monitor, detect, and quantify plastic marine debris. Specifically, are there potential advantages as well as the limitations of utilizing AI/ML algorithms to quickly and inexpensively classify plastic pollution and report/visualize the findings in a publicly accessible way?
> 
> Currently, marine debris observation systems are in their infancy. Due to the broad diversity of sizes, types, shapes, buoyancy, and chemical composition of the debris, remote sensing is the only technology capable of providing the uniform observation necessary to address this challenge. Your solution should input remote sensing data into a database that can be built into a dashboard to enable access to this information.
> 
> To address this challenge, you will use existing remote sensing data on plastics and apply AI/ML capabilities to:
> 
> 1)	Create a visualization database based on AI/ML algorithms that will aid in classifying and detecting these plastics using remote sensing data. Look to sites like The Global Forest Watch, funded in part by USAID, for examples.
> 2)	Understand the potential advantages and limitations of utilizing AI/ML algorithms to classify plastic pollution.
> 
> Your solution should allow data on plastic waste to be more accessible and valuable to citizen scientists, remote-sensing experts, as well as policy makers and regulators. It should enable scientists to better detect plastics utilizing remote sensing data and policy makers to use this information to effectuate change.

你的挑戰是要利用人工智能和機器學習來監控、探查和量化塑料汙染。具體來說，利用人工智能和機器學習的演算法，快速、便宜地對塑料污染進行分類，並用大眾可得的方式報告或可視化結果，是否存在潛在優勢和限制？

目前，海洋垃圾觀測系統還處於剛開發階段。由於碎片的大小、種類、形狀、浮力及化學成份的廣泛多樣性。遙測是唯一能夠提供應對這項挑戰所需的統一觀測技術。你的解決方案應該要將遙測的數據輸入資料庫中，該資料庫可以內置於儀表板中，以便能夠使用這些資訊。

為了應對這個挑戰，你將使用現有的塑料遙測數據，並將人工智能及機器學習應用於：

1. 創建一個基於人工智能和機器學習演算法的可視化資料庫，以幫助使用遙測數據分類及檢測這些塑料。可以參考美國國際開發總署中部分資助的全球森林觀察等網站的例子。
2. 了解使用人工智能和機器學習演算法來分類塑料污染的潛在優勢及限制。

你的解決方案應該要讓民間科學家、遙測專家、政策制定者和監督者們，更容易獲得這些塑料廢棄物的數據，使其更有價值。它應該使科學家能夠更好的利用遙測數據檢測塑料，並讓政策制定者能夠利用這些資訊來實施改革。

### Potential Considerations 潛在考量
> When developing your solution, you may (but are not required to) consider the following:
> 
> -	Please consider utilizing citizen science data from apps. Search the app store for “Debris Tracker.”
> -	When classifying the data, please include a timestamp, location, depth, and note whether it is a single item of debris, patch, or filament.
> -	Potential keywords you may search: global forest watch, ocean scan, debris tracker

在研發你的解決方案時，你可以（但不是必須）參考以下事項：
* 請參考使用應用程式中的民間科學數據。在應用程式商店搜尋“Debris Tracker （垃圾追蹤）”
* 對數據進行分類時，請包括時間戳記、位置、深度，並注意是否為單一碎片、片狀物或是絲狀體。
* 你可以搜尋的潛在關鍵字：全球森林觀察、海洋掃描、垃圾追蹤。

# Resources 相關資源
> <https://2021.spaceappschallenge.org/challenges/statements/leveraging-aiml-for-plastic-marine-debris/resources>


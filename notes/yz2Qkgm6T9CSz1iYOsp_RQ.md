---
tags: digital_development
---

# gov諮詢：如何以公私協力方式，建立與政府作業及便民服務相關之共用資訊服務開發環境以及類似GitHub的程式庫。

## 緣起：
郭耀煌政委日前負責數位發展部籌備工作，日期曾聯絡揪松團成員，希望邀請 g0v 成員開會討論並提出建議。基於 g0v 社群的特性，經與政委辦公室溝通，希望由郭政委辦公室先提供初版方案內容，由 g0v 社群熟悉的共筆方式進行開放討論，後續也許再規劃線上諮詢討論。

### g0v 坑主（待定）：
* 目前暫由揪松團 Isabel 協調聯繫，並協助貼共筆。後續開放討論如何繼續協作，並歡迎跳坑。 
* 以下提出回應或建議請標示姓名。
* 討論頻道：~~#digital_development~~ -> #moda


### 提案人：
郭耀煌政務委員辦公室

### 提案內容：

### 如何以公私協力方式，建立與政府作業及便民服務相關之共用資訊服務開發環境以及類似GitHub的程式庫。

### 背景/案由
1.	軟體開源化（Open Source）已為全球趨勢。Fortune 500企業中，99%已採用開源軟體或為開源專案重要貢獻者。
2.	美國政府數位服務推動小組（18F）以精益創業（Lean Startup）模式開發政府服務，並將每一個專案都開源，以利各州政府的使用。
3.	2018美中貿易戰，美國加強對中國輸出管制，軟體使用者條款受制出口管制條款（EAR）。GitHub亦配合EAR宣告出口禁令條款，開源軟體目前是許多公司軟體產品的基石，需考量軟體自主能力。
4.	GitHub為全球最大開源社群。但因美中貿易戰影響，中國工程師擔心以後是否不能使用GitHub。對此，GitHub CEO曾表示，將在北京成立子公司，並於中國設置GitHub伺服器。考量資安與戰略性，我國建立自主的GitHub程式庫似有其必要。
5.	軟體工程發生變革，從 waterfall 改為 agile 模式，雖更貼近資訊服務改版頻率加速的需求，但也增加了管理的難度，需有效的 DevOps環境及工具支援。

### 現況彙整
1.	國內雖有不少開源組織在運作，但產業真正投入開源的比例並不高，政府部門使用開源產品的比重也不高，開源推動仍有努力空間。
2.	國內軟體業者規模普遍都不大，難以獨力研發開發環境，多以使用開源軟體為主，自己開源或是成為貢獻者的業者並不多。但開源對新創很有幫助，可以快速地兜出產品。
3.	開源的授權協定甚多，且有不同的規範，國內業者在使用開源開發產品時，很容易因為不熟悉授權協定而被告，進而付出龐大的代價。
4.	軟體開源多會與DevOps一起討論，以加快軟體開發與交付速度、滿足軟體更版週期縮短、更動幅度變小、開發與維運站在同一陣線等特性。
5.	目前常見的DevOps開源工具有：需求與議題的溝通工具（Redmine等）、程式版本的控管工具（GitHub、GitLab等）、建立系統運行環境工具（Kubernetes等）、功能檢測與資安掃描工具（SonarQube等）、正式環境部署工具（Jenkins等）。但每套開源工具的安裝門檻不一，若能整合成完整的開發環境，將有助於開源工程師使用。
6.	資策會已於2020年完成DevOps整合工具開發環境，以開源解決方案為基礎，提供多種不同的功能與特色，並支援多項開源/商用軟體提供最大的使用彈性，可開放供產學研使用。
    - https://www.iiidevops.org/


### 初步構想與需求
1.	由政府需求帶頭，以公私協力方式，鼓勵各界參與建立共用資訊服務開發環境及類GitHub程式庫，並允許廠商使用開源軟體為政府開發資訊系統，搭配沙盒機制及創新採購制度，帶動國內開源風氣。
2.	人才：帶動教育體系投入開源人才培育及政府及產業人才參與，以擴大國內軟體人才規模，厚植開源實力。同時，透過鏈結國內社群與國際知名的開源社群，培養國內軟體人才之國際觀及貢獻度。
3.	技術：普及開源文化與思維，推廣agile開發模式，整合並廣泛採用自動化工具，以達到事半功倍效果。
4.	法制：
* 	深入研析掌握各類開源授權協定，合規且有效運用開源。
* 	發展符合本地使用特性的開源授權協定，並規劃可連結本計畫開源成果之公共治理沙盒及創新採購法制。
5.	永續經營：
* 	參考國外開源基金會作法，由法人及民間合作成立營運組織，政府提供補助或資源，吸引國內外團體及人才參與。
* 	從推薦開源軟體與工具出發，將各種開源軟體與工具經過基本的檢測與資安驗證後上架，鼓勵公私部門使用。
* 	由政府部門提出新建資訊服務需求，營運組織帶動各方開源團隊投入開發，並搭配政府採購及沙盒機制加速導入應用。
* 	建立多邊國際合作鏈結關係，也提高對國際開源之貢獻。
* 	營運組織透過各類活動及教育訓練，強化各界對開源的了解及重視，並建立諮詢輔導



### 20210714 線上交流會議，民間成員的發言內容綜合整理

關於「政府內部程式碼平台」
- 可理解「政府內部程式碼平台」，不一定等同於開源平台。
- 民間社群較推薦政府採用 gitlab 的開源方案，來建立政府內部的程式碼平台。
- 民間企業也會採用 gitlab 方案來自架內部程式碼平台。
- 資訊採購結案情境之一，廠商繳交光碟方式提供程式碼給機關，這樣的方式期待能改由「政府內部程式碼平台」上傳與確認等方式取代繳交光碟

如何促進「機關」的資訊採購行為中，將程式碼上傳至「政府內部的程式碼平台」，並且釋出給「其他政府部門」使用？
- 提供「指引文件」讓機關同仁參考
    - 好的案例：
        - 例如各地方政府的資料開放平臺，有些縣市至今尚未建立平台，若能透過採用其他縣市方案，則可以推進全國整體開放資料業務
    - 「指引文件」從「釋出端」角色，來進行考量與撰寫
    - 「指引文件」從「採用端」角色，來進行考量與撰寫
- 針對「採購範本」在內容中提供此類選項
    - 以範本鼓勵採購方針調整的近期案例，例如採購範本中加入了 OpenAPI 的選項，期待促進更多機關網站能一併提供開放資料服務。
- 關於這部分地細節，singing 有提到，美國日前公布新的行政命令，有關於 Software Bill of Materials (SBOM) ，要求資訊廠商說明開發成果中，使用到哪些其他程式，以便於對此專案的「資安風險評估」與「若要開源釋出，要採用哪一種開源授權方案」，方便機關同仁了解。[請參考此議題的相關資料彙整頁面](https://g0v.hackmd.io/cR-5FrZUR6WElXTQkbN-IA)。

如何促進「機關」的資訊採購行為中，將程式碼上傳至「政府內部的程式碼平台」，將程式碼釋出給「開源社群」協作？
- 提供「指引文件」讓機關同仁參考
    - 內容建議包含「較佳實踐案例」：
        - chewei> 這部分可以諮詢「已運用 github 推動機關業務的單位」，於初期共同參加相關研商，例如中研院臺灣生物多樣性資訊機構、PDIS、國家發展委員會-支援ODF文件格式軟體工具、立法院資訊處、臺北市立濱江國小..等，[盤點名單與 FB 討論串](https://g0v.hackmd.io/bt4AsE2mQy-gFGaU-PvQqA?view)
    - 若政府機關評估後覺得程式碼成果，適合作為開源程式碼釋出，社群成員會建議，基於從開源協作社群能量與公共曝光效益來說，同步將這類屬性為開源程式碼的成果，一方面上傳在政府內部的程式碼平台，另一方面也應推到 github 上面，讓全球社群與開發者可以看到成果，進行協作。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_74dd5fc6a0081b0594433dfd919a7986.png)




### 20210818 線上交流會議，資策會 DevOps CI/CD 整合工具平台介紹及交流

會前資訊
- 會議名稱：資策會 DevOps CI/CD 整合工具平台介紹及交流
- 線上會議時間：8/18 週三傍晚 6:00-7:00
- 說明：資策會正開發一套 DevOps CI/CD 整合工具平台, 平台介紹如：https://www.iiidevops.org/iii_devops/
- 擬邀平台開發團隊與 g0v 社群夥伴就此平台進行介紹及交流
- 會議網址：尚未確認，預計在 #digital_development 頻道釋出會議網址

會議簡記
- 講者提供：20210814 III DevOps 操作展示影片
    - https://youtu.be/_WVTJl0GLgc



-----
## 其他各類補充資料區 
- 社群共筆文件 [政府 IT 委外制度，引入開源碼發展模式可能性研究既建議草稿](https://g0v.hackmd.io/2rwO1fHBStS7pMbdeBKlGA?view)
- 社群共筆文件 [政府開源採購](https://g0v.hackmd.io/k4A2FZRrRPq3uIUDDTUzAQ)
- [Government best practices/Github](https://government.github.io/best-practices/)
---
tags: IoT
---

# 論文研討第二輪

:::warning
目錄
[TOC]
:::

## 1. Blockchain for IoT Security and Privacy: The Case
### 智慧家庭，網路安全，區塊鏈
- Introduction: 強調物聯網（IoT）在現代生活中的普及以及隨之而來的安全和隱私挑戰。它這邊講的是說傳統安全解決方案在面對大量分散的IoT設備時遇到的限制，所以她的解方是透過區塊鏈技術作為一種潛在的解決方案來增強IoT設備的安全性和隱私性。
- Home Components
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5f4f388dfadc88a97a3d4e016ed5c428.png)

這邊在講區塊鏈有哪些組件
1. Transactions
就是講說Local跟local間的聯絡就叫做交易紀錄這樣。後面就是解釋性定義。
2. Home Miners
這是一種設備，這在智能家居系統中起著中心處理角色，負責處理进出智能家居的交易。礦工設備可以與家庭的互聯網閘道器整合，或作為一個獨立的設備存在，例如放置在設備和家庭閘道器之間。除了執行傳統的安全任務（如認證、授權和審計交易）外，礦工還有其他附加功能，包括生成創世交易、分發和更新密鑰、改變交易結構，以及形成和管理集群。礦工將所有交易收集到一個區塊中，並將完整的區塊添加到區塊鏈上，同時管理本地存储以提供額外的容量。簡單來說就是礦工這個設備主要是用來管理居家內的系統地，可以把一個家庭想成一個block，然後這個就是用來處理這個block。
3. Local BC(私有區塊鏈)
這東西是用來追蹤交易並實施用戶政策，確保進出交易的安全性和合規性。它利用創世交易串聯設備交易於不可變賬本中。區塊包含區塊頭和政策頭，前者確保BC連貫性，後者用於設備授權和實施控制政策。交易的五個參數詳細記錄，包括設備ID和交易類型。本地礦工負責維護此BC，保障智能家庭網絡的安全和隱私。
* 創世交易 這個是指說你第一筆交易紀錄會被稱為創世交易，這樣能確保你後面的交易都是按照時間順序被放在後面的。
4. Local Storage
不重要，本地記憶體，遵守FIFO。

- THE BC-BASED SMART HOME
1. 初始化過程：這段話畫是在描述如何將設備和政策頭部加入本地區塊鏈，包括利用Diffie-Hellman協議生成創世交易和分享密鑰，以及企業主根據提議的政策結構創建和更新Policy。具體作法是這樣的，你的miner跟你的device會都拿到一個key，會被存放在創世紀錄裡面。智能家居業主會根據建議的政策結構創建並實施自己的政策。業主將這些政策作為政策頭部加入到區塊鏈的第一個區塊中。當需要更新政策時，業主應該更新區塊鏈中最新區塊的政策頭部，以確保政策保持最新。

2. 交易處理：涵蓋設備間的直接通信、礦工如何分配共享密鑰以實現設備間安全交互、本地與雲存儲數據的管理方法，以及礦工如何控制許可權和無效密鑰來保障數據安全。
他這邊有兩種方式來進行這件事情:
    -(設備to設備) 智能設備可以直接彼此通信，或與智能家居外部的實體通信。家中的每個*設備*可能會請求來自另一台內部*設備*的數據，以提供某些服務，例如，燈泡從運動傳感器請求數據，當有人進入家時自動開燈。為了實現用戶對智能家居交易的控制，應由礦工分配共享密鑰給需要直接相互通信的設備。為了分配密鑰，礦工檢查策略頭部或向所有者請求權限，然後在設備之間分發共享密鑰。接收到密鑰後，只要密鑰有效，設備就可以直接通信。為了拒絕授權許可，礦工通過向設備發送控制消息將分發的密鑰標記為無效。這種方法的好處是雙重的：一方面，礦工（因此所有者）有一個共享數據的設備列表；另一方面，設備之間的通信通過共享密鑰得到安全保障。
    - (設備to礦工)設備在本地存儲上存儲數據，這指的是為了在本地存儲數據，每個設備需要通過共享密鑰進行認證。為了授予密鑰，*設備*需要向*礦工*發送請求，如果它有存儲權限，礦工生成一個共享密鑰並將密鑰發送給設備和存儲。接收到密鑰後，本地存儲生成一個包含共享密鑰的起始點。擁有共享密鑰後，設備可以直接在本地存儲中存儲數據。
    
其他可能的交易包括訪問和監控交易。這些交易主要由家庭所有者生成，以便在外出時監控家中，接收到來自覆蓋網絡中節點的訪問交易後，礦工檢查所請求的數據是存儲在本地存儲還是雲存儲上。如果數據存儲在本地，礦工從本地存儲請求數據並將其發送給請求者。另一方面，如果數據存儲在雲中，礦工要麼從雲存儲請求數據並將其發送給請求者，要麼將最後一個塊號和hash值發送給請求者。後一種情況允許請求者閱讀設備在雲存儲中存儲的全部數據，通常適用於*數據是針對唯一設備的情況*。否則，如果數據涉及多個設備，用戶的隱私可能會因連接攻擊而受到威脅。
當礦工收到監控交易時，他們會將請求的設備當前數據發送給請求者。如果請求者被允許在一段時間內接收數據，礦工會定期發送數據，直到請求者向礦工發送關閉請求並終止交易。監控交易使家庭所有者能夠觀看攝像頭或其他定期發送數據的設備。為了避免過載或可能的攻擊，所有者通常應該為定期數據定義一個以分鐘為單位的閾值。如果礦工發送數據給請求者的時間達到閾值，則連接將被礦工終止。
3. 共享覆蓋網絡：解釋當個體擁有多個智能家庭時，如何透過共享礦工和存儲來減少管理成本和複雜性，包括設立VPN確保不同家庭間的安全通信和數據路由。

當一個個人擁有多個住所時，他需要為每個住所設立獨立的礦工和存儲設施。為了減少在這種情況下的成本和管理負擔，我們定義了一個共享覆蓋網絡。共享覆蓋網絡由至少兩個智能家居組成，由一個共享礦工集中管理，被視為單個家庭。共享覆蓋網絡類似於智能家居，但是共享區塊鏈的結構與智能家居不同。在共享區塊鏈中，每個家庭都有一個起源交易，所有設備的起源交易都由共享覆蓋網絡的礦工連接到各自家庭的起源交易上。在共享覆蓋網絡中的另一個不同之處是家庭與礦工之間的通信。與礦工位於同一家庭的設備不會有任何改變，而對於其他家庭的設備，將建立一個虛擬私人網絡（VPN）連接，連接互聯網閘道器與共享覆蓋網絡的礦工，以將數據封包路由到共享礦工。

- 安全性分析:
機密性、完整性和可用性，這三個是所謂的CIA。積密性確保只有授權用戶能夠讀取消息。完整性確保發送的消息在到達目的地時沒有任何更改，可用性意味著每個服務或數據在用戶需要時都可用。阿前兩個就是上面再談的，所以這部份作者主要是針對可用性來談。這是通過將接受的交易限制為每個設備建立了共享密鑰的實體來實現的。來自覆蓋網絡的交易在轉發到設備之前需要被礦工授權。此外，可以認為我們基於區塊鏈的框架只會引入與現有智能家居網關產品相比的事務處理延遲的輕微增加。還有一個額外的初始化延遲，用於生成和分發共享密鑰。總之，額外的延遲不是很顯著，不會影響智能家居設備的可用性。 也就是說系統透過故意性的SLIGHTLY DELAY能達到想要的結果。

然後下面是這個系統主要防範的兩種攻擊。
DDOS攻擊：我們的設計對此攻擊有層次的防禦。第一級防禦可以歸因於一個事實，即攻擊者不可能直接在智能家居設備上安裝惡意軟件，因為這些設備無法直接訪問。*所有交易都必須經過礦工的檢查*。讓我們暫時假設攻擊者仍然設法感染了設備。第二級防禦來自於一個事實，即所有出站流量都必須經過礦工的授權，通過檢查策略頭部。由於構成DDoS攻擊流量的請求不會被授權，因此它們將被阻止離開家庭。  所以DDoS攻擊不成立。
鏈接攻擊：為了防止這種攻擊，每個設備的數據都是通過唯一密鑰共享和存儲的。礦工為每個設備在雲存儲中創建唯一的數據帳本。從覆蓋網絡的角度來看，礦工應該為每個交易使用唯一的密鑰。就不會被攻擊。

- 性能評估
結論，開銷非常低，包括性能，能源，時間，價格各方面都是有優化的。

-----------------------------------------
## A Reciprocal and Extensible Architecture for Multiple-Target Tracking in a Smart Home
### 智慧家庭，多感測器，CAMERA，壓力墊
實驗中使用了載荷感測地板作為無縫感測器，以及RFID作為有縫感測器，展示了所提架構的有效性。目的是為了在智能家居環境中同時追踪多個目標，提高位置估計的準確度並彌補每種感測器或追踪算法的限制。實驗結果顯示，透過這種方法能夠靈活地添加或移除追踪感測器/模型，以適應真實人類需求，並提高了追踪多目標的可靠性。

這篇文章所使用的策略是一個混和策略，其混和了有縫策略跟無縫設備以促進它們的協作互動，
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d45b07caab4cf0f534db107097bc9f64.png)
這個是表格一。
作者認為有縫設備會要求受試者帶著一個令牌，這是不切實際的。
然而無縫設備則是常常會在多居民環境中，居民的ID可能很容易混淆。
通過相互合作，這項工作可以在不忽視以人為中心的關注點以及大多數基於令牌的傳感器固有的功耗問題的情況下跟踪居民。

這種分類可以作為用戶根據他們對分辨率、成本、隱私、準確性等方面的關注，選擇當前可用傳感器的靈活組合以獲得令人滿意的多目標跟踪結果的指導。通過有效利用普透計算，使人們而不是環境在日常和工作實踐中變得更智慧和主動。此外，該架構可以作為一個平台來改進當前可用的跟踪方法，這也是我們選擇通過改進我們以前的單傳感器方法，也就是即分別使用RF識別RFID和感應地板來驗證我們的架構的原因，以顯示混合的無縫和有縫設計確實可以增強我們以前的工作。

- PROPOSED APPROACH:
他們在這邊提出了一個基於SOA概念的通用多代理系統架構，用於智能家居。除了繼承先前工作的優勢外，通過引入互惠合作和以人為中心的設計概念，進一步增強了先前的架構，以便更好地開發具有定位感知功能的應用程序。
在所提出的架構中，有一個整合平台，用於處理智能家居系統中各種組件之間的消息交換。每個組件都有其對應的代理，這是基於先前工作的概念設計的，但在這裡專門用於定位。代理可以以事件驅動的發布者/訂閱者方式分發消息，以便系統中的代理可以高效且方便地相互通信。
如圖1所示，利用整合平台在架構中的優勢是在各種連接的組件之間交換和共享消息的角色。對我們先前架構的一項增強是，整合平台內部的共享消息隊列處於一個分層/分層的邏輯結構中，以便所提議的架構中的每個代理可以在某些適當的級別（包括原始數據、特徵、上下文、命令或其他更高級的信息）上共享信息以獲益。因此，整個多目標跟蹤任務可以以分治方式運行。
對我們先前的架構的另一項增強是連接組件之間的合作互動。對於設備之間的互惠合作，每個設備代理從其關聯的跟蹤設備中提取重要特徵並將其發布到整合平台；同時，該設備代理訂閱來自平台的感興趣的上下文信息，以便控制其關聯的設備或與連接到平台的其他設備合作。為了應對跟蹤居民的動態性質，新增加的設備代理只需要關注通過平台交換的消息，並遵循統一的消息交換格式（或協議），而不是通過與其他代理的直接通信，以促進可擴展性。這種鬆散耦合的架構使得跟蹤設備的加入和分離變得更加容易。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_79151ea6e3589666dd29f21892b76fbb.png)
這張圖主要的意思就是，在進去Intergration 的platform裡面之前他們的分層處理能讓他們可以保有是否使用那些設備的部分彈性。
其他內容:
* 設備分類和整合：該架構整合了不同類型的底層設備，包括無縫傳感器（seamless sensors）和有縫傳感器（seamful sensors）。無縫傳感器主要用於連續監測居民的存在，而有縫傳感器則在無縫傳感器無法區分不同目標時或信心值低於某個閾值時才啟用，以節省能源。此外，還引入了“活動傳感器”和“互動設備/界面”兩個類別的底層設備。活動傳感器用於更好地估計居民的活動，而互動設備/界面則用於提供準確的校正信息。虛擬傳感器/執行器用於簡化架構評估，以通過模擬驗證架構的韌性和可擴展性。

* 特徵處理和上下文推斷：底層設備的代理利用這些設備生成盡可能多的可區分特徵，以提高位置估計的性能。擁有選定的信息特徵後，可以使用概率推理和數據關聯等方法來估計每個目標的位置，並處理多個傳感器帶來的意外模糊性。推理代理可以主動檢測與位置相關的上下文數據的質量並根據需要調整其貢獻水平，以應對設備故障等挑戰。

* 上下文表示和應用建立：推斷的上下文數據存儲在數據庫中，供後續開發位置感知應用程序使用。智能家居系統可以以創新的方式表示實時或歷史上下文數據，並根據客戶端設備類型（例如手持設備）提供定制信息。此外，該架構支持多模型合作，允許多個模型訂閱感興趣的上下文信息並執行不同的算法，以改進最終估計值。

多目標的tracking:
* 無縫傳感器：這些傳感器持續運行，是主要的跟蹤設備。它們檢測居民的存在並估算其位置。對其估算的信心取決於居民之間的距離。

* 有縫傳感器：這些傳感器僅在無縫傳感器的數據存在潛在歧義時才會被激活。它們的目的是提供額外信息以提高準確性。

* 信心因子：系統根據無縫傳感器的數據計算信心因子。這個信心因子反映了任何兩個目標（居民）之間的接近程度。兩個目標相距越遠，無縫傳感器的估算就越有信心。

* 行動區塊：系統使用“行動區塊”來建模居民運動的有效範圍。這些行動區塊被表示為2-D高斯分佈。它們有助於評估居民之間的接近程度。

* 行動區塊的重疊：當行動區塊共享常見區域時，它們被視為重疊。行動區塊之間的重疊程度影響信心因子。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_58261d37f42475a35a662c0d7800cdd5.png)

* 效用函數：系統定義了效用函數，以控制一個傳感器的數據對另一個的影響程度。這些函數有助於確定有縫傳感器應何時以及如何協助無縫傳感器。

實驗本身:
ActiveMQ在這個實驗中被主要用到，這是一個java的（JMS）標準的中間件工具包，它提供了分佈式消息交換的事件驅動的發布者/訂閱者機制。這個工具包非常適合我們實現提出的架構。我們已經使用Java或C#實現了所有代理，然後使用GeNIe和SMILE ，一個圖形模型工具包，來訓練位置推斷引擎背後的貝葉斯網絡（作為推斷代理）。https://zh.wikipedia.org/zh-tw/%E8%B2%9D%E6%B0%8F%E7%B6%B2%E8%B7%AF 
貝葉斯網路的主要組成部分包括：
節點（Nodes）：代表不同的變數或事件，這些變數可以是離散的或連續的，它們之間的依賴關係由DAG中的連接表示。
弧（Arcs）：表示變數之間的依賴關係。如果從節點A指向節點B的弧存在，則意味著節點B的條件概率分佈依賴於節點A。
條件概率分佈（Conditional Probability Distribution，CPD）：每個節點都有與之關聯的條件概率分佈，描述了該節點在不同條件下的可能取值。
貝葉斯網路的主要應用包括：
機器學習：用於分類、回歸和概率預測問題。貝葉斯網路可以建模複雜的依賴結構，並用於預測未知變數的概率分佈。
決策支持：用於決策分析和風險管理。貝葉斯網路可以幫助做出基於不確定性信息的合理決策。
自然語言處理：用於語言模型和語義分析。貝葉斯網路可以捕捉詞語之間的語境依賴性。
貝葉斯網路的一個重要特點是它可以處理*不確定性信息*，並通過結合先驗知識和實際證據來更新概率分佈。這使得貝葉斯網路在許多實際應用中都具有強大的建模和推斷能力。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_13ff3419755de31252aed7b9ab237f89.png)
這圖片是講說他們怎麼布置設備的。
A. 情境模擬以展示相互合作
儘管我們更加關注無縫和有縫設備之間的相互合作，但合作並不限於這兩種類型的傳感器。因此，我們模擬了在CoreLab中部署的不同傳感器/執行器之間的三種類型的合作情境，下表總結了這三種類型的相互合作如何實現。這些情境展示了各種設備的協同作用如何通過所提出的架構提供更滿意的用戶體驗和穩健的估算。然而，為了繼續進行本研究的主題，我們在下一節的跟蹤情境中僅評估了更有趣的相互合作類型，即“無縫和有縫設備”進行多目標跟蹤。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3b4f7e2880e8a6f91df85cc0ce11f34a.png)
無線電流流感測器：用於偵測與家電相關的活動，並在智能家居中用戶存在時提高功率效率。模擬合作中，它與其他感測器相結合，延長電池壽命。

無線壓力地墊：提供用戶的位置信息，以正確地關聯數據。在合作模擬中，與活動相關的感測器互相協作，以提高識別精準度。

攝像頭：在需要照明時提供用戶坐標或識別信息。夜間，它們可用於檢測入侵者並啟動燈光。

無線接近感測器：用於確定位置，以節省能源。它們可以在特定條件下激活或關閉其他裝置。

感應地板：在可疑活動時喚醒攝像頭，用於存儲數據以節省能源。它們可以在不可靠的識別情況下進行補償。

攝像頭與感應地板：在燈光條件需要調整時提供互助合作，攝像頭可以在不需要全時監控時進入休眠模式，以節省資源。

B. 跟蹤情境設計
基於先前討論的信心評估，設計了三種跟蹤情境，旨在故意混淆無縫傳感器（感測地板），以便有縫傳感器（RFID系統）將被激活以幫助校正無縫傳感器的數據關聯結果，即，在這些情境中，居民的運動模式不夠規律，以至無法從無縫傳感器中正確推斷出他們的位置。

以下是這三種情境的簡要描述：

突然停止情境（Sudden Stop Scenario）：一名居民突然停下來，另一名居民繼續前進。

同時轉向情境（Coincident Turnaround Scenario）：兩名居民同時轉向。

同時轉彎情境（Simultaneous Turn Scenario）：兩名居民同時轉彎。

這些情境的目的是故意引起無縫傳感器的混淆，以證明有縫傳感器可以提供校正信息，從而改善無縫傳感器的估算結果。圖中展示了每種情境的原始路徑，無縫傳感器的估算結果以及有縫傳感器提供的校正結果。通過這種合作，可以實現無縫和有縫設備之間的相互合作。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2f6a092d984eaaf84ed9b2b69431067d.png)
過程:
在這三種跟蹤情境的基礎上，首先評估了在不考慮相互合作的情況下利用我們之前的單一傳感器方法進行多目標跟蹤。在給定的跟蹤情境下，地板（或地板準確性）的跟蹤準確性定義為在整個重複測試的跟蹤情境（如圖4所示）中，正確ID的總計數占ID的總計數的平均百分比。

一開始，兩個帶有RFID標籤的人反復沿著預先安排的路線行走，如跟蹤情境所示。在沒有有縫RFID傳感器的幫助下（或者關閉RFID標籤），地板的平均誤差距離在76%的測試情況下可以達到28.28厘米。然而，在這三個跟蹤情境中，即使在兩個人碰面後，地板的準確性分別降至0％，0％和22％，即使在多居民情況下，平均性能令人滿意，但地板幾乎失去了對居民的跟蹤，這可能導致智能家居中的錯誤服務提供。另一方面，在沒有無縫地板的幫助下，如果標籤不斷發送封包（例如，如果系統每秒發送一個封包，則RFID標籤的電池電量平均在三天內耗盡），主動RFID標籤將迅速耗盡電池電量。

因此，本研究將相互合作的概念應用於擴展和增強我們之前的工作。圖5總結了基於我們的三個跟蹤情境的實驗結果。每種情況在每個情境中平均測試了十次。*一旦由感測地板計算的信心因子低於其對應的閾值，RFID將被喚醒以提供校正信息*，同時開始消耗電力。圖5(a)、(c)和(e)中標有Case-I的曲線分別說明了這三個跟蹤情境中跟蹤兩個人的地板準確性，而不考慮跟蹤設備的任何可能故障，即Case-I代表了電池中的主動標籤完全充電，因此標籤可以按預期提供可靠的校正。

如果閾值設為1，則Case-I的準確性可以達到0％的故障，前提是RFID可以正常工作（或RFID故障率為零）。作者認為，大多數情況下，居民在家中會按照規律的運動模式移動，他們不會總是像三個跟蹤情境中那樣執行不規則的運動模式。此外，這項工作的實驗結果主要是基於有意設計的三個情境獲得的，這些情境的主要目的是混淆跟蹤系統，這些情境可以被視為智能家居中不規則運動模式的三個最壞情況的示例。

為了為改進我們的測試結果增加變化，我們還考慮RFID無法提供即時校正或居民可能以其他不規則的跡跡移動的情況。這相當於考慮RFID系統上可能發生某種故障率（概率）的事件，包括：1）RFID標籤可能因電池電量不足而無法傳輸其標籤字符串；2）RFID閱讀器可能因信號干擾而接收到亂七八糟的標籤消息；3）RFID定位器可能無法喚醒電池電量低的標籤。基於這些事件，作者模擬了兩個額外的測試案例，其中Case-II模擬了RFID系統的故障率為20％，Case-III為50％。從結果來看，即使利用RFID校正信息，Case-II和Case-III的準確性可能比不使用校正信息的情況更糟，如圖5(a)、(c)和(e)所示。令人感到意外的是，結果惡化是因為RFID可能會產生誤導性信息，從而混淆原本正確的ID估算。然而，我們相信，隨著RFID相關技術的進步，這種故障最終將得到相當的改善。

與預定的閾值相比，感測地板計算的信心因子可以被RFID系統用來確定是否應激活RFID標籤以傳輸校正信息。圖5(b)、(d)和(f)顯示了三種情境中Case-I的RFID標籤的節能結果以及與準確性的關係。*RFID標籤的節能大致成反比於主動標籤的頻率（或激活百分比）。結果顯示，與當前信心因子相比，閾值的降低也會導致RFID系統激活頻率的降低，從而增加RFID系統的節能*。

在圖5(b)、(d)和(f)的每一對曲線中，我們可以找到一個交叉點，兩個曲線在此處相遇，用戶可以確定一個合理的閾值，以在減少RFID系統電能消耗和提高感測地板準確性之間進行權衡，從而確認了我們之間的合作意圖兩個不完美的傳感器之間的相互合作。需要注意的是，實驗結果顯示，跟蹤情境III似乎比其他兩個情境具有更高的準確性。原因是與情境I和II相比，這種情境具有更規則的運動模式，即在這種情況下，快速轉彎可能不足以混淆感測地板。


結果:
該理論工作的目標是提出一種更有組織的方法，而不是隨機選擇傳感器和效用函數，以有效促進它們之間的相互合作。在這裡，我們的測試結果呈現出類似的曲線和預期趨勢，因為我們只考慮了以下測試情況：1）所有情境都是經過精心設計的，以便首先混淆感測地板，然後RFID將被觸發以提供理想的校正信息；並且2）這些RFID定位器有意沿著志願者的移動路徑部署，以便可以喚醒RFID標籤以提供即時校正。

從實驗中，我們還了解到RFID定位器的位置和閾值應該是用戶和服務相關的。例如，照明服務可以在晚上檢測到用戶時自動打開燈光，這是與用戶無關的，服務的閾值可以設置為零以增加節能。相反，關於廚房的刀具監控服務就是用戶相關的；因此，閾值應該設置為1，以便跟蹤系統可以確保正確識別，以提高廚房的安全性（特別是對兒童）。在這項工作中，成本考慮絕不是主要考慮因素，因為每個家庭都有其自己獨特的位置感知應用的考慮因素。至於實際部署，可以通過使用最先進的跟蹤傳感器或根據每個用戶的獨特需求，通過所提出的架構合併更複雜的跟蹤模型，進一步提高所需的跟蹤準確性。

---
## Internet of Things (IoT) for building Smart Home System

### 智慧家庭，安全事件，遠端操控
如何利用FLIP（Frugal Labs IoT Platform）來監控和控制智慧家庭環境。文章中提到的實驗使用了溫濕度感測器、光線感測器，並透過FLIP平台進行控制指令的傳輸。具體的實驗代碼用於發布溫度、濕度和光線強度數據，並允許遠程開關燈光。實驗結果表明，該系統能夠有效地進行環境監控和設備控制，從而提升了能源和資源的利用效率。

主要實驗的目的：
* 監控和控制智能家庭環境。
* 改善空氣質量和安全性。
* 遠端控制家電、門窗鎖。
* 在特定條件下產生警報和通知。
* 通過感應室內光線強度和溫濕度自動調節照明和空調系統。
實驗代碼：
* 使用C語言編寫的固件代碼，被上傳到FLIP裝置上。
* 該代碼發布溫度、濕度和光線強度數據。
* 允許遠程開關燈光。
實驗使用的器材：
* FLIP裝置連接到感測器、燈光、空調、攝像頭以及窗戶和門系統等家電。
* 該裝置透過閘道器連接到互聯網，並增加了智能家庭網絡的安全層。
實驗得到的結果：
* 
* 可以持續監測室內空氣質量，並在檢測到健康風險時向用戶發送警報。
* 增強了安全性，用戶可以監控家中的每一個活動並控制窗戶和門。
* 系統通過智能照明、智能家電和智能空調系統確保了能源和資源的更好利用。
* 實驗測試的性能符合預期

甚麼是flip?
FLIP（Frugal Labs IoT Platform）是由位於印度班加羅爾的Frugal Labs開發的一個開源物聯網（IoT）平台。這個平台不僅僅是一系列的設備和感測器或雲服務的集合，而是一個完整的IoT平台，旨在幫助開發者、愛好者以及任何對IoT感興趣的人將他們的想法轉化為可行的概念。

在這個實驗中，FLIP的功能包括：

* 連接性：FLIP板通過Wi-Fi/藍牙模塊為設備層提供連接性，這些模塊可以通過6針接口直接連接到FLIP基板。Wi-Fi模塊直接將FLIP裝置連接到互聯網，而藍牙模塊則透過架構中的閘道層將FLIP裝置連接到互聯網。

* 設備層：包括控制器通訊模組、感測器和執行器。在這一層中，FLIP基板基於Arduino Nano，用作控制器。FLIP智慧家居擴展板被堆疊在基板上以擴展基板的功能。智慧家居擴展板配有溫度和濕度光照強度（LDR）感測器，並允許連接其他感測器，如PIR、各種氣體和空氣質量感測器、聲音感測器等。它還有交流電（AC）繼電器，可以控制最高7安培、250伏特的電流，從而連接家用電器、家庭照明等。

* 閘道層：由基於Linux操作系統的本地處理單元組成。FLIP架構使用Raspberry PI 3作為閘道裝置，該裝置具有藍牙連接功能，允許其他裝置連接到它。在架構中，所有裝置都連接到閘道，閘道通過乙太網或Wi-Fi連接到互聯網。

* 雲層和應用程式SDK層：包括代理和數據庫。代理連接所有裝置，數據庫存儲來自裝置的數據。雲層有三個主要結構：MQTT代理（Mosquitto）、Mongo DB數據庫和Node.js用於後端處理。應用和SDK層位於最頂層，包括網絡應用和儀表板，用於使用小部件和圖表進行數據可視化。利用儀表板可以監控和控制設備。SDK具有基於Python的規則引擎，可以定義設備的邏輯，例如當溫度達到某一水平時開啟空調，也可以連接到社交媒體或第三方應用。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_eace1acde89d46f67cc47ec248aa379d.png)
在這項實驗中，FLIP用於：

監控環境質量和安全。
遠端控制家庭裝置，如門窗、燈光等。
根據環境數據自動調節室內照明和溫度。
生成和接收預設條件下的警報和通知。

--- 
## IoT based Smart Home Design using Power and Security Management
### (OUTDATED) APP，遠端操控，智慧家庭
這篇文章主要是做了一個app，前面先介紹了相關的其他系統，後面介紹了自己的系統，這邊直接介紹他們做的系統。 他們也是透過PIR(sensor)去感知的。
這個模型是基於以太網的系統，讓使用者能夠監控電器設備的實時開關信息，並通過 Android 應用程序進行控制，同時在不需要的情況下監控家庭的安全，例如不受歡迎的人進入或火災。該模型使用溫度感測器和煙霧感測器來檢測家中的火災，使用PIR運動感測器來檢測家中是否有不受歡迎的人，並通過基於Android的移動應用程序監控和控制所有電器設備的實時跟蹤和開關。該系統通過互聯網連接到此Android應用程序，以實現更好和更快的通信。

該模型的核心是基於以太網的Intel Galileo第2代板，它允許設備和傳感器連接到互聯網。這個Intel Galileo板基於Intel Quark SoC X1000，具有32位的Intel Pentium處理器級別的SoC。它與Arduino Uno R3的硬件、軟件和引腳都是兼容ㄉ。

在模型的另一側，有一個基於Android的移動應用程序，該應用程序具有跟蹤設備開關時間、通過觸摸模式或語音模式控制設備開關以及在安全性違規或火災情況下生成警報的選項。該應用程序是基於Android的，可以通過Wi-Fi或移動數據連接到互聯網。它連接到基於Intel Galileo的伺服器，讓用戶可以通過內部移動計時器監控並使用Google API語音識別工具進行觸摸或語音切換。用戶可以手動打開或關閉PIR感測器或火災追蹤系統，甚至在它們檢測到變化時獲得警報。警報實時發送到用戶應用程序，顯示在警報選項卡中。

該模型通過在家中的原型房間上部署並測試，其中連接了4個220V設備以及安全蜂鳴器和火災警報系統。所有這些結果都被記錄下來並拍攝了屏幕截圖。該模型的系統架構由以下圖示解釋，其中包括與Intel Galileo板連接的移動Android應用程序的截圖，該板控制著220V設備並使用內置計時器和繼電器模塊跟蹤它們的切換時間。

下面是他的app截圖:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_302ba3c63919cac4740a101080d4a127.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1bce8c1ff37f05410c126ba376e6f0ec.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0cc317b4c94d2d21015612b1a87b09a7.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1049ba91245f9776f2c03c0d88712658.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_16e648f04d4a4c1947d8b26e45d7d2cd.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_57296cf4f46bb7cd4ec34593e175d599.png)

--- 
## SVM-Based Multi-Modal Classification of　Activities of Daily Living in Health Smart Homes:　Sensors, Algorithms and First Experimental Results
### 多感測器，活動辨視，ML
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0f93591bbf8347d416b30a32e1706d6c.png)
實驗的目的是監測獨居於家中的個體日常生活活動，並自動對七種活動進行分類。實驗協議相當簡單：個體佩戴可穿戴*傳感器*進入公寓，並像在自己家中一樣行動。個體被要求至少一次執行預先定義的每項日常生活活動。這些活動無需遵循特定順序或時間限制，且個體被要求按照他們通常的方式進行這些活動。該實驗由13位健康年輕的受試者（6位女性和7位男性）完成，平均年齡為30.4歲，平均身高為1.76米，平均體重為69公斤，平均實驗執行時間為51分40秒。
在分類結果方面，使用了一個和二階多項式核（Polynomial Kernel）和高斯核（Gaussian Kernel）來測試活動的分類。採用了“留一法”（leave-one-out）進行驗證。對於高斯核，通過最小化全局錯誤率來選擇核參數的最佳值。多項式核的時間框架分類準確率為75.9%，而高斯核為86.2%。混淆矩陣顯示，分類結果會受到訓練數據庫中類別代表性的影響，少數類別的錯誤分類率較高。例如，衣著/脫衣活動的錯誤大多分配在睡眠和休息類別，這些類別在數據庫中有更好的描述。整體而言，訓練數據庫中代表性較高的類別擁有較高的分類準確率。最終全局分類準確率為86%，分類效果最好的是那些在訓練數據庫中代表性更強、數據項目更多的類別
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2d9136d182691f94553e6aafb96ebff3.png)
這張圖是再說真實的根被認定的比例分別是多少，可以看到hygiene比較容易被誤認。這是預期之中的，因為數據庫中最具代表性的類別在模型中描述得最好，並且在進行測試時去除一個元素時最為穩健。(使用了位置（存在紅外線）感測器、用於聲音和語音識別的麥克風、由加速度計和磁力計組成的可穿戴式感測器，用於指示行走時期和體位轉移，以及家用電器（冰箱、櫥櫃和梳妝台）上的門磁觸發器，最後還有溫度和濕度感測器。在介紹了各種感測器及其在公寓中的安裝後，我們提出了每個感測器的特徵選擇。這些特徵之所以被選擇，是因為它們代表了一個活動並允許正確區分兩個不同的活動。然後，這些特徵被結合在一起，創建了一個明顯代表一個活動的特徵向量。使用“一對一”算法確定了監控的七個日常生活活動的模型。) 

未來發展方向:
1. 找老年人來當受試者 雖然被認為年輕人跟老人理論上並沒有太大差異在這個實驗中，但還是需要實驗佐證。
2. 必須創建一個額外的類別，代表兩個活動之間的過渡。事實上，當算法對一個時間幀進行分類時，這個幀可能包含1分30秒的烹飪活動和1分30秒的休息活動。這種幀應該被分類到這個新的類別中。
3. 在不考慮其他因子的情況下這個實驗是否可行?(EX: 季節，住公寓還是套房...) 也就是畏懼會有所謂的指導效應（我們對實驗方式對個人執行方式的影響）。
4. 作者也考驢過直接定義可能行為為正常(如12:00吃飯，6:00晚餐)，但這樣可能也會導致限縮人群的比例。將通用模型添加到受試者學習的行為中應該會損害這種檢測，因為它會減少全局模型中特定部分（涉及受試者或人口的部分）。一個未來的問題在於，插入這些先驗知識是否能夠彌補算法的較低的泛化能力所帶來的改進（以靈敏度和特異性來衡量）。答案將隨著對更大且不同人群的結果以及醫學角度的實際效益而來。因此，必須確定可接受的錯誤率與人口預定條件的數量之間的平衡。






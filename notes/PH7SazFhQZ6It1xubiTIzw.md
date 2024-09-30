# 殭屍網路
[toc]
## 集中型(HTTP、IRC)
- 集中式殭屍網路（Centralized Botnet）是目前使用最為廣泛的一種殭屍網路，也是殭屍網路發展初期時最常見的一種。集中式殭屍網路是由少數C&C伺服器作為控制中心，以及大量的殭屍所組成的殭屍網路。
- 集中式的殭屍網路是由主控者藉由將指令發布到C&C伺服器中，殭屍再從C&C伺服器取得指令的方式管理整個殭屍網路。
- 因為架構簡單，如今仍是主要的殭屍網路結構方式。其缺點在於存在單點故障的問題，只需將C&C伺服器做重點清除，即可使殭屍網路失效。
:::warning
C&C伺服器是掌握殭屍電腦的中心化位置，攻擊者可以通過C&C伺服器發送指令給所有感染的電腦。這使得攻擊者能夠協調和控制整個殭屍網路，進行各種攻擊，如分佈式拒絕服務攻擊（DDoS攻擊）或大規模的網路詐騙。
- 如何製造一台C&C server
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6028ee15f851db3160bca4f2f4ca2186.png)
所有被感染的電腦會和 C&C Server 進行回報，報告的內容包含了自己的 IP、作業系統版本、電腦的資訊，例如 CPU 時脈、記憶體的大小，以及所感染的程式版本等。依駭客的不同需求，所回傳的資訊有所差異，但一定會包含 IP 資訊，以用於後續的遙控及管理。
:::
### 集中型殭屍網路構成演變
copy by 殭屍網路活動偵測工具研發(論文)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0df834ad3a0445f997d37e9233bc81c9.png)
- 在集中型的殭屍網路演進過程中，由於採取單台 Server 容易被偵測到，因此許多駭客改為採取多個 C&C Server 的方式。每台 Server 之間彼此會定期或不定期的交換資訊，以確保單部伺服器被偵知時，不會造成整個殭屍網路被瓦解。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_572dcb369e335391b00cd9e003a09777.png)
- 集中型的殭屍網路亦引進階層式的觀念，所有被感染殭屍程式的電腦並不直接和 C&C Server 作連結，被感染的主機僅知道上層主機的位址 (此上層主機亦是被感染殭屍程式的電腦) ，因此要從下層被感染的主機查獲 C&C Server 相當的困難。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6d3f023316c9f25775558a1f27187d45.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e636e490ae21c9ef218ec4004ad8c13e.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ba3745d7fde0a56a925db807664b72f0.png)
- 機器人：被代表 Botmaster 的 Mirai 類惡意軟體感染和危害的物聯網設備。

- 命令與控制中心（C&C）：負責殭屍網路控制的伺服器，向殭屍程式發出命令以發動不同類型的攻擊（例如垃圾郵件、DDoS）。

- 掃描器：物聯網設備或伺服器，用於識別其他易受攻擊的物聯網設備，掃描 IPv4 位址空間以尋找開放的 TCP/UDP 連接埠。

- 報告伺服器：記錄掃描結果、活動機器人和被盜憑證的伺服器。

- 載入程式：伺服器從報告伺服器取得掃描結果和憑證，以便登入易於攻擊的物聯網設備，並指示它們下載殭屍網路惡意軟體。

- 惡意軟體伺服器：也可以充當載入程式伺服器的伺服器，託管惡意軟體程式碼，這些程式碼將由受感染的物聯網裝置下載。
### 集中型殭屍網路解決方法
:::info

- 集中式殭屍網路由於殭屍與固定的C&C伺服器間的通訊行為頻繁且密集，容易產生大量的異常流量，因此網路安全人員能輕易地發現C&C伺服器的存在，並進一步利用C&C伺服器清除與其相連的殭屍。
- 一旦C&C伺服器被關閉，殭屍網路便會失去所有與此C&C伺服器關聯殭屍的控制權。

- 除此之外，若網路安全人員針對C&C伺服器的異常流量進行分析，甚至可以追蹤到主控者的位置。由此可見，集中式殭屍網路對於隱蔽性與存活性的能力較低，當受到網路安全人員的攻擊時應變能力較差。
:::

## 去中心化型(peer to peer)
peer to peer:每個用戶端既是一個節點，也有伺服器的功能，任何一個節點無法直接找到其他節點，必須依靠其戶群進行資訊交流。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f65c2122dd6caaeb8b026ddc8a03d326.png)
### P2P殭屍網路
- 每一個被感染的主機都可以擔任 C&C Server 的角色，其網路架構也沒有星狀或網狀的特色，某些高階的殭屍程式在交換資訊時也是非定時非定量的，因此在偵測上的難度更高。在 P2P 型的殭屍網路架構中，彼此間的通訊亦可能進行加密，因此要確實的偵測出其活動的難度甚高。
- P2P殭屍網路與集中式殭屍網路相比，擁有更高隱蔽性與存活性。在P2P殭屍網路中，主控者不會與固定的C&C伺服器通訊，殭屍間相互通訊是依靠鄰居清單（Peer List）維繫，Peer List即為每個殭屍所擁有的鄰居節點，由於每個殭屍都擁有大量的鄰居，所以當殭屍向鄰居進行通訊時，會從清單中任意選擇一個鄰居進行溝通，以取得主控者所發布的指令，因此殭屍網路不會因為部分的殭屍被清除，從而影響主控者對其他殭屍的控制權。而且，主控者與殭屍沒有直接的聯繫，網路安全人員無法針對單一殭屍的異常流量分析，而追蹤到主控者的位址。

- 然而，由於主控者剛發布指令時，只有少數的殭屍接收到，其他殭屍也無法直接向已收到主控者發布指令的殭屍取得指令，而是必須透過與自身的鄰居以相互聯繫的方式進行傳遞指令，如此會導致殭屍網路在初始傳遞訊息時的傳播率受到嚴重的影響。
:::success
peer list紀錄 ID,IP,PORT,連線狀態,其他元數據
:::
### P2P殭屍網路校驗機制
- 根據P2P 協定特性，理論上任何人都可以加入這個網路並與其他節點通訊。整個過程中，BotMaster 必須保證只有他自己可以發送有效的控制指令或文件，其他節點可以進行常規通信(遍歷節點、查詢臨近節點信息、接收指令或文件等等)，但不能發送控制指令或文件。其他節點發出的指令或文件，整個網路中的Bot 節點都不會接受。

- 要實現這樣的特性，BotMaster 必須給這些關鍵通訊加上校驗機制。例如利用非對稱加密演算法，透過只有BotMaster 一人掌握的金鑰給通訊內容加上數位簽章。接收到指令或文件的Bot 節點，會用自己的另一個金鑰來校驗資料的合法性，合法的通訊才接受，非法的則丟棄。

### P2P殭屍網路解決方法
:::info
- P2P殭屍網路的通訊結構非常依賴Peer List，一旦網路安全人員發現部分殭屍的Peer List，便能透過Peer List列舉和破壞殭屍網路的連通性，甚至能瓦解整個殭屍網路。
:::

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9c2991048e278e250b20bb806e5da63f.png)


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5106535e0a2c28c1b779c0fa0be1dc77.png)
## 混合式P2P殭屍網路
- 混合式P2P殭屍網路（Hybrid Peer-to-Peer Botnet）是結合了集中式殭屍網路與P2P殭屍網路的特性，所形成的一種殭屍網路架構。混合式P2P殭屍網路分別將殭屍區分成Servent殭屍與Client殭屍，整體由駭客、Servent端和Client端所組成。

- Servent端是由可被外界瀏覽的公開且靜態IP殭屍所組成，而Client端則是由不可被外界瀏覽的私有且動態IP殭屍所組成。Servent殭屍擁有P2P殭屍網路的特性，同時扮演著集中式殭屍網路中的C&C伺服器，可視作一群擁有P2P殭屍網路特性的C&C伺服器，主控者只須將指令發布到其中任何一台殭屍設備，便能將指令傳達給所有Servent殭屍，Servent殭屍能同P2P殭屍網路的通訊行為進行訊息相互傳遞。而Client殭屍則是一般的殭屍，僅會與它已知的Servent殭屍進行通訊，取得主控者所發布的命令。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9a14a1c3081f1cde150fe298f0977aa4.png)
### 混合型P2P殭屍網路解決方法
::: info
- 混合式P2P殭屍網路改善了集中式殭屍網路隱蔽性較差的缺點，同時也修復了P2P殭屍傳播率差的問題，提升殭屍網路的存活性與訊息傳播率。但是，混合式P2P殭屍網路與P2P殭屍網路擁有相同的缺點，因為殭屍與殭屍間的通訊行為仍依賴著自身的Peer List，只要網路安全人員針對Peer List進行分析，便能輕易地列舉殭屍並破壞整個殭屍網路的連通性。
:::
# 物聯網運作原理
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1d8e34de3863ecec476e75fe3551eab0.png)

# 物聯網僵屍架構
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0395d9b3f26d1ea7de7216cb31029d71.png)
- 步驟 1：掃描器/機器人使用包含 62 個可能憑證的預先配置硬編碼列表，採用暴力攻擊來尋找預設設備憑證。憑證在來源檔案中以其編碼形式定義。

- 步驟 2：成功後，設備特徵將透過引入不同的連接埠號碼轉發到報告伺服器。

- 步驟 3、4、5：查詢報告伺服器，然後命令載入程式將可執行檔傳播給潛在的受害者。裝載機接受命令。

- 步驟6、7：指示殭屍網路向目標伺服器發動攻擊，導致伺服器服務癱瘓。

## mirai殭屍病毒
- 出現於2016年
- 目的在感染基於 Linux 的物聯網設備
- 主要利用物聯網（IoT）設備的弱密碼來感染和控制設備
- 透過網際網路掃描可能的目標設備
- 一旦找到開放的Telnet端口
- 使用預先定義的用戶名和密碼組合進行暴力破解攻擊
- 成功登錄後，Mirai 在目標裝置上安裝並執行惡意軟體，將裝置納入其殭屍網路
- 主要用於DDOS
:::success
Mirai的源代碼在互聯網上洩露，導致出現了多種變種和改進版本
:::
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_17857cc0127a52e8cf0fad6f3fa84fd6.png)

## mozi殭屍病毒
- 發現於2019
- 為mirai變種
- 基於DHT協定實現的P2P殭屍網路
- 透過ECDSA384以及xor演算法保證自身和P2P網路的缺陷和安全性
- 各節點的指令執行由Botnet Master下發的名為Config的Payload驅動
- 主要用於DDOS、加密貨幣挖礦

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0674e114481771379b01376f76b96342.png)
:::info
- 今年8月mozi活動量急劇下降

- 有個神祕的終止開關(kill switch)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_032a7793db5abdc560ad19dc2ec920db.png)
:::



# 資料來源
知己知彼方能因應　看清殭屍網路肆虐真相
https://www.netadmin.com.tw/netadmin/zh-tw/technology/5F56F8CC54014484878C1F84414C8A9D
殭屍網路活動偵測工具研發(論文)
https://hdl.handle.net/11296/nva327
Profiling IoT Botnet Activity in the Wild(論文)
https://ieeexplore.ieee.org/document/9686012
Apprehending Mirai Botnet Philosophy and Smart Learning Models for IoT-DDoS Detection
https://ieeexplore.ieee.org/document/9441212
以 P2P 的方式追踪 DDG 僵尸网络
https://jiayu0x.com/2019/04/11/track-ddg-botnet-by-p2p-protocol/
P2P
https://hackmd.io/@leviliangtw/HkFDs3hCP
AI 驅動的蜜罐可增強物聯網殭屍網路偵測
https://ieeexplore.ieee.org/document/9275581
了解 Mirai 殭屍網路原理和 IoT-DDoS 偵測的智慧學習模型(論文)
https://ieeexplore.ieee.org/document/9441212
P2P殭屍網路：Mozi分析報告
https://blog.netlab.360.com/p2p-botnet-mozi/
連Ethereum都在用！用一個例子徹底理解DHT
https://medium.com/taipei-ethereum-meetup/%E9%80%A3ethereum%E9%83%BD%E5%9C%A8%E7%94%A8-%E7%94%A8%E4%B8%80%E5%80%8B%E4%BE%8B%E5%AD%90%E5%BE%B9%E5%BA%95%E7%90%86%E8%A7%A3dht-f772ea2c6dcf
P2P 網路核心技術：Kademlia 協議
https://zhuanlan.zhihu.com/p/40286711
Who killed Mozi? Finally putting the IoT zombie botnet in its grave
https://www.welivesecurity.com/en/eset-research/who-killed-mozi-finally-putting-the-iot-zombie-botnet-in-its-grave/
基於 IoT 的 Mirai 漏洞掃描器原型
https://ieeexplore.ieee.org/document/9214099
物聯網IoT的安全威脅防範與案例分析
https://www.itc.ntnu.edu.tw/wp-content/uploads/2019/07/security-1080821.pdf
A lightweight deep learning framework for botnet detecting at the IoT edge
https://www.sciencedirect.com/science/article/pii/S0167404823001050
Benefits of Internet of Things (IoT) Applications in Health care - An Overview
https://ieeexplore.ieee.org/abstract/document/10141452
Understanding the Mirai Botnet
https://www.usenix.org/system/files/conference/usenixsecurity17/sec17-antonakakis.pdf
A survey: contribution of ML & DL to the detection & prevention of botnet attacks
https://link.springer.com/article/10.1007/s40860-024-00226-y
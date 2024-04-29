企資網課輔(5/1)
[TOC]
# ch 06
## Omnidirectional and Dish Antennas(p.12)
-  Omnidirectional Antennas:訊號向各個方向傳播，但訊號快速衰減，無須對準接收者
-  Dish Antennas(碟型天線):傳播訊號角度縮小，可傳較遠，但須對準接收者
## Wireless Propagation Problems(p.14)
- Dead Zones(dead spots):當遇到障礙物時，頻率越高，越無法繞過
- Multipath Interference:直接訊號和反射訊號可能會產生干擾，如果兩個波異相(相位不同)，它們將相互抵消，不發出訊號
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_af6ca1a8916f4b2c7057f0522c46f7c5.png)
- Electromagnetic Interference (EMI):由電磁場引起的干擾，通常會導致電子裝置、設備或系統的性能下降或中斷
### attenuation
- Inverse Square Law Attenuation:訊號強度與距離平方成反比  (1/r)^2
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8ecd2bff5832b975fc4b1bae96da0612.png)
- Absorptive Attenuation:水氣會吸收signal
----------------------------------------------
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1d98b98f8ff9d6cf6f2cf81b10e61658.png)
- 跟吸收有關:Inverse Square Law Attenuation,Absorptive Attenuation
- 跟頻率有關:Absorptive Attenuation,Dead Zones
## Frequency Spectrum, Service Band, Channels
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_daac180e4f13dbda6b6295a717a38091.png)
## Signal Bandwidth(p.30)
- 頻寬越大，速度越快
- 頻寬加倍使傳輸速度加倍
- 寬頻(boardband)意味著寬廣的無線電頻道頻寬
## 2.4 GHz and 5 GHz Service Band(p.34)
### 2.4GHz
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5d2acebcb9dd29be96d71e9ff0bc96ba.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bc7f4d37f87397801926f1da9deb2097.png)
### 5 GHz
- 更多頻寬，因此有 11 到 24 個不重疊的 20 MHz channels
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ad349bdf945749c332d4f63fc39e527f.png)
## Spread Spectrum Transmission(p.45)
- 展頻:頻寬的寬度需要比要求的還要寬
## Orthogonal Frequency Division Multiplexing(P.48)
- OFDM:訊號與訊號間處垂直(垂直堆疊)狀態時部會彼此干擾
## Basic Service Set (BSS)(P.55)
- Basic Service Set (BSS): An access point and its wireless hosts
- Service Set Identifier (SSID) is the name of the network.
## Extended Service Set (ESS)(P.56)
- Extended Service Set:由一個或多個無線存取點（Access Point，AP）組成的集合，這些存取點使用相同的服務集識別碼（Service Set Identifier，SSID）
- Hand off:行動裝置在從一個無線存取點（如Wi-Fi路由器或基地台）到另一個存取點之間無縫切換網路的過程
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_35264d771b27d4c64b3c7fe64d25c075.png)
## CSMA/CA+ACK(p.59)
- CSMA(Carrier Sensing with Multiple Access):如果另一個設備正在傳輸(transmitting)，它會等待(waits)，不能同時傳輸(當有人同時發言會造成Collision，要暫停發言)
- CA : Collision Avoidance(避免碰撞，還是可能發生) 決定隨機值再發言
- ACK (Acknowledgement):
  - 接收方立即發回(ACK)確認
    CA 其他設備的隨機延遲保證有足夠的時間立即 ACK
    如果發送方未收到確認，則使用 CSMA 重傳
- CSMA/CA+ACK有很多等待，這使得它效率低下(inefficient)
- 比RTS/CTS有效率

## RTS-CTS(p.65)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b13e3b790b7024704a6ec321ea226c7e.png)

1. 傳送前，發送端要先傳送一個RTS(Request-to-Send) Message
2. 基地台要傳送一個CTS(Clear-to-Send) Message，告訴發送端可以送出資料並且告訴其他的無線裝置在這段時間內不能傳送任何資料，以避免碰撞
3. 如果兩個或多個客戶端站無法相互聽到時適用，可以阻止它們同時傳輸
## MIMO(Multiple Input/Multiple Output)(p.78)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e6f2653b84913a9e89e2c0f34983f13a.png)
1. 多支天線，可以增加速度、距離，因為它可以在一個頻道中發送更多資訊。
2. 在同一個頻率(頻道)中發送相同的內容
3. 送達的時間差可以讓訊號得以分離和被理解。
## Beam Forming(p.81)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6659fd2913450b5f8946cc3a32a3c81b.png)
- 比較有方向性，訊號僅在範圍內，不會互相干擾
# ch07
## Wireless LAN Security Threats(p.6)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b2b665750edce4d2ef266d4fa1a4528e.png)
- 為避免被竊聽，需要先做認證，認證通過後做加密。每一個訊息都要進行CIA
- CIA: Confidentiality(機密性)、Integrity(完整性)、Authentication(認證)
## 802.11i Security Protection(P.8)
- 主要保護Wireless Host and the Wireless Access Point
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8e61d86fc4e6090743cc13913a73424e.png)

1. 802.11i Security is Not Enough
    - Rogue Access Point:是在沒有本地網絡管理員明確授權的情況下安裝在安全網絡上的access point
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3b7a532c8b490c77b23d650cd31bb887.png)

    - Evil Twin:配置有相似或相同的SSID和密碼設置的偽造的無線access point，中間人攻擊的一種
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f3b3054d7a095f375b77166de39b9789.png)

2. 802.11i 提供Wireless Host和Wireless Access Point之間的安全，為機密性、身份驗證和消息完整性加密消息
3. 使用強大(strong)的加密標準，包括用於機密性加密的 AES
4. 本身對應Wired Equivalent Privacy (WEP)，但已經被破解(Never ever select) 
5. 分為:
    - Pre-Shared Key Mode (PSK: 大家用一樣的key，僅作為認證用，真正加密使用Unshared Session Key) 、generated from passphrases密語(允許有空白)
   -  802.1X Mode (使用帳號密碼，伺服器認證後開啟服務)
   ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_86335aaccc9d5c849a036250e318e077.png)







# 企資網課輔(5/1)
[TOC]
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


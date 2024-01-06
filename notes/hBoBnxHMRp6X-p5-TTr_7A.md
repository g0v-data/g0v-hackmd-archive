# 作業系統

## Ch1 Introduction 

### 何謂作業系統?
--讓使用者妥善地使用軟硬體資源的系統程式

### 如何解決IO造成的CPU idle?
#### 1.off-Line 運作
以磁帶機取代極慢的I/O device,ex: 讀卡機(輸入裝置), 印表機(輸出裝置)

#### 2.緩衝區
I/O Bounded job: 空的input buffer,滿的output buffer
CPU Bounded job: 空的output buffer,滿的input buffer

#### 3. Spooling
把磁碟當成巨大的緩衝區使用
2 v.s. 3: spooling 可以同時執行許多工作

### 各類系統型態

#### 1. Multi-programming
透過context switching讓CPU always busy

#### 2. Time sharing (Multi-tasking)
讓多個使用者能透過終端機與作業系統互動

#### 3. 分散式作業系統(Distributed System)
1.每個processor有自己的clock以及memory
2. 每個processor有自己的clock以及OS
3. Processor之間的溝通依靠網路(message passing)
ex: client server system, peer to peer system
優點:
1. 資源共享
2. 加快計算速度: 平行計算
3. 可靠性: 一台掛了,其他台還能運作

#### 4. 即時作業系統(RTOS)
1. Hard real time:
(x)virtual memory
(x) time sharing 
(o)所有資料存在RAM or ROM

#### 5. 多處理器系統(Multi-processor)
1. 增加產量
2. 經濟度量: 共用周邊設備
3. 增加可靠度
對稱式 (SMP): CPU之間互相監督
非對稱式 (ASMP) : 一台不做事,只負責監督

#### 6. 叢集式系統 (clustered system)
將不同電腦,透過LAN緊密連接
ex: asymmetric clustering, symmetric clustering




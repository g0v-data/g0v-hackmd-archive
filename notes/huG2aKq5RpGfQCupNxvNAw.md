計算機組織
===
###### tags: `計算機組織`,`U5`

[TOC]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_416ffb4615b0349275d3e006e68dd7be)
---
## 區域性:
- 時間區域性(temporal locality):若被存取 下次可能很快的被存取
- 空間區域性(spatial locality):附近的資料有即將被存取的傾向
--- 
## 記憶體階層(memory hierarchy)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ccb090df79d30f7d24e2bb547b2c61b4)
- 最快的 最貴 最貴的最小 最小的 最靠近 cpu
- 資訊最小的單位稱為一個 區塊(block)
- 資料只在兩層間複製

## 5-1
- 命中(hit) : 找到我要的東西
- 錯失(miss)
- 命中時間(hit time): 找到後要花多久時間把他讀出來
- 錯失懲罰(miss penalty): 要花多少代價把下一層的東西搬上來

---
## SRAMs
- 每位元使用六到八個晶體來讀取
## DRAM
- 以電荷的形式存在電容中(電容要大)
- DRAM 一定在cpu 外面
- 加快速度用
- 在每個周期要 重新 存電荷 (ms)
- 因為電荷會漏電 所以為動態
- 比sram 慢
-  在讀取前 必須做刷新
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0664057ce8b3bcb1031db77ccc1d15ad)
## SDRAMs
- 同步
- 有個緩衝器 使 dram 如 sram 一樣快
- 輸出大量位元(burst)
    - 先送一筆 address
    - 可以 接著讀下去
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a37189ff3719aa57cf86b27d879d5e60)

## 雙層資料速度 DDR
- 在正負緣都讀資料
- 可建構多個 bank(每個皆有自己的緩衝器)
- address interleaving : 可以對不同 bank 同時存取
 ## flash
 - 為 EEPROM(可插除 電子 可程式化 唯讀記憶體) 的特殊構造的一種形式
 - 寫入會損耗 
 ## 磁碟
 - 無寫入損耗的困擾
 - 堅固
 
 ## 快取
 - 直接對映 ( direct mapped)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c66f9fd839e09702477935615358f06a)
-  tags 標籤
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_914d61488e0b11018a270b7fb9caf19a)
-  ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_51fa28364ebb2161f8ea28cb01b7b8bd)
- ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fcd3c791a4ec4f5d8b35c1b6a918c256)


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ebe7327db562aa960d6ccdfd7c95ce2d)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0391f398b8cf4e7076663b3120d4c193)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f2afe5cf59b5e83d5b206b2ca12784c5)

- 例題:
    MIPS CACHE 64 K Words
    
    1. 64k=2^16
    2. index=16
    3. tag=32-16 -2=14
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a4879f61629193babed6993d80d8e9e1)

- 例題2:
    address 32 bits
    CACHE 2^n
    block 2^m words
    
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d41f83bac08ac4a1f7abcdb30a06c0bc)
     

| 32-n-m-2 | n | m | 2  |
CACHE : 2^n(1+(32*2^m)+32-n-m-2)

- 慣例上不計算 標籤荷有效位元大小
- 例如: cache 4kib 且 m=3
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_eef2fd3414c0e0618c1c8faa7f1a65a8)
    2^3 words =8*4=32
    4096/32=128=2^7
    index=7
    tag=32-7-3-2=20
    
- cache 要大
- 增加 block 會使 miss rate 增加
- 較大的 block 可以降低 tag 儲存量 但增加了 錯失代價
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_030f79aace48c8c884af729069a415c9)

-  會把 tag block 分開 : 增加快取 的每秒鐘的處理量(可以同時讀)
- ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_42da52ae3bc0154b0cf3ca733643521a)

### 快取錯失
- 重新快取
- cpu 暫停 (pc=pc-4(pc 還原))
- 管線停止

### 處裡寫入
- 寫入 miss
    - write -through(寫透) (不保證一致性)
        - 寫入快取後 同時使用完整的 位置 將自組寫入記憶體
        - write allocate  (寫入配置)
            - 當 write -through 時 會在主記憶體搬一塊上來 
        - no write allocate (不寫入配置)
             -更新在記憶體中被寫入的部分 而不再快取中配置  
    - write buffer 寫入緩衝器 : 
        - 當資料寫入快取和緩衝器時  處理器可以繼續執行 
        - 會有個處理器將 緩衝器 寫入記憶體
        - 當緩衝器寫入記憶體後 緩衝器位置可被釋出
    - write back 寫回
        - 新的值寫回快取區塊 
        - 當更新區塊時 才寫入記憶體
        - 如果有個 快取 miss 且 要被取代的是修過的  則 必須先寫入記憶體
    
### 快取效能
- clock bus
- 例題:
- 1 bus address transfer(位置傳給dram)
- 15 bus  pre DRAM access(讀取時間)
- 1 bus pre data tranfer(把資料轉入)
- ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2e56cb22bbc24608ae49d9926f97ab65)
    (a).4-word block 1-word-wide
    miss penalty(miss 代價)=
    1+4*15+4*1=65 bus cycle
    bandwidth(頻寬)(一個cycle 會讀幾個byte) = 4words/65 bus cycle=16 byte/65 bus cycle =0.25 B/cycle

(b) 4-word block 4-word wide 
(一次的時間 可以獲得 4 個 words )
miss penalty=1+15*4/4+1*4/4=17
bandwidth=16/17=0.94 B/ bus cycle

(c) 4-word block 
4- bank interleaved memory 
(丟一次 四個記憶體可以同時收到各自的位置 但還是要花四次轉入)
miss penalty=1+15*4/4+1*4=20
bandwidth=16/20=0.8 B/ bus cycle

## cpu time
- 程式執行時間
### memory stall cycle(當發生 cathe miss )
   ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_daf521570a1841bbf4a97e878a63df16)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_bb310e53528b906a41f2f3c342369236)
### 平均存取時間(AMAT)
AMAT=Hit time +miss rate * miss penalty
- 例題:
    cpu: 1ns clock hit time=1 cycle miss penalty =20 cycle i-cache missrate=5%
AMAT=1*1ns+20cycle*1ns*0.05=2ns

## 減少cache miss
- 全關聯式(fully associative)
    - block 可以放在任何位置
    - tag 要全紀錄
    - 
- 集合關聯式(set associative)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6f7a89a26567accfb256fb41aa3c14cd)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9d700f0b03de9f9c94ec027feff4118f)
- 關聯度增加 2 位元 (one -way-> two -way) tag+1

## 虛擬記憶體
- 區快稱為 頁(page)
- 記憶體錯失 稱為 page fault
- 處理器產生的位置 稱為 虛擬位置(virtual address)
- 一個程式在 虛擬記憶體的位置是連續的 但在實體記憶體不一定
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3d50d2dc63589ed00d6a3fe6bdb00acd)
- page table 對映
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9e5945f651a7c03cd873a089d1425f14)

## TLB
- 每次的存取至少需要花兩倍的時間
- 發生錯誤 需判對為 page 錯失 還是 TLB2的錯失
- TLB 紀錄中含有參照(ref) 和汙染(dirty)位元
    - dirty 有改過 1 
    - ref 被使用過 1
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6a09f03dc270e578560c316ca7c8151b)
- 當tlb miss 時 到 page table 去找
- 當access bit 為 off 不能寫入
- 為 page table 的子集合
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_74fe23e9e19586bd84b9408e23e9408a)

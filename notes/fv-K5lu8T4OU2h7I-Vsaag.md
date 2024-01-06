計算機組織
===
###### tags: `計算機組織`,`U4`

[TOC]
 
---
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e4eff07dad02ff5b585fa298da79802c)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_26d3b1e4f93c60cacbf51577fd8edb1d)

0. pc+4
1. 先將rs($s2),rt($s3) 做ALU(用Control 選擇要做的ALU 像是 + , - )(例題為+)
2. 再將出來的答案送回registers的data
3. 此時由於Control 使 MemWrite 和MemRead 都為零 ，所以不會寫入記憶體
4. 最後 Regwrite 為1 使data 寫入 rd($s1)
---

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6e1a6c3c5ccba22b4e8f4152673e2e54)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_22654298d9a3d6e1e3d5fcc7859e4466)

- Control 使 MemWrite=0, MemRead=1 ,Regwrite=1
- 常數非register所以走下方
0. pc+4
1. 先將rs($s2)和下方的值 做ALU(用Control選擇要做的ALU 像是+,-)(例題為+)
2. 從記憶體讀出得到的答案的值(M[s2+10])
3. 再將值寫入register(s1)
---
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ec7aa7749d22911a6a410ce5021e9017)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_94000949d8b3982b8e773e0f481a992c)

0. pc+4
1. 將rs($s1),rt($s2) 做ALU(用Control 選擇要做的ALU 像是 + , - )(例題為- 因為算出是否相等)
2. 同時做上方的add (pc+4+(10*4)) 
3. 如果為零，則zero = 1 ，例題為 beq 使 control branch=1 
4. 做多工，把結果從回去 (pc=pc+4+40)
---
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e9fb22572c6d43eaa318458ce0a9eacc)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d054f9a9472419cf18f615b4e8faf011)

- 雖然為J指令 但一樣會切割rs st rd shamt funct 只是毫無作用
0. pc+4
1.  做上方的add (pc+4+(10000*4)) 
3. control 使 branch=1 會想辦法使 zero 也為 1
4. 做多工，把結果從回去 (pc=pc+4+40000)
---
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3a75a867c2c51f801c6fc030f092079a)
- 打勾的為組合邏輯 (input 改變output 直接改變)
- 打圈的為序向邏輯(狀態元件)

---
- 最慢的指令為clock 的最小周期

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_56dda0f6368614b9e34e7684adc879fa)

- 每個指令需要何種數據通道元件

1. 
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_113b26d217743dfdd5bccfd99e82f304)
- 每行指令 以4byte為單位 ，所以下一行為pc+4

2.
 ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3b8268668616a1d7ee55565c3b720827)

- data 為32 bits 
- 當 RegWrite =1 時 才會寫入 Write register

3.
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9d05c1d4b3ee7ebb7098144080ceb931)

- 記憶體

4. 
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e96d961d99f99454b05a09fa5a14c7cb)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_79806dd5d58b16dea034aeab221bfe8a)


-  ALU 為32bits 計算 但在立即定值法為16 bits ，所以要座位元延伸

---
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0cc96fbc3bd160fbd741b476add32fd2)

---
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ce83adad52a88e5a6f84c75958ded88b)

---
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6b1c696b7066b837275aca201e8bd63b)

---
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cc6c6f56a7bb42be000dcb32ac236f3f)

---
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ef6b2e58de5ade9bb12b09683d5dc61c)

---
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_86c7130f38790843d49d28fb6a5b77e5)


- 目的指令會有兩種地方
* - r-type (15:11)
* - i-type (20:16)
---
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0afb660f5bc23e815926d7e163481f5b)

---
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2550b38347af68e2539474d6e75d26fb)

---
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ab97271eeaf1b0f5c761fe19c0109a55)


在mips 指令集中 分支指令是被延遲的

- 
## 管道化(pipelining)
- 改善處理量(throughput)
    - 不會減少每一個的工作時間

假設 read/write 花100ps
其他200ps
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ad68b95d9e9632d26b8ea9a4875325f4)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f7633a97b53670c2e05e110cb1376c61)
- 每個200ps
- 管道化時間:
    - 管道平均時 管線化時間= 單一管線時間/stages的數量
    - 非平均 speedup 會減少
- 倍數 (例題:800/200=4)
### 管道化的設計
- 所有 MIPS 指令 為相同長度
- MIPS 格式種類少
- 來源暫存器欄位在相同位置
- 指令記憶體與 DATA 記憶體是分開的
### 管道化的障礙

#### 結構危機(struct hazard)
- 不能在同一個時間使用同一個資源
#### 數據危機(data hazard)
- 因為某個步驟 必須等待其他步驟的完成而停滯(stall)
  - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e26463d3fde8422a85b406491e69cc54)
  - bubble 似nop指令 => 什麼都不做
  - 方法:提早獲取所需要的資料=>前饋(forwarding)![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_46ef34f264cc9da175ab893d5e3f197c)
  - 前饋無法避免所有的管道停滯
  - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b8bd85c090fd4162ff0714ee4a86e77f)
    -![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_aadc5e54d4079fc30eaca8fd41dd3d22)
    -![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_57d3eb92852dd91d658b291e44692503)
1. 當後面的管線暫存器目的地(rd)=前面的暫存器來源(rs,rd) =>發生hazard
    - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d05ad63ff93014096b02456d315abc91)
    - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1ff34958f4db2e4e1d7a4966e796767e)
    - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f86429ad9d3caf8e8a9cf7af335e2a13)
有寫入暫存器的才會發生hazard
#### 控制危機(control hazard)
beq
- 法一: 停滯
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_208d6bf4248561e35143c0a8963538d2)
- 法二: 預測 如: 預測分支不會發生
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d702fe791908d8d08402e3587d27e90f)
- 法三: 延遲判斷(delayed decision)
    - (利用一個無關的指令來取代bubble)![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d3b2a5d4a6eb24853696356a195cbc49)

## 管線階級
n 級管線 => 時脈週期最多同時有n道指令正在執行
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_71bd63776b100d310736fc390fa98cee)

IF:指令
ID:解碼& 讀暫存器
EX:ALU & 位置計算
MEM:memory 存取
WB:寫回暫存器
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c7c952933ea51076e5101ebecb8e069d)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cfe088ec90031e85c17865dc00da93f6)

- 加暫存器去阻隔每次管線處理過的資料(似移位暫存器 在clock後進入下一個階段)
- 塗顏色為有使用到的資源
---
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4d062aab9be4a2c7b7ca7cbd3b6592fb)
- 右半部是讀，左半部是寫
- 當同一個時間使用暫存器讀寫時不會發生衝突
- ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f3fc75e9ce44960c86cc20702cca5a02)

---
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_32374bd67c45cabe15030e969da3ab15)

- 目標指令須跟著管線跑
- ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3713cea5d6228aedeed37446a14b00cb)![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c174ec8bcbc0a7c40a537b340bf3f96a)

---
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d84cba9e8c1283f4fdc6196319df7a86)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ccc3b7e73a895835348cffc5ced2b0e6)

#### forwarding
##### EX hazard
    - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f50c44c3d80fed3ff8b76350bdb028e6)  
     - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_bf74e942d123b966ff6cf0eeaf5e2043)

##### MEM hazard
    - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_71ea4f3aba8e00b290466dcd5c34e97f)
    - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fdf8db6456634bf5f69dc04899203e9d)

##### Double Data Harzard
    - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a5d6808fd104d376667c72e775b982fb)
---
## forwarding 無法解決
當指令要讀取前一個值令寫入得暫存器時
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_723e4c3b068b3d2ea2e4d920f4867988)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9a1b816af5cf451b83da622c897f6643)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3fee062d32f5040690ceddf55f332418)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a8cdd975423fd3ecd033b04016ccd287)

---
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a220aff2621289b92e03148e1ee5ffdc)

## branch hazard
分支跳躍在memory 才決定
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_dfb85bd781555cc06e0bf56a5fcd81f6)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8e36efa446440b3a281c85f81ebc383e)

### 減少分支的延遲
- 提早計算分支的目標位置 和提早判斷
    - 將分支的加法器移至ID 
    - 把比較器放在ID的階段

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cf672ea46ae149bfb682aeb41be68b6f)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5d8ae198c8a5181bf0491047a934a2c1)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_102028cc3113dd2c879729639d536abe)

- ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d6405ce31981850d7f0285cc311db27d)
- ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3770bad5cfe53f19e46d09cf6c73ea85)


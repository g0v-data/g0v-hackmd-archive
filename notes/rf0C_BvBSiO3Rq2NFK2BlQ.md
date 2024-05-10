企資網課輔(5/8)
[toc]
# ch08
## Hierarchical IP addresses
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5c361c87afd88671a07b57c6938fbd68.png)
- Network part:在哪個網路(代表某一IP、某公司…)
- Subnet part:在哪個子網路(代表某一單位)
- Host part:第幾台Host 
- IP總長度合起來一定是32 bits
## Border Router, Internal Router, Networks, and Subnets
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f9b941fec9db63eb9aa0901f15acbd53.png)
- 轉送封包由router負責
    - Border router : 連接對外的網路(Network)
    - Internal router : 對內各個子網路(Subnet)
- 私人網路:
- 10.0.0.0~10.255.255.255
- 192.168.0.0~192.168.255.255
## mask
- problem:僅透過查看IPv4位址本身，是無法直接分辨出網路、子網路和主機部分的大小的。
- ans:要理解一個IPv4位址的組成，你需要知道使用的子網掩碼。子網掩碼指定了網路部分和主機部分的分隔。子網掩碼中的“1”表示網路部分，而“0”表示主機部分。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fd84e6cfdead9e859a8f6c32866355e2.png)
- /16表示總共32個數，前16個數字是1，後16個數字是0
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7b12c6623e5a0df6a30a009bed332e3e.png)
### Bitwise AND
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_dd3f0f4edd020a8651f26c6ecffc2f54.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1660a0bb92d502ec11d3761ab3aad9e9.png)
## Ethernet Switching versus IP Routing
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9f9c6e3d44a20896ba7278f5f4c73ed5.png)
- 路由器以網狀排列，具有多個替代路由。 （可靠性）
- 因此，路由器可以將封包傳送到多個介面（連接埠），但仍可將封包傳送至其目標主機
- 必須找到具有替代路線的所有行
- 選擇最佳替代路線
## The Routing Process
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3c60e7dad76ddc6815fc12c96692633c.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_145b63bb80802a31e24c3ebf8e9966cb.png)
1. Finding All Row Matches
    - Step1 檢查/找出所有能到目的地的IP位置(目的地包含在範圍中)
    - Step2 計算IP與mask計算結果是否等於目的地，如果有即match
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7ed7635db656218430956aaefa971811.png)

    - Step3在Match的路徑中選擇Best-Match Row 傳送封包
2. Finds the Best-Match Row (Mask跟Metric)
    - 優先選擇符合要求的，依照Metric來選擇(cost或speed)
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_de8d9d05abc12c819bb1fea3204079b2.png)

    - ==選擇Mask最長的==
    - 如果Mask一樣，則cost選擇較便宜(低)的，speed選擇較快(高)的
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7d4b94298fc6d0b7330db09faa699460.png)
    ==ans:row345==
    
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a26985040d2c0a599dc566187405239d.png)
    ==ans:row 682==
3. 根據最佳匹配行中的指示將資料包發送回 
- 將封包從最佳匹配行中指定的路由器介面（連接埠）發送出去。
- 將封包傳送到next-hop路由器列中的路由器。
- 如果位址顯示“local”，則目標主機位於該介面之外。
- 將封包傳送到frame中的目標IP 位址
## Decision Caching 
- 一些router會記住decision並將它們放入cache的列表中
- 如果傳入的目標 IP 地址與cache中的 IP 地址範圍匹配，則使用相同的decision
- 目標主機的最佳路由經常變化，基於緩存的決策可能效率低下甚至是錯誤的
- cache條目過期後立即刪除有助於確保使用者再次存取資料時收到最新資訊。
## Masks that Don’t End at 8-Bit Boundaries
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b553f700ae74c0d6421e2cc7d1489ca5.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_966466d78bfcffa1b7bdf6945c7de385.png)
## Address Resolution Protocol (ARP)
The problem:
- 路由器想要將封包傳送到下一跳路由器或目標主機。
- 路由器知道 next-hop-router 或目標主機的 IP 位址。
- 路由器不知道目標設備的資料鏈結層位址(MAC address)
==這時候就需要ARP!!==
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_92d1f2f4180988bf0d76f695eda03750.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2c5b0114ff461add4bd44234c722e41e.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4acf5a66be9a321fafd43d0b7093330f.png)

## IPv4 Packet
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a48404b3cffae3bacf16785bf99e72ca.png)










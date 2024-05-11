# 5/8
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
- 172.16.0.0~172.31.255.255
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
# 5/15
## IPv4 Packet
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a48404b3cffae3bacf16785bf99e72ca.png)
-  第二行用於重新組裝分片的 IP 封包
-  TTL:初始的TTL 值，一般為64 或128，每經過一台路由器，TTL 的數值就會減一。當TTL 的值減至零時，封包會被丟棄，並向發送者發送ICMP "Time Exceeded"訊息。
-  Protocol:指IP 封包中的資料部分是使用的哪種協議，以便接收方能夠正確地解析和處理資料。
- Header checksum:一個16位元的字段，用於驗證IPv4 資料封包頭部的完整性。
- ipv4 IP Address有32bit
- ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_95e6f83fd6d54356519b7264a2ad225a.png)

## IPv6 Packet Header
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d95493f7cca0710fbef3b61dfa7bfad4.png)
- Flow label:標示該封包為特定類別
- Payload length:IPv6 標頭始終為 40 個八位元組長。 有效負載長度是封包剩餘部分(除了header以外)的長度（以八位元位元組為單位）。
- next header(Protocol):IPv6 有許多下一個標頭，每個標頭透過下一個標頭欄位連結到下一個標頭
- hop limit:最多可以經過幾個router(對應ipv4的TTL)
- Source and Destination Addresses are 128 bits long.
- 跟IPv4相比缺少packet fragmentation，過大的packet不做分割，直接丟掉
- ipv6沒有checksum
## Writing IPv6 Addresses
- IPv4 address:
    - 將 32 位元位址分為四個 8 位元段。
    - 將每個段轉換為十進制數。
    - 在各段之間放置點。
- IPv6 address:
    - 將每 4 位元轉換為十六進位符號(二進位轉十六進位)
    - 以小寫形式書寫字母符號 (a … f)
    - 將 4 個符號組合成一個段
    - 用冒號分隔 4 個符號段
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_20a5bc3649ff543053658a3085aa1dab.png)
## rule to written IPv6 Addresses
- 每段中的前導0可以刪除
==如有整段都是0的可以直接省略，需留下 :==
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d53af5cff861f8c46e4c6b47ba92c985.png)

- 如果存在一組全為零的連續段，則僅保留外部冒號
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4073feed126cc5115e5cc20f4d09589e.png)

- 如果有多於一組連續的全為零的段落怎麼辦？刪除最長冒號中的內部冒號。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_794308ed86e82346ed781bbbfd541641.png)

- 如果最長的全零段組存在平手怎麼辦？刪除第一個冒號的內部冒號
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_42ede5822ca448821ce144210e25db8c.png)

## TCP
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c9ac7be10366150253e8840baea35ea6.png)

- 五層架構中第四層的protocol
- 對訊息做Fragment (message 🡪 segments)，並將segments分開在不同封包傳送
- 每個封包在傳送時都做獨立處理，並給序號(sequence number)註明是第幾個byte
- 支援可靠性(reliable)
- TCP Header : 20 bytes

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7990be22a00d20a1592d556079b82d4d.png)
### Flag fields
- SYN/ACK, FIN :同步與回應、結束
- RST :Reset(緊急情況直接reset)
- PSH :Push(提醒應用層已經把所有訊息傳給TCP、TCP要將完整訊息傳出去)
- URG :(urgent緊急的，設成1時優先給應用層)

## TCP Session Openings and Closings

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_166cbd5679419c9ae1047fb3ff8d1953.png)

- 三向交握:
    - step 1:客戶端向伺服器傳送一個SYN，表達想進行連結
    - step 2:伺服器收到訊息後，如果願意建立連接，會回傳SYN+ACK，ACK表確認收到客戶端發送的SYN，SYN表自己也想要建立連接
    - step 3:客戶端接收到訊息後會回傳ACK作為最後的確認，表示連線已建立完成。




















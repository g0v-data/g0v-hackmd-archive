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
## mask
- problem:僅透過查看IPv4位址本身，是無法直接分辨出網路、子網路和主機部分的大小的。
- ans:要理解一個IPv4位址的組成，你需要知道使用的子網掩碼。子網掩碼指定了網路部分和主機部分的分隔。子網掩碼中的“1”表示網路部分，而“0”表示主機部分。



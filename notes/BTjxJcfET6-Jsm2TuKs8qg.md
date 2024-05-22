# 5/22
[toc]
# ch 09
## IPv4 Subnetting
- If a part has N bits, it can represent 2N - 2 subnets or hosts per subnet.
- 全部都是0或1不算，所以要-2
- 全是1表廣播
- 全是0表未指定地址
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_29c1dbc36ee14be081e3765a59b74bf5.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1093de98d4feea55f8f84b43bfa3550d.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_622401521d7abed0e66f3bf969f942d7.png)



## Private IP Addresses
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_50ffcbd3e8942cd050cde6476f8744b7.png)

- 這些只能在公司內使用 ，永遠不會在互聯網上使用

## Network Address Translation (NAT)
- 在私人網路和公共網路之間轉換ip address
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9b1e3fbbe8e7bb7ce1d9fca52b4c2f9e.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_dd8367551376b07cd903db7944f7539c.png)

- 使用NAT的好處
    - 外部監聽者無法得知內部IP
    - 擴大可用IP地址的數量:一個ip可用的port大約有4000個，假設有248個ip address，表有248*4000個 external connection

## DNS

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b41cf56e07cb4af8a3b00f9934de5b89.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_33c165a7a03f583bc118c7286e891a21.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1b4912daacbc28829fe7d08dab35b2ac.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ea9d4f0f1f3bfaa42c9fad58e1ed2e42.png)

- DNS有層次結構
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0ac6d5e14e55b783e6e06e3212b8a876.png)

## VPNS(虛擬專用網路)
- 一種在公共網路上建立私人網路連接的技術
    1. 建立隧道：在用戶設備和 VPN 服務器之間建立一個加密的通信隧道。
    2. 數據加密：在數據進入隧道之前，使用加密技術對數據進行加密，確保數據在傳輸過程中保密。
    3. 數據傳輸：加密的數據通過公共網路（如互聯網）傳輸到 VPN 服務器。
    4. 數據解密：VPN 服務器接收到加密數據後，對數據進行解密，然後將其發送到目標資源。
### two types of VPNS
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_38588593bb6cdaa34f3c0ef251a9b99c.png)
1. remote access VPN:用戶連接到網站上的VPN Gateway
2. Site-to-site VPN:每個站點都會有VPN保護兩個站點之間的所有流量
## IPsec
- IPsec：IETF 的 IP 安全標準，運行在internet層，保護傳輸標頭、應用程式內容和一些 IP 標頭內容。
- IPsec has two modes (ways) of operating:
    - Transport mode:來源端到目的地端都保護，可以避免Insider(較安全，連防火牆都看不到、cost較高)

    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_144ef94b3610c0515aa3c68450d58d55.png)

    - Tunnel mode:只在Internet有保護，較便宜
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ae9b70dc49fdff8e802d0540d4948d4f.png)
    
## IPv6 Subnetting
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5c0315d2a8f42d586b24809e666fa5c7.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b3c6718cff3187c583ba6578d852e08b.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_91c4dcca2a9e0eba8aef80a80ca4bf99.png)

## Dynamic Routing Protocols
- 通訊必須透過動態路由協定標準化，動態路由協定有多種
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_077796d8ec87e23beec139ec7b977020.png)

## ICMP
- ICMP 提供錯誤建議訊息
- 幫助診斷錯誤
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_dee6d65c3e3fe96f3a20eb4355ccec3b.png)

- request:發送方主機請求測試連通性
- reply:接收方主機響應連通性測試請求

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_307378d8377433f2d557bab00da11a51.png)

- Ping：檢測目標主機的可達性和響應時間。
- Traceroute：追蹤數據包到目標主機的路由路徑，定位網路中的瓶頸或故障點。

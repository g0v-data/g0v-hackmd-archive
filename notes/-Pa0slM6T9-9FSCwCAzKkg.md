# 0309


###  Switch、Router 和 L3 Switch 的差異
1. Switch（交換器）
* 運作原理：
　交換器主要在 OSI 模型的第二層（資料連結層）運作，使用 MAC 位址來轉發資料。
　當交換器收到資料封包時，它會檢查封包的目標 MAC 位址，並在自己的 MAC 位址表中尋找對應的連接埠。
　如果找到對應的連接埠，交換器會將封包直接轉發到該連接埠，實現點對點的資料傳輸。
　如果找不到對應的連接埠，交換器會將封包廣播到所有連接埠，直到目標設備回應。
　交換器透過這種方式建立和維護 MAC 位址表，提高資料傳輸效率。
* 應用場景：
　用於建立區域網路（LAN），連接辦公室、家庭或其他場所的多個設備。
　提高區域網路內的資料傳輸速度和效率，減少網路擁塞。
　常用於需要大量內部資料傳輸的環境，如企業內部網路、資料中心等。

2. Router（路由器）
* 運作原理：
　路由器主要在 OSI 模型的第三層（網路層）運作，使用 IP 位址來轉發資料。
　當路由器收到資料封包時，它會檢查封包的目標 IP 位址，並在自己的路由表中尋找最佳路徑。
　路由表記錄了到達不同網路的路徑資訊，路由器根據路由表將封包轉發到下一個路　由器或目標網路。
　路由器負責選擇最佳路徑，實現跨網路的資料傳輸。
　路由器還具有網路位址轉換（NAT）和防火牆等功能，增強網路安全性和靈活性。
* 應用場景：
　用於連接不同的網路，如區域網路、廣域網路（WAN）和網際網路。
　實現跨網路的資料傳輸，如家庭網路連接網際網路、企業網路連接不同分部。
　用於需要網路安全和流量管理的環境，如企業網路、資料中心等。

3. L3 Switch（第三層交換器）
* 運作原理：
　L3 Switch 結合了交換器和路由器的功能，既能進行高速的 MAC 位址轉發，又能進行 IP 位址路由。
　L3 Switch 具有硬體路由功能，可以實現高速的路由轉發，比傳統路由器更快。
　L3 Switch 常用於大型區域網路中，實現 VLAN 間的路由和高速資料傳輸。
* 應用場景：
　用於大型區域網路，實現 VLAN 間的路由和高速資料傳輸。
　提高區域網路內的路由效率，減少網路延遲。
　常用於需要高性能路由的環境，如企業內部網路、資料中心等。

---

| 特性 | Switch（交換器） | Router（路由器） | L3 Switch（第三層交換器） |
| -------- | -------- | -------- | -------- |
| 主要功能 | 區域網路內的資料傳輸 | 不同網路之間的資料傳輸 | 區域網路內高速路由與交換 |
| 工作層次 | OSI 第二層（資料連結層） | OSI 第三層（網路層） | OSI 第二層與第三層 |
| 資料轉發依據 | MAC 位址 | IP 位址 | MAC 位址與 IP 位址 |
| 主要用途 | 建立區域網路 | 連接不同網路，包括網際網路 | 高速區域網路路由 |
| 傳輸速度 | 非常快速 | 相對較慢 | 非常快速 |
| 路由能力 | 無 | 有 | 有 |
| 應用場景 | 辦公室、家庭內部網路 | 家庭網路連接網際網路、企業網路連接不同分部 | 大型企業網路、資料中心 |


---
## show interface

![](https://g0v.hackmd.io/_uploads/S1HW8d9sJx.png)


---


## show ip interface
指ipv4的顯示介面

![](https://g0v.hackmd.io/_uploads/rkyUUO5jJe.png)

access list 沒有設置流量


---

## show ipv6 interface

顯示ipv6的顯示介面

![](https://g0v.hackmd.io/_uploads/SklJ3Ld9i1x.png)

沒有顯示FF02::2
代表沒有開放路由使用




---

##B2

![](https://g0v.hackmd.io/_uploads/ryGSk9cjye.png)

 侏儒訊框 RUNTS
 巨人訊框 GIANTS
 碰撞 collision
 延遲碰撞 Late collision

----

## SSH支援

![](https://g0v.hackmd.io/_uploads/HJLYg5qskg.png)

使用show version 來確認
要有包含 K9 內容的組合

---

## SSH 設定

![](https://g0v.hackmd.io/_uploads/SJKtWcqsJg.png)

非對稱用來保護對稱式的key
對稱式預先產生key
非對稱key
唯一主機+網域名稱

使用指令生產RSA金鑰
*#crypto key genrate
設置 1024 bit 以上
會跳欄位詢問要輸入多少bit
*刪除指令 #crypto key zeroize rsa


*transport input ssh 就只可以使用SSH連線
*login local 要求使用本地的使用者資料庫進行身分驗證

*範例
![](https://g0v.hackmd.io/_uploads/HJbMmqcjyl.png)
![](https://g0v.hackmd.io/_uploads/HkVrtc9jJx.png)

-顯示ssh資料
show ip ssh

-顯示ssh連線資料
show ssh

---

*電腦連接過去
![](https://g0v.hackmd.io/_uploads/Bk9WY59s1l.png)

c> ssh -l 使用者名稱 ip位址
後面有設置的話就會跳密碼輸入位
再輸入密碼

---

VLAN類型

![](https://g0v.hackmd.io/_uploads/SJxL4135syl.png)

VLAN1
在SVI介面存在
作為預設的管理介面

CISCO
預設
1002-1005 無法刪除

![](https://g0v.hackmd.io/_uploads/ryZmlhqiye.png)

---

## CLI（Command-Line Interface，命令列介面）/interface跟line控制

1. interface 控制：

* 定義：
　interface 控制用於配置網路設備的物理或邏輯介面。這些介面是設備與網路連接的點，例如乙太網路連接埠、序列連接埠或虛擬區域網路（VLAN）。
* 功能：
　配置介面的 IP 位址、子網路遮罩、速度、雙工模式等網路參數。
　啟用或停用介面。
　配置路由協定、存取控制清單（ACL）等網路功能。
* 應用：
　設定路由器或交換器的連接埠，使其能夠與其他網路設備通信。
　配置 VLAN，以劃分網路並提高安全性。
　設定路由，以控制網路流量的流向。
* 舉例:
　interface GigabitEthernet0/1：進入GigabitEthernet0/1這個介面的設定模式。
　ip address 192.168.1.1 255.255.255.0：設定介面的IP位址。
　shutdown：關閉介面。
　no shutdown：開啟介面。

2. line 控制：

* 定義：
　line 控制用於配置 Cisco 設備的虛擬終端機線路，這些線路允許管理者透過不同的方式（如主控台、Telnet 或 SSH）存取設備的 CLI。
* 功能：
　設定使用者登入設備的密碼。
　配置登入超時時間。
　設定存取控制，以限制哪些使用者可以存取設備。
* 應用：
　保護設備免受未經授權的存取。
　管理遠端存取設備的使用者。
　設定連線方式。
* 舉例:
　line console 0：進入主控台線路的設定模式。
　line vty 0 15：進入虛擬終端機線路（Telnet/SSH）的設定模式。
　password cisco：設定登入密碼。
　login：啟用密碼驗證。
　transport input ssh：限制線路只接受ssh連線。
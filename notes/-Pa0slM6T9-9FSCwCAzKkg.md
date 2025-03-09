# 0309


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

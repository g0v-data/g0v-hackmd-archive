---
title: "立法院議場網路 SSL MITM 訊息澄清"
tags: CongressOccupied,cyberwar,hackpad
---

# 立法院議場網路 SSL MITM 訊息澄清

> [點此觀看原始內容](https://g0v.hackpad.tw/aZNHYZ3GsHW)


### 摘要


抗議人士反應現場網路連結 Facebook 時，出現憑證錯誤訊息。目前判斷是由於院內網路憑證過期，被重新導向到登入網站。由於登入網站使用的 SSL 憑證與 Facebook 不同，所以出現了錯誤警告訊息。解決方式使連到任何一個未加密的 http 網站，會進入登入系統，隨意填入空白資料後即可繼續上網。

但請注意，**務必不要**填入其他人的個人資料，以免觸犯刑法第  358 條「無故輸入他人帳號密碼」罪責。

#### _尚無明顯證據顯示公部門__以__監聽__方式，__竊取現場抗議民眾資料__，或篡改網站內容__。 _


### 細節


立法院議場二樓提供有線網路與無線網路供媒體或民眾使用，為了安全控管因素，第一次上網以及每二十四小時會被導引到無線網路登入系統 (Captive Portal [https://en.wikipedia.org/wiki/Captive_portal](https://en.wikipedia.org/wiki/Captive_portal))。需填入個人資料後申請開通，但登入網站並無實際審查，輸入任何資料都可以立即開通網路。

認證機制實作的方式利用 DNS redirection [https://en.wikipedia.org/wiki/DNS_hijacking](https://en.wikipedia.org/wiki/DNS_hijacking)，若該臺電腦 (依照網路卡 MAC ID 確認)尚未上網認證，則所有網域名稱查詢會指回 172.16.198.228 登入網站

```
Starting Nmap 6.40 ( http://nmap.org ) at 2014-03-21 07:06 CST
Nmap scan report for 172.16.198.228
Host is up (0.00088s latency).
Not shown: 988 closed ports
PORT      STATE SERVICE
80/tcp    open  http
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
1025/tcp  open  NFS-or-IIS
1028/tcp  open  unknown
1030/tcp  open  iad1
3071/tcp  open  csd-mgmt-port
3306/tcp  open  mysql
3389/tcp  open  ms-wbt-server
49152/tcp open  unknown
50000/tcp open  ibm-db2
MAC Address: 00:1E:67:09:A7:F9 (Intel Corporate)
Device type: general purpose
Running: Microsoft Windows XP|2003
OS CPE: cpe:/o:microsoft:windows\_xp::sp2 cpe:/o:microsoft:windows\_server\_2003::sp1 cpe:/o:microsoft:windows\_server_2003::sp2
OS details: Microsoft Windows XP SP2 or Windows Server 2003 SP1 or SP2
Network Distance: 1 hop

OS detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 15.57 seconds

```
院內只開放唯一 DNS 伺服器 (10.12.8.3) 以 UDP Port 53 連到外部網域名稱伺服器，因此使用者無法使用自訂的名稱伺服器。

### 網路安全建議

雖然沒有證據顯示公部門監聽網路使用或使用 MITM 中間人攻擊，但為了安全因素，建議通訊加密
- 網頁加密技術
    - Firefox 使用者請安裝 HTTPS Everywhere  - [https://www.eff.org/https-everywhere](https://www.eff.org/https-everywhere)
    - Chrome 使用者請安裝 KB SSL Enforcer \- [https://chrome.google.com/webstore/detail/kb-ssl-enforcer/flcpelgcagfhfoegekianiofphddckof](https://chrome.google.com/webstore/detail/kb-ssl-enforcer/flcpelgcagfhfoegekianiofphddckof)
- 加密通訊
    聯絡不使用 SMS, Line, WeChat, WhatsApp. 建議採用開放源碼的 Telegram
    - [https://telegram.org/](https://telegram.org/)
    - iOS - Telegram Messenger on the App Store on iTunes [https://itunes.apple.com/us/app/telegram-messenger/id686449807?mt=8](https://itunes.apple.com/us/app/telegram-messenger/id686449807?mt=8)
    - Android - Telegram - Google Play Android 應用程式 [https://play.google.com/store/apps/details?id=org.telegram.messenger](https://play.google.com/store/apps/details?id=org.telegram.messenger)
    - Web - [http://zhukov.github.io/webogram/](http://zhukov.github.io/webogram/)
- 電子郵件請使用 GNUPG 加密 [http://www.gnupg.org/](http://www.gnupg.org/)
- 盡可能全程使用 VPN

### 參考

- 蔡志展 \- 在立法院周圍或議場內部上網的朋友，請安裝 EFF 的 HTTPS Everywhere, 他會自動使用 SSL... [https://www.facebook.com/chihchun/posts/10152347405987915?notif_t=like](https://www.facebook.com/chihchun/posts/10152347405987915?notif_t=like)
- Hong Yu Lin - 動態時報相片 [https://www.facebook.com/photo.php?fbid=10152986312632524&set=a.187162337523.159469.788597523&type=1](https://www.facebook.com/photo.php?fbid=10152986312632524&set=a.187162337523.159469.788597523&type=1)
- 在 Linux 上移除 CNNIC 憑證 [http://blog.nutsfactory.net/2010/02/02/remove-cnnic-cert-on-linux/](http://blog.nutsfactory.net/2010/02/02/remove-cnnic-cert-on-linux/)

### 原始作者

Rex Tsai <rex.cc.tsai@gmail.com> [http://www.facebook.com/chihchun](http://www.facebook.com/chihchun)


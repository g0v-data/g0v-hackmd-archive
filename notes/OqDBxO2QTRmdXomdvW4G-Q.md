# 去中心化 solution 之點對點傳播
如果阿共啊打過來，網路都斷訊了，我們怎麼辦

## 過去的討論
在會場中建立可靠的訊息傳遞網路
情境問題
一般民眾：現場網路不通

專案目標
在萬人環境下可運作
解決對內/對外資訊傳播問題
提供Lib 支援其他g0v專案使用
使internat資料的取用像是吃下了過期春藥具有以下特性
惡劣的網路環境耐受性：網路中斷時，資料仍可透過外圍節點向內部提供
快速傳播資訊更新

實作方式
對內傳送
靜態網頁像是hackfoldr可以作為git trunk在節點間更新與同步
主節點，負責從internat pull git repo、推送給大量節點
主節點的條件：有充電、網路暢通
推送給多少個節點?
可能透過群播方式？
沒有充電的節點，被動更新、推送給較少節點
低電量節點，以較長間隔檢查更新
對外傳送
(犧牲整體網路速度)確保消息隨時可對外傳播不會中斷
透過wifi、藍芽動態連線建立隨意路由、減少隨意網路對外(3G、4G行動網路)連線數以減輕行動網路負擔
提供Android、iOS 平台支援
iOS 平台無法控制系統資源，如果單純透過 APP sandbox 的作法，也許只能透過 bluetooth or P2P 的方式達成網路共享，但是缺點是需要透過該網路的功能都必須內建在此 App，似乎不是終極解決之道。
App 使用者可以作為wifi熱點分享給其他沒有安裝的人
Android HotSpot 有人數上限: 5人
rsync 資料同步
http://rsync.samba.org/download.html
http://gimite.net/en/index.php?Run%20native%20executable%20in%20Android%20App
目的是要解決同步資料時的不完整性，理論上可做到各節點間同時是發送端也是接收端

可能應用
用git在會場同步需要擴散的網頁資料，
支援會場中民眾以點對點/群組方式互相通訊與傳輸檔案
支援會場後勤管理人員資訊彙整
做得像Pushbullet，緊急呼叫可以全面通諜(mail/irc/IM/透過周圍的人XD)該目標人員
配合GPS定位回報
時呈現群眾分布情況
支援網頁呈現地圖
突發事件回饋按鈕(警察有動作、有人受傷需要醫療支援、需要糾察人員支援)
GPS定位以及加速度感應相關sensor開啟時，電力消耗較大，必須考慮電力耗損問題。（會場的手機有蠻高比例得不到穩定的充電來源，所以要考慮省電）
在解決了前面幾點提到的建立手機間通訊方式的前提下，可以考慮以輪班＼隨機等方式，決定開啟手機本地端GPS Tracker, motion detector的時機。
例如有3000台手機加入了，APP間互相協調，同時只有100台需要輪值開啟motion detector，但當緊急狀況發生，APP會互相通知，3000台的motion detector此時同時打開並且回報。
配合加速度感應元件
凸顯群眾集體移動事件(遭到警方鎮壓/驅趕？)




Refs
* 製作遊行現場可以暢通的網路系統（自幹ＩＭ系統） （2013-8-19_考察紀錄）
* 吃鋰電池的基地台（Ir-clog ）
* opengarden
* Open Garden 串連所有連網設備，大家可以分享和共用頻寬（FireChat 是由Open Garden 利用其技術所開發出來的iOS 平台傳訊軟體）
* FireChat
** 手機沒訊號也可傳訊息，FireChat 怎麼辦到的？
* Qaul.net
* 之前2012年Ars Electronica國際新媒體藝術節有贊助一個很類似的project叫做Qaul.net，是因應阿拉伯之春時網路被國家斷網所以寫的，也許可以參考。目前做法是讓每個行動裝置都可以成為網路的一個節點，互相通訊與傳輸檔案。目前還在Beta版，可以參考這個網址： http://www.qaul.net/software.html
* 3/22 的 moed2ct 萌典第二次黑客松：即時文字轉播 有為 #congressoccupied 反黑箱服貿佔領立法院運動，測試 Firechat，但未知現場工作人員應用後的使用經驗如何。
* BitTorrent Sync
* https://api.search.g0v.io/?q=firechat

---
title: "X86型車載路由器兼UTM"
tags: hackpad
---

# X86型車載路由器兼UTM

> [點此觀看原始內容](https://g0v.hackpad.tw/U2Dd3HcSqG8)


(應付更多的攻擊和惡劣的環境) 本專案將可做為[此專案](https://g0v.hackpad.tw/lk9pamtKwyr)  的延伸


> 要不要考慮把這個視為[這](https://g0v.hackpad.tw/jgLrXNuSB33)個的子專案？
> [name=Pc C]

> 怎麼視為子專案呢? 因為我才剛碰HACKPAD不太會用
> [name=許正昇]

> 直接移到那邊去討論之類的… 我的意思是跟那個去配合
> [name=Pc C]

> OKOK 但要怎麼轉呢?  我覺得我需要適應HACKPAD
> [name=許正昇]

> 怎麼發言啊  拜託
> [name=許正昇]

> 請問一下這個路由器的Uplink是走哪種線路出去的？
> [name=波卡Poka]

> 1.  3G/4G (USB萬能)  2.光纖
> [name=許正昇]

> 3G/4G可能還要查證  但光纖一定行  
> [name=許正昇]

> 如果Uplink是3G / 4G，那麼使用一般Router接上Uplink和使用x86的Router的優勢在哪邊？
> [name=波卡Poka]

> 我如果是攜帶設備的人員，一般的Router相比這台設備來的更方便易用
> [name=波卡Poka]

> 可以再說清楚點嗎   
> [name=許正昇]

> 一台AP本來就不是設計給200-300人使用，換個說就是想要一台設備解決這個問題就連企業等級的AP都有一定的困難。3G/4G上下傳頻寬本來就小了，你會希望在這台設備上面放幾個Client？
> [name=波卡Poka]

> 真的假設100個人都放到這台AP上面，大家分到的頻寬有多小Orz
> [name=波卡Poka]

> 若是直接接光纖，現場設備光電轉換器、Router和Layer2 Switch可以解決這個問題，只要有正確設定。
> [name=波卡Poka]

> 我想要了解一下標題寫的「攻擊」和「惡劣環境」的範圍和情境，方便列一下嗎？
> [name=波卡Poka]

> 惡劣環境  比如說 沒發電機   
> [name=許正昇]

> 那你覺得該怎麼做比較好  因為本人才剛踏入電腦因為本人才剛踏入電腦這塊3-4年 有很多需要學習
> [name=許正昇]

> 先了解一下線路相關的背景知識，還有可以看看這篇：[2014 03 08 ](https://g0v.hackpad.tw/jG9uno4d9H8) 和這篇 [g1v.tw ](https://g0v.hackpad.tw/2KWlYWGfr7I) ，很多時候除了硬體和頻寬的限制，最大的限制是使用環境和可用的預算
> [name=波卡Poka]

> 真的要幾千人到幾萬人的Solution我相信做得出來，只是這樣如果要花1000k以上（無誤）你願意嗎？
> [name=波卡Poka]

> 在合理的範圍提供網路，有線網路與無線網路分別都有適用的環境，在無線網路的天線方面著手也是一個方向
> [name=波卡Poka]

> 我說的是Solution解決方案，1000K很正常啊，ThinAP搭配Controller架構XD
> [name=波卡Poka]

> 樓上+1   真的，這個計劃是可以實行，但是應該是拿來做[這個](https://g0v.hackpad.com/jgLrXNuSB33)的外圍AP用。
> [name=Pc C]

> 如果是跟一般router一樣基本上就是無用了
> [name=Pc C]

> 恩 的確  如果把它拿來做一般的ROUTER就太可惜了   好吧  就跟[這個](https://g0v.hackpad.tw/jgLrXNuSB33) 結合吧  但我不知道對方會不會採用
> [name=許正昇]

> 但車載這部分就有勞大大們去實作了 我是一個剛要升高一的學生 經濟能力不夠啊    然後延伸的專案【腳踏車載AP兼擴音器】 這專案我負擔的起  我就先做出來
> [name=許正昇]

> 還是直接改裝成UTM 
> [name=許正昇]


小弟目前正在研究如何讓精簡型客戶端變成無線路由器，讓下次圍總統府時有更好的安全和網路體驗，目前分析的優缺點如下
建議專案和目的分開，"不因特定目的"才會有更多的人投入。
優點
1.擴充性大
一個Router會想要擴充什麼功能
> 記憶體
> [name=許正昇]

> 32MB或是64MB夠用就好擴充Ram幹嘛....
> [name=波卡Poka]

> 真的夠嗎?!
> [name=許正昇]

> 聽說記憶體跟連線數有很大的關係
> [name=許正昇]

2.安全
> 安全性取決與良好的設定，要不要說明一下這個「安全」是針對哪個方面？
> [name=波卡Poka]

> 更進階的防火牆 和更進階的防毒閘道
> [name=許正昇]

> 防火牆不是應用在這個層面啊，提供網路的立場，我們不應該去試著阻絕外部服務，可以做限流、QOS等處理方式，但是主動是防火牆你想要偵測哪種攻擊行為？
> [name=波卡Poka]

> 是沒錯   但我們面對的是國家級攻擊，不守
> [name=許正昇]

> 直接把你的車吊走或是拔掉源頭不就好了，哪需要那麼麻煩.....
> [name=波卡Poka]

> 「國家等級的攻擊行為」還是沒有說清楚是「什麼」攻擊型態.
> [name=波卡Poka]

> 抱歉     搞錯東西  車是可以移動
> [name=許正昇]

> 沒有人會把網站放在車上.....
> [name=波卡Poka]

> 比如說竊取封包 然後解析封包內容  盜用網路身分?
> [name=許正昇]

> 你用任何一種網路架構都會有上面的問題啊....
> [name=波卡Poka]

> 無線網路傳輸本來就是broadcast，和你想要做的X86沒有關係，自己用無線網路的時候記得要用https或是打VPN通道才是解法...
> [name=波卡Poka]

> 如果想要避開上面的問題，用有線網路也只能減少被竊取的機會，但是還是要使用端點加密不然無解
> [name=波卡Poka]

> 別忘了X86無敵阿，可以加防毒閘道阿
> [name=許正昇]

3.彈性大
> 同_上，哪方面的「彈性」？_
> [name=波卡Poka]

> _隨時改裝隨時用_
> [name=許正昇]

> _那和我直接拿一台TPlink刷DDwrt直接上的差別？後者刷機時間還比較快耶.....XD_
> [name=波卡Poka]

> _但電腦並不是都只剩下路由功能阿，稍微˙重灌還可以做其他事情_
> [name=許正昇]

> 那就會回到上面的第一點，一個Router應該就乖乖做Router的事情，把其他的功能切去給其他系統做。
> [name=波卡Poka]

> 這樣有非網路問題排修（ex: 系統因為影音直播沒有回應等），也不用讓包含整個網路停掉或是重新啟動。
> [name=波卡Poka]

> 還這樣好了，車載先做有線路由，然後在接上一部無線路由，不知道效果怎樣
> [name=許正昇]

> 效果就和你平常用的一樣啊，車載不過就只把DC in改成從車用電瓶啊，直接找12V的不就好了，電線接上去就直接上了XDDDD
> [name=波卡Poka]

> 對好處就在這裡
> [name=許正昇]

> 那如果直接用既有設備，連改都不用改啊XD?
> [name=波卡Poka]

> 但移動不方便阿
> [name=許正昇]

> 既有設備指的是已經存在的Router，不是x86改機....只要設備吃12V DCIN，就可以直接用
> [name=波卡Poka]


4.比高階路由器便宜
缺點
1.比一般路由器貴
2.攜帶不方便
3.需要技術人員來設定
4.需要電12V 5A(這部分可能要交給懂車的朋友了 直接變車載)


而所謂的精簡型客戶端就是使用INTEL ATOM VIA C7M這種處理器，至於有使用i5/i7就不用講 太貴了，然後硬碟很小2-64GB

系統就用BFW

## 要解決的問題

### 目前需要克服的難題

1\. 車輛改裝後的安全性問題EX:火燒車

2.比一般路由器貴

3.攜帶不方便

4.需要技術人員來設定

5.需要電12V 5A(這部分可能要交給懂車的朋友了 直接變車載)
##

### 衍生的專案


衍生出腳踏車載擴音器和WIFI點(只使用一般AP 非x86路由器)和遙控飛機型路由器     這兩種載體載的都是純WIFI AP並不是使用X86路由器
##

目前已經討論到雛形(可以做幾部機器出來操)

Router / Firewall OS List：
[http://en.wikipedia.org/wiki/List\_of\_router\_and\_firewall_distributions](http://en.wikipedia.org/wiki/List_of_router_and_firewall_distributions)

## 目標與功能（要如何解決）

### 預定功能


提供防火牆和防毒閘道，整合WIFI AP(可以使用純WIFIAP取代)
> 直接 pfSense 解決?
> [name=波卡Poka]


### 預定使用者

1.在WIFI車附近的群眾

2.工作人員的網路變安全˙，防止病毒 木馬入侵

## 徵求協作者

### 分工與成員

- [x] NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
- [x] NeedsDesigner: 需要介面設計
- [x] NeedsData: 需要資料（擷取、清理）
- [x] NeedsTech: 需要技術支援（程式、架站 etc)
- [x] NeedsProcess: 需要幫忙設計作業流程
- [x] NeedsMoney:需要金援

## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿)


### 雛形


使用桌上型電腦做為雛形，有時間的話應該會一一把主流的路由系統都測過一遍，配備如下。
HDD: Lexar 4GB CF+ IDE轉接卡

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fc31687a8a54809ed067203c68d21e54)



![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0d2e47a2c4a9843c6a5969135afcea09)

MB+CPU: ASUS P5Q-EM D0(OEM)+ E8200
RAM: Apacer DDR2 800 1GBX2
NIC: Intel PRO/1000 PT 9402PT DualPort + Intel 82567LM Gigabit LAN controller + Intel Pro/1000 82540EM

### 使用樹梅派改裝?


這個 [Controlller和AP教材.doc](http://waoffice.ee.kuas.edu.tw/download/%E5%AE%B6%E6%94%BF%E7%A0%94%E7%A9%B6%E6%89%80%E8%B3%87%E6%96%99/Aruba%20%E6%95%99%E6%A1%88/Controlller%E5%92%8CAP%E6%95%99%E6%9D%90.doc)
文件給大家參考 是不是如此一般 sorry 我不太會用這東西討論 如有需要移動或刪除請 管理人員直接處理
Overview | Setting up a Raspberry Pi as a WiFi
[https://learn.adafruit.com/setting-up-a-raspberry-pi-as-a-wifi-access-point/overview](https://learn.adafruit.com/setting-up-a-raspberry-pi-as-a-wifi-access-point/overview)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0a42c54161e42399046c6e17748b111d)
[https://learn.adafruit.com/system/assets/assets/000/009/048/medium800/raspberry\_pi\_pi_ap.jpg?1396881587](https://learn.adafruit.com/system/assets/assets/000/009/048/medium800/raspberry_pi_pi_ap.jpg?1396881587)
[https://learn.adafruit.com/downloads/pdf/setting-up-a-raspberry-pi-as-a-wifi-access-point.pdf](https://learn.adafruit.com/downloads/pdf/setting-up-a-raspberry-pi-as-a-wifi-access-point.pdf)
安裝說明 Raspberry Pi 才讓各參加的學生以後除了可自制需求的路由器 也可日後在業界中直接來接軌
Raspberry Pi 是公版 也可以自己變化發展 私用版本

### 四種方法來轉換舊的PC變成一ZZZASX

[http://www.practicallynetworked.com/networking/convert\_old\_pc\_to\_new_router.htm](http://www.practicallynetworked.com/networking/convert_old_pc_to_new_router.htm)
忘記把這一篇po在這  裏面有許多寶石資料 可以協助你們 開發選用的基本思維
DD-WRT X86  有不少硬體是可相容他的基本設計
[http://blog.cscworm.net/?p=4500](http://blog.cscworm.net/?p=4500)
[http://killvirus.org/index.php?topic=1545.0](http://killvirus.org/index.php?topic=1545.0)
[http://aimojay.blogspot.tw/2012/02/asus-n12-dd-wrt.html](http://aimojay.blogspot.tw/2012/02/asus-n12-dd-wrt.html)

[https://www.youtube.com/watch?v=xr0VkuZL-Dc](https://www.youtube.com/watch?v=xr0VkuZL-Dc)
上述的四種方法 請參考看看

[http://jp.techcrunch.com/2014/04/23/tc-hackathon-osaka-report/?fb\_action\_ids=594847460610578&fb\_action\_types=og.likes](http://jp.techcrunch.com/2014/04/23/tc-hackathon-osaka-report/?fb_action_ids=594847460610578&fb_action_types=og.likes)
[https://www.indiegogo.com/projects/pocketduino-innovation-from-your-pocket#home](https://www.indiegogo.com/projects/pocketduino-innovation-from-your-pocket#home)

[https://www.youtube.com/watch?v=rcPYUjs_fJg#t=24](https://www.youtube.com/watch?v=rcPYUjs_fJg#t=24)


### [DIY平板電腦-主機板篇](https://g0v.hackpad.tw/bGOjFtkTlmh#DIY平板電腦-主機板篇)並且改成想要的功能


轉貼自Coolaler論壇的 [**rrimera**](http://www.coolaler.com/member.php/104054-rrimera)**大大**

之前我家小白的車載電腦從第一代的P-M PANEL PC進化到第二,第三代1DIN的1.66 GHz雙核心,
本來想說跑跑GARMIN導航,跟我家小白溝通就已夠用了,
後來看到INTEL出了超薄主機板,這時我想到小白第一代的PANEL PC厚度有6CM,
如果用超薄主機板做成PANEL PC不就接近平板電腦了嗎?
本來也想賣掉手中的車載電腦換成平板電腦,可是可跑WINDOW系統的平板電腦便宜的大部分CPU太弱,
ATOM的雖然比較便宜,可是效能就算了,C2D的又貴得要死
所以想說來DIY好了
> 用這個？ [http://goods.ruten.com.tw/item/show?21402171612568](http://goods.ruten.com.tw/item/show?21402171612568)
> [name=波卡Poka]

是可以 但不知道支不支援lvds，不支援的話就還要接vga螢幕(不然看看支不支援vnc)


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_45a79ee677be52b25626e230d3e15be8)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_bdb926ac0ba5b21c5ad3f28979c98213)


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f60b868236a291b48b4aeadce2ed8020)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_21bd08bdf59c8d67c7ce12a58f208518)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_bd7fc1bec27868ab9b2149918270344d)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_88f051179453b41e2876a4e4792cca5a)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f63d6ac6f6da1f9bb58f13c3c8bd9de6)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_727079788dcf53d6cf4ad187e6b8424e)
[http://www.coolaler.com/showthread.php/298911-DIY%E5%B9%B3%E6%9D%BF%E9%9B%BB%E8%85%A6-%E4%B8%BB%E6%A9%9F%E6%9D%BF%E7%AF%87](http://www.coolaler.com/showthread.php/298911-DIY%E5%B9%B3%E6%9D%BF%E9%9B%BB%E8%85%A6-%E4%B8%BB%E6%A9%9F%E6%9D%BF%E7%AF%87)

### 使用Android棒改刷其他韌體

用這主機板 只會浪費資源 因為是PC的 尤如以前的 car pc  如只是过渡開發時期 還可以 要當server一定不行
使用 草梅派 主要是把server架成分散的架構 因為是崁入式系統 由Linux或戴維斯 跑單晶片 分工模式 比PC穩定
資源損耗較pc小 以單純的工作來說 才變的比pc更穩定
買 中國製的 mk802 差不多1800元就取代這塊板了 以安卓的功能來說+ 無線鍵盤

[https://www.youtube.com/watch?v=ANhkYF7PEss](https://www.youtube.com/watch?v=ANhkYF7PEss)
[http://chen6721.pixnet.net/blog/post/47258438-mk802%E9%96%8B%E7%AE%B1%E6%96%87android\_minipc\_2](http://chen6721.pixnet.net/blog/post/47258438-mk802%E9%96%8B%E7%AE%B1%E6%96%87android_minipc_2)
MK802是一台對岸做的迷你Android多媒體播放合(反正就類似TV box之類的產品)
[http://dl.dropboxusercontent.com/u/61164954/homepage/mk802/index.htm](http://dl.dropboxusercontent.com/u/61164954/homepage/mk802/index.htm)

[https://www.miniand.com/products/MK802%20Android%20Mini%20PC](https://www.miniand.com/products/MK802%20Android%20Mini%20PC)


[https://www.youtube.com/watch?v=19X0anqR_rM](https://www.youtube.com/watch?v=19X0anqR_rM)
這改裝有困難性，但可以試試看
其實他不困難拉 就如刷機樣 但你要自己加程式或軔體才困難
Android Mini PC MK-802 刷機教學
[http://zakipush.blogspot.tw/2012/08/android-mini-pc-mk-802.html](http://zakipush.blogspot.tw/2012/08/android-mini-pc-mk-802.html)
[如何在MK802迷你電腦電視盒上運行Ubuntu Linux操作系統](http://www.buydvb.net/blog/how-to-run-ubuntu-linux-on-the-mk802-mini-pc-tv-box.html)
[http://www.buydvb.net/blog/how-to-run-ubuntu-linux-on-the-mk802-mini-pc-tv-box.html](http://www.buydvb.net/blog/how-to-run-ubuntu-linux-on-the-mk802-mini-pc-tv-box.html)
因為他是中國製的 我不太想po這產品 不過他與 草梅比 不論金額或功能都有的比
其中 不論是 PC主機版或mk802 或草媒 要大流量使用 注意散熱問題
汽車上使用 CAR pc主機版 電源要除了ACC接 還要穩壓突波 使用省電的草媒或mk802 由點煙器接
但如要發動車時 仍建議加設直流的穩壓限流器 以免啟動電流突波早成電子零件 壽命過短
限流也可以找LED的相關周邊配件

新Rikomagic MK902 - 四核安卓電腦 - 8GB閃存
[http://www.cloudsto.com/android-mini-pc-s/rikomagic-mk902-quad-core-8gb-flash-dhl-express-shipping-detail.html](http://www.cloudsto.com/android-mini-pc-s/rikomagic-mk902-quad-core-8gb-flash-dhl-express-shipping-detail.html)
[http://www.cloudsto.com/android-mini-pc-s/rikomagic-mk902-quad-core-16gb-flash-dhl-express-shipping-detail.html](http://www.cloudsto.com/android-mini-pc-s/rikomagic-mk902-quad-core-16gb-flash-dhl-express-shipping-detail.html)
想不到902出這樣快

> [g8v.tv](https://g0v.hackpad.tw/lk9pamtKwyr) 這的網址 建議看深入點 可能會有意外的收獲  路由器 過渡期 使用dd WRT來刷 找可刷的牌子 如華碩等很多
> [name=Jack S]

> 但問題是我覺得他們的硬體都被鎖死，無法擴充升級
> [name=許正昇]



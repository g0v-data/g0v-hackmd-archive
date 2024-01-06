---
title: "適合正式場合的網路直播：方案組合、場地規劃、網路設定、器材選購與外包資源列表"
tags: hackpad
---

# 適合正式場合的網路直播：方案組合、場地規劃、網路設定、器材選購與外包資源列表

> [點此觀看原始內容](https://g0v.hackpad.tw/c4hIuYG6gAV)

文件授權： CC BY all contributors

### TL;DR: 結論


不求品質的素人直播很容易上手，但要求品質的正式場合的直播需要投資器材、根據個案規劃適合的方案，如果內部不是經常有活動要自己直播，建議外包


### 各種參考資料，還沒整理

[http://etblue.blogspot.tw/2015/06/g0vtw-hackath14n.html](http://etblue.blogspot.tw/2015/06/g0vtw-hackath14n.html)
[https://g0v.hackpad.com/--PTFbdcOTdSZ](https://g0v.hackpad.com/--PTFbdcOTdSZ) 線路松空白模版
[1024 ](https://hackpad.com/PyetfW6jtPf)
[https://g0v.hackpad.com/g0v-YouTube-Live-Windows-DV-yQm4e4nbRqV](https://g0v.hackpad.com/g0v-YouTube-Live-Windows-DV-yQm4e4nbRqV)
[https://g0v.hackpad.com/iPadUstream-tDeV59HdAa4](https://g0v.hackpad.com/iPadUstream-tDeV59HdAa4)
[https://g0v.hackpad.com/e2uv6HB47HT](https://g0v.hackpad.com/e2uv6HB47HT)
[https://g0v.hackpad.com/GsPtGlyEX9q](https://g0v.hackpad.com/GsPtGlyEX9q)
[https://g0v.hackpad.com/XB5JOWTtnly](https://g0v.hackpad.com/XB5JOWTtnly)
[https://g0v.hackpad.com/ADYWtwNY3zN](https://g0v.hackpad.com/ADYWtwNY3zN)
[https://g0v.hackpad.com/2014-03-08--jG9uno4d9H8](https://g0v.hackpad.com/2014-03-08--jG9uno4d9H8)
[https://g0v.hackpad.com/iPadUstream-tDeV59HdAa4](https://g0v.hackpad.com/iPadUstream-tDeV59HdAa4)
[https://g0v.hackpad.com/-iPad--Tbh26PIxbwW](https://g0v.hackpad.com/-iPad--Tbh26PIxbwW)
[http://febon.blogspot.com/](http://febon.blogspot.com/)

## 直播方案選項


### 方案一、從攝護線 Stella / Yutin 那邊聽到的夢幻懶人版，新版直播盒疑似開發中

DV鏡頭+DV麥克風→傳輸線→夢幻懶人直播盒→有線(?)網路→YouTube Live
- 那個夢幻懶人直播盒目前還是個謎，感覺應該是新出來的東西，沒時間好好研究的話可能不太敢跳下去用

### 方案二、==高==畫質==高==音質==高== FPS ==高==穩定度標準版

DV鏡頭+DV麥克風→傳輸線→擷取卡→傳輸線→筆電中控程式→有線網路→YouTube Live
- 條件許可的話最推薦用這個組合

### 方案三、==高==畫質==高==音質==中== FPS ==低==穩定度陽春版

iPad/iPhone鏡頭→Wirecast Cam程式→區域無線網路→筆電中控程式+外接麥克風→無線網路→YouTube Live
- 這是平常我在 g0v 大松的作法，因為訊號全部要透過 WiFi，所以無線頻擁擠的話就會跳格或馬賽克，所以不太適合用在正式大型活動的官方直播，上次新書發表會之所以這樣用是因為實在太趕了，沒辦法 lol

### 方案四、==低==畫質==高==音質==高== FPS ==高==穩定度克難版

Webcam鏡頭→USB線→筆電中控程式+外接麥克風→有線網路→YouTube Live
- 追求穩定度但無法投資DV的話，用webcam會便宜非常多，但對焦跟白平衡也無法控制，畫面會很悲劇

## 場地規劃


### 鏡頭位置


#### 平面位置

鏡頭通常在面對舞台正中央大後方

#### 垂直位置

鏡頭在大後方的話，為了避免被擋住，通常需要比人頭還高，看要用大腳架，還是小腳架放在桌上

### 筆電位置

走有線時，筆電最好在鏡頭同個位置，不然要另外拉很長的訊號線，很麻煩
p.s. 以新書發表會的例子來說，因為走無線，所以我的筆電可以放在講台旁邊，現場喇叭的音源線剛好就在那裡，所以控網路直播時可以同時控現場背景音樂，如果走有線也就是筆電要移動到大後方，那要另外安排一個人控現場背景音樂（如果有的話XD）


## 網路設定

固定 IP / 浮動 IP：選固定 IP
頻寬：下載至少\_\_M，上傳至少\_\_M

會議中心的工程師詢問，直播服務要選用哪一種方案？
一、共享頻寬有線網路服務 ( 中華電信光世代頻寬)
　1.  5M/5M 頻寬。
　2.  10M/10M 頻寬。
　3.  採 DHCP 制，提供虛擬 IP。

二、==專屬頻寬==有線網路服務 ( 中嘉光纖上網頻寬)
== 　1.  5M/5M 頻寬。==
> 印象中有線的上傳有 5M 應該就非常足夠了，但保險起見我還是等 LY 跟 macpaul 他們確認一下
> [name=ET B]

> ET，所以我跟國際會議中心那邊確定用固定 IP，5M 頻寬 OK 嗎？國際會議廳的工程師也是說 5M 應該是夠的。
> [name=Trista]

> 他說夠應該就 ok 了 XD
> [name=ET B]

 　2.  10M/10M 頻寬。
 　3.  可提供==固定ＩＰ==或採 ＤＨＣＰ 提供虛擬 ＩＰ。
> 直播都建議用固定 IP（原因我也不太清楚，但師父都這樣教）與專屬頻寬（才不會被別人搶頻寬）
> [name=ET B]

> 我也贊同妳說的，應該要用固定 IP。上次新書發表會是用 WiFi，不知道效果如何。
> [name=Trista]

> 上次印象中也是用固定IP，只是不是走網路線，是走 WiFi（固定IP是對外連線，至於內部區域網路用網路線或WiFi則是另一件事情），走WiFi 如果不是5G 頻寬的話，很容易塞車，因為2G的頻道一堆無線設備都在用，非常擁擠 XD
> [name=ET B]

 工程師的結論是：
 1.  直播服務一般會比較建議採用專屬頻寬。
 2\. 活動前需要提供點位（網路線拉設位置）。



## 器材選購：DV / Webcam


### Macpaul 的選擇


#### 高品質：SONY HDR-CX900

[http://store.sony.com.tw/product/HDR-CX900](http://store.sony.com.tw/product/HDR-CX900)
[http://goods.ruten.com.tw/item/show?21306243557750](http://goods.ruten.com.tw/item/show?21306243557750)

#### 低品質：SONY HDR-CX405

[http://goods.ruten.com.tw/item/qa?21531223943689](http://goods.ruten.com.tw/item/qa?21531223943689)

### WebCam: Mindos 的選擇


#### logitech 的某型號...



## 器材選購：擷取卡


### Mac 筆電

FEBON? USB2.0 FEBON168 UVC HDMI 免驅動程式擷取卡
BlackMagic?

### Windows 筆電

很多...


## 器材選購：麥克風


### DV / 筆電通用


#### Macpaul 的選擇: sony 某外接麥克風（需電池）



### Mac 專用


#### Apogee Mic 96k（不需電池）

錄 vocal 等級的麥克風，專門拿來直播有點浪費，但如果剛好有的話直接拿來用也蠻好的。只能接 Mac / iPad / iPhone


## 器材選購：固定支架


### 固定 WebCam / DV


內建雲台接口，直接接上一般的腳架就可以

### 固定 iPad / iPhone


iPad / iPhone 沒有接雲台的孔，要先用專門的支架固定才能連接到腳架雲台

#### Takeway 平板座 / 手機座

[http://www.takeway.tw/products.html](http://www.takeway.tw/products.html)

## 外包資源


### 公民攝影守護民主陣線

窗口： 雨停 / Jonet
網址： [https://www.facebook.com/ShotForDemocracy/](https://www.facebook.com/ShotForDemocracy/)
聯絡方式： facebook page 私訊

### CPR Team 線路組

窗口：
網址： [https://www.facebook.com/CPRTeam.TW/](https://www.facebook.com/CPRTeam.TW/)
聯絡方式：




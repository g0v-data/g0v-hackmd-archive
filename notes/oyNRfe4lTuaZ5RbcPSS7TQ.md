---
tags: digital-resilience, resilience, internet-shutdown, digiresi, civil-defense, 民防, 數位韌性松, DigiResiTh0n, hackathon
image: https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_85ba0700fa1a5c79c701ccd58e18bcb1.png
---

# 20231104 DigiResiTh0n 第零次數位韌性松
:::info
[↩️ 回到籌備文件](https://g0v.hackmd.io/@paulpengtw/DigiResiTh0n-home)
:::

:::success
當您參與本活動，即代表您已經同意 [g0v 宣言](https://g0v.tw/intl/zh-TW/manifesto/zh-TW/) 並願意遵守 [行為守則 Code of Conduct](https://g0v.hackmd.io/s/COC)。
:::

:::warning
- 加入 [g0v Slack 聊天室 #civic-defense 頻道](https://app.slack.com/client/T02G2SXKM/C056EHM42B1)（辦帳號超快超簡單）
- 線上遠端與會連結 [請點此](https://meet.jit.si/g0v-digiresi)
- [大合照！](https://drive.google.com/drive/folders/1LOczvWW8cSQaKtZJl7TNXhj2vZTA09J7?usp=share_link)
:::

## 時間地點

- 2023-11-04 Sat. 1300 - 1700
- [NPO HUB Taipei 台北NPO聚落](https://maps.app.goo.gl/XPrvzSdqgszbfRBV8) 4F 廚房
    - [「如何入場」及場地使用規定](/9pwDPOXLTr6IJKiLofl3qg)

## 活動流程

| 時間 | 活動名稱 | 備註 |
| -------- | -------- | -------- |
| 1230 - 1300 | 活動入場 |  |
| 1300 - 1315 | 介紹 | 介紹完記得拍大合照XD |
| 1315 - 1345 | 提案 | |
| 1345 - 1630 | Hacking | a.k.a. 開始做專案 |
| 1630 - 1700 | 成果發表 | |

## 報名連結
- [KKTIX 報名連結](https://g0v-digiresi.kktix.cc/events/digiresith0n)

## 自由提案報名區
歡迎自由編輯～

| 提案名稱           | 提案人稱呼 | 提案網址或內容                                                                                                  |
| ------------------ | ---------- | --------------------------------------------------------------------------------------------------------------- |
| 島內 Mesh 網路     | Paul       | 為避免國內電信機房線路故障或損毀，導致島內網路無法連線，是否有機會事先建立無線的 community-based mesh network？ |
| 網路模擬報告       | ronny      | [20230826 戰時網路  @ 開源普渡黑客松](/UkmNKU9AQKC1uDgVddEu-g)                                                  |
| 重要防災資訊分流   | ronny      | 防災資訊鏡像站點（可以找校/系計中問能否分流，好處是 USR 之類的）、IPFS [戰時網路規劃 @ 2023-10-15 g0v hackath58n](/VQlEkK9fTmyqoHM2qRVo6w?both)                                          |
| 防災地圖圖資       | ronny      | 防空避難所座標和圖資（e.g. OSM）、                                                                              |
| 防災知識庫         | billy3321 | CPR 教學、 詢問沃草或黑熊...是否能開源防災、民防資訊                                                            |
| 離線版防災資訊     | billy3321 | CPR 教學、緊急救災知識等                                                                                        |
| 重要網站列表與檢測 | Irvin      | a.列舉急難時(對外中斷時)的重要網站<br>b.如何評估、檢測或倡議島外斷網時上述網站的韌性狀態<br>https://g0v.hackmd.io/@irvin/BJxP7MImQ6                                              |
| P2P 服務測試    | Irvin           | [newnode](https://www.newnode.com)、[Quite](https://tryquiet.org/) 跟 [Keet](https://keet.io/) 吧                                          |
|  海纜狀況地圖    |   seadog007       |    讓一般民眾快速了解台灣海纜連接狀況，順便增加危機意識（嗎）  |
| 社會韌性| Eli | 戰時除了基礎設備的韌性很重要，面對認知作戰跟混亂民眾腦袋也要內建韌性 [大家來安裝公眾的數位韌性韌體](https://g0v.hackmd.io/Ex7L9ag7QfOnJXkwyz5iqg)
| OSINT | CH | 拿 IORG 的資料庫來偵測中共行為模式 |

---

## 提案紀錄
### 島內 Mesh 網路

- 為避免國內電信機房線路故障或損毀，導致島內網路無法連線，是否有機會事先建立無線的 community-based mesh network？
- 研究外國案例是怎麼做的
- 研究是否有其他新的案例
- 境外案例
    - 德國朋友分享的 wireless mesh network https://freifunk.net/wie-mache-ich-mit/community-finden/
        - OPENWRT based firmware
        - 理論上使用原裝 openwrt 也能做到相同功能
    - 美國的 mesh network 社群 https://peoplesopen.net/
    - Meshtastic方案 https://meshtastic.org/ 
        - 他是基於lora，有 AES 加密，很適合在災難情況下去做
            - 好處：不用執照就能用
                - LoRa 晶片本身, 有幾百 MHz 頻寬, 是在各國被限制在各自的 ISM 頻段
                - 915~923(或926)
                    - 433 不確定是否合法 (433MHz為緊急救難頻率)
                        - 433.000MHz 緊急救難頻率只是 FM 通訊使用，433MHz ISM 其實中心頻率在 433.920MHz 那邊，不影響，但是臺灣屬於 ITU-R3，沒有 433MHz ISM Band 可以使用
                    - 目前假定是 按 NCC lora 規範使用,915mhz.但烏克蘭案例.戰時任意頻道都能用.且戰時軟體直接支援.
                    - >NCC規範應是920MHz~925MHz，詳見中華民國無線電頻率分配表。
                - 穿透能力不強，因為輸出功率不大（且法規有限制發射 Duty-Cycle，不能把傳輸速率降低太多）
            - 它的廣播演算法 https://meshtastic.org/docs/overview/mesh-algo
            - 通訊範圍 2~5 公里
            - 只要跟手機配對就能用
            - 會掉封包或沒收到（畢竟就是無線電）
                - 畢竟不是 TCP/IP
            - 但頻寬很窄，只支援文字 (類 GPRS)緊急救難就能用
                - 座標之類的也行
            - 不需要中央 server 架構
                - 有金鑰
                - 同一個 key and channel，就能互通，也有加密（號稱 AES128）
            - 有 android/ios app 可用 https://meshtastic.org/docs/category/android-app
                - 使用簡單，不太需要太多先備知識
            - 很省電，外國玩家有使用太陽能中繼站，就把中繼站丟在戶外
                - 每個點既是 client 也是 relay
                - 120 毫瓦
            - 缺點是：節點越多，頻寬越窄（？）
                - 還沒算出多少節點數量是最佳解
                - > 目前台灣有人實測Meshtastic 100 pcs 穩定，距離 10km 内 [name=gavin]
                - > 我想詢問這消息的詳細內容[name=SCWhite]
            - comments
                - 任何的Mesh，包含使用 LoRa 的實體層，難題在互通性，包含 MAC 層和加密協定
                - > techo 品質不穩定....幫人買（幫協助保固.淚）使用請留意充電部份 [name=Gavin]
                - > 可以考慮移到 MCU 端做, 那就要考慮互通性問題 [name=..]
                - > 是不是持續發, 是 MAC 層決定，Meshtastic 有自己的 Flooding 式廣播 [name=..]
        - 有些玩野外的搭配 TAK 地圖在用 https://read01.com/zh-tw/PzOJLL4.html
            - 可以搭配哈爸的 ATAK，可掛 Lora，working proof
            - 傳一個座標需要一分鐘，可以但效能不理想，還是比較適合 text 傳輸
              - 傳一個座標需一分.設定錯誤? 效能不會這樣差.請列出FW版本和app版本. [name=gavin]
              - 對，我也很意外。目前使用ATAK 4.10 / Meshtastic官方Plugin 1.0.4 / Meshtastic 韌體 2.1.11 / APP 2.2.12 [name=SCWhite]
              - 在使用atak-forwarder時狀況沒這麼差，不過也要10多秒 [name=SCWhite]
      - 多數硬體為中製，是疑慮
          - 硬體esp32 and nrf52 可自製需求版本
          - t-echo.t-beam....留意購買品質
          - 但開源社群很活躍，所以有人會自己做
          - 目前有自組非中製的版本
    - [AREDN, Amateur Radio Emergency Data Network](https://www.arednmesh.org)
        - 頻寬較高
        - WiFi, 2.4GHz or 5GHz
        - 2440~2450MHz 是業餘無線電頻段，可以把功率拉到 200W（但是標準 Wi-Fi 頻寬就有 20MHz）
        - 非定向傳輸距離 300 M ~ 500 M，定向至少數 km
        - 指向性天線要指得準
            - 其實不用指得很準，20dBi 天線的 -3dB Beam Width 還有 20 度角
        - 可點對點或點到多點，只要同頻道，單 Radio 就可以做到中繼（但是效能會因為 CSMA/CD 碰撞下降得很快）
        - 多 Radio 可以做不同頻段中繼
        - 不仰賴現有架構的社群 mesh network
        - 門檻較高
            - 支援的路由器台灣比較難買
            - 支援的不一定有過 NCC 認證（進口可以簽自用切結書）
        - 可以有很多個節點，三個節點有兩個網路，只要其中一個節點有連到 Internet，其他兩個節點就能連線
        - 可以透過定向天線打到 5 ~ 8 公里
            - 能夠外接天線的普通家用產品 (~NT$3000) 都可以做到類似的傳輸距離
            - e.g. MikroTik hAP ac3 或是 ASUS RT-AC88U
            - 台灣最貴的mesh設備是mpu5 軍規和商用 mpu5 預算決定想像空間 可直接連網路.手機通訊.衛星.
            - > 我看到有人說9K USD 大概不是民間能輕易取得的價格
        - 定向天線的取得：
            - 天線只有分運作頻段和功率極限而已，就算一邊是 RP-SMA 一邊是 SMA 也能轉接（轉接頭也會有功率損耗，但通常小到可以忽略不計）
            - 無人機 2.4GHz / 5.8GHz 天線好買到，也便宜，但要確認好轉接問題 
        - 在美國算普及，實際應用：router放在易有野火地區
        - 有沒有機會用家用 WiFi 用指向性天線？
            - 只要是有 SMA (RP-SMA 或是 SMA 都行) 的機器都能，但是 NCC 低功率射頻器材規範裡面有規範天線增益的限制，規則比較複雜： https://www.ncc.gov.tw/chinese/files/20071/%e4%bd%8e%e5%8a%9f%e7%8e%87%e5%b0%84%e9%a0%bb%e5%99%a8%e6%9d%90%e6%8a%80%e8%a1%93%e8%a6%8f%e7%af%84%e5%85%a8%e6%96%87%20-1090813v2%20-%20%e5%8a%a0%e7%9b%ae%e9%8c%84.pdf
            - 5725-5850MHz 之間沒有天線增益管制
            - 當然 NCC 通常也沒在嚴格管制，所以大家懂得

    - 真的在意距離, 可以看這個測試數據
        - https://meshtastic.org/docs/overview/range-tests
        - > Current Ground Record: 254km
            - 極端值
        - Wi-Fi 距離世界紀錄可以到 304km，在臺灣應該比較難達成（因為制高點周圍通常還有其他山環繞）
            - https://en.wikipedia.org/wiki/Long-range_Wi-Fi
    - 公民守護山域提案
      - 之前 Gavin 有過提案 https://docs.google.com/presentation/d/1OG4NIeO_6lDo5YVe1rXPHvPbQDWF7OKt/edit#slide=id.p1
    - 比無線電好的地方
      - mpu5
        - 預算決定想像空間 
        - 可直接連網路.手機通訊.衛星.無人機
    - 手機上衛星
      - Motorola Defy 2
        - 使用聯發科方案 
        - 台灣目前還沒開通
        - https://motorolarugged.com/en-gb/motorola-defy-satellite-link/#coverage
        - 首部支援雙向衞星通訊的手機
        
    - Meshtastic.AREDN.相關硬體 自用向ncc 登錄自用.(印象中 1pcs 2000元) 自行上 ncc查
    - 還有 wifi 時可以用 Keet 之類的P2P IM，真的沒基礎網路時再用 Meshtastic
    - TAK 相關軟體
      - tak 相關軟體授權為美國政府 (https://github.com/deptofdefense)
      - tak.gov ATAK-CIV 受商務部工業與安全局 (BIS) 管理的《出口管理條例》(EAR) 的約束，該條例建議該物品歸類為 EAR99。
      - 公開部份 atak.itak.pitak.webtak.tak server
      - 開源部份 FreeTAK.taky. (但請留意版本安全.USA社群及專業社群轉為tak-server為主.FreeTAK備用)
      - atak 相關 Google play商店 https://play.google.com/store/apps/developer?id=TAK+Product+Center
      - itak apple商店 https://apps.apple.com/us/app/itak/id1561656396
      - 硬體部份 mpu5.三星手機9-23(官方指定和三星有支援).Somewear.moto數位無線電.Beartooth MK II.各種無人機.gotenna pro x.
      - 架構 使用server或是vpn及mesh網路.
      - 協定相關 cot
    - APRS
      - 需要業餘無線電執照才可使用，在 144.640MHz FM (25kHz FM, 5kHz deviation)
      - 業餘無線電最大最活躍的的封包網路 (aprs.fi 上面可以看到現況)
      - 在臺灣有非常多現成的 Digipeater（中繼站）和使用者
          - 但是現成也有幾個有問題的垃圾站臺，導致部分地區頻道容易擁塞
      - 傳輸方式是 1200bps AFSK over FM，普通便宜的 FM 手持機配合音頻轉接線插上手機即可使用
          - 一般手持機輸出功率有 5W，配合適合的天線（比如 Diamond RH-770 這種在 VHF 上面是 1/2 wave radial-less），不經過中繼就可以傳 40km+
      - 每個封包頂多 200 byte 左右，大多數直接 APRS 的設備不支援中文（比如 Kenwood TH-D7/D72/D74, TM-D700/D710 或是 Yaesu VX-8DR / FT1/2/3/5DR）
      - 也有手機 App 可以使用（例如 APRSDroid，但維護得不怎樣）
    
### 網路模擬報告
- 中共可能不會斷我們的網絡？（想放大投降聲音？）
- 完全斷 <> 完全不斷之間的狀況
- 大松做的「[戰時網路模擬器](/UkmNKU9AQKC1uDgVddEu-g)」

> 其實昨天 Cloudflare 已經幫我們做過海纜斷線模擬了XDD [name=seadog007] 

### 重要防災資訊分流

盤


### 防災地圖圖資


### 防災知識庫
- （謎）沃草下一版的手冊會免費（？）
> 哦哦哦哦哦 [name=paulpengtw]
> [物資哪裡買](https://g0v.hackmd.io/@billy3321/ryMJ68XQ6)

- 日本方案
    - ["TOKYO BOUSAI", a disaster prevention book by NOSIGNER](https://nosigner.com/tokyo-bousai)
    - ["OLIVE", a wiki to centralize and share information that is useful when disasters strike.](https://nosigner.com/olive)
    - ["THE SECOND AID", A disaster prevention kit included survival food and supplies](https://nosigner.com/the-second-aid)
        - 這是防災包+防災知識庫


| Service | Link |
| -------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Survival Manual (Offline App)                      | [F-Droid](https://f-droid.org/packages/org.ligi.survivalmanual/), <br />[Google Play Store](https://play.google.com/store/apps/details?id=org.ligi.survivalmanual), <br />[Amazon appstore](https://www.amazon.com/ligi-Survival-Manual/dp/B06WW43R3T). |


### 離線版防災資訊

### 重要網站列表與檢測

- https://g0v.hackmd.io/@irvin/BJxP7MImQ6

> 或許也可以整理哪些官方或可信賴的 AM/FM 電台可以聽（真.零時電台 [name=paulpengtw]
> 這應該是屬於樓上知識庫的範圍 [name=irvin]

- 盤點重要網站（網路服務）（沒有就會很痛苦的服務 /app / ）
- 想想如何檢測服務的可存續性
- 聯繫這些 service provider 詢問對方是否有應變計畫


### peer-to-peer 服務測試
moved to https://g0v.hackmd.io/@irvin/p2p-chat



### 海纜狀況地圖
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c7458d19c3bee0c8e15cde5c86eba9e6.png)
> 哦哦哦！有來源連結嗎？ [name=chihao] 
> https://www.submarinecablemap.com/country/taiwan [name=seadog007]

講個故事
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b4dc20d7ac8725ca8170e2719c47b983.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e094fd376b603c5ecaecfe8a0286720c.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_36b912d46fa977c4fb2d0e911becb0e6.png)![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1393ea54af04db45eb1f29e5e6e1b619.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a027d19aae252ffc4188ce1a160842b4.png)


### 社會韌性
- 當戰爭發生時，民眾要怎麼應變網路資訊，現行有一些烏克蘭的案例可以參考
- 想整理一些軍事社會學的研究，
    - [name=chihao] ++ 要不要開新共筆，就可以開始貼連結
    - [大家來安裝公眾的數位韌性韌體](https://g0v.hackmd.io/Ex7L9ag7QfOnJXkwyz5iqg)

### 公開資料偵測中共行為模式
- IORG 目前有哪些資料
    - 中國政府重要對外單位
    - 中共官媒、黨媒（中央 + 地方）
- 還需要哪些資料
- 這些資料可以怎麼用？

- 可可可可可可可


---

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_85ba0700fa1a5c79c701ccd58e18bcb1.png)

---


最近意外看--ê 無線通訊相關參考分享，感覺有需要研究（` by Ku龜（無報名純資料分享）`

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8c97fe4eba0ebd2ce0f987173a4f500a.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7f59efea4732b4869fdced64722effed.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3bee9d3c40378c9e14c28c6e790dd470.png)

Rutgers University Confirmed: Meshtastic and LoRa are dangerous
https://youtu.be/EAQI2ZSmxPU?si=79z6dnDWkNphe_74

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_865381246a62b91f556f9fedc0208ed6.png)
Doomsday Communicators by Armachat ＃[Github](https://github.com/bobricius/armachat)
https://youtu.be/tX8KjV6DEJk?si=J7oaco20PFHIPk3N

---


若有任何問題、建議或操作上的疑問歡迎到 [g0v slack 討論區](join.g0v.tw) 的 [#civil-defense 頻道](https://app.slack.com/client/T02G2SXKM/C056EHM42B1)，或是寄信給 [籌備夥伴 Ronnywang](mailto:ronnywang@gmail.com)，也可以私訊 [籌備夥伴 Paul 臉書](https://fb.com/paulpengtw) 詢問
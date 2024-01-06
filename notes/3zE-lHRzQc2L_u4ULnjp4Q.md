---
title: "IoT 空污偵測 DIY"
tags: IoT,hackpad
---

# IoT 空污偵測 DIY

> [點此觀看原始內容](https://g0v.hackpad.tw/B1xkj9fUqqH)


## 參與方式

- 請先加入 [http://join.g0v.today/](http://join.g0v.today/) ，然後找到 pm25 頻道訂閱

## 源起頭

[https://www.facebook.com/pulipm2.5/posts/1583904825219960?hc_location=ufi](https://www.facebook.com/pulipm2.5/posts/1583904825219960?hc_location=ufi)
[http://logbot.g0v.tw/channel/g0v.tw/2015-04-19/18](http://logbot.g0v.tw/channel/g0v.tw/2015-04-19/18)
[http://logbot.g0v.tw/channel/g0v.tw/2015-04-19/61](http://logbot.g0v.tw/channel/g0v.tw/2015-04-19/61)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1b948791649d2e0a6d6d3b90dafc86c1)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c59e690d900458a3f32001cb59350ced)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_90bdc56f41934b835d12334b376e418e)

### 目標

- 夠便宜，能讓志願收集資料的人負擔得起
- 夠準確，提供一般參考及學術研究
- 畫出全台灣的 PM2.5 即時地圖


## AirCasting

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_165d0f787182562132839626491f499f)
- [http://aircasting.org/](http://aircasting.org/) \- USD$200
    - (open hardware + open source, 元件列表在 [http://www.habitatmap.org/habitatmap_docs/HowToBuildAnAirCastingAirMonitor.pdf](http://www.habitatmap.org/habitatmap_docs/HowToBuildAnAirCastingAirMonitor.pdf) page 8  )
    - ref: [http://www.takingspace.org/](http://www.takingspace.org/)
    - Aircasting 有測 PM2.5, 溫度, 濕度, CO, NO2, 然後配合其它零件，測噪音、心跳、活動率、活動率、核心溫度
    - NO2 Aircasting 用的是  MiCS 2710
    - 神榮 ppd42ns 淘寶40RMB，aircasting 拿 US$5.53
> 神榮 PPD42NS 其實不能測 PM2.5, 它測的是 1µm 的粒子，詳見 [http://www.seeedstudio.com/wiki/index.php?title=Grove_-\_Dust\_Sensor_%E7%B2%89%E5%B0%98%E4%BC%A0%E6%84%9F%E5%99%A8&uselang=zh](http://www.seeedstudio.com/wiki/index.php?title=Grove_-_Dust_Sensor_%E7%B2%89%E5%B0%98%E4%BC%A0%E6%84%9F%E5%99%A8&uselang=zh)
> [name=miaoski]

### AirQualityEgg

- [http://airqualityegg.com/](http://airqualityegg.com/)  USD $196 + addon (~ 60 USD)
    - [http://shop.wickeddevice.com/product-category/air-quality-egg/](http://shop.wickeddevice.com/product-category/air-quality-egg/)
    - NO2, CO
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1c237b55383e8b79f117095bb3cbd70c)

### Smart Citizen Kit

- [https://smartcitizen.me/](https://smartcitizen.me/)
- 155,00 EUR
> super expensive （不知道有沒有看錯）
> [name=Pomin W]


## DIY

### BOM Cost

| 零件 | 價格(原單位) | 價格(TWD) | 備註 |
| --- | --- | --- | --- |
| Sharp DN7C3CA006 | 135 RMB | 675 |  |
| Arduino Nano |  | 180 | 可改用單顆 IC (NT$55) 或 Arduino Pro/Mini (約 12RMB) |
| DHT-22 | 17 RMB | 105 |  |
| LCD1602 | 6 RMB | 30 | 選配 |
| ESP8266 ESP-01 | 13.8 RMB | 70 |  |
| MQ7 一氧化碳偵測器 | 8 RMB | 40 | 選配 |
| WSP1110 NO2 感測器 | 150 RMB | 750 | 選配 |
| 電容、電阻 ... |  |  |  |
小計 NT$1,850 (不含運費)
總之要比 US$200 便宜啊啊啊啊啊啊


### 各項零件

    - Sharp gp2y1010au 測粉塵 [https://www.sparkfun.com/datasheets/Sensors/gp2y1010au_e.pdf](https://www.sparkfun.com/datasheets/Sensors/gp2y1010au_e.pdf)
        - ICShopping NT$250 無風扇
        - 程式: <[http://lafudo.blogspot.tw/2013/12/arduino-gp2y1010au0fpm25.html](http://lafudo.blogspot.tw/2013/12/arduino-gp2y1010au0fpm25.html)>
> 這顆沒辦法分辨 PM2.5
> [name=AceChen]

> 新一代的 gp2y1012au 就可以了 ^^; 含風扇的型號 DN7C3CA006 要價 135RMB.
> [name=miaoski]

    - [夏普 PM2.5傳感器 Dust Sensor第三代 DN7C3CA006](http://www.digikey.tw/product-detail/zh/DN7C3CA006/425-2896-ND/5114242)
        - [http://media.digikey.com/pdf/Data%20Sheets/Sharp%20PDFs/DN7C3CA006_Spec.pdf](http://media.digikey.com/pdf/Data%20Sheets/Sharp%20PDFs/DN7C3CA006_Spec.pdf)
        - 淘寶 135RMB
    - Arduino 一顆
    - MQ9 一氧化碳、煤氣、液化瓦斯 / MQ5 液化石油氣、天然瓦斯 / MQ3 酒精蒸氣
> 應該改用 MQ7 只要測一氧化碳就好
> [name=miaoski]

        - ICShopping NT$270 / MQ7 淘寶 6-8RMB
        -  <[http://www.seeedstudio.com/depot/grove-gas-sensormq9-p-1419.html?cPath=25_27](http://www.seeedstudio.com/depot/grove-gas-sensormq9-p-1419.html?cPath=25_27)>
    - CO 感測器 [http://goods.ruten.com.tw/item/show?21404014964757](http://goods.ruten.com.tw/item/show?21404014964757)
    - 專業的 NO2 感測器一顆報價 5 千
    - WSP1110 NO2 平面傳感器
        - [http://goods.ruten.com.tw/item/show?21312239079267](http://goods.ruten.com.tw/item/show?21312239079267)
        - NT$1230
    - WiFi 模組 NT$275
        - TI 3300?
        - EST8266 (13.3RMB) 還不知道怎麼用
            - [https://github.com/sandeepmistry/esp8266-Arduino/tree/master/esp8266com/esp8266/libraries/ESP8266WiFi](https://github.com/sandeepmistry/esp8266-Arduino/tree/master/esp8266com/esp8266/libraries/ESP8266WiFi)
            - [http://www.electrodragon.com/w/ESP8266\_wiring\_with_Arduino](http://www.electrodragon.com/w/ESP8266_wiring_with_Arduino)
            - [http://zeflo.com/2014/esp8266-weather-display/](http://zeflo.com/2014/esp8266-weather-display/)
            - 淘寶 link: [http://trade.taobao.com/trade/detail/tradeSnap.htm?spm=a1z09.2.9.26.PlkYeC&tradeID=947883827521695&snapShot=true](http://trade.taobao.com/trade/detail/tradeSnap.htm?spm=a1z09.2.9.26.PlkYeC&tradeID=947883827521695&snapShot=true)
            - ESP8266モジュールでArduinoからWi-Fiを使う
                - [https://github.com/itead/ITEADLIB\_Arduino\_ESP8266](https://github.com/itead/ITEADLIB_Arduino_ESP8266)
                    - 上面這個是 GPLv2 所以我們的授權會被感染
                - [http://ehbtj.com/electronics/esp8266](http://ehbtj.com/electronics/esp8266)
            - 我們買的 ESP8266 似乎比網路上的教學更新，但它對電源很敏感，直接接 FT232 甚至由外部供電都會沒辦法通訊。Arduino 可以。
> ESP8266好像是對電壓的穩定性比較要求,我試過UART轉USB的5V接出來之後經過一顆3.3V的LDO就很穩定
> [name=cs8425]

                - AT+GMR
                - AT version:0.21.0.0
                - SDK version:0.9.5
    - 溫濕度用 DHT-11 約 NT$55
        - 更準的話改用 DHT-22 約 NT$180
            - [https://github.com/adafruit/DHT-sensor-library](https://github.com/adafruit/DHT-sensor-library)
        - 還想更準的話可以用 [HIH6130](http://sensing.honeywell.com/honeywell-sensing-humidicon-hih6100-series-product-sheet-009059-6-en.pdf) 或 [SHT15](http://www.sensirion.com/fileadmin/user_upload/customers/sensirion/Dokumente/Humidity/Sensirion_Humidity_SHT1x_Datasheet_V5.pdf)
    - 3G 找到最便宜的要 47 歐元
> 應該用 GSM/GPRS 就夠了 [http://seller.pcstore.com.tw/S134700302/C1021133941.htm](http://seller.pcstore.com.tw/S134700302/C1021133941.htm)
> [name=AceChen]

> 好貴上面那個要 NT$1600 耶
> [name=miaoski]

    - [http://www.arduino.cc/en/Main.ArduinoGSMShield](http://www.arduino.cc/en/Main.ArduinoGSMShield)
> GSM/GPRS還有另一個選擇，MTK的LINKIT ONE，本身有MCU，不需要另外的ARDUINO，還包了BLUETOOTH，WIFI，GPS，只是不知道需不需要這麼多東西 [http://www.seeedstudio.com/depot/LinkIt-ONE-p-2017.html](http://www.seeedstudio.com/depot/LinkIt-ONE-p-2017.html)
> [name=Ken L]

> ps. 可以幫忙焊電路@台北
> [name=Ken L]

    請問~ 這顆如何? DustDuino : [http://www.publiclab.org/wiki/dustduino](http://www.publiclab.org/wiki/dustduino)
    - [不用靠 Google，你也可以做自己的空氣品質監測](http://www.inside.com.tw/2015/08/11/intel-exploring-air-quality-monitoring)

### 眉眉角角

    - 自幹的程式放這邊 [https://github.com/miaoski/pm25](https://github.com/miaoski/pm25)
> 選用 DN7C3CA006 是因為考量到風扇嗎？可是他讓費好多腳位QQ
> [name=劉宇庭]

    - Linux 下燒 NodeMCU 的方法: [http://hanneslehmann.github.io/2015/01/ESP8266Module_LUA/](http://hanneslehmann.github.io/2015/01/ESP8266Module_LUA/)
        - FT232R 直接切到 3.3V，這樣 TX/RX/VCC 都是 3.3V TTL 不用再 level down.
        - RST pull high, CH pull high, GPIO0 pull low 就算不能 AT command 也沒關係，esptool.py 直接燒就對了
        - 燒完後就是 Lua + 9600bps 萬歲！
    - NodeMCU API [https://github.com/nodemcu/nodemcu-firmware/wiki/nodemcu\_api\_cn](https://github.com/nodemcu/nodemcu-firmware/wiki/nodemcu_api_cn)
    - 測試中的畫面 [http://i.imgur.com/Hl7egG3.jpg](http://i.imgur.com/Hl7egG3.jpg)
    - 需要 calibration
        - [https://groups.google.com/forum/#!topic/airqualityegg/8ZX5_eQOVuI](https://groups.google.com/forum/#!topic/airqualityegg/8ZX5_eQOVuI)
        - [http://www.takingspace.org/evaluating-low-cost-gas-sensors/](http://www.takingspace.org/evaluating-low-cost-gas-sensors/)
        - [http://www.kandrsmith.org/RJS/Misc/calib_dht22.html](http://www.kandrsmith.org/RJS/Misc/calib_dht22.html)
            - DHT22 使用二週後，濕度從正常的 70%RH 降到 50%RH 了，外面很濕也一樣
        - 可能會因為沒辦法在家中校準，讓數據失去意義
    - DN7C3CA006 的校準
        - 取樣 250 次做平均，第一顆在 210 (1.025V) 左右，第二顆在 230 (1.123V) 左右。
        - 要加一個電晶體，開機的時候把風扇關掉做 Vs 的校準 :(
        - 出廠校準是抽測，所以可以預期每一顆都不一樣
        - 原來環保署也是需要校準的...
        - [http://taqm.epa.gov.tw/pm25/tw/Download/細懸浮微粒(PM2.5)自動監測數據發布校正原則.pdf](http://taqm.epa.gov.tw/pm25/tw/Download/細懸浮微粒(PM2.5)自動監測數據發布校正原則.pdf)
        - 公式: pm25 (µg/m^3) = a * b * (Vo\[mV\] - Vs\[mV\])
            - a 建議值 0.6
            - b 在 RH50% 以下是 1 ，以上是 (1 - 0.01467 * (h - 50))
> 應該還是可以校正baseline，不過linearity是有點麻煩…
> [name=AceChen]

    - MQ9 和 MQ7 都會受溫、濕度影響，而且需要在標準氣體校準。不要測這一項？
    - GP2Y1050AU0F 後來新出這顆內建MCU會不會比較準一點?
### 耗電量計算

        - WiFi 傳送時約 150mA (3.3V)
        - 風扇 max 140mA
        - DN7C3CA006 除風扇外約 40mA
        - DHT-22
        - MQ9 預熱 340mW 運作時電流未標註
        - 除MQ9預熱外 330mA
    - 電源穩壓：DC supply - 並聯大小電容 - GND

## Prototype

### 台南北區開元派出所

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2c5fb2c56279d50169bf486b82416ecf)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c4bf769af13eb7c3fd289ed4853ee1b0)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5c64c567712e2320e467e94c9ae9ca76)
- raw data: [https://www.google.com/fusiontables/DataSource?docid=1BapkNrqyxds1AlmJo_Y4XiYyf-Rxliz9TvZIPOUJ](https://www.google.com/fusiontables/DataSource?docid=1BapkNrqyxds1AlmJo_Y4XiYyf-Rxliz9TvZIPOUJ)
- 與 epa.tw 資料比較： [https://plot.ly/~miaoski/69/epatw-vs-kiang/](https://plot.ly/~miaoski/69/epatw-vs-kiang/)
- 另一份資料： [https://sheethub.com/miaoski/pm25](https://sheethub.com/miaoski/pm25)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b94f71c326d4f999e8805270f27f8aec)
> BS 建議取樣一分鐘一筆，每秒鐘取樣一次就好。
> [name=miaoski]


### 短期目標

- 製作 3 個 pilot 測試不同的 LCD 點燈、熄燈、等待的參數
- 在環保署測站旁放置儀式，測試準確度
- 在開放文化基金會提案，製作 10-20 個 pilot 裝置


## 募集

- 前端 / 視覺化呈現
- 維修人員 / 略懂電子電路
- 校準儀器或重新設計感測元件的強者
- 放置裝置的志願者
> 我在台北文山, 可以幫忙焊接組裝測試, layout/程式的話有空也可以幫忙
> [name=Tzu-Hsi Y]


- [ ] 找人跳坑寫後端 (目前 realtime 送到 sheethub.com ，但還有些要改)
> 後端的需求有哪些？我剛到，但是對後端很有興趣0w0
> [name=Pichu C]

> 主要是需要能夠接收串流資料並且即時呈現的系統，像是 [https://thingspeak.com/](https://thingspeak.com/)
> [name=Finjon K]

> 後端用node.js+任何SQL,前端用D3.js那類的東西把資料畫出來,中間用websocket or ajax做資料更新,這樣自幹一套如何?
> [name=cs8425]

> (感應器資料就不走http了,開個tcp連線丟資料就好>< 想玩看看MQTT、_C_OAP也是可以orz
> [name=cs8425]

> 我這邊會PHP  + ZMQ，node.js有碰過，大致上知道Xively是用RoR做的
> [name=Pichu C]

- [ ] ~要和 AirCasting 連嗎？~
- [ ] ESP8266 收到 Arduino 更新時閃燈號 (GPIO0)，收到 server 端 OK 時閃燈號 (GPIO2)
- [x] 安全問題：洗掉設定檔那邊應該由 Arduino 來處理，不應該 fallback 到 AP mode
- [ ] 發 ID 給 client 的方法
- [ ] OCF 提案請 Intel / MTC 贊助？


## 相關專案

- [輻射地圖](https://g0v.hackpad.tw/91ZImrFjGvx)
- [http://www.gcmonitor.org/](http://www.gcmonitor.org/)
- [LASS Group](https://www.facebook.com/groups/1607718702812067/?fref=ts) [LASS Code](https://github.com/LinkItONEDevGroup)  台灣公益感測網路
- [https://github.com/Lafudoci/ProbeCube](https://github.com/Lafudoci/ProbeCube) 空汙感測器專案
    - 前端： [https://github.com/immortalmice/ThingSpeak-Visual-Map](https://github.com/immortalmice/ThingSpeak-Visual-Map) 空汙共同觀測地圖專案
- 環保署：全台空污現形！ 可測PM2.5微型感測器明年3月上市
    - [http://e-info.org.tw/node/111674](http://e-info.org.tw/node/111674) (比較貴「初期產品價格會壓在數千元」)
- Raspberry Pi 版：[https://www.fangfufu.co.uk/wiki/doku.php?id=public:raspberry\_pi\_weather\_station\_board](https://www.fangfufu.co.uk/wiki/doku.php?id=public:raspberry_pi_weather_station_board)


---
tags: digital-resilience, resilience, internet-shutdown, digiresi, civil-defense, 民防, 數位韌性松, DigiResiTh0n, hackathon, meshtastic, mesh, lora
image: https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_85ba0700fa1a5c79c701ccd58e18bcb1.png
---

# Meshtastic / DigiResiThon

:::info
[↩️回到籌備文件](https://g0v.hackmd.io/@paulpengtw/DigiResiTh0n-home)
:::

## 材料名單
- https://www.ruten.com.tw/item/show?21309058514794
- https://www.ruten.com.tw/item/show?22324954367793
    - 註明sx1262
    - 然後選915Mhz
- https://www.ruten.com.tw/item/show?22050299448779
- https://www.ruten.com.tw/item/show?22310159373545
- https://www.ruten.com.tw/item/show?22323912154543
- https://www.ruten.com.tw/item/show?21918310238468
    - 90度內孔

## 測試經驗
- 第壹次數位韌性松用三台裝置測試開多個新頻道
    - LoRa 裝置三台硬體 spec
        - Adafruit Feather nRF52840 Express 
        - Lora SX1262	
        - NEO 6M GPS	
        - SSD1306 OLED	
        - 僅 PCB 不同
        - Firmware 2.1.11
    - Meshtastic App devices
        - 2 androids, 1 iOS
    - iOS 開新 Channel 有機會 fail 接收訊息和傳送訊息

## 找洞
- 如果無法順利把訊息傳出去或接收
    - 重開 LoRa 裝置
    - 關掉手機 App 重開
    - 關掉手機藍芽重開
- 若以上都不行
    - 請直接重新用 QR CODE 傳送所有頻道訊息重設

## introduction
- 第零次介紹
    - Meshtastic方案 https://meshtastic.org/ 
        - 他是基於lora，有 AES 加密，很適合在災難情況下去做
            - 好處：不用執照就能用
                - LoRa 晶片本身, 有幾百 MHz 頻寬, 是在各國被限制在各自的 ISM 頻段
                - 915~923(或926)
                    - 433 不確定是否合法 (433MHz為緊急救難頻率)
                    - 433千萬別用,台灣Lora免照請用915,Fw刷完設定TW就能使用915了."145 MHz及433 MHz為呼叫及緊急救難頻率，任何電臺不得停留佔用及干擾。來源ncc" [name=Gavin]
                    - 目前假定是 按 NCC lora 規範使用,915mhz.但烏克蘭案例.戰時任意頻道都能用.且戰時軟體直接支援.
                     - >NCC規範應是920MHz~925MHz，詳見中華民國無線電頻率分配表。
                - 穿透能力不強，因為頻率不強
                    - 功率？ [name=pichu]
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
            - 原文 https://hackaday.com/2022/09/08/the-tak-ecosystem-military-coordination-goes-open-source/
            - 可以搭配哈爸的 ATAK，可掛 Lora，working proof
            - 傳一個座標需要一分鐘，可以但效能不理想，還是比較適合 text 傳輸
              - 傳一個座標需一分.設定錯誤? 效能不會這樣差.請列出FW版本和app版本. [name=gavin]
              - 對，我也很意外。目前使用ATAK 4.10 / Meshtastic官方Plugin 1.0.4 / Meshtastic 韌體 2.1.11 / APP 2.2.12 [name=SCWhite]
              - 在使用atak-forwarder時狀況沒這麼差，不過也要10多秒 [name=SCWhite]


## 目標
- > 或許可以變成 g0v 社群或開源社群在緊急或網路障礙情況下暢通無阻的交換資訊方式 [name=paul]

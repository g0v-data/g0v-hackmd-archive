---
title: "現場轉播作業流程"
tags: 線路松,hackpad
---

# 現場轉播作業流程

> [點此觀看原始內容](https://g0v.hackpad.tw/ADYWtwNY3zN)






20140320 加入 Youtube live 直播
手機、平板，目前推薦使用 Google+ hangout 或 Ustream


YouTube Live 多攝影機模式
- iOS & android：請協助選個免費的、支援 RTMP 協議的直播軟體
> 目前 OS Broadcaster 跟 Android Broadcaster 都不行。
> [name=caasi H]

> 手機平板，BroadcastMe 可直播到 YouTubeLive，iOS NTD60，Android Free
> [name=Bropheus H]

- Windows：請裝 Wirecast for YouTube / Open Broadcaster Software
- Mac OS X：請裝 [Wirecast for YouTube](http://www.telestream.net/wirecastforyoutube/cb-landing.htm)
1.  跟頻道管理者要 RTMP Server （通常是 rtmp://a.rtmp.youtube.com/live2）
2.  跟頻道管理者要 Stream Key（一串英數字如 ）
3.  管理者：影片管理現場活動頁面→內容擷取
- 大家的攝影機會進到同一 YouTube Live 網址
- [https://g0v.hackpad.com/e2uv6HB47H](https://g0v.hackpad.com/e2uv6HB47H)[`](https://g0v.hackpad.com/e2uv6HB47HT)T






### 摘要

本文目的為
1.  根據實際經驗列舉現場可能遭遇的事項。請依照問題列出過去活動中曾經應對的方案。
2.  舉出出席志工應該準備的標準配備
3.  調查各種技術方案的優劣。

### 志工裝備

- 3G 或 WiMax 大力玩  [http://www.g1.com.tw/play.php?s=spec](http://www.g1.com.tw/play.php?s=spec)
    - 推薦 HTC J ，同時支援多種網路系統。
- Laptop
- 延長線
- 水與乾糧。

### 應解決問題

- 轉播主控台 aka 棚內主播
    - 主播可以遠端切換轉播畫面，因現場網路不穩定，時常會有斷線
    - 透過 Google Hangout Air 可以同時最多 10 組載具登入轉播，由主播決定播出那個畫面。
    - 使用單一 Google Hangout Session，可維持一固定 youtube 轉播網址。唯轉播仍有時間限制。
- 應用多重載具 (Android Phone, iPhone, iPad, Laptop) 直播
    - 最好是使用個人帳號，而非共享帳號，以免現場設定費時。
    - 越多人持有能夠簡單上網啟動直播的裝備，越能取得更多即時畫面！
    - 主播可先建立 Google Hangout  Air event，提供網址給現場擁有載具的人員使用。外部人員準備好可隨時在 Hangout session 中啟動轉播。
- 網路連線問題
    - 現場人員太多，會癱瘓 GSM/WCDMA 電信網路，同時大量手機的行動熱點與藍牙也會使 2.4Ghz 也會過於擁擠無法使用。
    - 由於 WiMAX 使用人較少，頻譜相對寬敞。用 USB 連 WiMAX Dongle 可確保品質。
        - WiMax 大力玩  [http://www.g1.com.tw/play.php?s=spec](http://www.g1.com.tw/play.php?s=spec)
    - 破解無線網路方式 \- 許多機關無線網路認證設計不良，雖需登入，但未過濾 DNS 查詢。因此可用 IPv4 over DNS tunnel 連上網路。但需要於外部設定 DNS Tunnel VPN Server - kryo.se: iodine (IP-over-DNS, IPv4 over DNS tunnel) [http://code.kryo.se/iodine/](http://code.kryo.se/iodine/)
    - 最好仍有實體線路。
- 電力問題
    - 可能資源有
        - 行動電源 \- USB 行動電源，可支援手機、WiMAX Wireless AP.
        - 發電機 \- 吃柴油或汽油，體積龐大、製造噪音，若於會場中央使用燃料有安全疑慮。
        - 現場電力 \- 如轉播現場舞台活動、可試圖聯絡附近的燈光、音響組人員取得較好視野與電力資源。需先備好延長線 (2014-03-19 經驗)
- 接班問題
    - 接力請填班表，並留下手機給主播或協調人，以接收轉播狀況之簡訊通知。
- 雨棚
    - 裝備怕雨 \- 解決方案 TBD
- 現場聯絡
    - 由於轉播點通常位於高點或會場中心，相對擁擠，沒有足夠空間作業或討論。可於場地附近選一支援會合點，提供食物以及臨時物資支援使用。
    - 無線電數組 \- 若現場人數增加，將癱瘓電信網路，造成聯絡困難。若有數組人員，可置備無線電。
- 轉播品質
    - WebCam
        - 入夜後，一般的 WebCam 拍出的畫面亮度過暗。
        - 若離會場太遠，需要指向性麥克風收音。
        - 20140319 經驗 - Macbook Air / Macbook Pro + HD WebCam (Logitech C920)
    - Desktop + HD DV
        - Laptop 沒有 HDMI input 無法接 DV。如有固定區域，可使用 Desktop + HD DV. 但密集場地，會造成難以移動。

### 20140319 經驗

    - HSDPA 在人多時很慢 改用 WiMAX (3/19經驗)
    - WiMAX USB adapter 抓不到網路 改用 WiMAX 大力玩
    - 現場 WiFi 訊號很髒，大力玩常斷 改用 USB 連接模式
    - Desktop 很難搬動
    - Laptop 沒有 HDMI input 無法接 DV

### 技術方案調查

- YouTube Live
    YouTube Live（不選用 hangout 直播，選自訂編碼選項，改用 OBS, Wirecast 等軟體）
    可以備援串流、多攝影機同步上傳（每觀眾自選畫面），不會斷線就要自動換網址
    如果多攝影機接到同一台電腦，主播用 OBS / Wirecast 切畫面，觀眾只看被選畫面。
-  Google Hangout
-  UStream
    Ustream 是頻道網址永遠直播最新狀況，每次事後給獨立網址，都顯示在頻道旁邊
    YouTube 是每個網址就是即時直播＋事後影片，按每次直播分網址
- Using Google Hangout API to start Google Hangout Streaming
    - write
    - API  : [https://developers.google.com/+/quickstart/python](https://developers.google.com/+/quickstart/python)


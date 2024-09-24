# meshtastic heltec v3 串資料筆記

## 準備
- 購買一台 heltec v3
- 可以透過 USB + Chrome 透過 https://flasher.meshtastic.org/ 自行刷韌體
- 透過 https://client.meshtastic.org/ 可以用電腦查看連結狀況
    - Connect New Device > Serial > 選設備

## 資料串接
- 用 USB + TypeC 把電腦跟 meshtatic 連結起來
- 利用 python 程式抓取 meshtastic 所有記錄
    - [test.py 程式碼](https://gist.github.com/ronnywang/4a466f963bc2419ec1e454bd9ee64039#file-test-py)
    - 需要 pip install meshtastic
    - 程式會持續將收到的 log 寫進 log.jsonl 檔案內
- 利用 PHP 處理兩邊的串接
    - [slack-link.php 程式碼](https://gist.github.com/ronnywang/4a466f963bc2419ec1e454bd9ee64039#file-slack-link-php)
    - 透過 [slack 彈幕 API](https://g0v-slack-archive.g0v.ronny.tw/index/getmessage?channel=C056EHM42B1) 每秒檢查有無新訊息
    - 透過 [線上揪松 Bot](http://meet.jothon.online/bot) 機制，取得 slack 貼文　token
    - 程式每秒檢查是否有來自 meshtastic portnum=TEXT_MESSAGE_APP 的記錄，有的話，就透過揪松bot API 貼到 slack
---
title: 懶人包：購買後要如何設定 - 刷韌體 / DigiResiTh0n
tags: digital-resilience, resilience, internet-shutdown, digiresi, civil-defense, 民防, 數位韌性松, DigiResiTh0n, hackathon, meshtastic, mesh, lora
---

# [懶人包] 購買後要如何設定 - 刷韌體

作者：@dryden（g0v slack）

https://www.facebook.com/groups/meshtastictw/permalink/414578450951353

**⚠️注意!⚠️ 在沒有連結天線的情況下，請不要開啓裝置的電源，可能會損害無線電晶片！**

##### 將 Meshtastic 韌體刷入開發板

在收到你的裝置以後，除非它是已經預裝好 Meshtastic 的開箱即用型產品 （例如 Nano G1 Explorer、或是由我協助設定的版本） ，不然它其實都只是一塊開發板，需要你把 Meshtastic 韌體刷進去。刷的方法並不難，步驟如下：

-   以 Chrome 瀏覽器開啓這個刷機網頁 https://flasher.meshtastic.org/
    
-   Device 的地方，先選擇你的裝置型號（如果你是購買我推薦的 Heltec ESP32 LoRa，就選擇 Heltec V3）
    
-   Firmware 的地方，請選擇 Stable 中，版本號最大的（如下圖，選最新的版本）
    
-   按下 Flash
    
-   在跳出的視窗中，選擇 Update
    
-   此時會跳出要你選擇 USB 裝置的對話框，選擇類似： USB Single Serial （cuusbserial-1234567890）的裝置 （如果你沒有看到裝置出現在列表上，請到下面這個網頁，根據指示安裝驅動程式 https://meshtastic.org/docs/getting-started/serial-drivers/ ）（如果你是購買我推薦的 Heltec ESP32 LoRa，就是選擇 ESP32 的頁面）
    
-   當電腦和 USB 裝置連線並選好以後，刷機網頁就會開始將 Meshtastic 裝進你的開發板
    
-   在跑到 100% 時就是完成了，此時就可以嘗試用手機上的 Meshtastic app 跟它連線囉！
    
-   如果以上說明看不太懂，可以來這裡看看英國大叔的教學 （因爲網頁後來有改版、UI 稍有不同，但大同小異） https://youtu.be/mdN1iy4MKOI?t=178

## Q&A

- baud rate應該選啥?
    - 預設的就好，我改過一次，刷了以後有問題XD
    - 不過我現在問題是進不去刷機模式，一打開就進入Lora Mode 0?
        - Lora Mode 0 是還沒刷機前會看到的一種畫面，是正常的。確認看看驅動程式有沒有安裝成功
        - 看來是驅動沒安裝好，自動安裝程式沒辦法抓到驅動，要手動進入控制台裝置管理員裡面指定安裝，完成了
        - 有時候需要在開機前將gpio 0拉為low方可進入下載 串口也會打印下載模式的字串…

- 請教一下: 刷到最新版的stable韌體(2.3.6)，手機的 mesh app 就無法透過藍牙連線了，但是用Web CLI 是可以進去做設定，已經成功設定Lora地區，而且螢幕有顯示功能抓到我的另外一個 Heltec V3 (firmware v2.3.3)，想請問這個問題要怎麼解決?
    - 沒有開 wifi 哦, 就只有刷機、改Region。其實昨天試刷 2.3.4就不行了，而且ios手機的 mesh app 會一直嘗試抓這台，而不顯示我的另一台，無論我怎麼取消 (斷開)連線，app 都一直是嘗試對這台連線並倒數，最後倒數結束就關閉app.
        - 到手機的藍牙設定裡面把這臺裝置遺忘掉看看
        - 解決了! 確實是清除藍牙設定並重抓就可以了!
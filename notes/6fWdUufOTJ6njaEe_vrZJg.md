---
tags: cofacts, meshtastic, heltec, 電池, 太陽能
---

# Cofacts 快速回應韌性計畫

## 電池

### iSolar SB600
- [Spec](https://www.isolars.com.tw/zh-TW/products/600w%E8%A1%8C%E5%8B%95%E5%85%85%E9%9B%BB%E7%AB%99):
	- 600W AC output
	- 300W AC input
	- 電力 500Wh
- ~~說明書~~ 只有英文說明影片 https://www.youtube.com/watch?v=3jLYIIXbzEQ
- 可以接哪些電器
	- 電腦+螢幕+燈+喇叭+一堆電器：80W 以內，可用 6 小時
    ![](https://g0v.hackmd.io/_uploads/BJU-28m8Ze.png =x200)
	- 400W 小吹風機 [name=mrorz] 可用
	- 600W 快煮鍋
	- 微波爐：定頻微波爐會使用約 1200W，微波爐會自動熄滅，且會電池進入過載保護狀態（顯示 OVERLOADED 燈）。
		- 微波爐是 pulse wave modulation [name=alfred]
- Check light：要按住
- 市電充電速度
	- 理論：1.8 hr 完全充滿
	- 實測：任意家用插座 1.5 hr 後即顯示 100%、input 瓦數歸零停止充電 [name=mrorz]
	- 實測：從 66% 到 95% 大約 20~30 分鐘，但是卡在 95% 5分鐘以上(輸入顯示維持在 300 W)，不知道發生什麼事 [name=nonumpa]

### iSolar SB200
- [Spec](https://www.isolars.com.tw/zh-TW/products/200w-%E8%BC%95%E4%BE%BF%E8%A1%8C%E5%8B%95%E5%85%85%E9%9B%BB%E7%AB%99%E5%8F%AF%E6%90%AD%E9%85%8D%E5%A4%AA%E9%99%BD%E8%83%BD%E6%9D%BF%E4%BD%BF%E7%94%A8)
	- 200W AC output
	- 36W DC input (15V 2.4A)
	- 電力 155Wh
- 可以接哪些電器
	- 投影機 + 充電，可用於行動投影最新訊息或指示用 ![](https://g0v.hackmd.io/_uploads/SJcLXDmU-g.png =x200)
	- 投影機 + 筆電：使用 50 分鐘 
- 注意處
	- 接上帶有喇叭的電器（如投影機），會有明顯電流聲，但不影響使用
- 市電充電速度
	- 理論：4.3hr（只有 DC input）
	- 實測：


## 太陽能板

- [Spec](https://www.isolars.com.tw/zh-TW/products/125w-%E8%BC%95%E5%9E%8B%E5%8F%AF%E6%8A%98%E7%96%8A%E5%A4%AA%E9%99%BD%E8%83%BD%E6%9D%BF)
	- Pmax: 125W
- 實驗：[name=mrorz] ![](https://g0v.hackmd.io/_uploads/HJgHCDw7UZe.png =x200) ![](https://g0v.hackmd.io/_uploads/HkTyuP7UZl.png =x200)
	- 時間：2026/1/25 12:00 左右
	- 溫度：攝氏 24 度有風
	- Cloud Type: Altocumulus / Ac（高積雲）
	- Cloud Cover: 7/8 ![](https://g0v.hackmd.io/_uploads/Hy-W_vXUbg.png =x200)
	- Light: Diffuse
	- Solar input: 20W~40W
		- 若以 30W 平均、發電 5 小時計，僅能充 150 Wh，是 500Wh 電池的 30%

## Meshtastic

> https://heltec.cashier.ecpay.com.tw/product/000000000869165
> [Modem 模式](https://www.facebook.com/groups/meshtastictw/posts/753684390374089/)：Medium Fast（MF），Frequency Slot：1

### Heltec V4 裝置
1. 解開背後螺絲打開背蓋，放進電池（注意正負極
   ![](https://g0v.hackmd.io/_uploads/rJVmeVTSbl.png =x200)
2. 裝入電池後即會開機；可以先長按按側邊 PWR 按鈕，把機器關掉
3. （Optional：把夾子裝上背蓋後）裝回背蓋
4. 長按 PWR 開機；RST 重開機
5. 長按 USER 進入選單
   ![](https://g0v.hackmd.io/_uploads/BJgXBGB6H-e.png =x200)
6. 進入 Set the LoRA region：短按 USER 到出現 `TW` 之後，長按 USER 選擇
   ![](https://g0v.hackmd.io/_uploads/rkAwGraSZg.png =x200)
7. 自動重開，進入主要畫面
   ![](https://g0v.hackmd.io/_uploads/S1lUd7HaHbx.png =x200)

:::info
這款 Meshtastic 顯示的介面叫 [BaseUI](https://meshtastic.org/docs/configuration/device-uis/baseui/)
:::

### 手機
1. 安裝 App
	- Android app https://meshtastic.org/docs/category/android-app/
	- Apple app https://meshtastic.org/docs/category/apple-apps/
2. 打開 App 將一開始的權限設定完成後，點開「連線」Tab，開啟藍芽
3. 點擊 Heltec V4 螢幕上顯示的裝置名稱
5. 輸入 Heltec V4 螢幕上顯示的配對密碼
   ![](https://g0v.hackmd.io/_uploads/r1lv9VB6H-l.png =x300) ![](https://g0v.hackmd.io/_uploads/S1RMNHpHWe.png =x300)


### 在手機上完成 Heltec 設定

> 以下內容出處: https://www.facebook.com/share/p/1Hftn51U3N/
1. 用手機掃描 QRcode 它會幫你完成基本頻率的設定（Medium Fast、Slot 1、加入台灣頻道） ![](https://g0v.hackmd.io/_uploads/SJ7VDE6SWg.png =x200)
   - 使用 QRcode 設定後，會出現四個頻道，以下解釋各個頻道的用途
      - MediumFast：預設頻道。這個是 Meshtastic 內建的預設頻道，此頻道的內容沒有加密，因此大家通常也不會用這頻道講話。
      - SignalTest：測試頻道，讓大家隨意測試使用，各種機器人也會在此回應大家的測試。
      - MeshTW：討論頻道。不過由於和平時期不太會有事情需要在上面討論，所以這裡面平常沒什麼對話。iOS 用戶在掃描 QRcode 之後有高機率不會出現這個頻道，請手動把它加入。頻道名稱：MeshTW。金鑰長度：256。金鑰：isDhHrNpJPlGX3GBJBX6kjuK7KQNp4Z0M7OTDpnX5N4=
      - Emergency!：緊急頻道。當需要透過 Meshtastic 求救時請使用這個頻道。若沒有緊急需求，則不要隨意在此頻道內發言。
		- 接受後 Heltec 會重新開機
2. 接下來進入 Meshtastic app 設定頁，一起完成基本設定
    - 用戶設定→幫自己的裝置取一個好記的名字吧！這樣不論是自己看、或是其他人識別，都會比亂碼來的好記。做完以後並儲存設定。
    - 如果出現錯誤訊息說裝置已斷線，這是正常的。可以在裝置自動重開機完成後，再次確認一下裝置名稱是否已經改變。如果已經改變就可以往下一步邁進。
3. MQTT 發訊息測試
    1. 模組設定 MQTT → 最上方「啓用」 MQTT 的開關打開、並且把「加密」的開關也打開。
       「根話題」的部分設定成「msh/TW」（要完全一樣）。「客戶端的代理」也要打開。
    	 儲存、等待機器重開
    2. 點選畫面左下角的圖示，進到發訊息的畫面，選擇「SignalTest」，輸入 @ab newbie 並發送
    3. 如果有成功，你會看到一個名為 8780 的機器人重複你剛剛說的 @ab newbie
       ![](https://g0v.hackmd.io/_uploads/Syl9ZLHTBWe.png =x500)
    4. 如果重複試了三次都沒有收到機器人的回應，可以回到上一步檢查設定是否正確。如果檢查不出來哪裡有問題，把以上設定的畫面截圖或錄影，傳送到 [Meshtastic Taiwan 社團](https://www.facebook.com/groups/meshtastictw) 的聊天室中讓大家幫你看看
4. 改用 LoRa 發訊息測試
   1. 設定關閉 MQTT
   2. 點選畫面左下角的圖示，進到發訊息的畫面，選擇「SignalTest」， 輸入 @ab lora 並發送
   3. 如果有成功，你會看到一個名為 8780 的機器人重複你剛剛說的 @ab lora，而且[訊息顯示有 Hops 數](https://www.facebook.com/groups/meshtastictw/posts/755783756830819/?__tn__=%2CO*F)，就代表你成功了！可以繼續往下一關邁進！
      - 什麼是 Hops 數？因爲 Meshtastic 是去中心化的網路，你發送的訊息會透過其他的裝置，一路跳著傳播出去，因此 Hops 數就代表著你的訊息跳著經過了幾台裝置。如果 MQTT 開啓，訊息透過網路直通 @ab 機器人，就不用跳，就不會有 Hops 數。
      - 如果你看到 8780 有回應你，但訊息沒有顯示 Hops 數，這時候可能你還是使用 MQTT 在對話，可以到設定頁確認看看 MQTT 是否有關閉。
      - 果你有傳送出去，但卻沒有收到機器人的回訊。這時候可以使用 Telegram 這個通訊軟體，搜尋並新增一個好友 @MeshTW_MQTT。這裡面會顯示所有被轉發到 MQTT 上的訊息。所以有時候我們的訊息有成功出去、也有成功上到 MQTT，但機器人回覆回來時因爲一些問題，導致最終沒有收到機器人的回訊。這時候就到 Telegram 的 @MeshTW_MQTT，找到 SignalTest 這個分類，看看你剛剛傳的訊息有沒有出現在上面。
      - 如果你的訊息有出現在上面，機器人的回應也有出現在上面，那可能是你的訊號不太穩，所以沒有收到回來的訊息。
      - 如果你的訊息有出現在上面，但沒看到機器人的，那可能是機器人在忙，可以稍後再試。
      - 如果在上面沒看到你的訊息，那可能你附近沒有其他節點可以幫你轉發到 MQTT 上面，這時候可以到社團的聊天室問問看，附近有沒有人可以跟你一起測試訊號。

### TODO

- 約定通訊頻道與方式
	-  [How Meshtastic Channels Actually Work (They're Not Frequencies)](https://www.youtube.com/watch?v=wUqr6skhVCw)
	-  [Set Up Private Meshtastic Channels](https://www.youtube.com/watch?v=egAZP4KKHNo)
- 實地測試

### Hardware 

- 預設沒有裝電池，從玻璃外看到的是電池盒外殼
	- 電量顯示僅供參考，應該是用電壓算的
	    - 4.19V --> 100%
	    - 4.07V --> 91%
	    - 3.96V --> 77%
	    - 3.74V --> 52%
	    - 3.54V --> 31%
	    - 3.16V --> 3%
	- 放電到最後快沒電時，會進入自動關機+開機循環
	- 充電充到進不去之後，一直到上面的自動關機+開機循環，大約可以放 16 小時
- 可以插 Usb 直接使用
- USER 按鈕長按是確認/MENU，按一下是導覽(靈敏度好像有點低？常常按一下不會動)

### App

- App 與 mesh 藍芽配對時，mesh 上會顯示配對密碼
- 藍芽連線後會自動 sync 時間，default time zone utc+0，可在 mesh 上改 time zone (App 上找不到選項)

------

# Insights

- 烏克蘭的狀況
	- 供電：一天停 8hr ~ 16hr ([Source](https://www.cna.com.tw/news/aopl/202511090085.aspx))
	- 網路：不會停 [name=bil]
- 500Wh 的行動供電站：
	- 2hr 內可以充電完成，可在輪流供電的時候完全充飽。
	- 在電腦耗電 50W 的情形下，可以供電 10hr [Reference: Mac mini](https://support.apple.com/en-hk/103253)
	- 若需要使用電腦處理事務，功耗較桌機低的筆記型電腦還是首選。
	- 考慮筆電（Macbook 內建電池 50Wh ~ 70Wh）、手機（內建電池 16Wh，可用於連接 mobile network）、meshtastic 節點（內建電池 12Wh，用於連接 meshtastic 備援文字通訊），500Wh 電源應可支持多組以上 setup 進行全天候作業。
	- 若所在現場需要螢幕或投影顯示資訊給不特定人，500Wh 行動供電站僅供 100W 的螢幕恆亮 5 小時，較斷電時間為短，需要謹慎安排。
	- 維生方面若需要煮食，以卡式爐為佳；更高功率輸出的充電站（1200W）較貴且也比卡式爐難保存。
	- 推薦用途：
		- 不僅用於通訊與數位化作業
		- 較適合救災「團隊」，需要多組電動手工具充電、偵查無人機充電。
- 155Wh 的行動供電站：
	- 由於沒有 AC 充電，充電速度反而比 500Wh 的慢，但 4hr 仍能在供電時間內完成。
	- 155Wh 其實足夠筆電、手機、meshtastic 三裝置充飽 1~2 次，恰可維持一人全天候作業所需，但可能沒有其他餘裕。
	- 推薦用途：維持通訊以及數位化作業。
	- 考量戰時可能需要移動，行動供電站的重量與體積，可能會比容量和功率更為重要。因此，較爲建議採用 155Wh 之行動充電站或能充筆電的大型行動電源。
- 太陽能：不太需要
	- 要能充得進電池的太陽能板，即使是可以折疊的可攜型充電板，體積也相當大
	- 台灣北部天候不穩定，發電效率不佳
	- 輪流供電的時間即可讓電池充飽
	- 發電機：[name=ed]
		- 2000~5000 NTD 二手
		- 穩定、瓦數大
		- 缺點：噪音、熱源、汽油儲存（半年以上要加穩定劑）
		- Honda 保養比較好
- 可以考慮鉛酸電池 + 逆變器 [name=alfred]
	- powerbank 比較小、方便
	- 鉛酸電池：二手要找內電阻檢測器、逆變器 power output
- 要訂定目標：需要撐多久 [name=ed]
	- 第一次停電會比較猝不及防，但之後會有輪流供電。 [name=bil]
	- 烏克蘭經驗是飲食三天，電可能也可以比照辦理。
	- 初次攻擊大多是凌晨 3am（防衛最薄弱）[name=alfred]
- Alternative: 無線電
	- HF 台北到高雄（地形允許的話）[name=alfred]
	- 考個執照 (三級 --> 二級，一級需要持有無線電一年)
	- 可以先買無線電，考完執照直接去電檢
	- 最便宜：https://24h.pchome.com.tw/prod/DMAECB-A900JJ7Y3
	- 但比較推 Motorola

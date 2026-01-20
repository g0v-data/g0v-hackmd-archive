# Cofacts 快速回應韌性計畫

## 電池

- 說明書
- 可以接哪些電器
	- try 吹風機 [name=mrorz]
- Check light：要按住
- 市電充電速度

## 太陽能板

- 是否可以幫電池充電
- 什麼樣的天氣可以提供多少電、要充多久

## Meshtastic


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

### 手機
1. 安裝 App
	- Android app https://meshtastic.org/docs/category/android-app/
	- Apple app https://meshtastic.org/docs/category/apple-apps/
2. 打開 App 將一開始的權限設定完成後，點開「連線」Tab，開啟藍芽
3. 點擊 Heltec V4 螢幕上顯示的裝置名稱
4. 輸入 Heltec V4 螢幕上顯示的配對密碼

### 在手機上完成 Heltec 設定

> Source: https://www.facebook.com/share/p/1Hftn51U3N/
1. 用手機掃描 QRcode 它會幫你完成基本頻率的設定（Medium Fast、Slot 1、加入台灣頻道） ![](https://g0v.hackmd.io/_uploads/SJ7VDE6SWg.png =x200)
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
	  4. 如果重複試了三次都沒有收到機器人的回應，可以回到上一步檢查設定是否正確。如果檢查不出來哪裡有問題，把以上設定的畫面截圖或錄影，傳送到 [Meshtastic Taiwan 社團](https://www.facebook.com/groups/meshtastictw) 的聊天室中讓大家幫你看看
4. 改用 LoRa 發訊息測試
		1. 設定關閉 MQTT

### TODO

- 約定通訊頻道與方式
- 實地測試

### Hardware 

- 預設沒有裝電池，從玻璃外看到的是電池盒外殼
- 可以插 Usb 直接使用
- USER 按鈕長按是確認/MENU，按一下是導覽(靈敏度好像有點低？常常按一下不會動)

### App

- App 與 mesh 藍芽配對時，mesh 上會顯示配對密碼
- 藍芽連線後會自動 sync 時間，default time zone utc+0，可在 mesh 上改 time zone (App 上找不到選項)

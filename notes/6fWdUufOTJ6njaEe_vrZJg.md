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

> 設定：https://www.facebook.com/share/p/1Hftn51U3N/
> [Modem 模式](https://www.facebook.com/groups/meshtastictw/posts/753684390374089/)：Medium Fast（MF），Frequency Slot：1

### Heltec V4 裝置
1. 解開背後螺絲打開背蓋，放進電池（注意正負極）![](https://g0v.hackmd.io/_uploads/rJVmeVTSbl.png)
2. 按下電池後即會開機；可以先長按按側邊 PWR 按鈕，把機器關掉
3. （Optional：把夾子裝上背蓋後）裝回背蓋
4. 長按 PWR 開機；RST 重開機
5. 長按 USER 進入選單
6. 進入 Set the LoRA region：短按 USER 到出現 `TW` 之後，長按 USER 選擇
7. 自動重開，進入主要畫面

### 手機
1. 安裝 App
	- Android app https://meshtastic.org/docs/category/android-app/
	- Apple app https://meshtastic.org/docs/category/apple-apps/
2. 打開 App 將一開始的權限設定完成後，點開「連線」Tab，用藍芽


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

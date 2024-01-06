# iot 構想
透過rfid與wifi連線，並透過類似git的方法更新大氣資料的檔案

## sensor unit
wifi+lora+其他中遠距離傳輸通訊 sensor rfid-module
透過rfid對機器資料進行更新與監測
並透過rfid進行狀態更新
- 對於outside control unit的狀態更新->是否要開始記錄他的資料(創建一個讀它資料的block)
- 需要對於自己的rfid id做紀錄

## outside control unit
- 有rfid_id->user_define_id的對應
- 收資料，並儲存於sd卡
- 固定時間再上傳資料
- 

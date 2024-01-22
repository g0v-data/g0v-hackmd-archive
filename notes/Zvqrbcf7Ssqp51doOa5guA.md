# SD2AIO學習筆記（SmallDesktopDisplay）
Github：https://github.com/stu9458/SD2AIO_Emp

## 原始介紹
* 原  作  者：Misaka
* 修      改：微车游
* 讨  论  群：811058758、887171863
* 创 建 日 期：2021.07.19
* 最后更改日期：2021.09.14
* 更 改 说 明：V1.1添加串口调试，波特率115200\8\n\1；增加版本号显示。
    * V1.2.0
        * 亮度和城市代码保存到EEPROM，断电可保存
    * V1.3.1 
        * 更改smartconfig改为WEB配网模式，同时在配网的同时增加亮度、屏幕方向设置。
    * V1.3.2 
        * 增加wifi休眠模式，仅在需要连接的情况下开启wifi，其他时间关闭wifi。增加wifi保存至eeprom（目前仅保存一组ssid和密码）
    * V1.3.3  
        * 修改WiFi保存后无法删除的问题。目前更改为使用串口控制，输入 0x05 重置WiFi数据并重启。
        * 增加web配网以及串口设置天气更新时间的功能。
    * V1.3.4  
        * 修改web配网页面设置，将wifi设置页面以及其余设置选项放入同一页面中。
        * 增加web页面设置是否使用DHT传感器。（使能DHT后才可使用）


## 運行順序(void Setup())：
1. 開啟Serial
2. 從EEPROM中讀取背光、屏幕等資料
3. TFT顯示屏幕設定、搭配背光顯示
4. 從EEPROM中讀取Wi-Fi的資料，並啟動WiFi，若失敗則會顯示Fail，可以自行用網頁重新連線
5. 從EEPROM中讀取City的資料
6. 在螢幕上顯示溫度、濕度的圖標
7. 關閉Wi-Fi.

## 運行順序(void loop())：
1. 重新刷新LCD的屏幕，使用函示「LCD_reflash」
2. 開啟串口Serial_set()
    * 可從外部用UART設定亮度
    * 地址(城市代碼)
    * 屏幕顯示方向
    * 設置天氣更新時間
    * 重啟WiFi.

## 參考資料
1. TCP 和 UDP 是什麼：簡單的說明. https://nordvpn.com/zh-tw/blog/tcp-udp-bijiao/
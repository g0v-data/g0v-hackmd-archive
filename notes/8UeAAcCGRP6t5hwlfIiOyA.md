# ESP32: FastLED  vs. NeoPixel Library

資料來源: https://blog.ja-ke.tech/2019/06/02/neopixel-performance.html

* **簡介:** 驅動 WS2812B 的 RGB LED 中三個最受歡迎的程式庫效能比較，一切都是用邏輯分析儀測量的。

* **函式庫在 ESP32 平台上產生訊號的方法:**
    1. Adafruit NeoPixel 程式庫完全透過軟體實現（classic bit banging）。
    2. NeoPixelBus 利用 I2C 控制器硬體將資料寫出。
    3. FastLED用RMT，一個 ESP32 特定驅動程序，實際上用於紅外線遙控訊號，但對於許多其他應用來說足夠靈活。
    
    
* **NeoPixel的缺點:**
    經典的NeoPixel 函式庫有一個嚴重的問題，位元碰撞在ESP32 上不適用於超過33 個像素，因為底層FreeRTOS 每毫秒都會進行一次勾選（可能還有任務切換），這會導致資料損壞:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_666efda168874e4ed488f3e5541eef30.png)
(每個像素這裡應該是0x001a00）
這也會擾亂後續晶片的回傳，因此它們通常都會顯示錯誤的顏色。

* **測試方法:**
1. 將一個 LED 切換為綠色和黑色.
2. 用單一顏色填充整個條帶並將其關閉（黑色）.
3. 計算具有線性色調漸變的彩虹並再次將其關閉。
    
    每個動作都以盡可能快的速度完成一百次。
5. 此外，程式碼為邏輯分析儀寫入一個觸發引腳，並在每次循環後透過序列列印出可用堆 (RAM)。

    **測試時的版本:**
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e061d3e011ca84a07c62b02d469ed4c4.png)

**比較:**
1. Flash(快閃記憶體):
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_303057314d3c8b3db03fb6e584afbec6.png)
由於 FastLED 至今擁有最多的功能，而 NeoPixel 的功能最少，因此這一結果並不令人意外。


    **推論**: Flash的使用量與功能數有關

2. RAM
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fe39a5e9a7bf951068dac39c61ec87dd.png)

    **Adafruits NeoPixel < FastLED  .**



3.  **使用100LED燈條的傳遞延遲:**
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a84d279cf75564da7a10402296021f65.png)
    
    **Adafruits NeoPixel < FastLED  .**
    
    NeoPixel 幾乎沒有延遲（只有 2 μs），位元碰撞幾乎不需要任何設定。
    不過，他們似乎將重置持續時間設定為不必要的長 300 μs，這使 FastLED 總體上略微領先。
    

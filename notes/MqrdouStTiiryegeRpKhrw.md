# ESP系列學習筆記

1. 使用CH340的ESP-12F(DOITING)的，燒錄與反應上時常會Timeout，即使使用成BaudRate 9600也是一樣. 
2. CH340的使用上有時候會遇到Permission(權限)的問題，使用2011年的Driver即可
3. 交叉比對轉換成CP210x後的NodeMCU 1.0反倒無此問題，燒錄上就算使用較高的BaudRate反而可以加快速度(921600)


WS2811/WS2812的使用注意事項:
1. NeoPixelBus此Lib使用只有在ESP32上. 主要對應IC的PinPort不同. 若要延伸在ESP8266上的話不少Lib的腳位要改、甚至要自己增添Defined.

2. ESP12/ESP8266建議使用Adafruit NeoPixel


主要Function:
* 大部分的函式使用: strip.函式

1. Adafruit_NeoPixel pixels(燈數, 訊號腳, NEO_GRB + NEO_KHZ800):宣告NeoPixel strip物件
    設定
    // NEO_KHZ800 800 KHz 位元流（大多數 NeoPixel 產品帶有 WS2812 LED）
    // NEO_KHZ400 400 KHz（經典‘v1’（不是 v2）FLORA 像素，WS2811 驅動程式）
    // NEO_GRB 像素連接至 GRB 位元流（大多數 NeoPixel 產品）
    // NEO_RGB 像素連接為 RGB 位元流（v1 FLORA 像素，而非 v2）
    // NEO_RGBW 像素連接為 RGBW 位元流（NeoPixel RGBW 產品）

3. begin():初始化MCU對WS2812的Output動作與電位.
4. updateLength():可以修改Pixcel(即燈數)![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ebc7127a9e64962263b792a4f05c86d5.png)

3. updateType():改變Pixcel的Format. 例如原本是RGB, 可以改成GBR等.![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5ce37b7ce20e6a0405de3762300a1247.png)

4. show():讓WS2812顯示所接收到數值.在ESP8266的對應中，他使用了Function espShow(pin, pixels, numBytes, is800KHz); 腳位對應好後、位移亮燈.
6. delay_ns()
7. setPin(): 修改MCU對應的腳位輸出.(即Arduino對應腳位)
8. setPixelColor()
9. fill()：填滿全部或部分的燈具，可輸入參數包含顏色、從哪一個index開始、共幾顆燈![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_34b028d35764589750aca266b7b9c33e.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4c2220ed9892bcbbdf5e756ff326b835.png)
fill ( uint32_t color,uint16_t first, uint16_t count)

10. ColorHSV():修改色調、飽和度、亮度![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_79f4ee91b408da0abbadedcdd8bcd98d.png)

11. getPixelColor():因為setBrightness()的關係. 可以取回相對應Pixcel設定的值![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4e6f46776db77b0b5bbba4183ca8add0.png)


12. setBrightness():燈具亮度調整，用bit shift的寫法來控制燈具亮度，且可以避免使用者輸入錯誤導致除以零的情況![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e78d5a6f80a90c21fcd925f9a638a674.png)

13. getBrightness():取回最後用setBrightness()設定的結果.
14. clear():將全部的Pixcel都清除成0.
15. gamma32():調整32bits的GAMMA值，Gamma是為了解決人眼對自然亮度非線性感知的問題，其二是因為人眼記錄存儲的有限性。舉例而言，一間未點燈的屋子內，點亮了一隻燈泡，人眼會感覺照亮整間屋子，持續點亮第2個、第2個......燈泡後，人眼會感覺屋子逐漸變得明亮，此時再點亮第N+1個燈泡，其實人眼沒有什麼感覺甚至微乎其微
其實亮度對人眼的刺激是非線性的，第1個和最後一個燈泡點亮對人眼的刺激感覺是不同的，人眼感覺黑->白範圍「有限」，燈泡可以無限，但感覺會趨於一個有限制值
所以可以理解為：此時輸入＝燈泡的強度，輸出＝人眼的感覺，大自然中，感覺的差別閾限隨原來刺激量的變化而變化，這是著名的韋伯定律![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a5dd17348a7b3bda3f880fd8d7d7bb93.png)



1. 函式參考網址: https://adafruit.github.io/Adafruit_NeoPixel/html/class_adafruit___neo_pixel.html#aa1898f089b9a4e02841cec2e63b88c33
2. ESP32: FastLED vs. NeoPixelBus vs. NeoPixel Library: https://blog.ja-ke.tech/2019/06/02/neopixel-performance.html#ws2812b-protocol


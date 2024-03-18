# Fastled 4.0(arduino)

## 簡介:
* **特色** : 
1. 切換LED模組，只需要修改些許設定
2. 有直觀的顏色呈現方式
    * **CRGB** 以紅、綠、藍的比例改變顏色，且函式庫內建顏色也可引用
    * **CHSV** 以色調(顏色座標)、漂白度(數值越**小**就越**白**)、亮度
3. 有數學運算可以幫助LED做出變化
    * 三角函數, ex. sinbeat()
    * 隨機變數 noise()
    * 淡化顏色 fadeToBlackBy()
4. 基本上所有的數值都在0~255的範圍之內

* **使用模組WS2812B的特點**: 
1. 只需要1個input就可以控制多個LED
2. 使用bit-banging通訊協定
3. 燈條上的LED由3個顏色組成，8個Byte一個顏色，1個LED佔24 Byte

* **作者使用此庫的邏輯**:

1. 做好**初始設定**(LED陣列、模組設定)
2. 將每一個變化做成個別**副函式**
3. 在主體函式中設置**選擇副函式**的函式
4. 用`FastLED.show();`使LED表現
5. 
## 使用前設定
![螢幕擷取畫面 2024-03-16 213817](https://hackmd.io/_uploads/rJw7-QXA6.jpg)
1. **建立LED一維陣列**
`CRGB leds[NUM_LEDS];`

    ```
    leds     = 自訂義的陣列名稱
    NUM_LEDS = 所有的LED數量
    ```

* 補充 : 可宣告一個帶有一個額外像素的 LED 作為緩衝區。
    ex. [ NUM_LEDS+1] 

2. **初始設定**
`FastLED.addLeds<LED_TYPE, LED_PIN, COLOR_ORDER>(leds, NUM_LEDS);`

    ```
    LED_TYPE    = 使用模組
    LED_PIN     = 訊號腳位
    COLOR_ORDER = 顏色接收方式 ex. RGB、GRB
    leds        = LED燈串陣列
    NUM_LEDS    = 燈串上的LED數量
    ```
 
## 基礎function
1. **設定亮度**
    `FastLED.setBrightness(value);`

    **亮度(0~255)**, **0為熄滅**.
    下圖為亮度數值測試:1、10、50、100、150、255

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3429940efe922e713ef0b1d2667aaa28.jpg)


2. **讓LED顯示顏色**
    `FastLED.show();`

3. **描述顏色**

* **RGB(紅綠藍)**
![image](https://hackmd.io/_uploads/SyNFSCBTa.png)
    ```
    leds      = LED陣列
    i         = 第幾個LED(LED位移量)(從0開始)
    CRGB(, ,) = ()內為初始設定中顏色表現方式ex. rgb 紅綠藍
    ```
     

    Color代碼:      http://www.taichi-maker.com/homepage/reference-index/arduino-library-index/fastled-library/rgb-color/
      ![image](https://hackmd.io/_uploads/S1f54ABa6.png)
      
    * 三值相同，白光 ; 三值皆為0則不亮。
    * 簡易的方法輸出(引用內建顏色)CRGB::顏色名稱(Black熄燈)

* **CHSV**
![image](https://hackmd.io/_uploads/H1RwECB6T.png)

    ```
    leds      = LED陣列
    i         = 第幾個LED(LED位移量)(從0開始)
    CHSV(, ,) = ()內為色調(顏色座標) 漂白度(越小越白) 亮度
    ```
    
    **補充**
    可先設定好顏色，再引用
            ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e29aa73a3ba368c622f1b7b5ba80688b.png)
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6c2010af0edf4b9875da29639702c0f5.png)
    * **rgb分別對應HSV數值 :** 
        r = 0; g = 95; b = 160;

## 填色function
* **大致架構** : function(LED陣列+偏移量, 長度, 顏色, ...其他設定);
    * 偏移量 = 從第n+1個LED開始填色
    
1. **將單一顏色放入n個相鄰的LED中**
    **fill_solid();**
    
    
    `fill_solid( leds+i , 2 , CRGB::Red);`  

    ```
    leds+i    = 從第n+1個LED開始填色
    2         = 要填滿多少個LED(長度)
    CRGB::Red = 顏色(不拘)
    ```

    **範例:**
      
    V`fill_solid(leds, 8, CRGB(255,0,0));    ` (CRGB)
    V`fill_solid(leds+1, 1,CHSV(0,255,255) );` (HSV)
    X`fill_solid(leds+1, 1,0);_____________        .` (HSV錯誤 : **顏色**不能只填Hue值)
    
    **補充:**
   *  `fill_solid(leds,numLED , CRGB::Black);`
       可以清空所有一定範圍內LED的顏色(熄滅)。
       
       
2. 	**將LED以固定色差填色**
    **fill_rainbow ();**
    
    `fill_rainbow( leds+i , 2 , 0, 20);`
      
    ```
    leds+i    = 從第n+1個LED開始填色
    2         = 要填滿多少個LED(長度)
    0         = 初始色調值，亦可放入CRGB顏色
    20        = 相鄰LED的色差值
    ```     
     V`fill_rainbow( leds+i , 8 , CRGB :: Red, 20);`(CRGB)
     V`fill_rainbow( leds+i , 2 , 0, 20);__________`(CHSV)
     X`fill_rainbow( leds+i , 8 , CRGB(255,0,0), 20);`(CRGB錯誤)
    
    

    **test:**
    ![image](https://hackmd.io/_uploads/SkCnOdoiT.png)

    **補充:**
    * 255為色差上限值 = 色差0 = 顏色不變
    
3. **將LED填色，但開始&結束LED會之間的色差會 = 其他相鄰的LED之間的色差**  **(可改變色差增加的方向，順時針/逆時針)**
    `fill_rainbow_circular( leds+i , 5 , 0, false);`
      
    ```
    leds+i    = 從第n+1個LED開始填色
    5         = 要填滿多少個LED(長度)
    0         = 初始色調值，亦可放入CRGB顏色
    false     = 是否反轉
    ```




    **test:**
    ![螢幕擷取畫面 2024-02-04 220647](https://hackmd.io/_uploads/ryQOsGT9T.jpg)
    //因漸層不清楚所以之後會再用更多LED的燈串進行一次測試
    
4. **在LED_A(顏色1)到LED_B(顏色2)之間的LED，做出顏色1~顏色2的漸層.(最多可以支援到3次漸層變換)**
    `fill_gradient() & fill_gradient_RGB()`
    
     **功能:** 
     
    fill_gradient()
    ![image](https://hackmd.io/_uploads/ByYKNMKqa.png)
    
    fill_gradient_RGB()
    ![image](https://hackmd.io/_uploads/BydHEzKca.png)

    **相同:** 
    1. 有2種函式寫法分別為
        * 2點顏色 : 用於一次漸層
        * 起點顏色+長度+結點上的顏色 : 用於多次漸層(結點至多4個)
    2. **多次漸層變化** : 會將所有的LED平均長度分配每一段漸層。
        若分配不均，則顏色節點會不均勻分布，而不是被平均分配，並被隱藏。
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8df7681f5a4112d1ef3129952dfe6a7c.png)


    **不同:** 
    1. `fill_gradient();`、`fill_gradient_RGB();`分別只能放入CHSV、CRGB的顏色。
    2. `fill_gradient();`可調整漸層方向，`fill_gradient_RGB();`不行
    3. `fill_gradient_RGB();`比較直觀
    

    * **2點之間的漸層**
    `fill_gradient_RGB ( leds+i , 0 , CRGB :: Blue , 7 , CRGB :: Purple );`

        ```
        leds+i         = LED起始位置(i為位移變數)
        0              = LED在陣列編號，漸層開始的LED
        CRGB ::Blue    = 漸層開始的LED的顏色
        7              = LED編號，漸層結束的LED.
        CRGB :: Purple = 漸層結束的LED的顏色
        ```       
        **test:**
    ![image](https://hackmd.io/_uploads/B1tLzGFca.png)
        
    * **以起點、長度、顏色作漸層**
    `fill_gradient( leds+i , 7 ,  CHSV(20,255,255) , CHSV(100,255,255) ,  FORWARD_HUES );`
        ```
        leds+i           = 從第n+1個LED開始填色
        7                = 顏色漸層要進行的長度
        CHSV(20,255,255) = 漸層開始的LED的顏色
        CHSV(100,255,255)= 漸層結束的LED的顏色
        FORWARD_HUES     = 設定漸層的方向(下方有可輸入內容&例子)
        ```
        ```
            FORWARD_HUES: hue always goes clockwise
            BACKWARD_HUES: hue always goes counter-clockwise
            LONGEST_HUES: 長色調過渡(選色調變化大的方向做漸層)
            HORTEST_HUES: 短色調過渡
        ```
    
    **test**
    ![image](https://hackmd.io/_uploads/S162sGKc6.png)


5. **透過熱量控制燈的顏色.**
    `HeatColor();`

    ![image](https://hackmd.io/_uploads/B14CIw5qp.png)



 fadeToBlackBy( leds, NUM_LEDS, 10);數值越大，淡化越多(亮度減少n/255)


## **幫助**
1. **check**
    * 在LED陣列中，LED數量與實際是否相符
    * 是否有正確設定模組...
        `FastLED.addLeds<LED_TYPE, LED_PIN, COLOR_ORDER>(leds, NUM_LEDS);`
    * 是否有使用FastLED.show();來使LED顯示顏色

2. **簡易測試用程式碼**
```
#include <FastLED.h>
#define NUM_LEDS 60
CRGB leds[NUM_LEDS];
void setup() { FastLED.addLeds<NEOPIXEL, 6>(leds, NUM_LEDS); }
void loop() {
    leds[0] = CRGB::White; FastLED.show(); delay(30);
    leds[0] = CRGB::Black; FastLED.show(); delay(30);
}
```

3. **Reddit 社群** https://reddit.com/r/FastLED
該群組中有數千名知識淵博的 FastLED 用戶，並且在過去的歷史中提供了大量的解決方案。
4. **提交**函式庫錯誤/請求對特定平台或 LED 晶片組的支持的地方
    http://fastled.io/issues。


5. **Lib**:  https://fastled.io/docs/group__lib8tion.html
2024/01/23 對照FastLED 3.6.0版本

6. **ESP32: FastLED vs. Adafruit NeoPixel Library** :
https://hackmd.io/ggUsEFdSTEyn-3PZyRRDpA
7. **範例閱讀**: https://hackmd.io/ZAe2UHTpThaQr3gXXbzMcw?view

## **應用:**
1. **外在的表現形式**

    1.1 **顏色意義**:
例子.
裝置收到簡訊/電話就亮顏色，爸爸是藍色、媽媽是紅色、姊姊是紫色.....，使用者可以輕易地讀取裝置所傳遞的訊息。
也可以讓裝置發出的聲音與顏色綁定。

    1.2 **頻率意義**:
    例子.
    裝置收到家人、公司的簡訊/電話，就亮3下，普通的提醒亮2下、其他亮1下。

    1.3 **裝飾意義**:
    例子.
    某些人可能喜歡閃爍移動的東西，就可以設置一個主動觸發在裝置上，被觸發後呈現美麗的色彩變幻。

2. **暗號**:

    透過特殊的頻率與朋友、戀人溝通，像是1長燈光訊號代表:"你在嗎?"，回復1長燈光:"我在!"，此方向可透過螢幕做出連動。

## **資料來源:**
**Fastled 3.6.0版本:**
https://fastled.io/docs/group__lib8tion.html

**Fastled 3.0(Arduino)** (前一版本筆記)
https://hackmd.io/h8BaXEyNQVCjUq-Pc266WQ?view
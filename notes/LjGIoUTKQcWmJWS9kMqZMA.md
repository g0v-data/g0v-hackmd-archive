# Fastled(Arduino)
#include <fastLED.h>函示庫
  **前置**
1.   CRGB 物件名稱[NUM_LEDS]
        建構物件，物件名稱可自訂，括弧中的參數NUM_LED為串接的LED數量
        
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cdaf5cb4c621e37f53ffd158048135e7.png)

2.   FastLED.addLeds<WS2812B, DATA_PIN, RGB>(自訂義, 燈數);
      設定串列全彩LED參數，其中
      WS2812B : 控制LED模組的晶片型號，其他可支援的型號請參考函式庫說明
      DATA_PIN : 控制LED模組的資料腳位
      RGB : 控制LED模組RGB三原色的順序，須根據所連接的訊號線路調整
  
      
 **顏色函式**
 i: 第i顆LED
 
 1. 類別名稱[i] = CRGB(R值, G值, B值);
     RGB顏色模型，設定LED的顏色，參數範圍如下
     R值 : 0~255
     G值 : 0~255
     B值 : 0~255

     可用簡易的方法輸出    CRGB::顏色名稱(Black即為無色)
* color代碼:
  http://www.taichi-maker.com/homepage/reference-index/arduino-library-index/fastled-library/rgb-color/
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_89367c0607d6aed240c0c47c2e1bc527.png)



 2. 類別名稱[i] = CHSV(H值, S值, V值);
     HSV顏色模型，設定LED的顏色，參數範圍如下
     H值 : 色相/色調 (Hue) 0~255
     S值 : 飽和度(Saturation)  0 ~ 255 
     V值 : 色調  (Value) 0~255
 
 
此為矩陣*數值輸入的用法
```
int rainbow16[8][3]={{255,   0,   0},    //紅
                     {255,  85,   0},    //橙
                     {255, 170,   0},    //
                     {255, 255,   0},    //黃
                     {170,   0, 255},    //
                     {255,   0, 255},    //洋紅
                     {255,   0, 127},    //
                     {255, 255, 255}};   //白
                     
                     
    for(int i=0;i<NUM_LEDS;i++)  //輪流讀表設定LED顏色
    {
    faya_colorSticker[i] = CRGB(rainbow16[i][0],rainbow16[i][1],rainbow16[i][2]);
    FastLED.show(); 
    delay(200);
    }
```
**其他函式**
1. FastLED.setBrightness(BRIGHTNESS);
    設定串列LED的亮度 (BRIGHTNESS範圍 : 0~255)
2. FastLED.show();              點亮已設定好顏色的LED.
3. FastLED.clear();             熄滅所有的LED.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_09a8da50fda7b8e69508901fd24d0f0c.png)


# **FastLED 2.0:**
https://g0v.hackmd.io/lTwR96qzRqindP5JtOZW3w?view





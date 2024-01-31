# **FastLED 3.0 addition**

# Function: 
1. fill_solid()
    
    功能: 將LED填滿單一顏色，範圍可調整。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f09eb1dcfb4a15c54c971bc5ede76b90.png)


    **ex.** `fill_solid( leds+i , 2 , CRGB::Blue);`
    
    **用法:**
  i = 從第幾個LED開始填色
  2 (數字) = 要填滿多少個LED(長度)
  CRGB :: Blue = 顏色，用CRGB、CHSV都可以
    
    **tip:**
    *      要記得在填完顏色後用FastLED.show();顯示.
    *      fill_solid(leds,numLED , CRGB::Black);可以清空所有LED的顏色.
        `p.s. numLED = 放入燈條上LED數`

    *      leds的名稱目前不能改變(未探討，應該與leds[NUM_LEDS];有關).
    *      用CRGB、CHSV的顏色時可以用設定好的顏色.
    (但不能GRGB :: 自訂義顏色名)
    
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e29aa73a3ba368c622f1b7b5ba80688b.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6c2010af0edf4b9875da29639702c0f5.png)
2. 	fill_rainbow ()

    功能: 將LED填滿不同顏色，LED之間色差範圍、長度可調整。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f0ed8b4c4aa973b088949a1a15152fe2.png)
**ex.** `fill_rainbow( leds+i , 2 , 10, 20);`
  i = 從第幾個LED開始填色
  2 (數字) = 要填滿多少個LED(長度)
  10 = 第一個LED的色調
  20 = 之後相鄰LED之間的色調差

# Other:

1. leds[NUM_LEDS];  可能為初始化LED陣列的函式


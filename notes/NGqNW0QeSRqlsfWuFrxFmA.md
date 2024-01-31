# **FastLED 3.0 addition**

# Function: 
1. fill_solid()
    
    功能: 將LED填滿單一顏色.(長度可調整)
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

    **功能:** 將LED填滿不同顏色，相鄰LED有相同的色差值.(可變更色差、長度)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f0ed8b4c4aa973b088949a1a15152fe2.png)
**ex.** `fill_rainbow( leds+i , 2 , 10, 20);`
  i = 從第幾個LED開始填色
  2 (數字) = 要填滿多少個LED(長度)
  10 = 第一個LED的色調
  20 = 之後相鄰LED之間的色調差
    
    **tip:**
    *      要記得在填完顏色後用FastLED.show();顯示.
    *      leds的名稱目前不能改變(未探討，應該與leds[NUM_LEDS];有關).

    **test:**
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7c7a4dcf43c753008a647cb019051ed1.png)
    255為色差上限值 = 色差0
    
3. fill_rainbow_circular ()
    
    功能: 將LED填滿不同顏色，相鄰LED有相同的色差值，且燈帶末端和開頭之間的色調是連續的.(可調整長度、是否reversed顛倒)
    
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7ebda746b30ab5b8027a663bab818404.png)

    **test:**
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5a062d1bba92540708001b98797dde14.png)



# Other:

1. leds[NUM_LEDS];  可能為初始化LED陣列的函式


# **FastLED 3.0 addition**

# Function: 
* 功能表: 
    1. 單一顏色
    2. 色差固定的變色 rainbow
    3. 由長度控制的所有(包括first_LED & last_LED)色差固定的 rainbow
    4. 顏色漸層
    5. 體溫改變顏色






1. fill_solid()
    
    功能: 將LED填滿單一顏色.(長度可調整)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f09eb1dcfb4a15c54c971bc5ede76b90.png)


    **ex.** `fill_solid( leds+i , 2 , CRGB::Blue);`
    
    **用法:**
  leds+i = LED陣列位移i單位，i為+/-都可.  = 從第i+1個LED開始.(第一個LED編號0)
    (與 `CRGB leds[NUM_LEDS];` 有關)
    
      2 (數字) = 要填滿多少個LED(長度)
      CRGB :: Blue = 顏色，用CRGB、CHSV都可以
    
    **tip:**

    *      fill_solid(leds,numLED , CRGB::Black);可以清空所有LED的顏色.
        `p.s. numLED = 放入燈條上LED數`


    *      用CRGB、CHSV的顏色時可以用設定好的顏色.

    
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e29aa73a3ba368c622f1b7b5ba80688b.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6c2010af0edf4b9875da29639702c0f5.png)
2. 	fill_rainbow ()

    **功能:** 將LED填滿不同顏色，相鄰LED有相同的色差值.(可變更色差、長度)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f0ed8b4c4aa973b088949a1a15152fe2.png)

    **ex.** `fill_rainbow( leds+i , 2 , 10, 20);`
        
    **用法:**
  leds+i = LED陣列位移i單位，i為+/-都可.  = 從第i+1個LED開始.(第一個LED編號0)
    (與 `CRGB leds[NUM_LEDS];` 有關)
    
      2 (數字) = 要填滿多少個LED(長度)
      10 = 第一個LED的色調
      20 = 之後相鄰LED之間的色調差
    
    

    **test:**
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7c7a4dcf43c753008a647cb019051ed1.png)
    255為色差上限值 = 色差0
    
3. fill_rainbow_circular ()
    
    **功能:** 將LED填滿不同顏色，相鄰LED有相同的色差值，且燈帶末端和開頭之間的色調是連續的.(可調整長度、是否reversed顛倒)
    
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7ebda746b30ab5b8027a663bab818404.png)
    
    **ex.** `fill_rainbow_circular( leds+i , 5 , 10, false);`
        
    **用法:**
  leds+i = LED陣列位移i單位，i為+/-都可.  = 從第i+1個LED開始.(第一個LED編號0)
    (與 `CRGB leds[NUM_LEDS];` 有關)
    
      2 (數字) = 要填滿多少個LED(長度)
      10 = 第一個LED的色調
      false = reversed(反轉)開關，可以放入true / false

    **test:**
    ![螢幕擷取畫面 2024-02-04 220647](https://hackmd.io/_uploads/ryQOsGT9T.jpg)

    
4. fill_gradient() & fill_gradient_RGB()
    
     **功能:** 在LED_A(顏色1)到LED_B(顏色2)之間的LED，做出顏色1~顏色2的漸層.(最多可以支援到3次漸層變換)
     
    fill_gradient()
    ![image](https://hackmd.io/_uploads/ByYKNMKqa.png)
    
    fill_gradient_RGB()
    ![image](https://hackmd.io/_uploads/BydHEzKca.png)

    **不同:** 
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d87b6495066c097e2da46f47f71fb1c5.png)

    **相同:** 
    1. 有2種函式寫法分別為ex1(2點)、ex2(起點+長度)，但ex1的方法只能用於一次漸層，更多次漸層就必修使用到ex2.
    2. 在做多次漸層變化時，會傾向於將所有的LED平均長度分配每一段漸層。若分配不均，則顏色節點會不均勻分布，而不是被平均分配，並隱藏。
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8df7681f5a4112d1ef3129952dfe6a7c.png)

    
    **ex1. (2點)** `fill_gradient_RGB ( leds+i , 0 , CRGB :: Blue , 7 , CRGB :: Purple );`
        
    **用法:**
    leds+i = LED陣列位移i單位，i為+/-都可.  = 從第i+1個LED開始.(第一個LED編號0)
    (與 `CRGB leds[NUM_LEDS];` 有關)
    
    0 = LED編號，漸層**開始**的LED.
    CRGB ::Blue = 漸層**開始**的LED的顏色.
    7 = LED編號，漸層**結束**的LED.
    CRGB :: Purple = 漸層**結束**的LED的顏色.
    
    **test:**
    ![image](https://hackmd.io/_uploads/B1tLzGFca.png)
    
    **ex2. (起點+長度)** `fill_gradient( leds+i , 7 ,  CHSV(20,255,255) , CHSV(100,255,255) ,  FORWARD_HUES );`
        
    **用法:**
    leds+i = LED陣列位移i單位，i為+/-都可.  = 從第i+1個LED開始.(第一個LED編號0)
    (與 `CRGB leds[NUM_LEDS];` 有關)
    
    7 = 顏色漸層要進行的長度.
    CHSV(20,255,255) = 漸層**開始**的LED的顏色.(只能使用CHSV)
    CHSV(100,255,255) = 漸層**結束**的LED的顏色.(只能使用CHSV)    
    
    **fill_gradient_RGB()省略後面部分.**
    
    FORWARD_HUES: hue always goes clockwise(順時針)
    BACKWARD_HUES: hue always goes counter-clockwise(逆時針)
    LONGEST_HUES: 長色調過渡
    HORTEST_HUES: 短色調過渡
    
    **test1**
    ![image](https://hackmd.io/_uploads/S162sGKc6.png)
5.  HeatColor()

    **功能:** 透過熱量控制燈的顏色.
![image](https://hackmd.io/_uploads/B14CIw5qp.png)







     
    
# Other:

1. leds[NUM_LEDS];  可能為初始化LED陣列的函式

# tip:
*  要記得在填完顏色後用FastLED.show();顯示.

* leds+i = LED陣列位移i單位，i為+/-都可. = 從第i個LED開始.
    (與CRGB leds[NUM_LEDS]; 有關)

    ![image](https://hackmd.io/_uploads/HJDZtFcq6.png)


`
# **Q.**
Q1. 釐清是長度還是點  v
Q2. fill_rainbow_circular();
Q3. 整理筆記               v
Q4. 要合併筆記 v
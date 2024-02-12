# 程式庫測試:
* 用3個顏色測試
* 另外寫出來
* 要怎麼排版
* 另外獨立出來做對比



# **FastLED 3.0 addition**

# Function: 
* 功能表: 
    1. 單一顏色
    2. 色差固定的變色 rainbow
    3. 由長度控制的所有(包括first_LED & last_LED)色差固定的 rainbow
    4. 顏色漸層
    5. 體溫改變顏色

* 函式大致架構: 
    1. LED陣列位移
    2. 長度
    3. 顏色



1. fill_solid()
    
    功能: 將LED填滿單一顏色.(長度可調整)


2. 	fill_rainbow ()

    **功能:** 將LED填滿不同顏色，相鄰LED有相同的色差值.(可變更色差、長度)

3. fill_rainbow_circular ()
    
    **功能:** 將LED填滿不同顏色，相鄰LED有相同的色差值，且燈帶末端和開頭之間的色調是連續的.(可調整長度、是否reversed顛倒)
    
    
4. fill_gradient() & fill_gradient_RGB()
    
     **功能:** 在LED_A(顏色1)到LED_B(顏色2)之間的LED，做出顏色1~顏色2的漸層.(最多可以支援到3次漸層變換)
     
    fill_gradient()

    
    fill_gradient_RGB()

    
# **Q.**



Q4. 要合併筆記
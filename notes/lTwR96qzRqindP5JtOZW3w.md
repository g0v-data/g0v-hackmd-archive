Fastled 2.0(Arduino)
=========================================
**前置設定**
1. CRGB Name [ NUM_LEDS + 1];
    
    設定有幾個LED在燈條上.
    
    Q.為何要NUM_LED+1?
    A.可以宣告一個帶有一個額外像素的 LED 作為緩衝區。
ex. 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_211d7af6e790351a32c08537858067f4.png)

1. FastLED.addLeds<模組名稱,訊號輸出PIN,GRB>(leds,NUM_LEDS);
 
    設定模組名稱(WS2812)、訊號輸出PIN(自訂)、顏色配置(GRB)、NUM_LEDS = LED數量.

**其他前綴有FastLED.的函式:**


3. FastLED.setBrightness(96);
    設定LED燈條的亮度(0~255), 0為不亮.
    下圖為亮度數值測試:1、10、50、100、150、255
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3429940efe922e713ef0b1d2667aaa28.jpg)




5. FastLED.show();
    讓LED燈條輸出設定好的顏色數值.
    
5. FastLED.delay(1000/FRAMES_PER_SECOND);
    =delay();

6.   FastLED.addLeds<LED_TYPE,DATA_PIN,COLOR_ORDER>(leds, NUM_LEDS)
        .setCorrection( TypicalLEDStrip );
     

7. FastLED.addLeds<LED_TYPE,DATA_PIN,COLOR_ORDER>(leds, NUM_LEDS)
    .setCorrection(TypicalLEDStrip)
    .setDither(BRIGHTNESS < 255);

8. FastLED.setMaxPowerInVoltsAndMilliamps( VOLTS, MAX_MA);

# **Color**

1. 名稱[i] = CRGB(Red值, Green值, Blue值);
     RGB顏色模型，設定LED的顏色，參數範圍如下
     R值 : 0~255
     G值 : 0~255
     B值 : 0~255
    三值相同則，為白光 ; 三值皆為0則不亮。
     可用簡易的方法輸出    CRGB::顏色名稱(Black即為無色)
     ex. Name[0] = CRGB(100, 100, 100);
     
* **color代碼:**
  http://www.taichi-maker.com/homepage/reference-index/arduino-library-index/fastled-library/rgb-color/

    **用法:**
    ex. leds[i] = CRGB::Black;        
    *//i為 燈條上第i顆led燈，從0開始數*




 2. 名稱[i] = CHSV(H值, S值, V值);
     HSV顏色模型，設定LED的顏色，參數範圍如下
     H值 : 色相/色調 (Hue) 0~255
     S值 : 飽和度(Saturation)  0 ~ 255 
     V值 : 色調  (Value) 0~255

    ex. Name[0] = CHSV(100, 100, 100); 
    
# **建議:**
1. 

    



# **New knowledge:**
1. **uint?_t**
    uint8_t為0~2^8-1 (0x00~0xFF)
    uint16_t為0~2^16-1 (0x0000~0xFFFF)
    uint32_t為0~2^32-1 (0x00000000~0xFFFFFFFF)
    uint64_t為0~2^64-1 (0x0000000000000000~0xFFFFFFFFFFFFFFFF)
    
2. i是座標系統(目前無垂直向量):
```
//設定部分
// Params for width and height
const uint8_t kMatrixWidth = 16;
const uint8_t kMatrixHeight = 16;

// Param for different pixel layouts
const bool    kMatrixSerpentineLayout = true;
const bool    kMatrixVertical = false;

//座標系統部分(檢索座標):
uint16_t XY( uint8_t x, uint8_t y)  //一個大空間的副函式
{
  uint16_t i;  //設置i變數
  
  //1. 沒有垂直向量、所有的座標從左側出發
  if( kMatrixSerpentineLayout == false) {
    if (kMatrixVertical == false) {
      i = (y * kMatrixWidth) + x;
    } else {
      i = kMatrixHeight * (kMatrixWidth - (x+1))+y;
      
    }
  }
//=======================================================  
//2. 沒有垂直向量、下行的座標從上行的座標x處開始出發
  if( kMatrixSerpentineLayout == true) {
    if (kMatrixVertical == false) {
      if( y & 0x01) {            
        //0x01: 0x可視為前贅詞，後面為16進位的數字
        //ex. 0x10 = 十進位16
        //y是十進制數，將x的的值轉換為
        //二進制後，假若最低位是1，那麼if語句成立
        
        //偶數向後運行(y座標從0開始，0為偶數)
        uint8_t reverseX = (kMatrixWidth - 1) - x;
        i = (y * kMatrixWidth) + reverseX;
      } else {
        // 奇數向前運行
        i = (y * kMatrixWidth) + x;
      }
    } else { // 垂直定位
      if ( x & 0x01) {//x是十進制數，將x的的值轉換為
                      //二進制後，假若最低位是1，那麼if語句成立
        i = kMatrixHeight * (kMatrixWidth - (x+1))+y;
      } else {
        i = kMatrixHeight * (kMatrixWidth - x) - (y+1);
      }
    }
  }
  
  return i;
}
```

**3. millis()函式應用**
    
1. 先呼叫millis()，並把這個值先賦於給startTime，相當於在時間軸上做了一個標記。


3. 當程式進到迴圈時，就可以將”現在時間”-“開始時間”，就可以獲得”經過時間”，Duration=millis()-startTime。


5. 最後我們可以用判斷式if，來判斷Duration是否達到條件。



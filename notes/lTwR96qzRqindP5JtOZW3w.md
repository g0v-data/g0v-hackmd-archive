**Fastled 2.0(Arduino)**
=========================================
**簡介**
* 函式庫特色:
    1. 讓新的開發者可以快速的熟悉
    2. 無痛切換LED模組，只需要修改些許設定
    3. 高效能--盡可能地節省CPU效能

    



**前置設定**
1. CRGB Name [ NUM_LEDS + 1];
    
    設定有幾個LED在燈條上(NUM_LEDS)
    
    Q.為何要NUM_LED+1?
    A.可以宣告一個帶有一個額外像素的 LED 作為緩衝區。

    ex. CRGB leds_plus_safety_pixel [ NUM_LEDS + 1];


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

**Color:**

1. 名稱[i] = CRGB(Red值, Green值, Blue值);
     RGB顏色模型，設定LED的顏色，參數範圍如下
     R值 : 0~255
     G值 : 0~255
     B值 : 0~255
    三值相同則，為白光 ; 三值皆為0則不亮。
     可用簡易的方法輸出    CRGB::顏色名稱(Black即為無色)
     ex. Name[0] = CRGB(100, 100, 100);
     
* color代碼(英文):
  http://www.taichi-maker.com/homepage/reference-index/arduino-library-index/fastled-library/rgb-color/

    **用法:**
    ex. Name[i] = CRGB::Black;        
    *//i為 燈條上第i顆led燈，從0開始數*




 2. 名稱[i] = CHSV(H值, S值, V值);
     HSV顏色模型，設定LED的顏色，參數範圍如下
     H值 : 色相/色調 (Hue) 0~255
     S值 : 飽和度(Saturation)  0 ~ 255 
     V值 : 色調  (Value) 0~255

    ex. Name[0] = CHSV(100, 255, 255); 
    
# **幫助:**
1. 測試用程式碼
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

2. Reddit 社群 https://reddit.com/r/FastLED
該群組中有數千名知識淵博的 FastLED 用戶，並且在過去的歷史中提供了大量的解決方案。
3. 如果遇到此庫的錯誤，或者想請求對特定平台或 LED 晶片組的支持，請在http://fastled.io/issues 提交問題。


5. 線上文檔網址:  https://fastled.io/docs/group__lib8tion.html

    
# **應用:**
1. 我認為此燈條可以作為一種外在的表現形式

    1.1 顏色意義:
例子.
裝置收到簡訊/電話就亮顏色，爸爸是藍色、媽媽是紅色、姊姊是紫色.....，使用者可以輕易地讀取裝置所傳遞的訊息。
也可以讓裝置發出的聲音與顏色綁定。

    1.2 頻率意義:
    例子.
    裝置收到家人、公司的簡訊/電話，就亮3下，普通的提醒亮2下、其他亮1下。

    1.3 裝飾意義:
    例子.
    某些人可能喜歡閃爍移動的東西，就可以設置一個主動觸發在裝置上，被觸發後呈現美麗的色彩變幻。

2. 彼此之間的暗號:

    透過特殊的頻率與朋友、戀人溝通，像是1長燈光訊號代表:"你在嗎?"，回復1長燈光:"我在!"，此方向可透過螢幕做出連動。







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


# **問題：**
A.![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_dba6cbc416fb2e193125fe5768432836.jpg)


1. cos16( ms * (27/1) )
2. 中間的(int32_t)這個會括號意義
3. 前面的int32_t用int是因為時間會佔比較多的記憶體空間嗎?
Note. 這個程式視讓LED燈條隨著時間變化而改變色調，所以xHueDelta、yHueDelta分別代指x軸y軸位置上所增加的變量。
4. 不確定的敘述: 從宣告的那個時間點，millis （）就開始計時了,然後下面的函式有用到ms 視為讀取時間

B.


# **資料來源:**
**3.6.0版本:**
https://fastled.io/docs/group__lib8tion.html
(在找scale8函式時發現的)
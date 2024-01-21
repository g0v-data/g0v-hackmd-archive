Fastled 2.0
=========================================
**前綴有FastLED.的函式:**
1. FastLED.addLeds<WS2811,2,GRB>(leds,NUM_LEDS);
2. FastLED.setBrightness(96);
3. FastLED.show();

5. FastLED.delay(1000/FRAMES_PER_SECOND);

6.   FastLED.addLeds<LED_TYPE,DATA_PIN,COLOR_ORDER>(leds, NUM_LEDS)
        .setCorrection( TypicalLEDStrip );
     FastLED.setMaxPowerInVoltsAndMilliamps( 5, MAX_POWER_MILLIAMPS);

7. FastLED.addLeds<LED_TYPE,DATA_PIN,COLOR_ORDER>(leds, NUM_LEDS)
    .setCorrection(TypicalLEDStrip)
    .setDither(BRIGHTNESS < 255);

8. FastLED.setMaxPowerInVoltsAndMilliamps( VOLTS, MAX_MA);

# **Color**

1. 類別名稱[i] = CRGB(R值, G值, B值);
     RGB顏色模型，設定LED的顏色，參數範圍如下
     R值 : 0~255
     G值 : 0~255
     B值 : 0~255

     可用簡易的方法輸出    CRGB::顏色名稱(Black即為無色)
* **color代碼:**
  http://www.taichi-maker.com/homepage/reference-index/arduino-library-index/fastled-library/rgb-color/
**用法:**
 leds[i] = CRGB::Black;        
 *i為 燈條上第i顆led燈，從0開始數*




 2. 類別名稱[i] = CHSV(H值, S值, V值);
     HSV顏色模型，設定LED的顏色，參數範圍如下
     H值 : 色相/色調 (Hue) 0~255
     S值 : 飽和度(Saturation)  0 ~ 255 
     V值 : 色調  (Value) 0~255




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
  uint16_t i;
  //沒有垂直向量、所有的座標從左側出發
  if( kMatrixSerpentineLayout == false) {
    if (kMatrixVertical == false) {
      i = (y * kMatrixWidth) + x;
    } else {
      i = kMatrixHeight * (kMatrixWidth - (x+1))+y;
      
    }
  }
//沒有垂直向量、下行的座標從上個座標x開始出發
  if( kMatrixSerpentineLayout == true) {
    if (kMatrixVertical == false) {
      if( y & 0x01) {
        // Odd rows run backwards
        uint8_t reverseX = (kMatrixWidth - 1) - x;
        i = (y * kMatrixWidth) + reverseX;
      } else {
        // Even rows run forwards
        i = (y * kMatrixWidth) + x;
      }
    } else { // vertical positioning
      if ( x & 0x01) {
        i = kMatrixHeight * (kMatrixWidth - (x+1))+y;
      } else {
        i = kMatrixHeight * (kMatrixWidth - x) - (y+1);
      }
    }
  }
  
  return i;
}
```

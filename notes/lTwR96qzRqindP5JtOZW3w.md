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

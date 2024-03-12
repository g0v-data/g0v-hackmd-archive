# **範例閱讀**
## 1. Cylon
```
#include <FastLED.h>

// How many leds in your strip?
#define NUM_LEDS 20

// For led chips like Neopixels, which have a data line, ground, and power, you just
// need to define DATA_PIN.  For led chipsets that are SPI based (four wires - data, clock,
// ground, and power), like the LPD8806, define both DATA_PIN and CLOCK_PIN
#define DATA_PIN 5
#define CLOCK_PIN 13

// Define the array of leds
CRGB leds[NUM_LEDS];

void setup() { 
    Serial.begin(57600);
    Serial.println("resetting");
    LEDS.addLeds<WS2812,DATA_PIN,RGB>(leds,NUM_LEDS);
    LEDS.setBrightness(84);
}

void fadeall() { for(int i = 0; i < NUM_LEDS; i++) { leds[i].nscale8(250); } }

void loop() { 
    static uint8_t hue = 0;
    Serial.print("x");
    // First slide the led in one direction
    for(int i = 0; i < NUM_LEDS; i++) {
        // Set the i'th led to red 
        leds[i] = CHSV(hue++, 255, 255);
        // Show the leds
        FastLED.show(); 
        // now that we've shown the leds, reset the i'th led to black
        // leds[i] = CRGB::Black;
        fadeall();
        // Wait a little bit before we loop around and do it again
        delay(10);
    }
    Serial.print("x");

    // Now go in the other direction.  
    for(int i = (NUM_LEDS)-1; i >= 0; i--) {
        // Set the i'th led to red 
        leds[i] = CHSV(hue++, 255, 255);
        // Show the leds
        FastLED.show();
        // now that we've shown the leds, reset the i'th led to black
        // leds[i] = CRGB::Black;
        fadeall();
        // Wait a little bit before we loop around and do it again
        delay(10);
    }
}
```


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1e0d940313f825c85439e11729e599cb.png)
nscale8 : 將現在的亮度數值*N/256, 範例中N = 250

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_929d9ac99069e377ac60b3b037dfc849.png)
此函式與一內容相同但移動方向相反的函式組成此範例。

`fadeall();`會讓所有LED慢慢變暗，但`leds[i] = CHSV(hue++, 255, 255);`程式中亮度=255，所以前進方向的LED最亮，且其亮度數值被重設回255。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a2043f2204549b5b85375d40aac7d92d.png)
圖示，範例在燈條上運行的情況，前進的方向最亮，後面越來越暗

## 2. DemoReel100
```

#include <FastLED.h>
 
FASTLED_USING_NAMESPACE
 
// FastLED "100-lines-of-code" demo reel, showing just a few 
// of the kinds of animation patterns you can quickly and easily 
// compose using FastLED.  
//
// This example also shows one easy way to define multiple 
// animations patterns and have them automatically rotate.
//
// -Mark Kriegsman, December 2014
 
 
#define DATA_PIN    3
//#define CLK_PIN   4
#define LED_TYPE    WS2811
#define COLOR_ORDER GRB
#define NUM_LEDS    64
CRGB leds[NUM_LEDS];
 
#define BRIGHTNESS          96
#define FRAMES_PER_SECOND  120
 
void setup() {
  delay(3000); // 3 second delay for recovery
  
  // tell FastLED about the LED strip configuration
  FastLED.addLeds<LED_TYPE,DATA_PIN,COLOR_ORDER>(leds, NUM_LEDS).setCorrection(TypicalLEDStrip);
  //FastLED.addLeds<LED_TYPE,DATA_PIN,CLK_PIN,COLOR_ORDER>(leds, NUM_LEDS).setCorrection(TypicalLEDStrip);
 
  // set master brightness control
  FastLED.setBrightness(BRIGHTNESS);
}
 
 
// List of patterns to cycle through.  Each is defined as a separate function below.
typedef void (*SimplePatternList[])();
SimplePatternList gPatterns = { rainbow, rainbowWithGlitter, confetti, sinelon, juggle, bpm };
 
uint8_t gCurrentPatternNumber = 0; // Index number of which pattern is current
uint8_t gHue = 0; // rotating "base color" used by many of the patterns
  
void loop()
{
  // Call the current pattern function once, updating the 'leds' array
  gPatterns[gCurrentPatternNumber]();
 
  // send the 'leds' array out to the actual LED strip
  FastLED.show();  
  // insert a delay to keep the framerate modest
  FastLED.delay(1000/FRAMES_PER_SECOND); 
 
  // do some periodic updates
  EVERY_N_MILLISECONDS( 20 ) { gHue++; } // slowly cycle the "base color" through the rainbow
  EVERY_N_SECONDS( 10 ) { nextPattern(); } // change patterns periodically
}
 
#define ARRAY_SIZE(A) (sizeof(A) / sizeof((A)[0]))
 
void nextPattern()
{
  // add one to the current pattern number, and wrap around at the end
  gCurrentPatternNumber = (gCurrentPatternNumber + 1) % ARRAY_SIZE( gPatterns);
}
 
void rainbow() 
{
  // FastLED's built-in rainbow generator
  fill_rainbow( leds, NUM_LEDS, gHue, 7);
}
 
void rainbowWithGlitter() 
{
  // built-in FastLED rainbow, plus some random sparkly glitter
  rainbow();
  addGlitter(80);
}
 
void addGlitter( fract8 chanceOfGlitter) 
{
  if( random8() < chanceOfGlitter) {
    leds[ random16(NUM_LEDS) ] += CRGB::White;
  }
}
 
void confetti() 
{
  // random colored speckles that blink in and fade smoothly
  fadeToBlackBy( leds, NUM_LEDS, 10);
  int pos = random16(NUM_LEDS);
  leds[pos] += CHSV( gHue + random8(64), 200, 255);
}
 
void sinelon()
{
  // a colored dot sweeping back and forth, with fading trails
  fadeToBlackBy( leds, NUM_LEDS, 20);
  int pos = beatsin16( 13, 0, NUM_LEDS-1 );
  leds[pos] += CHSV( gHue, 255, 192);
}
 
void bpm()
{
  // colored stripes pulsing at a defined Beats-Per-Minute (BPM)
  uint8_t BeatsPerMinute = 62;
  CRGBPalette16 palette = PartyColors_p;
  uint8_t beat = beatsin8( BeatsPerMinute, 64, 255);
  for( int i = 0; i < NUM_LEDS; i++) { //9948
    leds[i] = ColorFromPalette(palette, gHue+(i*2), beat-gHue+(i*10));
  }
}
 
void juggle() {
  // eight colored dots, weaving in and out of sync with each other
  fadeToBlackBy( leds, NUM_LEDS, 20);
  uint8_t dothue = 0;
  for( int i = 0; i < 8; i++) {
    leds[beatsin16( i+7, 0, NUM_LEDS-1 )] |= CHSV(dothue, 200, 255);
    dothue += 32;
  }
}
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_68e661197074d78bac50a4c21bc56741.png)
宣告SimplePatternList(資料型態 = void)為 一個陣列gPatterns 的儲存空間
gPatterns陣列中的元素為動畫(副函式)的名稱。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0d2c6c1871e2f430c1122c92926d8a03.png)
陣列A中所佔的bits數/陣列中一個元素佔的bits數 = 陣列A中有幾個元素
(前提:所有元素的資料型態相同)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d363c2f5caedf57ef9c6c03da80e28e0.png)
選擇副函式
讓LED燈串表現
delay
一定時間後(短) 改變燈串上顏色
一定時間後(長) 切換到下個副函式

以下是副函示內的內容
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_604ee4e96eaf162d6621f57be5bf1648.png)
random8 : 隨機數0~255
如果隨機數 < chanceOfGlitter，則不做閃光
以更大範圍的隨機數決定燈串上哪個LED要閃光

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5d3623ee5b3af31bc76808fd0d4b4196.png)
fadeToBlackBy淡化顏色(0~255)
random16(NUM_LEDS) : 在0~NUM_LEDS之間求一隨機數
//之所以用random16是因為作者不確定使用者燈串上LED的數量，所以使用16bits(上限高)，而不是random8.

* 我懷疑`leds[位置]+=顏色`，是可以讓位置上的燈變成此顏色

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c193137fe2ec193e9eb127a7a4253c5a.png)

beatsin16(每分鐘頻率, 波值下限, 波值上限);
讓燈條上的LED來回亮起

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_869276f8ac4c55488751f2b12f4c0a67.png)
`leds[i] = ColorFromPalette(palette, gHue+(i*2), beat-gHue+(i*10));`
ColorFromPalette(調色盤, 色調, 亮度)   色調 = 調色盤內座標

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c6e6dcc1573dcc3c4591aeee54f88f6c.png)

### 模式簡介:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b67f43c9c4a25a6e343e7d88b2866f5e.png)

rainbow, rainbowWithGlitter, confetti, sinelon, juggle, bpm 

* **rainbow** : 以gHue的數值為初始色調數值，**每個LED的色調差為7**，因為模式刷新會增加gHue的值，所有**LED的顏色會一起變化**。
* **rianbowWithGlitter** : 保留rainbow模式的同時，增加隨機的**白色**覆蓋在燈串上，因為模式**快速刷新**，所以白色的部分看起來像是**閃光**。
* **confetti** : 
    1. 有函式可以讓所有燈都**變暗**些許，在模組刷新速度很快的情況下，如果沒有顏色重新填充，很快燈條上的燈都會暗掉。
    2. 顏色補充**位置隨機**(但被限制在燈條上)。
    3. **色調**被限制在一定範圍內**隨機**(gHue+random8(64))。

(confetti 內使用`fadeToBlackBy( leds, NUM_LEDS, 20);`如果在刷新速度很快的情況下，可以拿數值來控制顏色殘留在燈串上的速度，20是淡化數值，數值越大，LED越暗)
* **sinelon** : 與**confetti**的1.相同，顏色會**淡化**。因為beatsin16會從最小值到最大值，再從最大值到最小值，所以最後一個LED、第一個LED會亮2次，看起來像是**顏色停留**。
* **bpm** : 
`leds[i] = ColorFromPalette(palette, gHue+(i*2), beat-gHue+(i*10));`ColorFromPalette(調色盤, 顏色座標, 亮度)
* **juggle** : 



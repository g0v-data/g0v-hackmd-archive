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
此圖表示，此範例在燈條上運行的情況，前進的方向最亮，後面會比較暗




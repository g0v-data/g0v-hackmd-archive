調色盤

1. 宣告:
    `CRGBPalette16 myPalette；`
    
2. 自行填充或引用配色方案
    自行填充調色盤的範例: 
    ```
    CRGBPalette16 myPalette(
    CRGB::黑色，
    CRGB::黑色，
    CRGB::紅色，
    CRGB::黃色，
    CRGB::綠色，
    CRGB::藍色，
    CRGB::紫色，
    CRGB::黑色，
 
    0x100000,
    0x200000,
    0x400000,
    0x800000,
 
    CHSV（30,255,255），
    CHSV（50,255,255），
    CHSV（70,255,255），
    CHSV ( 90,255,255)
    ）；
    ```
    引用調色盤的範例:
    `myPalette = RainbowStripesColors_p ;`
    可以引用的範例: 
    1. ForestColors_p
    2. CloudColors_p
    3. LavaColors_p
    4. OceanColors_p
    5. RainbowColors_p
    6. RainbowStripeColors_p











# Q. 
1. 任何時候您想要將像素設定為調色盤中的顏色時，請ColorFromPalette()按如下所示使用：

```
uint8_t index = /* 0-255 之間的任何值 */ ;
leds[i] = ColorFromPalette (myPalette, index);
```
即使您的調色板只有 16 個明確定義的條目，您也可以使用 0-255 之間的「索引」。 16 個顯式調色板條目將均勻分佈在 0-255 範圍內，中間值將在相鄰明確條目之間進行 RGB 插值。

它比聽起來更容易使用。
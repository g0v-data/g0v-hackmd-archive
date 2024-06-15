# Arduino 入門及Infineon radar應用
編輯 :　吳冠穎

<!-- Put the link to this slide here so people can follow -->
<!-- slide: https://hackmd.io/p/template-Talk-slide -->

---

## 前言
本課程是介紹Arduino基礎操作及Infineon雷達進階應用，課程約2小時。
Arduino 將控制晶片和燒錄功能整合到一塊小巧的板子上。它的Pin腳設計讓接線更加簡便，能夠輕鬆地配合麵包板使用，這樣可以快速連接各種感測器和週邊設備。對於初學者來說，只要會插杜邦線，就能開始開發工作。

## 材料
- [ ] Arduino UNO板
- [ ] USB-B 信號傳輸線
- [ ] 杜邦線
- [ ] 伺服馬達
- [ ] 麵包板
- [ ] LED燈


---

## TOPIC 1 : 安裝Arduino環境

- 首先到Arduino官網安裝Arduino
https://www.arduino.cc/en/software
![](https://i.imgur.com/vobgca2.png)

- 在安裝成功後開啟

![](https://i.imgur.com/PHLLWbo.png)




---

## TOPIC 2 : Arduino UNO 和 LED

第一步需要先檢測Arduino UNO板及其他材料是否完好

- 接上線路 (注意LED燈長腳為正極，短腳為負極) 
![](https://i.imgur.com/Fk9neZE.png)
- 用USB 信號傳輸線連接Arduino UNO到電腦主機
- 設定Arduino IDE上方面板 
-- Tools/Board:"Arduino UNO"
-- Tools/Port
- 將code寫入到Arduino IDE
```typescript
void setup() {
  // initialize digital pin Mode 13 as an output.
  pinMode(13, OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(13, HIGH);  // turn the LED on (HIGH is the voltage level)
  delay(1000);                      // wait for a second
  digitalWrite(13, LOW);   // turn the LED off by making the voltage LOW
  delay(1000);                      // wait for a second
}
```
- Arduino IDE點選向右箭頭的圖示，將code燒錄至UNO板中
---



## TOPIC 3 : Arduino UNO 和 伺服馬達

Arduino的伺服馬達是一種常用的機電裝置，用於控制角度、速度和位置，適合用於各種自動化和機器人項目。這種馬達通常具有高精度和高效率，能夠根據輸入的控制信號進行精確定位。

- 接上線路 
![](https://i.imgur.com/ni9F1IA.png)



- 將code寫入到Arduino IDE
```typescript
#include <Servo.h>   //載入函式庫，這是內建的，不用安裝

Servo myservo;  // 建立SERVO物件


void setup() {
  myservo.attach(9);  // 設定要將伺服馬達接到哪一個PIN腳
}

void loop() {   
  myservo.write(0);  //旋轉到0度，就是一般所說的歸零
  delay(1000);
  myservo.write(90); //旋轉到90度
  delay(1000);
  myservo.write(180); //旋轉到180度
  delay(1000);
  myservo.write(90);
  delay(1000);
}
```
- Arduino IDE點選向右箭頭的圖示，將code燒錄至UNO板中

---

## TOPIC 4 : Infineon BGT60LTR11AIP board (選做)

- 描述
Infineon BGT60LTR11AIP radar board 是一顆都普勒雷達，其中BGT60LTR11AIP MMIC 是一款完全集成的微波運動傳感器，運行於60GHz ISM頻段，並具有4個四態 (QS1-4) 輸入引腳，可工作於SPI模式和自主模式。shield board在SPI模式下可接上MCU7底板且可由radar GUI觀測運動狀態。

![](https://i.imgur.com/dID992i.png)

- QS1 (R3)
BGT60LTR11AIP配置為在SPI模式下，可透過移除R3電阻進入自主模式。Shield board 具有4個(PD、TD、GND、VIN)腳位可對外連接。

- QS2 (R9, R10)
通過改變R9、R10電阻值調整感測範圍(Sensitivity)。
將shield board置於顯微鏡下並以膠帶固定，調整目鏡至適當距離後移除R10電阻，提高感測精度。

- QS3 (R19, R20)
通過改變R19、R20電阻值調整感測持續時間(Hold time)。
Hold time是指感測後保持訊號的時間，在所偵測目標快速移動相對需要即時回復的設計需降低Hold time，反之若是作為感測物體的有無，如陌生人靠近發出警報聲音的時間也由Hold time控制。
然而，對於特殊需求，雷達偵測時間可以由外部控制，預設QS3設定detector hold time較低，作為一般雷達應用，偵測已足夠靈敏，因此跳過這部分的焊接。



---

## TOPIC 5 : 用雷達控制LED燈發光 (選做)

- 新增材料
- [ ] Arduino MKR WIFI 1010
- [ ] USB-C 信號傳輸線
- [ ] BGT60LTR11AIP radar shield board

- Arduino IDE 配置
-- 左側欄位 BOARDS MANAGER/MKR 安裝
-- 左側欄位 LIBRARY MANAGER/radar-bgt60 安裝
- 將BGT60LTR11AIP radar shield board組合上Arduino MKR WIFI 1010
![](https://i.imgur.com/o9SYj9o.png)

- 接上線路
![](https://i.imgur.com/1usazre.png)

- 將code寫入到Arduino IDE
```typescript
#include <Arduino.h>

#include <bgt60-ino.hpp>

#include <bgt60-platf-ino.hpp>


#ifndef TD
#define TD  15
#endif

#ifndef PD
#define PD  16
#endif

Bgt60Ino radarShield(TD, PD);

void setup()
{
    
    Serial.begin(9600);
  
    Error_t init_status = radarShield.init();

    if (OK != init_status) {
        Serial.println("Init failed.");
    }
    else {
        Serial.println("Init successful.");
    }

    pinMode(1, OUTPUT);  
}


void loop()
{
   
    Bgt60::Direction_t direction = Bgt60::NO_DIR;

    Error_t err = radarShield.getDirection(direction);

    
    if (err == OK)
    {     
        switch (direction)
        {            
            case Bgt60::APPROACHING:
                Serial.println("Target is approaching!");
                digitalWrite(1, true); 
                break;
            
            case Bgt60::DEPARTING:
                Serial.println("Target is departing!");
                digitalWrite(1, false); 
                break;
            
            case Bgt60::NO_DIR:
                Serial.println("Direction cannot be determined since no motion was detected!"); 
                break;
        }
    }
    /* API execution returned error */
    else{
        Serial.println("Error occurred!");
    }

    delay(500);
}

```
- Arduino IDE點選向右箭頭的圖示，將code燒錄至MKR板中




---

## TOPIC 6 : 用雷達控制伺服馬達 (選做)

- 新增材料
- [ ] Arduino MKR WIFI 1010
- [ ] USB-C 信號傳輸線
- [ ] BGT60LTR11AIP radar shield board

- Arduino IDE 配置
-- 左側欄位 BOARDS MANAGER/MKR 安裝
-- 左側欄位 LIBRARY MANAGER/radar-bgt60 安裝
- 將BGT60LTR11AIP radar shield board組合上Arduino MKR WIFI 1010
![](https://i.imgur.com/o9SYj9o.png)

- 接上線路
![](https://i.imgur.com/bs38yme.png)

- 將code寫入到Arduino IDE
```typescript
#include <Arduino.h>

#include <bgt60-ino.hpp>

#include <bgt60-platf-ino.hpp>

#include <Servo.h>
Servo myservo;

#ifndef TD
#define TD  15
#endif

#ifndef PD
#define PD  16
#endif

Bgt60Ino radarShield(TD, PD);

void setup()
{
    
    Serial.begin(9600);
  
    Error_t init_status = radarShield.init();

    if (OK != init_status) {
        Serial.println("Init failed.");
    }
    else {
        Serial.println("Init successful.");
    }

    myservo.attach(1);  // 腳位1設定為伺服馬達訊號腳位
}


void loop()
{
   
    Bgt60::Direction_t direction = Bgt60::NO_DIR;

    Error_t err = radarShield.getDirection(direction);

    
    if (err == OK)
    {     
        switch (direction)
        {            
            case Bgt60::APPROACHING:
                Serial.println("Target is approaching!");
                myservo.write(0); // 伺服馬達轉軸轉動至0度
                break;
            
            case Bgt60::DEPARTING:
                Serial.println("Target is departing!");
                myservo.write(90); // 伺服馬達轉軸轉動至90度
                break;
            
            case Bgt60::NO_DIR:
                Serial.println("Direction cannot be determined since no motion was detected!"); 
                myservo.write(180);  // 伺服馬達轉軸轉動至180度
                break;
        }
    }
    /* API execution returned error */
    else{
        Serial.println("Error occurred!");
    }

    delay(500);
}

```
- Arduino IDE點選向右箭頭的圖示，將code燒錄至MKR板中

---

## Reference
- Infineon BGT60LTR11AIP board user guide : https://www.infineon.com/dgdl/Infineon-AN133733_BGT60LTR11AIP_EBG_Shield.pdf-ApplicationNotes-v01_10-EN.pdf?fileId=8ac78c8c872bd8d6018751c0ea39605c
- bgt60 radar github : https://github.com/Infineon/arduino-radar-bgt60/blob/master/examples/directionDetection/directionDetection.ino





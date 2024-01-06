---
title: Arduino for TOCC
description:: Arduino for TOCC，本裝置幫助防疫人員保持安全距離，協助民眾操作健保卡的過卡。
tags: COVID-19, TOCC, Arduino
---


> [name=Caleb Rogers]No need to purchase arduinos and speakers. Using old phones and computer equipment, simply record an audio file. I can easily put these audio files on my personal server, make a simple webpage with a button to click, and you can click the button to play the audio. Hook the phone or computer into any speaker you can find. We can use recycled materials to quickly and cheaply deploy this. Contact me on slack or caleb@calebjay.com. Later tonight I'll steal your audio files :3 and then create a simple website to show you what i mean. However if you also need funding let me know. 
>
> [name=Teemo]
> * Does it work without network?
> * How to replacement file?
>
> [name=wuulong sheu 哈爸]
> 1. 應該有不同且簡單的做法，如 Caleb Rogers 的建議
> 2. 應也能找到更合適簡單的硬體主板來協助實現
> 3. 第一台/第二台規格似乎應該做成同樣的就好，需要的話就做兩台
> 
> [name=tonysanv]
> These should work out of the box
> https://www.alibaba.com/product-detail/High-Quality-Programmable-Push-Button-Sound_60819105985.html
> need some soldering to redirect audio to a better speaker and larger battery support.

# Arduino for TOCC (已完成實作)
## 緣起
:::warning
我是防疫人員，我每天要持續講很多的話來引導大家通過體溫站時要過健保卡並且量體溫。
目前困擾的是單純播放固定台詞的引導廣播無法協同搭配手勢協助民眾操作健保卡的過卡。
希望能有使用遙控器或按按鈕撥放下方四句比較常講的句子來幫助防疫人員保持安全距離。
:::
:::danger
這件事對我來說非常重要，如果有這個裝置就可以跟來院的人保持距離，並完成過卡指引。
現在因為我戴口罩講話要很用力，而我們也要為閱讀障礙與學齡前小朋友引導通過體溫站，
在經過這樣一小時後我就沒聲音沙啞了，此時來的民眾為了聽清楚我在講什麼就會靠過來，
更用力的講話產生更多飛沫，這樣我們防疫人員與來院民眾之間就無法保持彼此安全距離。
:::
:::success
當雙手帶著乳膠手套，使用智慧型手機無法觸控螢幕順利操作。
:::


## 現況
#### Android for TOCC [(apk)](https://app.box.com/s/35if1ksyewtmtr1g4eipdmp0k937hvbw)
:::info
目前採取 apk + 藍芽喇叭 ，暫無技術問題。
但這依然不是一個好方案，手機 TOCC APP 有操作困難，我帶手套無法觸控...
拿一枝觸控筆又要拿一支手機，
雙手手上很忙，
無法騰出手作指引或是舉說明板。
:::

#### Arduino for TOCC (本次提案已完成實作)
:::info
目前程式撰寫完成，硬體已完成實作。
挑戰來自於環境的限制，可以視為app的備案，
因為不是所有場合都能使用網路以及感染管制政策無法使用手機，
例如重新佈署新版本時，
要將手機回到IT手上的消毒程序，明顯比換掉一張SD卡片的門檻高。
:::


---
## 專案聯絡人
* [Teemo](https://t.me/ddqq7) (Telegram)
* [Teemo](https://g0v-tw.slack.com/archives/DV52VS48Y) (g0v slack)

## 目標
1. 兩台Arduino機器，使用於醫院TOCC場合
2. 使用遙控器控制，播放指定句子mp3

## 規格文件

### 規格
* 紅外線遙控器(對應控制按鈕放不同語音檔案)
* 使用一般行動電源，用USB線作為電源。
* 喇叭音質人聲清晰不會刺耳。
* 可以插記憶卡，並依檔案名稱的編號更語音檔案句子的mp3

### 功能與行為
預計要有4個獨立按鈕可以撥放4個mp3檔案，有1個終止撥放的獨立按鈕。
按鈕行為與範例的語音檔：
1. 按鈕-播放：[身分證或健保卡.mp3](https://app.box.com/s/9k2r803bo99bty55tlbh1q283yh94gym)
2. 按鈕-播放：[健保卡，晶片插下去.mp3](https://app.box.com/s/n4d0kvn7la0p79rfl67y31qt9iqruwk0)
3. 按鈕-播放：[請看一下鏡頭.mp3](https://app.box.com/s/mlkflg6peviq3f3cwf7dym50t3hybbsl)
4. 按鈕-播放：[OK，請進.mp3](https://app.box.com/s/ylzyqje9sisnybu5nu3pm3ma4eagze6f)
5. 按鈕-中斷停止任何播放


---
### 材料明細公開
* Arduino Nano V3.0 ATMEGA328P 改進版 
    * 台幣140~320之間
* Mini MP3-TF-16P播放器模塊(TF/SD卡MP3 Player mini開發模組)
    * 台幣35~90之間
    * microSD卡一張
* 紅外線接收器與遙控器組合 (因為接錯腳位發熱燒壞一個鐵殼紅外線接收器)
    * 台幣35~90之間
* 麵包板 MB-101 8.5 x 55 cm 400孔 有紅藍彩條
    * 台幣15~40之間
* 喇叭
    * 台幣25~50之間
    * 喇叭有回授聲音，Mini MP3-TF-16P 的 RX 到 Nano 的 D3中間，需要一個1KR的電阻
* 1/4w 1KR的電阻 
    * 4支/台幣1元、一小包10元
    * ![img](https://i.imgur.com/21uRyhc.jpg=50)
* 組合成功
![img](https://i.imgur.com/JJACZ0P.jpg=250) 

---

### 開源程式碼
```cpp=
#include "Arduino.h"
#include "SoftwareSerial.h"             // 採用SoftwareSerial程式庫
#include "DFRobotDFPlayerMini.h"        // 採用DFRobotDFPlayerMini程式庫
#include <IRremote.h>                   // IRremote: IRrecvDemo - demonstrates receiving IR codes with IRrecv
IRrecv irrecv(6);                       // Arduino Nano A6 腳位
decode_results results;

// 用來與DFPlayerMini通訊用
SoftwareSerial mySoftwareSerial(2, 3);     // mySoftwareSerial(RX, TX), 宣告軟體序列傳輸埠
DFRobotDFPlayerMini myDFPlayer;         //宣告MP3 Player
                                                             

void setup() {
  // put your setup code here, to run once:
  Serial.begin(115200);     // 定義Serial傳輸速率115200bps
  irrecv.enableIRIn();      // Start the receiver
  Serial.println("enableIRIn");

  // 定義mySoftwareSerial傳輸速率9600bps, DFPlayerMini的通訊速率為9600bps.
  mySoftwareSerial.begin(9600);  

  Serial.println(F("DFRobot DFPlayer Mini Demo"));   // 印出DFRobot DFPlayer Mini Demo字串到Serial通訊埠
  Serial.println(F("Initializing DFPlayer ... (May take 3~5 seconds)"));    // 以下用法依此類通, 不再贅述喔

  if (!myDFPlayer.begin(mySoftwareSerial))           // 如果DFPlayer Mini回應不正確.
  {  //Use softwareSerial to communicate with mp3.   // 印出下面3行字串
        Serial.println(F("Unable to begin:"));       // 然後程式卡死.
        Serial.println(F("1.Please recheck the connection!"));
        Serial.println(F("2.Please insert the SD card!"));
        while (true);                                     
  }
  // 如果DFPlayer Mini回應正確.印出"DFPlayer Mini online."
  Serial.println(F("DFPlayer Mini online."));  

  myDFPlayer.setTimeOut(500); // 設定通訊逾時為500ms

  //----Set volume----
  myDFPlayer.volume(30);     // 設定音量, 範圍0~30. 
  //myDFPlayer.volumeUp();   // 增加音量
  //myDFPlayer.volumeDown(); // 降低音量

  //----Set different EQ----  // 設定EQ(等化器 Equalizer)
  myDFPlayer.EQ(DFPLAYER_EQ_NORMAL);
  //  myDFPlayer.EQ(DFPLAYER_EQ_POP);
  //  myDFPlayer.EQ(DFPLAYER_EQ_ROCK);
  //  myDFPlayer.EQ(DFPLAYER_EQ_JAZZ);
  //  myDFPlayer.EQ(DFPLAYER_EQ_CLASSIC);
  //  myDFPlayer.EQ(DFPLAYER_EQ_BASS);

  //----Set device we use SD as default---- // 設定SD卡
  myDFPlayer.outputDevice(DFPLAYER_DEVICE_SD);

  //----Mp3 control---- // 設定MP3參數
  myDFPlayer.enableDAC();     //Enable On-chip DAC

  
  //----Mp3 play----  // 設定MP3播放參數
  //myDFPlayer.play(0001);  // 播放第1首音樂
  // 在SD卡裡放置MP3的目錄,然後放置名為1的MP3即可
  // SD\MP3\1.mp3
  // myDFPlayer.play(2);
  // 即是撥放SD\MP3\2.mp3這首歌
  // 接下來以此類推
    
}

void loop() {
  // put your main code here, to run repeatedly:
  if (irrecv.decode(&results)) {
    //Serial.println("--測試--遙控器按下");
    //Serial.println(results.value);
    //Serial.println("---------------");

  //這裡的3810010651要依據實際遙控器按下的按鈕來對照，所以如果換遙控器要另外設定值。
  if(results.value == 5316027){  //如果按下遙控器的特定鍵，就顯示訊息！
       myDFPlayer.play(0001);  // 播放第1首音樂
       Serial.println("Turn On! 0001 5316027");
  }
  
  if(results.value == 4001918335){  //如果按下遙控器的特定鍵，就顯示訊息！
       myDFPlayer.play(0002);  // 播放第2首音樂
       Serial.println("Turn On! 0002 4001918335");
  }
  
  if(results.value == 1386468383){  //如果按下遙控器的特定鍵，就顯示訊息！
       myDFPlayer.play(0003);  // 播放第3首音樂
       Serial.println("Turn On! 0003 1386468383");
  }

  if(results.value == 3810010651){  //如果按下遙控器的特定鍵，就顯示訊息！
       myDFPlayer.play(0004);  // 播放第4首音樂
       Serial.println("Turn On! 0004 3810010651");
  }

  if(results.value == 3622325019){  //如果按下遙控器的特定鍵，就顯示訊息！
       myDFPlayer.play(0005);  // 播放第5首音樂
       Serial.println("Turn On! 0005 3622325019");
  }
  
  if(results.value == 16769055){  //如果按下遙控器的特定鍵，就顯示訊息！
       myDFPlayer.play(0006);  // 播放第6首音樂
       Serial.println("Turn On! 0006 16769055");
  }
  
  if(results.value == 553536955){  //如果按下遙控器的特定鍵，就顯示訊息！
       myDFPlayer.play(0007);  // 播放第7首音樂
       Serial.println("Turn On! 0007 553536955");
  }

  //立即停止撥放 
  if(results.value == 1217346747){  //如果按下遙控器的特定鍵，就顯示訊息！
       myDFPlayer.stop();
       Serial.println("Turn off!");
  }
    
    irrecv.resume(); // Receive the next value
  }

}

```
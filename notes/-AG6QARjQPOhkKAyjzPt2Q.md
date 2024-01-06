# 揪己家 Jo Jitsi Plus 經驗分享

[揪己家連結](https://g0v.github.io/jitsi-screen/)
[github repo](https://github.com/g0v/jitsi-screen)
:::success

[summit 工作坊投影片](https://docs.google.com/presentation/d/1SW-8XtGHZrsHFXAj6NvzRsdKw4gb1ULVmFzqom3C1P0/edit#slide=id.p)

揪己家前身為ronnywang所開發的分割畫面小幫手，原始功能為將jitsi中特定會議室特定參與者的聲音畫面擷取出來，方便搭配OBS做直播使用。

在總統杯黑克松時為了滿足分倉分流+多方互動+中央控制的需求，開發了分割畫面小幫手2.0，有中控台可以控制送出設定好的畫面給viewer端。

在總統杯黑克松之後經過了多位貢獻者，完善成為了揪己家，有較良好的使用環境、更穩定的功能。

:::
## 用途
### 作為直播使用
這是一個非常棒的線上會議直播解決方案，除了人數受到jitsi效能的限制(大概25人)
[直播使用教學](https://g0v.hackmd.io/-AG6QARjQPOhkKAyjzPt2Q#%E7%9B%B4%E6%92%AD%E4%BD%BF%E7%94%A8%E6%95%99%E5%AD%B8)
### 作為會議使用
既然是base on jitsi 那當然可以做為會議軟體使用，不過單純的線上會議用原生jitsi好像就可以了
### 作為教學軟體使用
在討論過程中發現，揪己家的功能跟電腦教室中的中控系統是幾乎相同的，老師可以做為中控端，讓學生進入Viewer端，老師即可控制要推送給學生的不同畫面。

## 直播使用教學

### 需求
1. 中控電腦 *1
2. 投影用電腦 *1 (可用中控電腦，但會比較忙)
3. 投影機 *1
4. 電腦螢幕 *2↑
5. 現場畫面鏡頭 *N (視情況搭配導播機)(可用USB CAM取代)
6. HDMI Splitter *1 (將簡報畫面分離一個出來)
7. 影像擷取卡 *2↑ (一個擷取簡報電腦、一個擷取鏡頭)
8. 現場聲音系統
9. 聲音擷取設備 (錄音介面 or 外接USB音效卡)

### 接線方式
- 現場鏡頭 > 導播機 > OBS > VirtualCam > Jitsi會議室
- 簡報電腦開viewer or 原生jitsi
※一定要MUTE！！※
- 開一個多格的畫面，用來送出所有講者的聲音&當作monitor
- 獨立畫面只用來推送
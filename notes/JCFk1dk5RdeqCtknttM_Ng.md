---
title: "仿聲鳥計畫"
tags: 行動藝術,hackpad
---

# 仿聲鳥計畫

> [點此觀看原始內容](https://g0v.hackpad.tw/ca4xQKNQmBZ)

### Story

貳零壹肆年四月十一日，中正一分局包圍事件，由於擴音設備不足，帶頭的人講一句，群眾跟著講一句，句句複誦。直到有抗議人士緊急借用麥克風，始的有發聲權力。警方針對此次突發抗議事件，均將持有揚聲器者視為主謀，優先偵查起訴。這類突發抗議事件沒有實質領頭人，群眾的聲音，應該由群眾建立，話語權也不該只由揚聲器擁有者持有，參與網路者，即有話語權。
許多人都擁有具備小型喇叭的智慧型手機，若有群眾聚集，可利用手機的連網能力建立一小型「仿聲」網路，並透過網路傳播語音資料，並同步最大聲量播放，若大量群眾同意加入網路，即可擴音。
> 這個感覺滿實用的
> [name=Ken Y]

> [https://www.youtube.com/watch?v=NS9e8HBhCa0](https://www.youtube.com/watch?v=NS9e8HBhCa0)
> [name=Ken Y]

### Implementation

- Android first, iOS later.
- Wi-Fi Peer-to-Peer | Android Developers [https://developer.android.com/guide/topics/connectivity/wifip2p.html](https://developer.android.com/guide/topics/connectivity/wifip2p.html)
- UDP-based broadcasting Protocol for Audio.
    - synchronization is key for audio quality.


### Risks

- latency - 技術上會有音訊延遲問題。
- RF interference - 2.4Ghz 之 RF 干擾，可能使網路難以建立
- scalability - 行動裝置作為 P2P GO (group owner) 可能無法承載大量 client. 另外 wifi p2p 模式仍為中央式網路，無 Mesh Network 的 topological structure 擴散能力。
- security - 很容易被 DoS 擊敗，如 RF Jamming, De-auth Attack.

[#Intercom](https://g0v.hackpad.tw/ep/search/?q=%23Intercom&via=ca4xQKNQmBZ)

## References


### Android

- [Blue Talkie](https://play.google.com/store/apps/details?id=ki.bluetalkie) \- 藍芽對講機
    - Pro
    - Con - B luetooth, one master only accept 7 slaves in one piconet.
- pttdroid - pttdroid is a Push To Talk VoIP app for Android - Google Project Hosting [https://code.google.com/p/pttdroid/](https://code.google.com/p/pttdroid/)
- Push2Talk Free - [https://play.google.com/store/apps/details?id=com.ambientic.push2talk](https://play.google.com/store/apps/details?id=com.ambientic.push2talk)
- Android Intercom - [https://play.google.com/store/apps/details?id=com.androidintercom](https://play.google.com/store/apps/details?id=com.androidintercom)
    - [http://iteamserver.iteam.upv.es/revista/2012/4\_ITEAM\_2012.](http://iteamserver.iteam.upv.es/revista/2012/4_ITEAM_2012.pdf)[**pdf**](http://iteamserver.iteam.upv.es/revista/2012/4_ITEAM_2012.pdf)

### 人前還喇叭，人後偷雞鴨

- 還我喇叭花行動小組--5/5(一)上午11:00前進中正一 [https://www.facebook.com/events/635227179893048/?ref=22](https://www.facebook.com/events/635227179893048/?ref=22)
- \[爆卦\] 八六遭上銬帶走 \- 看板 Gossiping - 批踢踢實業坊 [http://www.ptt.cc/bbs/Gossiping/M.1399267673.A.B0E.html](http://www.ptt.cc/bbs/Gossiping/M.1399267673.A.B0E.html)
- 拘捕影片 [https://www.facebook.com/photo.php?v=10201693096601329](https://www.facebook.com/photo.php?v=10201693096601329)
- 陳為廷 \- 超扯。剛接到詹順貴律師的電話，他著急說洪崇晏剛被中正一的便衣押上計程車帶走，應是被現場拘提。... [https://www.facebook.com/a102579/posts/842804449069042?stream_ref=1](https://www.facebook.com/a102579/posts/842804449069042?stream_ref=1)
- 臺北市政府警察局 ─ 臺北市政府警察局拘提洪○晏聲明稿 [http://www.tcpd.taipei.gov.tw/ct.asp?xItem=75587496&ctNode=45192&mp=108001](http://www.tcpd.taipei.gov.tw/ct.asp?xItem=75587496&ctNode=45192&mp=108001)
- 國安局長蔡得勝請辭　李翔宙接任 | 政治 | 新聞 | 風傳媒 [http://www.stormmediagroup.com/opencms/news/detail/162770c4-d437-11e3-9580-ef2804cba5a1/?uuid=162770c4-d437-11e3-9580-ef2804cba5a1](http://www.stormmediagroup.com/opencms/news/detail/162770c4-d437-11e3-9580-ef2804cba5a1/?uuid=162770c4-d437-11e3-9580-ef2804cba5a1)



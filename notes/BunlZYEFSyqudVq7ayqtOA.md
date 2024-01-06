---
title: "太陽花盒子 - Android TV"
tags: 太陽花盒子,hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/9orBp0a61hk)


## 自己的媒體自己報

此共筆為原「太陽花盒子」([https://g0v.hackpad.com/Fr9H87GPcUM](https://g0v.hackpad.com/Fr9H87GPcUM)) 的第二回合，採用 Android TV 為目標設備。專案目標是以 Launcher + App + Remote Control 實現完整的 TV 體驗。

Target machine: mk802 (ex. [http://goods.ruten.com.tw/item/show?21405277754385](http://goods.ruten.com.tw/item/show?21405277754385))

## 主旨

以電視的使用習慣，推播社會新聞，是供理性客觀無過濾不加料的內容給不熟悉網路和社運消息的用戶，消除數位落差。收看社會運動現場實況LIVE，或是大腸花魚腸花，或是和社運有關的直播，立院質詢，公聽會……等等。

## Target User

- 社運觀注、參與的人，多一個閱聽的管道。
- 對 3c 使用、設定沒有障礙，但較少從網路吸收資訊的人，使其了解社運的消息。
- 做為社運觀注或非觀注者，協助家中長輩了解社運，揭發假新聞，偽新聞的工具。

## 徵求

系統工程師 x2 ( survey & provide android tv box 的平台和 total solution 的硬體架構 spec & price，提供 JVM 之外所有 system level 的 software / firmware support )
Android app. programmer x2 (TV App. 開發)
UX 設計師 x2 (TV App. 介面設計，操作動線設計， Icon / artworks 設計)


## Story card

1.  Alice 是長期的社運觀注者，她打開太陽花盒子後，自動跳出上回離開時正在觀看的頻道，若有直播，播放直播內容，若否，則播放相關網路新聞。
2.  Alice 從直播或新聞中聽到某一次公聽會或某人的演講很重要，在遙控器上按一個鈕跳出子選單，羅列與該議題有關的各視頻，Alice 可以找到該場公聽會或演講，選取後取代正在播放的畫面。
3.  Alice 觀注的另一場社運也正在進行中，她可以按頻道上下來搜尋該頻道。
(頻道以議題類型畫分，一段視頻可以被歸類至多個頻道)


## Cordova App Solution

第一階段用 [https://github.com/inLiveTW/server](https://github.com/inLiveTW/server) API，達到像 [Youtube TV](https://www.youtube.com/tv) 般在電視上的良好體驗。
### 困難點

1.  雖然對於極度客製化的電視 UI 使用 Web 來製作，開發速度會比 Native 快，不過在關鍵播影片的部分，體驗可能不佳。現在 inLiveTW 在播放時是利用 Cordova 的 In-app Browser 直接嵌入 Ustream 與 Youtube 頁面，Youtube 似乎無法播，Ustream 需要再點擊播放鍵才能播放，不適合電視體驗。
2.  搜尋了一下，Cordova 好像沒有 Launcher 的 Plugin ，要做成 Launcher App ，應該需要 Android 工程師幫忙。
### Cordova Plugin

1.  [_https://github.com/Urucas/OpenYoutubePlugin_](https://github.com/Urucas/OpenYoutubePlugin)
> 可以直接全螢幕自動播放 Youtube 連結，Hangout 直播連結沒試過 (看到都 Ustream 的)，播放完畢自動關閉，沒有播放清單功能，並且沒有播放結束的事件可以監聽，有點可惜。
> [name=Tzu-Sheng W]

2.  [https://github.com/dawsonloudon/VideoPlayer](https://github.com/dawsonloudon/VideoPlayer)
> 直接去開 Youtube App 來播，所以也會自動播放，但播放結束要按返回鍵，才會回到原 App。
> [name=Tzu-Sheng W]

3.  [https://github.com/matiasmolinas/YTPhoneGapPlugin](https://github.com/matiasmolinas/YTPhoneGapPlugin)
4.  [https://github.com/remcob00/cordova-phonegap\_youtube\_player\_api\_android](https://github.com/remcob00/cordova-phonegap_youtube_player_api_android)
> 待測試
> [name=Tzu-Sheng W]

5.  [https://github.com/Red-Folder/bgs-core](https://github.com/Red-Folder/bgs-core)


> 我是kkyo, 建議可以用舊的android手機當機上盒
> [name=Jeremy H]






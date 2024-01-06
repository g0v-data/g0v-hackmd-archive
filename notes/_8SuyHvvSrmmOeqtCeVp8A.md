---
title: "公民即時網路轉播"
tags: 線路松,hackpad
---

# 公民即時網路轉播

> [點此觀看原始內容](https://g0v.hackpad.tw/XB5JOWTtnly)

參考其他文件：[［共筆］立院學運資訊透明，g0v的動員過程經驗匯集](https://g0v.hackpad.tw/g0v-41moXiJr9GR)，
 [專職社運紀錄團隊、專業起底網站、監督政府地方建設並引導公民能夠實際參與建設提案的專職組織](https://g0v.hackpad.tw/H3CGEk6Mqm4)
> 不好意思，這裡小弟先寫下去了，寫的很亂請見諒
> [name=溫翊伶]

緣由
1.  318學運中，由於有許多突發或未料想的事件發生，於是會派出專人到事件發生的現場進行即時轉播
2.  現在的媒體是否能完整報導整個事件的過程令人懷疑(註:蘋果有派出直播但非全程)
3.  有必要傳達完整的事件發生過程全貌讓關心的公民了解，更避免抹黑或扭曲事實的發生

概念
利用"良好"的網路和"清晰"的畫面加上"清楚"的轉播，讓即時轉播"完整"呈現

未來展望
能成立(還是已經成立?)即時轉播組，在需要的時候出動並馬上讓關心的公民和鄉民知道直播網址，達到比一般媒體更快更完整的現場畫面
> 目前個人對即時轉播有興趣的是公聽會或小型抗議或遊街(割闌尾)，很多人上街的要克服人力器材和畫面混亂等問題
> [name=溫翊伶]

> 自己前陣子有整裡成一張圖([http://i.imgur.com/CknPg8X.png](http://i.imgur.com/CknPg8X.png))，比較是浮游砲的概念(以前的案子實用過)...不過還沒有很完備
> [name=Chen Y]

> 請問公民行動記者的企劃在哪呢?非常的有興趣!!!
> [name=溫翊伶]

> 這是前陣子學運剛退場那天主要轉播停止後有感而作的圖說，目前只有這張圖，本意是想要把整個可以應用現有方案的系統整合，以便讓已運作的/有意願的團體可以在無技術負擔下執行高品質的媒體內容。並想將此架構系統化將細項整理成參考文件、簡報以及網頁來提供執行參考。不過看到這邊在做討論彙集，想說貢獻出來，在這邊整合也不錯!! 
> [name=Chen Y]

> -14/4/16 把AI檔丟出來給大家用: ([http://goo.gl/2deDKv](http://goo.gl/2deDKv) )
> [name=Chen Y]


### 技術面


大腸花直播秘技(0418第三版)
[http://www.slideshare.net/yuting1987/0417-33607269](http://www.slideshare.net/yuting1987/0417-33607269)


曝光管道
- [Ustream](http://www.ustream.tv/)
- [YouTube](https://www.youtube.com/)
- 台灣地區本地的直播網站平台很重要!
- 自行架設Wowza 或 ff server
> 或者用nginx架
> [name=a0000778]

> 流量$$$...
> [name=AceChen]

單兵轉播套裝
- iPad + Upstream App + WiMax or 3G
    - 缺點:有WiMax的狀況下還是會發生斷線，雖然會馬上重連但影響檔案完整性(?)，如果連Wimax的收訊都有問題就更糟糕了(終極大腸花)
- HD Webcam + Laptop + WiMax or 3G + Google Hangout On Air
 缺點: 8Hours斷一次, 每次重開網址會變
> 可以改用Youtube live event網址就不會變了,而且也可自行調整很多選項
> [name=joey91133]

- GoPro + WiMax
- WiMax + Laptop _/w usb 3.0 port_ \+ HD DV /w external mic + 硬體擷取設備(HDMI to usb) + Wirecast 導播軟體 (可視現場連線頻寬調整streaming參數讓直播穩定 / 上字幕)
    - 優點：
        - Wirecast 可直接將轉播內容側錄成 flv or mp4，針對上傳遺失的轉播內容可以留下備份供事後使用。
        - 可視使用器材選取音訊來源，若能取得PA控台的音源，可大大提升直播的聲音品質。
        - 在電源 / 連線穩定狀況下有望達成1080p直播。
    - 缺點：需遷就電源。
- Wowza App + WiMax or 3G
> 行動電源也算基本配備吧 XD
> [name=Yuan C]

> 以上提的配備如果有是要直接捐(?)給g0v的名義使用嗎，不然個人的如有損毀較麻煩
> [name=溫翊伶]

- Ikea or 特力屋3層置物架 + 保鮮膜 (全天候使用，適合定點)
    - 攝影機 / iPad / 電源線可放在裡面(賤民直播台)
    - 若是使用SSD設備不怕震動，置物架可安裝滑輪方便搬移 (視移動區域地面平整度)。
- 電動輪椅+輪椅傘架+大陽傘+外加鉛電池
    - 優點：
        - 下層置物架整合固定式裝備，且有大容量行動電源(鉛電池轉交流電)
        - 移動不費力
        - 不容易被警察攻擊
    - 缺點
        - 需要無障礙空間
        - 若被攻擊毫無防禦力
        - 上廁所很麻煩
        - 颳風時無法遮雨
> 這個方案以前需要錄環景影像時用過，除了離開座位真的很麻煩外一切都很順暢
> [name=Chen Y]

> 如果是在馬路上路過這就很危險了XD 
> [name=溫翊伶]

- 轉播用背心
    - 收納行動電池，直播器材
    - 為了保護攝影器材，要有防水防污防撞的對策

輔助軟體
- 轉撥時畫面上若可以加上日期、時間戳記，對於逐字稿的編寫，以及未來歸檔都有相當大的幫助
    - Google Hangout外掛 [http://swem.github.io/hangouts-clock/](http://swem.github.io/hangouts-clock/)
    - [http://swem.github.io/hangouts-clock/](http://swem.github.io/hangouts-clock/gouts-clock/)[gouts-clock/](http://swem.github.io/hangouts-clock/gouts-clock/)
> 蘋果直播使用的就是這個，但有幾個缺點:：不能高畫質,斷線會出現帳號擁有者的大頭貼,8小時斷一次
> [name=溫翊伶]

> 哪個？Google Hangout 還是Google Hangout外掛？這裡講的是關於在畫面上加時間戳記的輔助軟體噢
> [name=PHLin]

    - 可加時鐘效果的軟體（無法使用Hangout外掛時可考慮）[http://manycam.com/](http://manycam.com/)  [http://camtwiststudio.com/](http://camtwiststudio.com/)

野戰-有線高速網路部署
- 申請中華電信高速網路
    - 需要附近有中華電信箱
- Streaming Server
- CHT Hinet 無線轉有線網路
- Wifly/TPE-Free/iTaiwan (備援)
- [利用電力通信線(PLC)裝置達成遠距網路通訊](https://g0v.hackpad.tw/PLC-RiKBaC4XT4Q)
公民轉播車
- 箱型商用車，配備發電設備、攝影燈光器材、影音剪輯工作平台(可彙整編採資料與製播)。
- 可能的網路連外設備：
    - 指向型天線: AirFiber

空拍設備
- 四軸飛行器
> 目前只看過51和55台出動過空拍用機器
> [name=溫翊伶]


LAN island for sharing message and files
- OccupyHere: a LAN island in an archipelago of affiliated websites.
    - [http://occupyhere.org/](http://occupyhere.org/)
> 請問這是什麼東西@@?
> [name=溫翊伶]

- 網路被斷掉時的區域網路，適用於被警察包圍起來的靜坐人士，將影像或是訊息傳出來

設立專門頁面
-

### 曾進行過的線路松

- [2014/03/08 線路松](https://g0v.hackpad.tw/2014-03-08--jG9uno4d9H8)
- 2014/03/18 佔領立法院
    - [太陽花學運背後的IT祕辛：第零次向日葵數位體驗營](http://www.ithome.com.tw/news/86701)
        - [Video](http://youtu.be/GwIMe3MNQ_Q)
> 可否結合[路人松](https://g0v.hackpad.com/-aka-user-story-dw3SAk6gdcb)？
> [name=AceChen]


### 法規面

- 拉固接網路到抗議現場合法還是非法?
- 集會遊行法 [釋字第718案](http://www.judicial.gov.tw/constitutionalcourt/p03_01.asp?expno=718)
-  公民記者

### 現有相關計劃

- [公民行動影音資料庫](http://www.civilmedia.tw/about)

Reference

資料傳輸方案
- Super Wifi
- 數位廣播頻道(單存用來送文字應該可以)
- 數位電視 broadcast, 然後用receiver收


---
title: "學運現場無網路的通訊解決APP方案"
tags: CongressOccupied,hackpad
---

# 學運現場無網路的通訊解決APP方案

> [點此觀看原始內容](https://g0v.hackpad.tw/h4wPgytCjac)

## 關於

- **發起人/拋磚人：Lrills**
- **狀態：** 集結各路好漢
- **專案簡介：**
        學運現場的無網路解決app方案
> 參考「**在會場中建立可靠的訊息傳遞網」**  [https://g0v.hackpad.com/d6rh3bXemcK](https://g0v.hackpad.com/d6rh3bXemcK) 兩案坑主可協作討論
> [name=venev]


- **工作目標：**
        短期可能目標：快速開發提供反服貿運動使用
> 要offline地傳送事件訊息、GPS經緯度、案發現場圖片到一server端
> [name=Clement C]

        長期可能目標：創造一個開放源碼的無網路通訊協定
- **授權方式：**
- **使用資料：**
- **徵求夥伴（有興趣直接簽名）：**
- **NeedsWriter (撰寫基本資訊、報導專案 etc)：**
- **NeedsDesigner (介面設計)：**
- **NeedsData (擷取整理資料)：**
- **NeedsTech (程式、架站 etc)：**
- **NeedsProcess (設計作業流程)：**
- **NeedsTalkingToRealPerson (需要真人溝通協調)：**

## 發想提案

[http://www.ptt.cc/bbs/FuMouDiscuss/M.1396630334.A.53A.html](http://www.ptt.cc/bbs/FuMouDiscuss/M.1396630334.A.53A.html)
ptt發想連結

--

目前想到的p2p流程圖如下，有要更正請幫忙指出：
A:案發現場人士、Z:3/4G對外使用者(一般是現場糾察)
節點間通訊用WiFi-D或BT
> 查資料時剛好看到這篇，裡面有提到幾個問題，雖然我都還沒查證但先提出來給大家參考：
> [name=Chang Y]

> 1\. wifi direct似乎有些4.x以上的機型硬體不支援 
> [name=Chang Y]

> 2.BT耗電，且最多與7個peer連線 
> [name=Chang Y]

> 3.BT-LE較不耗電但android 4.3以上才支援
> [name=Chang Y]

> [http://stackoverflow.com/questions/19439142/wifi-direct-bluetooth-or-internet-for-discovering-people-in-the-surrounding](http://stackoverflow.com/questions/19439142/wifi-direct-bluetooth-or-internet-for-discovering-people-in-the-surrounding)
> [name=Chang Y]

為了時間上要加速實現，目前簡單用一個節點通報兩個節點，若遇到重複就pass掉重連

A---通報--> B---通報---->D   以此類推， 直到傳到Z 去連結server回報訊息
                    B也通報   -->E
    A也通報->C-通報-->F
                      C也通報-->G

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1918191f7f740f8d7875ad50dac29ec9)
> 是這個意思嗎?但是z要回報給server什麼呢?
> [name=Chang Y]

> ps. 剛好看到這兩篇文章《資訊人眼裡的太陽花》，貼給大家看看
> [name=Chang Y]

> [http://www.cool3c.com/article/78110](http://www.cool3c.com/article/78110)
> [name=Chang Y]

> [http://www.cool3c.com/article/78231](http://www.cool3c.com/article/78231)
> [name=Chang Y]



--
> 你要不要先把PTT原文網址貼出來?
> [name=Mosi W]

> 好XD
> [name=佩承 劉]

> [http://www.ptt.cc/bbs/FuMouDiscuss/M.1396630334.A.53A.html](http://www.ptt.cc/bbs/FuMouDiscuss/M.1396630334.A.53A.html)
> [name=佩承 劉]

> ptt發想連結
> [name=佩承 劉]


> 其實有個很基礎的問題，就是你做成APP的話，沒有SERVER，要是在網路連線困難的情況下， 大家一開始還是沒有辦法下載XD
> [name=Mosi W]

> 所以可能要另外做出「任何人只要有裝APP 就可以成為第0台SERVER，雖然沒有企業CERT，但是最起碼可以提供APK給ANDROID USER下載安裝連上....」
> [name=Mosi W]


> 對 大概想法是這樣但是沒有相關通訊軟體的經驗沒什麼頭緒...但是web app沒辦法控制到裝置上的藍芽...
> [name=佩承 劉]

> 是的!! 希望能解決330那種狀況
> [name=佩承 劉]


> 你一樣是native app啊 ...
> [name=Mosi W]

> 要快速做出來的話可以考慮直接寫HTTP SERVER + 跑在 WEB SERVER上的 APP 
> [name=Mosi W]

> 不過因為現在立法院外面網路順暢 甚至有 g0v 的免費 WIFI AP.....
> [name=Mosi W]

> 所以回過頭來 這個project是不是定義成 "無網路環境下的區域通訊解決方案(含LOG)" ?
> [name=Mosi W]

> 其實我記得 g0v 有個很類似的坑..... 但是要找找看
> [name=Mosi W]

> 在這裡-\> [https://g0v.hackpad.com/d6rh3bXemcK](https://g0v.hackpad.com/d6rh3bXemcK)
> [name=Mosi W]


> 我個人認為這個APP最需要的權限是 強迫關閉手機 3g 連線XD
> [name=Mosi W]

> 然後自動挑幾隻當樹最上面的 node ，用 3g 連出去
> [name=Mosi W]

> 就跟直銷一樣...... 一路往下擴散傳資料
> [name=Mosi W]

> 每層 node 之間 sync 而不是p2p在 sync
> [name=Mosi W]

> 因為你要解決的是 330 那種 10k級的人數 
> [name=Mosi W]


> 會希望有頻道的功能分流，每個node建立起一個識別資訊，識別所屬的頻道
> [name=佩承 劉]

> 所以是把群眾分流程幾個區塊，各用一個節點連上server這樣嗎?
> [name=佩承 劉]


> 如果如果是iOS的話可以做到給每個裝置一個識別資訊，搜尋附近所有的頻道。
> [name=佩承 劉]


> 恩一開始想的是透過每個peer發布出去的時候可以自帶一個peer的info(4KB以內的dictionary)，從這裡來作識別，如果要提供列表資訊的話會變成一定要連上internet嗎?
> [name=佩承 劉]


> 不是一定要連上 internet 
> [name=Mosi W]

> 是在 user 推廣觀點.....
> [name=Mosi W]

> 今天一個 new user 進入你的場域
> [name=Mosi W]

> 有裝這個 APP 的人當然不用說 他們知道要開
> [name=Mosi W]

> 那沒裝的人呢?
> [name=Mosi W]

> 所以你↓↓看下面
> [name=Mosi W]


> 這個其實你不配個在 internet 上的統一入口
> [name=Mosi W]

> 是沒辦法把 user 導進你的 intranet 或是 darknet 的
> [name=Mosi W]

> 但是總而言之 無論 user 是在 intranet 還是 darknet 
> [name=Mosi W]

> 進來之後就是給他頻道列表讓他選 他再直接連上 primary node
> [name=Mosi W]


> 坦白來說 如果沒有 g0v 
> [name=Mosi W]

> 這種遊行現場的網路解決方案
> [name=Mosi W]

> 如果我要玩 那就是幾組 wimax+wifi ap，但是停留在 intranet 上
> [name=Mosi W]

> 讓user全部都連上我的 ssid 進我的 intranet
> [name=Mosi W]

> 然後我用幾台 android 機器跑 httpd server..... 
> [name=Mosi W]

> 一切都是 web app 這樣XD
> [name=Mosi W]

> 你要實作 open garden (firechat...)當然沒有問題啊
> [name=Mosi W]

> 問題是官方也才剛實做完XD
> [name=Mosi W]


> 好像真的是比較實際的做法...我沉澱一下下XD
> [name=佩承 劉]


> 也不是沒人再ios作http server唷 應該超多XD
> [name=Mosi W]

> 因為我看我每隻 player 跟 pdf reader 都有內建上傳檔案進APP用的http server 啊
> [name=Mosi W]


> 綜合另外一篇看了一下稍微懂了一點...
> [name=佩承 劉]

> 所以綜合一下可能的方案會是1.intranet 2.由可連線的node推播(如另一坑方案) 3.firechat方案 
> [name=佩承 劉]



## 技術分析與討論

可行方案優缺點分析：
### 1.intranet

    優：
    - 可快速由現有資源搭建或者修改，甚至不用上架到兩個 store
            - 活動現場支援用backpack ，真的包成一個背包出團，例如:  Server pack: wimax + wifi ap + nb + nb用行動電源 + webcam
            - Live pack: wimax + 行動電源 + iPad
    - g0v線路松支援後，可以直接從 intranet 變成 internet  **_(*1)_**
    缺：
    - 主辦單位或有心路人需在活動前準備好 Server pack 帶過去現場
    - 每個 server pack 的 session 數被 ap 限制
    - 因為是 s/c 架構，所以 server 的負載度需要考慮一下 ( node.js / Golang / backbone.js ....)
### 2.由可連線的node與雲端相連

    優：
    - 節省 3g 資源
    - 不論地點平台都能加入
    缺：
    - 需有前幾個 node (或者主辦單位都會裝的話那倒是不用煩惱)
    - 3g收訊死角造成盲區
    - 群首整組消失時? 例如整群人被水柱噴濕 offline
### 3.firechat(*2)

    優：
    - 去中心化
    - 不論時地都可使用
    - 只要中間有node串接，理論上支援範圍無限大
    缺：
    - 須先下載APP
    - 聽說目前版本iOS和Android不互通? (查證中...)**_(*__3__)_**
    - p2p同步較無效率，可能無法負荷如330遊行10k up人數**_(*__4__)_**
*1
> WiMAX hotspot 或WiFi AP support連線user數也會受限
> [name=Clement C]

> 如果把 wifi ap 的天線拔掉似乎可以透過距離縮短來減少使用人數? (誤
> [name=Mosi W]

> 可是不巧全球一動大力玩是內建天線(毆
> [name=Chang Y]

> 一般WiFi AP都可以簡單調整發射功率，看看大力玩是否也可調整WiFi的發射功率。如果不行，只好拿鐵便當盒蓋住XD 
> [name=Clement C]

> WiMAX 確定要淘汰了，未來 device 已經頃向 LTE
> [name=楊佑仁]

> FD-LTE系統中華電信會較先設立，目前已經cell plan中。至於WiMAX就看會不會就地升級成TD-LTE，不過device是絕對不相容的XD。但dervice都會弄成大力玩型態(誰叫WiFi普及率這麼高)，所以對APP設計(若是經WiFi-4G系統連上網)基本上影響不大
> [name=Clement C]

*2
> 從另外一篇文章看到有qaul.net跟Telegram都有同樣類似的效果，也可以download到手機試試看，我先借幾個Android手機來試試看這三個APP的實用性
> [name=Clement C]

> 我用了10隻Android手機試了firechat，一起打開的時候，只有3隻手機互相連線成功，剩下的找不到彼此。當中完全不知道是哪3隻手機連線中，只有講話的時候才會顯現出手機ID。而且若其中一隻手機從中途離開後重新連線會沒辦法看到兩隻之前傳送的訊息。
> [name=Clement C]

*3
> _ref:_ [_http://stackoverflow.com/questions/18884705/transfer-data-between-ios-and-android-via-bluetooth_](http://stackoverflow.com/questions/18884705/transfer-data-between-ios-and-android-via-bluetooth)
> [name=佩承 劉]

> 可能解法 1.android透過wifi監聽iOS device發布的bonjour服務(理論可行，但找不到實作的例子) 2.BLE (但android端有bug待解決)
> [name=佩承 劉]

> 剛請朋友測過Firechat的iOS跟Android連通，互相找不到dervice。所以可以由iOS一個大group，Android一個大group往下去sync資訊，只要iOS跟Android兩個節點的資訊同步即可!?   android也有firechat
> [name=Clement C]

> android是用什麼跟ios的firechat測的阿? 哦哦?上次我沒找到的說。我現在看到了
> [name=Chang Y]


*4
> 其實應該說 10K up 到底 p2p sync 要花多久...
> [name=Mosi W]

> 如果10層內可以傳完所有node應該是很快的，但是無法徹底解決對同一node重複播送的問題
> [name=佩承 劉]


> 我想問節點間的傳輸是always連線嗎?用bluetooth或WiFi?對外看起來可用WiFi或3/4G。Open garden提到用Bluetooth跟WiFi-Direct(Android4.x以上支援，這門檻會過高嗎?==>ok)，當然可以用Bluetooth連線。WiFi點對點我們有測過，大約戶外30公尺算極限了，bluetooth理論上會更短，不過傳message bluetooth應該絕對夠用。
> [name=Clement C]

> ios multipeer的話是apple已經幫包裝好搜尋所有wifi or bluetooth下的peer 
> [name=佩承 劉]

> Android 4.x market share 已經過半，理論上市場接受度是可行的 [http://developer.android.com/about/dashboards/index.html?utm_source=ausdroid.net](http://developer.android.com/about/dashboards/index.html?utm_source=ausdroid.net)
> [name=楊佑仁]

> 另外，節點間的 http 持續連線方式是不可行的，keep connection alive 會占用 device 資源，當量一大就會 crash，除非能確保 one-to-one
> [name=楊佑仁]

> 想了解一下，wifi或bluetooth有辦法判斷距離嗎?例如訊號要多高才進行連線和資料傳輸，以這種方式篩選附近的人數
> [name=楊佑仁]

> android 有 getScanResult( )，ScanResult 裡面有個值叫level可以得知wifi訊號強度(單位dBm)
> [name=Chang Y]

> [http://developer.android.com/reference/android/net/wifi/WifiManager.html#getScanResults%28%29](http://developer.android.com/reference/android/net/wifi/WifiManager.html#getScanResults%28%29)
> [name=Chang Y]

> 藍牙的似乎有個RSSI值是強度(單位dBm)
> [name=Chang Y]

> [http://stackoverflow.com/questions/15312858/get-bluetooth-signal-strength](http://stackoverflow.com/questions/15312858/get-bluetooth-signal-strength)
> [name=Chang Y]

> 想問一下在場對於開發進度的想法！要討論出一個雛型直接進行開發，或是先整理的完善一點，在4/19號的hackthon現場開發！？
> [name=佩承 劉]

> 想詢問一下目前開發進度？因為昨天出關就遇到這種困擾，還差點誤事..XD
> [name=小俞Yu]

> 直接 UDP 廣播封包會不會更省事？
> [name=波卡Poka]

> UDP廣播很省事，但怕packet loss，尤其人一多，更怕不知道誰有掉誰沒掉，這變得要想辦法克服packet loss。
> [name=Clement C]

> packet loss的問題可以考慮用forward error correction來解, 不過缺點是會把其他tcp流量打趴
> [name=Chang Y]


### 4.Zigbee 微型外接通訊設備

    參考資料：[http://zh.wikipedia.org/wiki/ZigBee](http://zh.wikipedia.org/wiki/ZigBee)
    優：
    - 支援大量網路節點的網路拓樸
    - 省電
    -
    缺：
    - 設備需要採購、製作
    - 手機需要外接設備（透過micro USB / lightning / ipad 30pin）
    - 頻寬較少，僅適合傳輸文字訊息
> Zigbee設備很便宜，也支援尋找附近鄰點的功能，但使用頻帶接近WiFi，很容易被WiFi干擾，要想辦法加入重傳功能或利用其他介面傳送。
> [name=Clement C]


## 介面設計

小俞：報名UI設計！
歡迎 感謝Q口Q
> 改成緊急事件回報 用途比較廣XD   
> [name=Mosi W]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8d0fd46663e3a6f05786ad77b26a69bd)



小俞：剛剛快速作了一些東西，有任何建議直接寫上來吧，其實因為現在flow還沒出來所以都亂做XDD（對了，名稱是亂取的）準備出門去守夜了掰！
> 現場有網路XD 
> [name=Mosi W]

> 我都收不到耶？是g0v的嗎？
> [name=小俞Yu]

> 青島東路的話 小七附近應該有 濟南的話應該很多隻啊我記得 (不過我只有用過g0v內部用的 沒用過開放給大家用的版本orz) 濟南路叫做 g0v-public 的樣子 開wifi搜尋一下
> [name=Mosi W]

> 那邊感覺完全被屏蔽啊QQ 中華電信工會你們不是要出來反對了嗎？快開個訊號車來嘛～
> [name=小俞Yu]

> 人太多 3g 沒訊號正常啦 而且我還真的沒看到中華的車耶 遠傳跟台哥大很多台XD
> [name=Mosi W]

> 我有看過一次神奇的車子，有拍到，照片再此：[https://flic.kr/p/mrS8L5](https://flic.kr/p/mrS8L5)
> [name=小俞Yu]

> 但其實不知道幹嘛用的就是了....感覺是私用（？）
> [name=小俞Yu]

> 那是小台基地台XD  用吉普車是方便颱風啊什麼時候進山裡面用的.... 那台車可以游泳的~~~
> [name=Mosi W]

> 已感動QQ  
> [name=佩承 劉]

> clement是ptt的sibaseman大嗎?  yes
> [name=佩承 劉]

> 謝謝你！需要高手qq
> [name=佩承 劉]

> 安安各位，結果3G網路可以通w
> [name=小俞Yu]

> 那是否需要把醫療事件獨立出來？
> [name=小俞Yu]

> 我覺得小俞 \+ MOSI W 的圖給出了一個開發方向，Firechat 提供了無差別發言平台，但無法針對某項訊息進行回應
> [name=楊佑仁]

> 可以就 bbs 或論壇的形式製作，例如：
> [name=楊佑仁]

> 1 . 依 GPS 標出事件地點
> [name=楊佑仁]

> 2\. 事件狀態粗分『待處理』『處理中』『處理中，待增援』『已解決』等等
> [name=楊佑仁]

> 3\. 一個事件底下包含內容、時間(系統產生)、地點(系統產生)、回應(依距離分出其可信度和有效性，也可用來做排序)
> [name=楊佑仁]

> 4\. 事件的產生和回應，可以用通用選項方式，加速回應速度，畢竟手持 device 的輸入速度仍舊快不過點選方式
> [name=楊佑仁]

> 是否結合Google地圖？
> [name=小俞Yu]

> 以上面的想法 Google Maps 是一定要的，但也需要提供依距離、狀態可進行排序、分類的列表(for offline device)
> [name=楊佑仁]

> 誰來判事件狀態的處理進度？
> [name=小俞Yu]

> 最簡單的方式當然是由事件發起人決斷，但如果遇到事件發起人被載去野放，可由現場人員發出最新狀態，但須列出該狀態發出筆數，每人限發一種狀態，並會取代同一事件同一人前一次狀態
> [name=楊佑仁]

> 例如：\[待處理\]小七前有人昏倒，此事件因為發起人被野放無法即時更新狀態，現場人員即可發出狀態『\[待處理(主)\]\[處理中(3)\]\[處理中，待增援(10)\]\[已解決(0)\]小七前有人昏倒』，從狀態中可看出大部分人認為仍須處理並增援
> [name=楊佑仁]

> 現場人員的定義同樣可用距離決定
> [name=楊佑仁]

> 所以可能可以用人數來判斷事件可信度(處理度)，然後顯示出來高中低這樣。
> [name=小俞Yu]

> 是否需要一個server去蒐集這些information(如GPS定位點與統計人數等等)後統整？  另外事件選項也是盡量簡化，如醫療、警備、衝突(攻擊行為)、社會安全或其他等等
> [name=Clement C]

> server 端要做的幾件事：
> [name=楊佑仁]

> 1\. 開發 API 供 APP 在進入網路環境中進行資料交換
> [name=楊佑仁]

> 2\. 能承受大量資料存取的儲存架構
> [name=楊佑仁]

> 3\. 資料統計與呈現頁面(**討論是否需要管理介面，由誰管理?**
> [name=楊佑仁]

> 我想到bitcoin的網路架構，而且bitcoin中的區塊鏈不用全都儲存。
> [name=楊日新]

> 如果能解決資料龐大的問題，我也投  的網路架構一票
> [name=楊佑仁]


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_aa98dd49b45fba28b8762b0f1a303b81)

再丟個圖給大家討論發想！！
> 建議，將鴿子動態改成政府單位動態，應用範圍會較廣，因為你不能保證不會動用軍方武力(大誤
> [name=楊佑仁]

> 可以談談訊號偵測的用意嗎？
> [name=楊佑仁]

> 看看適不適合，可以加 profile settings 在搜尋戰友時可以依技能、種族...喔不，是職業分類
> [name=楊佑仁]

> 訊號偵測是因為前一張圖有出現「目前頻道」與「連接節點」，我想也許可以用上
> [name=小俞Yu]

> 而關於使用者，是否要用到這麼個人化？我以為只是會給一個隨機固定的UID(?)就可以開始使用了，這樣也能避免被國安單位監控。
> [name=小俞Yu]

> 呃，新的圖怎麼又不見了= =
> [name=小俞Yu]

> profile settings 只是要讓個人的專長職業有地方填寫而已，當然，這東西有沒有必要就和大家討論一下囉
> [name=楊佑仁]


> 話說，雖然主戰場準備撤退，但按照大夥對「執政當局」的理解，這個APP總有一天會派上用場的，所以我個人建議把他做完。
> [name=小俞Yu]

> :emoji_1f44d:
> [name=Vendetta]

> 同意
> [name=Chang Y]

> 而且如果個人預測沒錯，最慢78月要簽貨貿的時候就有機會用到了…(唉…)
> [name=小俞Yu]

> 同意+1
> [name=Clement C]


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4e6800428101a561e338541ad76b9029)

用了類似PTT的方式去做，不知道各位覺得如何？
> 還是要加排序方式給user選比較好~
> [name=Mosi W]

> 額，對耶，而且我發現忘了放時間…
> [name=小俞Yu]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9edc7c7a4d57d1222ed2c97e3e1d7107)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_92ad76d0b73f43c82f663e2031391e43)
＊舊的過程圖檔自行清除了
詢求各位意見～


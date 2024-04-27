---
title: 懶人包：我要如何購買 Meshtastic 裝置 / DigiResiTh0n
tags: digital-resilience, resilience, internet-shutdown, digiresi, civil-defense, 民防, 數位韌性松, DigiResiTh0n, hackathon, meshtastic, mesh, lora
---

# \[懶人包\] 我要如何購買 Meshtastic 裝置

作者：@dryden（g0v slack）

source: https://www.facebook.com/groups/meshtastictw/posts/434624832280048/
[](https://www.facebook.com/groups/413628121046386/user/1648816647/)

Meshtastic 使用的是 LoRa 的傳輸技術，而 LoRa 的特色是，在可以直視目標物且沒有阻礙物的狀況下，傳輸距離可以達到數十甚至數百公里。但一旦中間有建築物阻擋，訊號傳輸的距離就會大幅下降到十公里以下。

而在都市裡，高樓大廈會讓 Meshtastic 的傳輸距離下降，因此在此會推薦購買兩種裝置，**手持的 Meshtastic 裝置**與 **Meshtastic 太陽能節點裝置、自製窗邊節點**：

##### **手持的 Meshtastic 裝置**

-   最適合入門的是 Heltec v3 ESP32 這台，可以直接在蝦皮的官方店購買到原裝版本、或是預安裝好 Meshtastic 版本。 
    · 需要自行參考教學文，透過電腦將 Meshtastic 韌體刷入，並在 app 內完成設定 
    · 購買連結 https://heltec.cashier.ecpay.com.tw/product/000000000612179 （可使用本社團專屬限量折扣碼 MESHTW101） 
    · 頻率請選擇 863-928，才符合台灣法規（台灣用的是 923） 
    · 配件爲鋰電池，若是搭配購買，未來在使用時會比較方便。 
    · 若沒有選購鋰電池，可以透過行動電源 + USB type-c 來供電。
    

##### **放置於高樓頂端的 Meshtastic 太陽能節點裝置**

高樓樓頂因爲比較不會受到建築物的阻礙，可以發揮 Meshtastic 長距離傳輸的特色，因此當一個城市中，大樓的樓頂都裝設了節點，就可以確保訊息可以互相串聯，傳送到遠處，將網路覆蓋範圍擴展開來。但由於高樓樓頂的電力往往不易取得，又或是考量到大型災害時需要確保大樓節點可以正常運作，因此推薦在高樓樓頂放置太陽能節點。

而目前在台灣尚未有廠商推出整套的 Meshtastic 太陽能裝置。  

-   因此可以選擇自行購買太陽能板、防水盒、充電電池、天線，組合出適合的太陽能節點
    
-   或是購買由板主我，將市售太陽能電池改裝後製作的太陽能節點  
    · 根據使用的開發板不同，分爲兩種版本  
    · 使用 Heltec v3 開發板，搭配 3 顆 18650 鋰電池  
    ·· 開發板成本較低、且容易取得，但開發板本身相對耗電，因此較適合放置在日照多的地區，例如臺灣南部  
    · 使用 RAK 開發板，搭配 2 顆 18650 鋰電池  
    ·· 開發板更省電，因此更適合用於太陽能裝置，尤其是容易多天不見太陽的台灣北部地區。但台灣沒有官方代理，需要從海外購入，成本較高。  
    · 購買連結 https://myship.7-11.com.tw/general/detail/GM2403162994445
    

##### **放置於窗邊的 Meshtastic 自製窗邊節點**

畢竟不是每個人都有頂樓可以使用，但絕大多數的人都可以在窗邊放置一個節點，也對於提升整個區域的訊號有幫助！

會需要以下配件

-   Heltec v3 開發板一個
    
-   塑膠盒一個（我使用的是 18650 電池盒，需要自己動手挖兩個洞）
    
-   USB type c 電源線一條、USB 充電器一個
    
-   品質良好的天線一個
    

組裝成果可以參考附圖，如果需要購入材料，一樣可以參考這個購買連結 https://myship.7-11.com.tw/general/detail/GM2403162994445

看完後如果有疑問，可以在爬完其他人的留言以後，在底下留言發文唷

下一篇：\[懶人包\] 購買後要如何設定 - 刷韌體  
https://www.facebook.com/groups/meshtastictw/permalink/414578450951353
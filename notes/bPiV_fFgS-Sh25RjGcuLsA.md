---
title: "太陽花盒子－自己的媒體自己報－"
tags: 0media,太陽花盒子,hackpad
---

# 太陽花盒子－自己的媒體自己報－

> [點此觀看原始內容](https://g0v.hackpad.tw/Fr9H87GPcUM)

## 此專案新開 Android solution 共筆於  [Android TV](https://g0v.hackpad.tw/9orBp0a61hk)

/\* 命名可以再思考一下更加有公民資訊透明含意，不過也許可以不用，這個名字也是很有歷史意義。 */
### 第一次來的人可以跳到最底下看 FAQ (麻煩讓 FAQ 置底)

> 經過嘗試，網樂通的開發成本偏高 (遙控器的 delay 太嚴重，播放影片的 navigation 會失敗， youtube, justin, ustream 的 plugin 要另外開發，需要再自己維護 repo server)，time-to-market 太長，還有即使完工，其 availability 的不確定很性高。目前決定暫停開發，轉為評估 android tv，可能選 mk802 / A10 為目標平台。高單價的 android tv platform 還有 mk808 和 rk3066。請對 android tv 有經驗的朋友不吝指教。因為 solution 改了，assumption 也改了， TA 也會跟著調整。目前鎖定為有能力自行設定 android tv 且與長輩同住的朋友。
> [name=Benjamin T]


## 主旨：

　　要挖的坑，設計「機上盒 or APP」，專門收看社會運動現場實況LIVE，或是大腸花魚腸花，或是和社運有關的直播，立院質詢，公聽會……等等。（[概念圖１](http://farm9.staticflickr.com/8288/7745942538_85bbe2d9b3_c.jpg)）（[概念圖２](https://www.facebook.com/photo.php?fbid=821715797842060&set=a.820703047943335.1073741837.100000109433022&type=3&theater)）
> ~建議把「App」改成「機上盒」，畢竟目的在把電視人的視線和網路人的視線交疊起來。無論如何就是接到電視，不是手機，也不是平板。至於機上盒的實作方式可以分流，也可以集中火力，用 App 或用刷機的方式實現。~
> [name=Hong-Bin T]

> 這主意不錯耶，「[第五權電視牆監看「評」台g8v.tv](https://g0v.hackpad.tw/g8v.tv-lk9pamtKwyr)」可以成為太陽花盒子之後的收視來源之一嗎www
> [name=NewCliCker]

> content management 會是下一個階段的問題，目前必須先做的是讓電視人有盒子可以看網路人的內容 :)
> [name=Hong-Bin T]

> content完全不需要擔心，如果有哪一個 channel可以有 10 萬個收視戶的話 (假設 50 萬個盒子收回 30 萬個，然後 20 萬個RMA變磚塊我們也不想理它)大概所有的藝大、新聞社團，都會想要來玩耍...
> [name=Zhemin L]


備註：
　　現在全中國大陸的電視頻道，都可以用某些機上盒（主要是軟體業者／視頻業者）通通看到，下面提供的 Android 環境的電視盒就有這個功能。
　　中共是宣傳媒體控制住之後，引導人類的說話內容與思想模式，這點省略不談。我們在臺灣實驗的模式，是「自由中國」這種雜誌的２１世紀數位模式、加上平民百姓可以「開電視台」／有些科幻片或是美劇不是常見「地下組織」的電台廣播，用些電腦電子學知識，傳遞資訊嗎？
PS.美劇《神盾局特工》（英語：Agents of S.H.I.E.L.D.），第一集一開始就是地下電台廣播。
> 那我們可以 recruit Skye 嗎？
> [name=Hong-Bin T]



## 成員：

前端 GUI: Mark (目前不熟 irc ，[透過 Facebook 找我](https://www.facebook.com/tzusheng))
fw engineer: hbtsai (@irc, @github, @facebook, @gmail)

## 黑客松

- 20140416 g0v.tw hackath8n | 台灣零時政府第捌次解除戒嚴黑客松 [http://g0v-tw.kktix.cc/events/g0v-hackath8n](http://g0v-tw.kktix.cc/events/g0v-hackath8n)
- [20140510支持松-太陽花盒子](https://g0v.hackpad.tw/QZ7WShK1gPu#20140510支持松-太陽花盒子) 〔支持松〕無限期支持 g0v 支持 CCSP Hackathon [http://ccsp.kktix.cc/events/hackathon](http://ccsp.kktix.cc/events/hackathon)

## 說明：

　　這個計畫也就是「家電上網」的其中一個環節、這個家電指的是電視，本計畫是要用市面上現成的產品來進行軟體平台的開發。
　　從市場的角度來看，用網路電視盒（棒）的意義在於，用「鍵盤+滑鼠」跟「電視遙控器」的差別，對原本只用電視吸取資訊的人降低門檻，也可以用同樣的習慣查閱網路上的資訊，擴大收視族群。
> 需要討論 TA (target audience) 的問題: 1)鄉下只有第4台、沒有網路的人，是不是 TA? 2) 會在手機上玩方塊看風行網的人，是不是 TA?
> [name=Zhemin L]

> 我所定義的 TA 是這樣：有關心時事，家裡有拉固網的人，對社群不熟，沒上 FB 也沒上 PTT，沒看 Youtube 也沒玩 Line。年齡層不一定，不是所有的年輕人都對網路有依賴性。但中年以上的人來說，看手機的字太小，滑手機手很痠，不如看電視。或是家庭主婦需要常常起身做家事，可以放著看放著聽。想拉攏這些人。1) 沒網路的抱歉了 2) 手機的重度 user 應該對 FB 很熟，可以是次要 TA，因為他本來已經會關注了，多個盒子只是多一個管道。手機的輕度 user，回家會看電視不會玩手機的，是 TA。
> [name=Hong-Bin T]


### 網樂通版

（募集計畫，細節補充在下面）
發想人：hbtsai
有鑑於看電視的人不看臉書，玩搖控器的人不玩鍵盤，很多社運相關的消息從現場發生後，第一手來自 PTT，第二手來自臉書，第三手才到媒體，已經被改到不成形了。
我提議將之前蘋果被腰斬的「網樂通」磚塊改機，做成一個機上盒，直接連到網路上的 content，可能是 g0v.today，也可能是 youtube  的 channel，也可能是直播頻道。簡單講就是把畫面直送進電視裡，不要再被媒體重製、詮釋、扭曲、抹黑、抹綠、抹紅、抹黃。
選擇網樂通是因為 1\. 蘋果已經免費送出約五十萬台 2. 效能說實在還不錯 3. 它現在完完全全就是磚塊。如果有其他可改機的磚塊要推薦，也請不吝提供。
> 在露天拍賣上，賣價大概是 150, 200, 300, 500, 1300 買價大概是 110. 看來市場上這個盒子離「免費」有點距離... 可能需要重新想像一下...
> [name=Zhemin L]

> 我們的刷機基本是免費，應該是自己拿著網樂通來請人刷，如果是伸手拿網樂通，基本也是有民眾免費捐的。
> [name=Hong-Bin T]

> 現在網樂通要取得的管道已經越來越少, 甚至連回收場都去問過也沒有, 50萬台實在是過於樂觀的數字, 可能大部分都直接被丟到垃圾場了吧...
> [name=Chia-Cheng H]


### Android版

發想人： Michael_LI
　　本人提議 Android 環境的電視盒，主要認為此平台長遠看來都是主流，影響力比較大，本人可以提供一款商業產品進行測試與開發。
> Michael 我們打算評估 Android TV 的 solution，想請教你手上的平台的 hw spec，還有它的成本，有沒有紅外線和搖控器和開發套件等等。
> [name=Benjamin T]

> 既然要開發 Android 我只能先評估看看 [https://github.com/Urucas/OpenYoutubePlugin](https://github.com/Urucas/OpenYoutubePlugin) 的可行性，如果不好用，可能就要再推其他 Android 工程師坑了。
> [name=Tzu-Sheng W]

> 可以參考一下 inLiveTw ([https://github.com/inLiveTW](https://github.com/inLiveTW)) 他們已經有用Cordova 了，只是還有些細部要調整。
> [name=Zhemin L]

> 那個只是用 in-app browser 去開網頁，那個都還要去點一下才會播放，不適合電視的體驗，之前敝公司開發產品也遇到無法自動播放的問題，上面貼的是整合了 Youtube SDK 的 cordova 套件，希望好用囉。 
> [name=Tzu-Sheng W]

> 可以開新頁討論，這頁有點長到太可怕。
> [name=Rex T]

> 另外改成 Android solution, 可以不管使用的硬體平台，直接做 TV Launcher 或 App 即可。
> [name=Rex T]


### Linux版

發想人：Michael_LI
**　　硬體：**[Raspberry Pi 樹莓派](http://zh.wikipedia.org/wiki/%E6%A0%91%E8%8E%93%E6%B4%BE)
　　這是比較便宜的且公開的軟硬體資源，如果有可能的話，可以直接變成行動轉播平台（人肉ＳＮＧ車），這樣子就是一個硬體具有兩種用途，也不一定要用到高價位的平板電腦。
補充：收入比較高的大都市社會運動，跟落後國家血腥鎮壓的社會運動，網路與硬體使用有非常非常大的區別。
> 或許可以朝開發XMBC的模組方向走，因為其跨平台(Android、 Linux、 BSD、 Mac OS X、iOS、Windows)且Open Source，
> [name=Chen Y]

> 這樣的話主要可以推行樹莓派的整合版本，但若使用者本身無意願購買樹莓派或無法入手的話也可自行使用別的系統當載體。
> [name=Chen Y]

> XMBC在Raspberry Pi上效能極差，完全不堪用。
> [name=Justin L]

> Raspberry Pi作為人肉SNG車比較大的問題可能是效能不足，要順暢轉播解析度需要降到320x240
> [name=Justin L]

> [http://bythegram.ca/2014/01/blog/ustream-raspberry-pi/](http://bythegram.ca/2014/01/blog/ustream-raspberry-pi/)
> [name=Justin L]

> 另一個問題是沒有內建音效卡，收音部分要外接USB音效卡，再接麥克風。
> [name=Justin L]

> [http://mutsuda.com/2012/09/07/raspberry-pi-into-an-audio-spying-device/](http://mutsuda.com/2012/09/07/raspberry-pi-into-an-audio-spying-device/)
> [name=Justin L]




## 近程

以下分幾個作業系統，先討論看看，

### 網樂通

網樂通改機的 reference:
[http://next.fishome.tw/bbs/index.php](http://next.fishome.tw/bbs/index.php)
[https://sites.google.com/site/debiansh4/application](https://sites.google.com/site/debiansh4/application)
[新版網樂通刷機方法(2011.07 以後製造)](http://goo.gl/KtWuFy)

先求能成功改機，包含 source code 開始可以啟動 x server 出現畫面。USB-TTL console 線很好做，我可以提供。黑客松當天做都 ok，但是 USB-TTL 轉板要自己買。 或是誰家附近有賣場在賣轉板，不用等貨運可以代購?  ([http://goods.ruten.com.tw/item/show?21301146721569](http://goods.ruten.com.tw/item/show?21301146721569))
> 我已經買了10顆，單芯線和杜邦和JST接頭都買好了，屆時會帶去。需要的人一顆是 $155 (家有妻小…不好意思不能「大扮」的送)。([http://goods.ruten.com.tw/item/show?21308225323607](http://goods.ruten.com.tw/item/show?21308225323607)) 稍微便宜一點點。
> [name=Hong-Bin T]

> 用 PL-2303 的人，需要自己準備母頭... pin2 (RX) pin3 (TX) pin5 (GND)
> [name=Zhemin L]


徵求：
- 有 linux embedded system 開發經驗 (有 MMP 經驗尤佳)
- 有網樂通可以自行開發
- 有不要的網樂通磚塊可以捐出



### Android 環境

預計要設計APP



## 中程

整合 10-foot GUI 和搖控器，使閱聽人可以透過搖控器來閱聽直送的內容。以這次太陽花為例，希望能讓閱聽人透過電視觀看以下內容

1.  直播(g0v, 蘋果, 機動...etc.)
2.  g0v.today 所連結到的網站
3.  youtube 警察攻擊紀錄片
4.  各社運團體youtube頻道
5.  獨立音樂人youtube頻道
6.  ustream等直播頻道
7.  後續追縱及來自世界各國的相關報導
8.  閱讀網路好文

徵求：
- Qt GUI engineer
- UI art designer
- Content organizer

## 遠程

1.  散布刷機的方法和志工，只要有簡單的工具就可以刷機
2.  建立線上 upgrade fw 機制使更新的韌體不必重刷
3.  釋出 middle ware + framework，使不只網樂通可以改機
> 或許可以以[樹莓派](http://zh.wikipedia.org/wiki/%E6%A0%91%E8%8E%93%E6%B4%BE) 當基礎硬體(便宜、開放源碼)，然後開放設計圖出來給大家自製(安裝系統，紙機殼pdf檔...等等 ) 參考：[XBMC](http://wiki.xbmc.org/index.php?title=Raspberry_Pi)
> [name=Chen Y]

> 希望可以走到能散佈 middleware 的一天 :)
> [name=Hong-Bin T]

> 我有用+賣 Android 環境的電視盒，依我之見 Android 這平台比沒有後續服務的網樂通更具影響力才對
> [name=Michael_Li]

> 或許可以分成兩組人，Michael Li 可以先試著用 Android 做做看? MK802 沒搭搖控器比較可惜...
> [name=Zhemin L]



## 網樂通募集計畫

（請思考一下各方面的工作程序以及募集到了之後改如何處理與活用與擴大利用價值）
### 開發:

- 有 embedded linux 經驗的人想加入開發卻沒有設備，可以從 pool 領取。
- USB-TTL 的 console 線我可以做，但轉板得自己買。 ([http://goods.ruten.com.tw/item/show?21301146721569](http://goods.ruten.com.tw/item/show?21301146721569))
- 開發分為三個階段
    1.  第一個階段是基礎建設，大約兩個人敲定 base system，dev. environment，source control，firmware upgrade，issue tracking 等開發維護工具
    2.  第二階段是 prove of concept，把從 UI 到 channel (youtube, justin, ustream ...etc.) 的操作流程包裝完成，可以送 alpha test。大約再加三個人。
    3.  第三階段是調校，除錯，畫面美化和新功能開發 (middleware 要怎麼做的更 standardized ? 怎麼做成 open platform 讓非 embedded linux 專長的人可以切入？還是不用想太多，就是要做嵌入式的才能玩的動？)。

### 測試

- 沒有 embedded linux 經驗但想加入專案的人，可以從功能測試開始，並回報問題。沒有設備的話可以從 pool 領取
- 功能的定義會是一個問題，從有 POC 之後慢慢會發散再收斂
- 部份終端的測試也可以從幫別人刷機後的問題回報來收集 (beta users)

### 硬體解碼

[https://www.facebook.com/photo.php?fbid=10152403731842915&set=gm.756226067731864&type=1](https://www.facebook.com/photo.php?fbid=10152403731842915&set=gm.756226067731864&type=1)

### 散佈

- 家裡有網樂通磚塊的可以帶來讓訓練過的小蜜蜂刷，家裡沒有的可以從 pool 領。

## 徵求：

- ... 到的了這裡再說~
- 電視 GUI 製作 ( HTML5 solution、Qt ?? )

## 參考資料

1.  網樂通拆解，改裝BT ... : [http://goo.gl/8pNcok](http://goo.gl/8pNcok)
2.  網樂通內裝: [http://goo.gl/SHCE0c](http://goo.gl/SHCE0c)
3.  使用 TTL方式連接: [http://goo.gl/jdL6jz](http://goo.gl/jdL6jz)
4.  新版網樂通刷機方法 (不用 TTL, 2011.7 以後製造的): [http://goo.gl/8mBnCf](http://goo.gl/8mBnCf)
5.  網樂通核心編譯: [http://oranqe.wordpress.com/2013/03/06/nextvod-kernel-compile/](http://oranqe.wordpress.com/2013/03/06/nextvod-kernel-compile/)
6.  **Android**維基百科條目: [http://zh.wikipedia.org/wiki/Android](http://zh.wikipedia.org/wiki/Android)
7.  樹莓派維基百科條目: [http://zh.wikipedia.org/wiki/%E6%A0%91%E8%8E%93%E6%B4%BE](http://zh.wikipedia.org/wiki/%E6%A0%91%E8%8E%93%E6%B4%BE)
8.  樹莓派紙機殼板型: [http://squareitround.co.uk/Resources/Punnet\_net\_Alpha3.pdf](http://squareitround.co.uk/Resources/Punnet_net_Alpha3.pdf)
9.  raspberry-pi-case github project: [https://github.com/AltJ/raspberry-pi-case](https://github.com/AltJ/raspberry-pi-case)
10.  XBMC wiki頁面: [http://zh.wikipedia.org/wiki/XBMC](http://zh.wikipedia.org/wiki/XBMC)
11.  Flv streaming Server: [http://www.red5.org/](http://www.red5.org/)
12.  Opera SourceCode [http://sourcecode.opera.com/](http://sourcecode.opera.com/)
13.  Chrome SourceCode [http://www.chromium.org/](http://www.chromium.org/)
14.  Linux 安裝 browser, 使用 streaming player 播放
15.  How to Play YouTube Videos Directly in VLC Media Player [https://youtu.be/_zpQq0DWVFY](https://youtu.be/_zpQq0DWVFY)
16.  VLCPlayer Source Code [https://www.videolan.org/vlc/download-sources.html](https://www.videolan.org/vlc/download-sources.html)
17.  Youtube TV 網站 [http://www.youtube.com/tv](http://www.youtube.com/tv)
18.  kernel source [https://github.com/suzuke/kernel-pdk7105](https://github.com/suzuke/kernel-pdk7105)
19.  uboot source [https://github.com/dlintw/twpda-uboot](https://github.com/dlintw/twpda-uboot)
20.  QT project on ST7105: [http://qt-project.org/wiki/ST7105](http://qt-project.org/wiki/ST7105) 這好像有硬解的 Frame Buffer
21.  [https://github.com/inLiveTW/server](https://github.com/inLiveTW/server)
22.  [_https://github.com/Urucas/OpenYoutubePlugin_](https://github.com/Urucas/OpenYoutubePlugin)
23.  [https://github.com/dawsonloudon/VideoPlayer](https://github.com/dawsonloudon/VideoPlayer)


### 開發者社群

- 網樂通改機俱樂部 [https://www.facebook.com/groups/477359555618518/](https://www.facebook.com/groups/477359555618518/)
- 網樂通開發/研究/貢獻/準開發者 [https://www.facebook.com/groups/401123299994345/](https://www.facebook.com/groups/401123299994345/)


### Debian for sh4 環境建置

#### ~Linux Container~ ~(sid)~ (此路不通，需要開疆闢土)

Host OS: Ubuntu 14.04, ... (歡迎補充其它可以使用的 Debian/Ubuntu 版本)
1.  安裝 lxc 以及 qemu-user-static
```
sudo apt-get install lxc qemu-user-static:i386 debian-archive-keyring debian-ports-archive-keyring
```
2.  修改 /usr/share/lxc/templates/lxc-debian (workaround)
    1.  將 36 行附近的變數改成 MIRROR=${MIRROR:-[http://ftp.debian-ports.org/debian/](http://ftp.debian-ports.org/debian/)}
    2.  將 190 行附近的 debootstrap --verbose 改成 qemu-debootstrap --verbose --keyring=/usr/share/keyrings/debian-ports-archive-keyring.gpg
    3.  將 163 行附近的 download_debian() 裡面的 packages=debian-archive-keyring,debian-ports-archive-keyring # 減少安裝的軟體套件，因為 sh4 可能會有許多軟體套件缺少的問題。
> 如果 E: Couldn't download packages: xxx 多試幾次即可.  進去後沒有 gcc , 還沒找到該裝哪個套件...
> [name=Zhemin L]

> 我覺得 E: Couldn't download packages: xxx 的問題是 ISP 網路或是所使用的網路設備品質不好的關係，我自己在家用社區寬頻 (後面接 Hinet) 常常會遇到，但是換成台灣大哥大的 3G 行動網路就好了，跟我所說的軟體套件缺少的問題不一樣，我說的問題是真的就沒有那些軟體套件，目前覺得可以用下面提到的 pbuilder 將缺少的套件補齊。>_<
> [name=FourDollars]

3.  產生 Linux Container
```
sudo lxc-create -t debian -n sid -- -a sh4 -r sid -c 2>&1 | tee sh4-debug.log
```
4.  啟動 Linux Container
```
sudo lxc-start -n sid -d
```
5.  登入 Linux Container
```
sudo lxc-console -n sid
```
補充資訊：
- 前 sh4 裡面無法使用網路，正在設法解決這個問題。問題的根源可能是因為 [https://packages.debian.org/search?keywords=iproute2&searchon=names&suite=all&section=all](https://packages.debian.org/search?keywords=iproute2&searchon=names&suite=all&section=all) 這個套件沒有在 sh4 裡面。(沒什麼人在用的 CPU 果然支援很差... Orz)
- 在正常情況底下，依照以上提到的步驟應該是可以成功地建立出 sh4 的 Linux Container，除非遇到了 DNS 解析的問題，\`while :; do nslookup ftp.debian-ports.org | grep "No answer"; done\` 這個指令可以用來檢查當下使用的網路是否有 DNS 解析的問題發生，如果沒有問題的話，應該是不會產生任何輸出，停止指令請用 Ctrl-C 停止。
    遇到這個問題有一個 workaround 的方法，就是修改 /usr/share/debootstrap/functions 裡面的 wgetprogress() 在 wget 後面加上 --tries=10 重覆試十次，下面的 pbuilder 也可以使用。
- 啟動之後的 rootfs 會存在 /var/lib/lxc/sid/rootfs/ 底下
- 已確認 Linux Container (Debian/sh4) 裡面編譯出來的 Hello World 程式可以直接放到網樂通上面執行

> 目前 Ubuntu 14.04 上面的 qemu-user-static 不支援網樂通所使用的 SH7724
> [name=FourDollars]

> `/usr/bin/qemu-sh4-static -cpu help` 只出現 SH7750R, SH7751R, SH7785 不過編譯出來的套件應該是通用的 (需要驗證一下)
> [name=FourDollars]

> qemu-user-static 我是直接從source code rebuild就可以用了
> [name=Chia-Cheng H]

> 我已經成功在 Ubuntu 14.04 i386 的環境底下建立 Debian sid sh4 的 Linux Container 並且登入使用，qemu-user-static 不用特別處理。
> [name=FourDollars]

> 其實在 Ubuntu 14.04 amd64 上面也可以成功建立起 Debian sid sh4 的 Linux Container 只要安裝 qemu-user-static:i386 就可以了，感謝 Debian 提供 multiarch 支援。 <(_ _)>
> [name=FourDollars]

#### Linux Container (wheezy)

Host OS: Ubuntu 14.04, ... (歡迎補充其它可以使用的 Debian/Ubuntu 版本)
1.  安裝 lxc 以及 qemu-user-static
```
sudo apt-get install lxc qemu-user-static:i386 debian-archive-keyring debian-ports-archive-keyring
```
> 改用 Debian Wheezy 來當 host. 需要加裝
> [name=Zhemin L]

> sudo apt-get install debootstrap
> [name=Zhemin L]

> sudo apt-get install cgroupfs-mount cgroup-bin cgroup-tools
> [name=Zhemin L]

2.  修改 /usr/share/lxc/templates/lxc-debian (workaround)
    1.  將 36 行附近的變數改成 MIRROR=${MIRROR:-[http://download.si-linux.co.jp/debian-sh/wheezy-sh4/](http://download.si-linux.co.jp/debian-sh/wheezy-sh4/)}
    2.  將 190 行附近的 \`debootstrap --verbose\` 改成 \`qemu-debootstrap --verbose --no-check-gpg\`
    3.  將 163 行附近的 download_debian() 裡面的 packages 變數中的 dialog 那行移除掉 # 因為目前 si-linux 沒有提供 dialog 這個套件
3.  產生 Linux Container
```
sudo lxc-create -t debian -n wheezy -- -a sh4 -r wheezy -c 2>&1 | tee sh4-debug.log
```
4.  啟動 Linux Container
```
sudo lxc-start -n wheezy
```
5.  修改 /etc/apt/sources.list
```
deb http://download.si-linux.co.jp/debian-sh/wheezy-sh4/ wheezy main contrib non-free
deb-src http://free.nchc.org.tw/debian/ wheezy main contrib non-free
deb http://people.linux.org.tw/~fourdollars/debian/ wheezy main contrib non-free
deb-src http://people.linux.org.tw/~fourdollars/debian/ wheezy main contrib non-free
```
> 沒有編輯器，所以請用...
> [name=Zhemin L]

> cat << END > /etc/apt/sources.list
> [name=Zhemin L]

> 把上面四行剪貼進來
> [name=Zhemin L]

> END
> [name=Zhemin L]

6.  設定 Linux Container 的網路
```
ifconfig eth0 10.0.3.2  指定 Static IP
route add default gw 10.0.3.1  設定 Gateway
echo "nameserver 8.8.8.8" > /etc/resolv.conf  設定 DNS
```
> 使用 Debian 的話:
> [name=Zhemin L]

> sudo apt-get install bridge-utils
> [name=Zhemin L]

> sudo brctl addbr lxcbr0
> [name=Zhemin L]

> sudo ifconfig br0 192.168.1.1
> [name=Zhemin L]

> sudo vim /var/lib/lxc/wheezy/config 設定 lxc.network.type=veth 以及 lxc.network.link=lxcbr0
> [name=Zhemin L]

> 做一下 IP Masquerading (假設你有用 ufw, 沒有可以跳過)
> [name=Zhemin L]

> sudo ufw allow in on lxcbr0
> [name=Zhemin L]

> sudo ufw allow out on lxcbr0
> [name=Zhemin L]

> sudo iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o wlan0 -j MASQUERADE
> [name=Zhemin L]

> 然後別忘了修改 /etc/sysctl.conf 把 net.ipv4.ip_forward = 1 然後 sysctl -p
> [name=Zhemin L]

> 進入 lxc 後，一開始 DHCP 會抓不到，沒關係，等它 timeout
> [name=Zhemin L]

> 在 lxc> ifconfig eth0 192.168.1.3
> [name=Zhemin L]

> 在 lxc> route add default gw 192.168.1.1
> [name=Zhemin L]

7.  更新 apt index
```
apt-get update
```
8.  關掉 gpg signature checks
```
echo 'APT::Get::AllowUnauthenticated "true";' > /etc/apt/apt.conf  因為 si-linux 沒有 sign deb 所以乾脆關掉
```
9.  接下來就是跟使用一般的 Debian 系統一樣了。 Have fun. :D
> 沒有  vim 太痛苦了，速速 apt-get install vim (誤)
> [name=Zhemin L]


#### ~p~~builder~ ~(sid)~ (此路不通，需要開疆闢土)

Host OS: Ubuntu 14.04, ... (歡迎補充其它可以使用的 Debian/Ubuntu 版本)
1.  安裝 ubuntu-dev-tools 以及 qemu-user-static
```
sudo apt-get install ubuntu-dev-tools qemu-user-static:i386 debian-archive-keyring debian-ports-archive-keyring
```
2.  執行 pbuilder-dist 創建一個新的 chroot.
```
PBUILDER\_DIST\_DEBIAN_MIRROR=http://ftp.debian-ports.org/debian pbuilder-dist unstable sh4 create --debootstrapopts --keyring=/usr/share/keyrings/debian-ports-archive-keyring.gpg
```
> 建議使用 --keyring=/usr/share/keyrings/debian-ports-archive-keyring.gpg 來檢查套件的合法性來取代使用 --no-check-gpg
> [name=FourDollars]

> 14.04 不用 sudo. 但，我仍然  E: qemu-debootstrap failed
> [name=Zhemin L]

> 我也遇到了這個問題，我看了一下發現跟上面 lxc 遇到的問題一樣，因為有缺一些必要的套件，或是即使有套件，但是套件本身的版號還是不夠新。
> [name=FourDollars]

> awk libbz2-1.0 libc6 libdb5.1 libdebconfclient0 libgcc1 liblzma5 libselinux1 libtinfo5 multiarch-support systemd-sysv tar upstart zlib1g
> [name=FourDollars]


#### Debian 移植資訊

Debian Ports [http://www.debian-ports.org/](http://www.debian-ports.org/)
    - SH4 - Debian Wiki [http://wiki.debian.org/SH4](http://wiki.debian.org/SH4)
    - Debian Mailing Lists -- Index for debian-superh [http://lists.debian.org/debian-superh/](http://lists.debian.org/debian-superh/)
    - SHPort - Debian Wiki [http://wiki.debian.org/SHPort](http://wiki.debian.org/SHPort)
    - Crosstoolchian  [https://wiki.debian.org/SH4/CrossToolchain](https://wiki.debian.org/SH4/CrossToolchain)

### 給新手的 Cross-Compilation Tool-Chain

- 如果還沒刷好 image: [http://www.twpda.com/2013/09/sh4twbox-07.html](http://www.twpda.com/2013/09/sh4twbox-07.html)  (我刷的是 sh4twbox-0.9.2.txz 剩下的來 cross-compile ?)
- 這篇文把我想寫的都寫完了: [http://jackden-diary.blogspot.tw/2013/05/install-stlinux-23-on-ubuntu-1204-32bit.html](http://jackden-diary.blogspot.tw/2013/05/install-stlinux-23-on-ubuntu-1204-32bit.html)
- 看安裝後的事項就好: [http://goo.gl/DrR7B6](http://goo.gl/DrR7B6)
- 網路規劃:
    - \[Host\] 192.168.100.1 (eth0)
    - \[VM\] VirtualBox 裡的 12.04 LTS 32-bit 192.168.100.2 (橋接介面卡)
- \[host\] apt-get  install nfs-server tftpd-hpa
- \[host\] /etc/exportfs 改成 /srv/nfs *(rw,no\_subtree\_check,sync,all_squash,anonuid=0,anongid=0)
    - anon = 0 是為了  uboot mount NFS時有些檔案需要  要 uid=0
- \[host\] mkdir -p /srv/nfs ; chown nobody:nogroup /srv/nfs
- \[VM\] mount -t vboxsf srv /srv 這樣比較方便
> 這樣很容易因為權限問題 protocol error, 還是乖乖用 NFS 吧.
> [name=Zhemin L]

- 改一下 /etc/default/tftpd-hpa 設一下 static IP (可以用預設)
- /srv/tftp 裡放 kernel source
    - \[host\] 從這邊下載: [http://www.ptt.cc/bbs/Linux/M.1374821355.A.95F.html](http://www.ptt.cc/bbs/Linux/M.1374821355.A.95F.html)
    - \[VM\] PATH 加上 /opt/STM/STLinux-2.3/host/bin
    - \[VM\] compile好後，執行 ./autoDone.sh 把 vmlinux.ub 複製到 /srv/tftp
    - VM 基本上就是個 server, 我都是從 host ssh 進 VM 做 cross-compile
- 重開網樂通，進 uboot (多按幾次 \[enter\])
    - print - 顯示目前設定
```
setenv ipaddr 192.168.100.5
setenv serverip 192.168.100.1
tftp 80000000 vmlinux.ub
setenv ip ip=192.168.100.5:192.168.100.1:192.168.100.1:255.255.255.0:sh4:eth0:off
setenv cm coprocessor_mem=4m@0x40000000,4m@0x40400000
setenv nwhwconf nwhwconf=device:eth0,hwaddr:24:cf:21:b2:a4:76
setenv console console=ttyAS0,115200
setenv nfsroot nfsroot=192.168.100.1:/srv/nfs/root
setenv bootargs ${console} ${nfsroot} root=/dev/nfs rw ${ip} mem=256M ${cm} ${nwhwconf}
bootm 0x80000000
```
- 開機 log: [https://gist.github.com/miaoski/11344418](https://gist.github.com/miaoski/11344418)
- 舊的 bootargs=console=ttyAS0,115200 rootdelay=0 root=/dev/sda2 rootfstype=ext4 rw rootflags=data=journal nwhwconf=device:eth0,hwaddr:10:08:E2:12:06:BD phyaddr:0,watchdog:5000 mem=256M bigphysarea=2048 bootcmd=usbcfg 0; usb start; usb info; usb part; fatload usb 0:1 80000000 vmlinux.ub; bootm 80000000
- 網卡最好接 Hub 不然 reset link 的時候 IP 可能會掉.
- 別忘了 [Chia-Cheng Huang](https://g0v.hackpad.tw/ep/profile/ADv4ZTWzjah) 的 debian repo 已經改到
    deb [http://forum.cse.yzu.edu.tw/Linux/debian-sh4/](http://forum.cse.yzu.edu.tw/Linux/debian-sh4/) wheezy all

### Co-Processor 的問題

```
st-coprocessor-0: No RAM reserved
st231.0 Coprocessor -------------------------------------------
not configured!
```
參考 陳天靖 & [Chia-Cheng Huang](https://g0v.hackpad.tw/ep/profile/ADv4ZTWzjah):
bootargs 最後面加上 coprocessor_mem=4m@0x10000000,4m@0x10400000
變成這樣:
```
st231.0 Coprocessor -------------------------------------------
    flags 0001 RAM start at 0xc1080000  size      0x00400000
                  cop. addr 0x10000000
    Channels : Not defined
    IRQ      : not used
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-
st-coprocessor-1: No RAM reserved
st231.1 Coprocessor -------------------------------------------
    not configured!
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-
```
- [http://www.stlinux.com/howto/multiple-CPUs/STb7100-ST231](http://www.stlinux.com/howto/multiple-CPUs/STb7100-ST231)
    - 把 ST40 boot 起來後，再 boot 兩顆 ST231.
    - 需要使用 stslave 開啟程式，才會放到 ST231 上執行.
    - Kernel: Device Drivers" / "STM specific devices" 下請選 firmware coprocessor support
- 如果 kernel cmdline 長度不夠，會被切掉的話:
    - 修改 linux/include/include/asm-generic/setup.h 裡的 COMMAND\_LINE\_SIZE 加大到 1024
- 有兩個 .elf 檔要去 TDT 抓下來放進 kernel 中... 但我還不知道怎麼做。

### Cross-Compile 一個 Hello World

- 隨便寫
```
#include <stdio.h>
int main() {
    puts("Hello World.");
    return 0;
}
```
- \[VM\] sh4-linux-gcc hello.c
- \[VM\] cp a.out /srv/nfs/root/usr/local/bin/hello
- 開進網樂通. /usr/local/bin/hello

### 派樂靈丹版的 firmware 怎麼 load

- cp ./STM/STLinux-2.3/devkit/sh4/target/lib/firmware/component\_7105\_pdk7105.fw /srv/twbox092/lib/firmware/component.fw
- cp ./STM/STLinux-2.3/devkit/sh4/target/lib/firmware/fdvo0_7105.fw /srv/twbox092/lib/firmware/fdvo0.fw
- 可是 stm312 還是沒有記憶體... 再想想辦法 :(

### XBMC

網樂通裡面安裝XBMC ([http://xbmc.org/](http://xbmc.org/)), 是最快的解決方案, 雖然說他的UI並不是很好用. 但現成的plugin很多.
且已經有人實驗成功. [https://www.facebook.com/huang.j.zheng.1](https://www.facebook.com/huang.j.zheng.1)
ustream for XBMC [https://github.com/divingmule/plugin.video.ustream](https://github.com/divingmule/plugin.video.ustream)

我也認為目前最快的方案應該就是用XBMC，plugin也不難寫(python)，我自己實做plugin來播CPBLTV也沒問題。
或許直接採用duckbox project來改XBMC的介面或許會比自己實做Qt Browser來的快一些?
PS. 不過目前XBMC版本是由Hans Yu發佈，似乎是沒有他目前版本的souce code (他有做了很多修正)
我手邊只有堪用的duckbox for pdk7105 版本 [https://github.com/suzuke/pdk7105-tdt.git](https://github.com/suzuke/pdk7105-tdt.git)
但是這個版本網路串流buffer部份是有問題的。

## 延伸閱讀

- [LiveTW／社會上事件現場，網路實況轉播列表工具／Chrome外掛／ ](https://chrome.google.com/webstore/detail/livetw/fhcffinobmpdchcoapdeoinhdmlihiok)
- [直播連結收集器（導播台）](https://g0v.hackpad.tw/VVlHNqKaQrC)
- [第五權電視牆監看「評」台g8v.tv草稿](https://g0v.hackpad.tw/g8v.tv-lk9pamtKwyr)
- [在會場中建立可靠的訊息傳遞網路](https://g0v.hackpad.tw/App-d6rh3bXemcK)
- [學運現場無網路的通訊解決APP方案](https://g0v.hackpad.tw/APP-h4wPgytCjac)
- [反黑箱服貿暨佔領立法院活動專題網（含贊成意見）](http://hack.g0v.tw/CSSTACO)　（[作業標準書](https://sites.google.com/site/CSSTACO)）

## 進度

1.  單芯線和轉板買好接好，可以看到 console 但是 tty 被擋起來了
2.  toolchain 可以用 crosstool-ng 來編，也可以直接抓 stlinux 2.3，但是 **Host  必須是 32 bit OS**
3.  要來 hackth8n玩耍的人請先裝好 32bit OS ... 現場裝可能就要花掉 2 小時以上了...
4.  **Android版電視盒可以先不用帶去了吧？我看大概只會先專心搞網樂通**
> 如果方便的話，可以帶著做 design reference 。同時瞭解一下各種方案的 pros/cons 。我提的網樂通的好處，加上開發的難度，以整體方案的目標來說，不見得比 android tv 好，也有種可能性是整個把 android tv 重刷成 closed system，然後找企業捐贈，用送的方式給出去。黑客松可能光是討論這個就可以去掉大半天了 @ 3@... 像網樂通雖然號稱發出去50萬個，但是現在還有多少個是活著的呢？這個問題也會讓這個 project 變成 hacking game 居多，可能還要問，除了網樂通還有什麼磚塊嗎？還有除了刷磚塊以外，如果目標是消除電視/網路的資訊落差，並且無償的贈給閱聽人，還有什麼可行的方法呢？我只是想拋「磚」引玉呀啊啊啊~~~
> [name=Hong-Bin T]

> 我要問個一個關鍵的問題，明天用網樂通，你們有準備如何接銀幕呢？本來我想帶螢幕過去，很辛苦就是，但是用得上也值得，但是場地中午前知道電力並不足，怕用不上之。（我的電視盒也是輸出AV,HDMI）
> [name=Michael_Li]

> 假設有直播組員先在用的視訊盒（AverMedia C875），也許只要用筆電就好，少帶大東西過去，最怕電力不夠讓接銀幕。
> [name=Michael_Li]

> to be honest, 根本是從零開始呀，應該根本用不到螢幕。
> [name=Hong-Bin T]

5.明天場地電力有限，需Ｂ計畫，各位現在有空到處問問有沒有視訊盒可以借到～～
> 搬螢幕去沒辦法用的話，太苦了～～
> [name=Michael_Li]

> 我現在先幫忙在 g1v 頻道問看看～一直再忙明天的要用的資料，今夜時間很少能幫助各位
> [name=Michael_Li]

> 管理場地的人回答嚕：
> [name=Michael_Li]

> [gavin-^^](https://www.irccloud.com/#%21/ircs://irc.freenode.net:6697/gavin-%5E%5E)\> 現場為了安全.除了投影和主網路設備.都可能要注意使用電流量.
> [name=Michael_Li]

> [gavin-^^](https://www.irccloud.com/#%21/ircs://irc.freenode.net:6697/gavin-%5E%5E)\> 建議找看你有沒有nb+webcam的方案.
> [name=Michael_Li]

> ／明天我不帶螢幕了／END~~本人不在了，準備資料去／
> [name=Michael_Li]


### 重新刷成 Debian Wheezy

1.  用派樂靈丹提供的方法刷好 u-boot ... [http://www.twpda.com/2013/09/sh4twbox-07.html](http://www.twpda.com/2013/09/sh4twbox-07.html) (~哇…變真的磚塊了 ...~ ) 備份原來 USB DOM 的 image，刷 Debian wheezy。開機速度真的慢 ...
2.  可以用自編的 rootfs 刷機了(一樣延用 twpda 的刷機 script) 下一步是用 nfsroot 開機來加速開發。(每次更新都要重刷是很痛苦的)
3.  nfsboot 成功，對開發來說輕鬆多了，晚一點再把細節寫成文件(細節在下面，請參考)
4.  ~目標更新成 Debian Jessie ~
5.  suzuke 的 github: [https://github.com/suzuke/kernel-pdk7105](https://github.com/suzuke/kernel-pdk7105)

> 開機速度慢的原因似乎是rc.local裡面用來校時的指令, 因為原本設定的time server掛了, 所以卡在那的樣子...(不過比起原本網樂通debian的開機的確是慢了點, 也許可以考慮一樣用busybox來客製化系統)
> [name=Chia-Cheng H]


apt-get update error message:
```
root@wheezy:/etc/apt apt-get update
Get:1 http://forum.cse.yzu.edu.tw wheezy-sh4/ Release.gpg [998 B]
Ign http://download.si-linux.co.jp wheezy Release.gpg
Get:2 http://forum.cse.yzu.edu.tw wheezy-sh4/ Release [998 B]
Hit http://download.si-linux.co.jp wheezy Release
Ign http://forum.cse.yzu.edu.tw wheezy-sh4/ Release
E: GPG error: http://forum.cse.yzu.edu.tw wheezy-sh4/ Release: The following signatures were invalid: NODATA 1 NODATA 2
```
[http://forum.cse.yzu.edu.tw/dists/](http://forum.cse.yzu.edu.tw/dists/) 404 error, probably removed.

> 這部分應該是apt-get 的位置後來有做變更, 但是刷機檔裡預設並沒有做更新
> [name=Chia-Cheng H]

> 目前主要的apt repositry 是由徐皓在維護([http://forum.cse.yzu.edu.tw/Linux/debian-sh4/download.php](http://forum.cse.yzu.edu.tw/Linux/debian-sh4/download.php))
> [name=Chia-Cheng H]


### 能不能直接hack原始的網樂通? → 不行

1.  原有程式的編譯環境: .GCC: (GNU) 4.2.4 (snapshot) (STMicroelectronics/Linux Base 4.2.4-64)
2.  把原始的資料 dump 好了(感謝 fourdollars & conrad) 壓起來 5GB
3.  mount:
```
!/bin/bash
mount -o loop,offset=$((19512)) twsh4box /mnt/1
mount -o loop,offset=$((617120512)) twsh4box /mnt/2
mount -o loop,offset=$((1234240512)) twsh4box /mnt/3
mount -o loop,offset=$((13819840512)) twsh4box /mnt/4
```
4.  partition 4 是放遊戲的地方，opkg 格式，放在  etc/opkg/opkg.conf
```
src game http://63.221.157.110/opk/repo ←  這個網址連不到了, 在 PCCW (香港)
```
5.  root partition 有 84MB 把 target.tgz 解開到 RAMDISK (?)
6.  邪惡的網樂通 allow remote login
```
\ start the telnet daemon to allow remote login
/usr/sbin/telnetd -l /bin/sh
source /root/run_a18.sh
```
7.  directfb 的 driver 在 usr/pub/lib/directfb-1.0-0/ , fb kernel module 在 root/modules/*
```
ljm@ljm-Aspire-S3-391:~/sh4/mnt\_system$ modinfo ./root/modules/stgfb\_core.ko
filename:       /home/ljm/sh4/mnt\_system/./root/modules/stgfb\_core.ko
license:        ST Microelectronics.
author:         STMicroelectronics Ltd.
description:    STAPI based frame buffer
depends:
vermagic:       2.6.23.17\_stm23\_A18B-PDK7105-32BITS-A18B preempt mod_unload SH4LE
```
8.  有 python, gtk-2.0
9.  cpuinfo :
```
root@wheezy:~ cat /proc/cpuinfo
machine         : pdk7105
processor       : 0
cpu family      : sh4
cpu variant     : st40-300
cpu type        : STx7105
cut             : 3.x
cpu flags       : fpu icbi synco fpchg
cache type      : split (harvard)
icache size     : 32KiB (2-way)
dcache size     : 32KiB (2-way)
address sizes   : 32 bits physical
bogomips        : 448.51
```
10.  遙控器使用標準的 lircd



```
0xd7                                                            0x01                    #power key
0xff                                                            0xff                    #Unknown key
0xff01                                                  0x01                    #power\\\\
0xff80                                                  0x10                    #board-CH+
0xff40                                                  0x11                    #board-CH-
0xff10                                                  0x12                    #board-VOL-
0xff20                                                  0x13                    #board-VOL+
0xff04                                                  0x14                    #board-OK
0xff08                                                  0x03                    #board-exit
0xff02                                                  0xF541                  #board-MENU
```
12.  開機流程 (尚未確定):
    1.  用 partition 1 boot 起來後，把 target.tgz 解到 ramdisk
    2.  busybox 叫起 /etc/init.d/rcSBB
    3.  叫起邪惡的 telnetd
    4.  remount / rw 之後 /root/run_a18.sh
    5.  /root/modules/load_modules.sh, frame buffer 驅動程式和 coprocessor 和 STM API 都在這裡
    6.  啟動 lircd (搖控器)
    7.  /root/bin/SCS_Server**.exe** (一個 libglade 的應用程式?) ← 為什麼會是 .exe QQ
    8.  在 /tmp/SCS\_fifo\_cmd 和 /tmp/SCS\_fifo\_ret 開兩個 FIFO
    9.  應用程式使用 libgtk-directfb-2.0.so
13.  會去連的網址:
    1.  [http://iptv-100-87.fulldynamic.com:38080/service/](http://iptv-100-87.fulldynamic.com:38080/service/)
    2.  [http://iptv-100-87.fulldynamic.com:18180/report/](http://iptv-100-87.fulldynamic.com:18180/report/)
    3.  [http://fdupdate1.iptv.fulldynamic.com/Group/getGroup.action?MACAddress=](http://fdupdate1.iptv.fulldynamic.com/Group/getGroup.action?MACAddress=)
    4.  [http://update.nexttv.com.tw/Group/getGroup.action?MACAddress=](http://update.nexttv.com.tw/Group/getGroup.action?MACAddress=)
    5.  [http://63.221.156.55/Group/getGroup.action?MACAddress=](http://63.221.156.55/Group/getGroup.action?MACAddress=)
    6.  [http://192.168.1.254/Group/getGroup.action?MACAddress=](http://192.168.1.254/Group/getGroup.action?MACAddress=)
14.  嗯，好像沒辦法直接改網址...

## 前端 GUI 畫面

[https://github.com/psdmac/SunFlowerTv](https://github.com/psdmac/SunFlowerTv)
靜態頁面：[http://psdmac.github.io/SunFlowerTv](http://psdmac.github.io/SunFlowerTv)

> 純提供參考文章 [http://wwssllabcd.github.io/blog/2013/01/31/how-to-setup-raspberry-pi/](http://wwssllabcd.github.io/blog/2013/01/31/how-to-setup-raspberry-pi/)
> [name=Jack S]

> [替raspberry pi安裝作業系統](http://www.takobear.tw/12/post/2013/06/raspberry-pi-raspbian.html)
> [name=Jack S]

> 其實把派當server看把安卓當客戶訊息感知 這樣2者運行不一樣的重點 因為派的可變性能比安卓大多了
> [name=Jack S]

> 另一款 相容性比派高的硬體 [http://www.openfoundry.org/tw/resourcecatalog/Embedded/Development-Tools/beaglebone](http://www.openfoundry.org/tw/resourcecatalog/Embedded/Development-Tools/beaglebone)
> [name=Jack S]

大部份有都po在 [g8v.tv](https://g0v.hackpad.tw/lk9pamtKwyr)  **第五權電視牆監看「評」台g8v.tv草稿**
> 重覆的地方刪除了，請參考上一行 g8v.tv 的部份。
> [name=Zhemin L]

> 誠心建議此頁只討論關於資訊接受端的產品，關於資訊產出端應該由其他專案來負責。否此此專案會無限膨脹。之前有 [公民即時網路轉播](https://g0v.hackpad.tw/XB5JOWTtnly) ，如果新增關於無人轉播載具，應該會是個很有趣的題目。
> [name=Lucian C]

##

## FAQ

Q: 什麼是太陽花盒子？
A: 太陽花盒子目標是社會運動專屬的機上盒，或稱多媒體播放器，類似產品有中華電信的 [MOD](https://zh.wikipedia.org/zh-tw/%E4%B8%AD%E8%8F%AF%E9%9B%BB%E4%BF%A1MOD)。我們發現，握鍵盤和拿搖控器的人看到的、聽到的、想到的、理解的，已經變成兩個[平行宇宙](http://zh.wikipedia.org/zh-tw/%E5%B9%B3%E8%A1%8C%E5%AE%87%E5%AE%99)，這是典型的[數位落差](http://zh.wikipedia.org/wiki/%E6%95%B8%E4%BD%8D%E8%90%BD%E5%B7%AE)，太陽花盒子的首要任務，就是透過最直接的影音畫面來消除落差。

Q; 為什麼要推太陽花盒子？
A: 有鑑於在台灣在這個時刻，不論有線無線的新聞都無法讓人信任，我們決定自己做機上盒，推送第一手的紀錄畫面，包括各種直播、公聽會、質詢紀錄等等到電視上。我們要創造專屬於公民的電視新聞媒體平台。

Q: 目標閱聽群眾是誰？
A: 從 318 學運發現，透過網路號召，動員的人力都是年輕族群。而透過電視了解這個運動，還會表達支持的中老年人，大多對社運並不陌生。支持社運、學運的人，除了要自己打貪反腐，了解法律、哲學、經濟等議題外，還得面對，以電視為主要資訊來源的家人，因為資訊落差所造成的觀念歧異，每每嘗試以和平開場的溝通，多以充滿失望、爭執、隔離結束所帶來的壓力。我們的目標閱聽群眾就是這些願意溝通、思考、理解政治、社會，但不太熟悉使用網路查找資料的中老年人。

Q: 什麼是網樂通？
A: 幾年前[壹傳媒免費奉送的機上盒](http://zh.wikipedia.org/wiki/%E7%B6%B2%E6%A8%82%E9%80%9A)，本來做為壹電視的傳播管道，後來被 NCC 轟下架。本來社會輿論認為黎先生很紅，被 NCC 下架時還額手稱慶，這兩年發現最紅的會變紫，然後變藍…
> 如果有原網樂通員工，或任何壹傳媒的員工，或有人認識壹傳媒的員工，希望能幫忙牽線，我們的計畫是讓所有的網樂通還魂。330 上街的 50 萬人，都是潛在的收視戶! 
> [name=Hong-Bin T]


Q: 為什麼選擇網樂通？
A: 為了降低數位落差，降低終端用戶，尤其是中老年人，的進入門檻是最重要的。網樂通有以下好處：免費、已經沒用、數量很大、已經成功放進用戶家裡。另外，這種機上盒如果收費，會被貼上營利的標籤，將招來不必要的質疑。

Q: 別的機上盒不行嗎？
A: 可以，只要閱聽人知道去哪裡找到這些資料。太陽花盒子的目的是幫你撈出這些運動的紀錄，第一手直播、第二手剪接、第三手紀錄片、還有事後的訪談、歌手 MV…等等等，與運動無關影音資料不會限制，但使用者須自己想辦法。
> 歌手MV?
> [name=Zhemin L]

> 印象中農陣、非核家園都有小型的樂團在背後。還有像主題曲一樣的島嶼天光，應該也有人想看，重點是紀錄片還沒出來，就有很多人用島嶼天光來 tag 像紀錄片一樣的影音片段。
> [name=Hong-Bin T]


Q: 網樂通再多，終究停產啦~
A: 所以我們需要募集你不用的網樂通 ... 就算停產，先前壹傳媒發出的數量也夠大了。

Q: 我有網樂通，要怎麼變身成太陽花盒子？
A: (…啊  ) 我們正在努力中。開發的進度也會不定期發佈在這個共筆裡。

Q: 我是工程師，想要幫忙，該怎麼做？
A: 請在這裡留言，跟我連絡!!
> 留言範本：我是 hbtsai 韌體工程師 / UI 設計師 / Qt 工程師 / *工程師，我想幫忙~ 
> [name=Hong-Bin T]

> Hi, 我做過 wifi-router/STB/寫過web/也會lamp，現在在做 switch ，我想幫忙
> [name=Yo S]

> hi Seikon, 請問你自己有網樂通, USB2TTL 嗎? 我們目前的進度還在 poc 較多，先熟練板子的特性。第一個目標是 Qt Embedded web browser, default 可以開啟 youtube 的某個 channel. 
> [name=Hong-Bin T]

> 收到，我晚點再回報我這邊的進度好了。在網樂通上裝好 wheezy 了，然後也在 ubuntu 13.04 上搞定 cross-toolchain, 可以寫出有效的 hellow world.
> [name=Yo S]


Q: 我不是工程師，但想幫忙，該怎麼做？
A: 請先找出自己家裡的網樂通、它的電源、搖控器，也請你的朋友找出他們不用的網樂通和配件，保護好它們，不要被回收，不要泡水，不要曬太陽。等我們釋出 firmware 的時候，它們就可以搖身一變成為太陽花盒子。


## 雜記

16:49:38 <[miaoski](https://www.irccloud.com/#%21/ircs://irc.freenode.net:6697/miaoski)\> 那個... 昨天的 kkyo 是不是今天的 kkkyo ?
16:50:04 <[miaoski](https://www.irccloud.com/#%21/ircs://irc.freenode.net:6697/miaoski)\> 目前太陽花盒子是停了沒錯，不過現在要接起來的話，有些利基喲!
16:50:23 <[miaoski](https://www.irccloud.com/#%21/ircs://irc.freenode.net:6697/miaoski)\> ustream 開放 HTML5 了，所以不再需要搞定 flash player, 而且 ustream 開始有 API 了
16:50:40 <[miaoski](https://www.irccloud.com/#%21/ircs://irc.freenode.net:6697/miaoski)\> 但壞消息是現在 ustream 同時觀看人數有限制了... XD
16:52:25  → [iMac](https://www.irccloud.com/#%21/ircs://irc.freenode.net:6697/iMac) joined  ↔ [likefool](https://www.irccloud.com/#%21/ircs://irc.freenode.net:6697/likefool) popped in
==16:55:06 <====[CindyLinz](https://www.irccloud.com/#%21/ircs://irc.freenode.net:6697/CindyLinz)====\> miaoski: 以前也是有限制啊.. 只是沒有明寫出來, 而且超過限制的時候是每一個人都不准看.... XD==
16:56:39 <[miaoski](https://www.irccloud.com/#%21/ircs://irc.freenode.net:6697/miaoski)\> CindyLinz: sokka...
16:57:01 <[miaoski](https://www.irccloud.com/#%21/ircs://irc.freenode.net:6697/miaoski)\> 然後我的 Chromecast 版目前看來是可以(很容易地)改寫了，但宇庭那邊的 feed 停了 QQ
16:57:26 <[miaoski](https://www.irccloud.com/#%21/ircs://irc.freenode.net:6697/miaoski)\> (Chromecast 版需要依賴宇庭的 inLiveTW)
16:58:17 <[miaoski](https://www.irccloud.com/#%21/ircs://irc.freenode.net:6697/miaoski)\> 網樂通版依然沒什麼辦法... hbtsai 最近把腦筋動到 Android 電視棒上面。有些細節要處理，但看起來還可以做。
17:06:29 <[a0000778](https://www.irccloud.com/#%21/ircs://irc.freenode.net:6697/a0000778)\> 網址上加參數 html5=true 就會有

> 我沒有停，只是坑太多哩QQ 現在直播組多半使用Livestream，準備要來串Livestream API
> [name=劉宇庭]



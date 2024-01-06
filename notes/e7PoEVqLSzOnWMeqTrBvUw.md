---
title: "CoCall 一起播"
tags: hackpad
---

# CoCall 一起播

> [點此觀看原始內容](https://g0v.hackpad.tw/poC9Ox6QDfB)


拋磚人：＠ymow
-  專案簡介：打電話進去警廣報路況太麻煩了，不如變成 Voice Tweeter
- 專案三個字：  NewsSpot  TrafficReport  MusicPlayer
-  討論：
    1.  Voice Twitter 其實市場上有不少成功案例，因此我覺得這個是有機會幫助市民更方便的生活與互助，有機會的話希望能變成 VoicePTT
    2.  waze正在被google以13億收購，台灣似乎沒有相似應用
    3.  昨天發昨天發現可以藉由Voice on Map量化各種新聞議題的擴散程度，適當搭配語音應用橋接各組專案，或是拓展Radio方面的議題傳播，使各組多一個堪用的傳播媒介
    4.  音樂方面除了市面上音樂應用串接，並在解決版權問題的前提下考慮套用NowIn成功的素人DJ模式
    5.  廣告是個插播套件，也就是可以讓使用者自由選擇有無電台廣告
    6.  音樂也是插播套件，可自由選擇插入音樂類型或是單曲或是ＤＪ
    7.  新聞也是插播套件，可自由選擇是否穿插新聞報導與新聞類別
    8.  交通也是插播套件，可自由選擇是否穿插播報附近交通狀態
    9.  整體來說就像個播放器，只是使用者可以選擇播什麼內容
    10.  iRadio 嵌入
    11.  TuneIn API
    12.  工研院文字轉語音：[http://tts.itri.org.tw/index.php](http://tts.itri.org.tw/index.php)
    13.  交通感應器 數據大資料分析：[everyone](https://g0v.hackpad.tw/QIcIhFSUF9l)
    14.  Music as a service [**Audiosocket**](http://audiosocket.com/) **and** [feed.fm](http://feed.fm)
    15.  全民記者：[newspoint](http://newspoint.biz/)and [blottr](http://blottr.com/)
    16.  文字轉語音導覽Text To Speaking：[Newology](http://globalstartup.co/companies/newology/)




reference
    1.  [http://voicetube.tw/](http://voicetube.tw/) 把聲音變成英語學習系統
    2.  基於[這篇](http://www.technologyreview.com/news/515966/the-internet-of-cars-is-approaching-a-crossroads/)跟[這篇](http://www.hksilicon.com/kb/articles/179408#.Uc0bbz789wo)，由ＵＧＣ產生的路況回報似乎還是太複雜的操作，我會想辦法簡化
    3.  國外的公司[inrix](http://www.inrix.com/internet-media.asp)也有作出相同概念的服務，還結合我交通感應器的構想XD
    4.  [spokenlayer](http://spokenlayer.com/) 使用類似工研院文字轉語音技術，被facebook共同創辦人Chris Hughes用於新聞網站[new republic](http://www.newrepublic.com/#).
    5.  我們要緊追以色列的[腳步](http://www.scoutti.com/)
    6.  突然之間，全民記者這種應用如雨後春筍冒出...這次是[英國](https://witness.guardian.co.uk/apps)
    7.  [Serendip](http://serendip.me/application/login)提供不間斷的[音樂流式播放](http://techcrunch.com/2013/01/23/serendip-brings-social-music-radio-service-to-mobile/)，同時為每首正在播放的歌曲提供了完整的社交分享功能。它還能分析與你音樂口味近似的用戶。但它不託管音樂文件，而是從YouTube, [Vimeo](https://vimeo.com/), [SoundCloud](https://soundcloud.com) 和 [Bandcamp](http://bandcamp.com/) 獲取音樂鏈接，創造一個播放列表，也有當DJ的功能。
    8.  紐西蘭[sneltreinapp](http://www.sneltreinapp.nl/)使用app查詢火車誤點狀態，並制定有趣的訂價策略
    9.  [http://echonest.com/](http://echonest.com/)  音樂分析 API
    10.  [http://appworld.blackberry.com/webstore/content/26725872/](http://appworld.blackberry.com/webstore/content/26725872/) ex.fm
    11.  Android platform, which now supports the [**Web Audio API**](http://www.html5rocks.com/en/tutorials/webaudio/intro/) for processing and synthesizing audio and [**WebRTC**](http://www.webrtc.org/)
    12.  最近國際上很多同質性商品，下次g0V要重度Hack！([soundgecko](http://soundgecko.com/), [窄播](https://itunes.apple.com/us/app/zhai-bo-zhi-ting-ni-xiang/id566526832?ls=1&mt=8)，[121cast](http://www.121cast.com/))
    13.  android全民記者：[QIK](https://play.google.com/store/apps/details?id=com.qik.android&hl=zh_TW)
    14.  new voice twitter : [http://croak.it/](http://croak.it/)
    15.  [Music Continues To Follow The Sound Of Developers](http://www.fastcolabs.com/3017016/music-continues-to-follow-the-sound-of-developers), [MusicID](http://www.gracenote.com/music/)
    16.  Radio reference:[Swell](http://www.swell.am/index.html#), [**Livio Radio**](http://livioconnect.com/)**,  Livio對這個計劃來說非常重要**
    17.  台灣也有[眾包地圖](https://play.google.com/store/apps/details?id=com.papago.letspapago)let's papago
    18.  Vocie News : [umano](http://umanoapp.com/)，[quickanddirtytips](http://www.quickanddirtytips.com/)
    19.  影像轉聲音服務：textteaser（[**API on Mashape**](https://www.mashape.com/mojojolo/textteaser#!documentation)） cruxbot [**Summly**](http://summly.com/)
    20.  語音導遊：[TourPal](http://www.tourpal.com/)
    21.  語意網：[http://mmdays.com/2008/09/22/semantic\_search\_engine/](http://mmdays.com/2008/09/22/semantic_search_engine/)
    22.  [語音控制API : voicesphere](http://voicesphere.herokuapp.com/ ) via [Disrupt Europe 2013 Day 1](http://techcrunch.com/events/disrupt-europe-berlin-2013/)
    23.  大陸車用音樂服務：[一路聽](http://www.1luting.com/)
    24.  google新工具：[新聞](http://www.google.com/get/mediatools/)  [地圖](http://www.google.com/enterprise/mapsearth/products/mapsengine.html)
    25.  [http://simplib.com/](http://simplib.com/) ： social network where people share websites.
    26.  [quick drive](http://ma9.mashupaward.jp/works/62)
    27.  Social transit app [Moovit](http://www.moovitapp.com/)
    28.  告訴你前方有攝影機或是警察，跟Waze一樣是眾包[http://cobrairadar.com/](http://cobrairadar.com/)
    29.  [**Shortwave**](http://get.shortwav.es/)  Anonymously speak your mind and get the pulse around you
    30.  語音辨識系統：[onstar](https://www.onstar.com/) and [inkanet](http://inkanet.pateo.com.cn/service/index.php?action=onekeyservice) and [wit](https://wit.ai/) and [http://api.ai/](http://api.ai/)
    31.  [http://www.ushahidi.com/](http://www.ushahidi.com/) 眾包地圖API
    32.  [http://developer.tomtom.com/](http://developer.tomtom.com/) TomTom API開始開放
    33.  [http://developer.echonest.com/](http://developer.echonest.com/)  echonest API 音樂智能資料庫公司\
    34.  [http://z.jd.com/project/details/21.html](http://z.jd.com/project/details/21.html)  車載語音進入新領域
    35.  [Waze 城市合作計畫](https:// http://technews.tw/2014/10/03/waze-launchs-connected-citzens-project-and-gets-the-future-road-construction-data/)
    36.  音樂＋歌詞 [http://gsound.com/](http://gsound.com/)
    37.  車語媒體 [http://www.autoradio.cn/](http://www.autoradio.cn/)
    38.  車用新音樂平台 [http://www.gracenote.com/](http://www.gracenote.com/)
    39.  BMW get a big deal [http://techcrunch.com/2014/11/17/uber-spotify-bmw/](http://techcrunch.com/2014/11/17/uber-spotify-bmw/)
    40.  why its so popular... [http://cartunesapp.com/](http://cartunesapp.com/)   at 2014/11/20
    41.  on demand [http://mobile.mapquest.com/roadsidehelp/?ncid=hsartusmqmo00000014](http://mobile.mapquest.com/roadsidehelp/?ncid=hsartusmqmo00000014)
    42.  [https://www.automatic.com/](https://www.automatic.com/)
    43.  [http://tisv.freeway.gov.tw/](http://tisv.freeway.gov.tw/) 高公局即時路況資料庫
    44.  [http://e-iot.iot.gov.tw/](http://e-iot.iot.gov.tw/) 交通服務e網通
    45.  [https://github.com/g0v/nowin_core](https://github.com/g0v/nowin_core) Now.in 開放原始碼！！！
    46.  最近有兩個交通議題 分別是 [雪山隧道改善計畫](http://hsuehshantunnel.devpost.com/details/landing_chinese) 跟 [台泰駭客松](http://opendata.tca.org.tw/hackathon/)
    47.  [the key of voice search](http://www.globalwebindex.net/blog/top-reasons-for-using-voice-search-on-mobile?utm_campaign=COTD&utm_content=21388662&utm_medium=social&utm_source=facebook)
    48.  [http://blinkrapp.com/](http://blinkrapp.com/)
at 2015/10/21 updated





> inrix他們[圖資用OSM](http://www.gisuser.com/content/view/25741/2/)
> [name=Ymow W]

> ![](http://s.siliconimg.com/kb/content_images/2013/06/28/179408/1372388502_619.jpg)
    
> [name=Ymow W]




-  工作目標：先搶警廣的飯碗 (誤)... 把 Voice Twitter 先做出來，讓民眾可以用這個報案，警廣的音樂部分與新聞部分可以用類似 Now.In 點播＋DJ的方式 (From Youtube or Grooveshark or SoundCloud 等串接，解決 Nowin 版權問題)，有機會從全民警廣轉形成全民記者或是任何進階版再討論
- 授權方式：[open source](http://opensource.org/)
- ProtoType: [http://d.pr/f/WZxA](http://d.pr/f/WZxA)
- 使用資料：目前想到是 Waze API 跟警廣報案資料 [http://rtr.pbs.gov.tw/realtime/RoadAll.php](http://rtr.pbs.gov.tw/realtime/RoadAll.php)
-  狀態：雛型制作
- 徵求夥伴：目前有兩位工程師與一位法律顧問
    - Needs  Designer: 需要美術套版
    - NeedsBackEnd:messenge delive

###  全民警察廣播電台1.0 第七屆動員戡亂改名玩CoCall




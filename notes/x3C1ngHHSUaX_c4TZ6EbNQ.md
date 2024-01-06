---
title: "公民直播＆文播，改善分工與量產之方法"
tags: 島嶼天光記實,inLiveTW,hackpad
---

# 公民直播＆文播，改善分工與量產之方法

> [點此觀看原始內容](https://g0v.hackpad.tw/ATtAnSyQnOM)

標　　籤：島嶼天光記實網站，inLiveTW，服貿專題網，
協助工作：1.[RC語音](https://www.raidcall.com.tw)（即時多人對話軟體）房間號碼25984239。
　　　　　2.[本專案的資料查詢目錄](https://drive.google.com/?tab=wo&authuser=0#folders/0B6ASgY1GMSOhTGxBcE5QZkdZVVE)


/*臨時備註
2014-07-30
/*
23:33:49 <Lee1092> 立法院開始 自我建立網路長城了? lol [http://www.appledaily.com.tw/realtimenews/article/politics/20140729/442393/](http://www.appledaily.com.tw/realtimenews/article/politics/20140729/442393/)
  23:33:51 <kcwu> Lee1092's url: \[【沃草】監委投票實況不給看？立法院封鎖直播網站Ustream | 即時新聞 | 20140729 | 蘋果日報\]
*/
01:41:50 <Michael_LI> ／23:33:49／Lee1092　週六順便討論我手上的VPN主機，跟這個未完成的坑／[https://g0v.hackpad.com/ATtAnSyQnOM](https://g0v.hackpad.com/ATtAnSyQnOM)
01:41:53 <kcwu> Michael_LI's url: \[公民直播＆文播，改善分工與量產之方法 - g0v.hackpad.com\]

--->
[https://www.facebook.com/groups/g0v.general/permalink/668812273195182/](https://www.facebook.com/groups/g0v.general/permalink/668812273195182/)
小弟之前挖過一個「逐字稿打字坊」的坑，看能不能開發一個可以結合影片或掃描文件來進行打字的工具，並且讓眾人合作編輯逐字稿，不過後來就無疾而終了。
 現在看到這個工具，雖然只能個人使用，但至少支援影音檔播放兼打字，應該可以提供有需要的朋友參考。
 逐字稿打字坊：[https://g0v.hackpad.com/ntF2esfIsSj](https://g0v.hackpad.com/ntF2esfIsSj)
 oTranscribe：[http://free.com.tw/otranscribe/](http://free.com.tw/otranscribe/)

 // 一起併入
公民直播＆文播，改善分工與量產之方法
[https://g0v.hackpad.com/ATtAnSyQnOM](https://g0v.hackpad.com/ATtAnSyQnOM)
－－－－
*/



## 一、概要說明︰

　　由於學運期間的直播檔案數量與時間都很多，為了更能夠「[分身伐樹](http://happy.bobi.tw/pic/bomb/e9869118826739579b1.jpg)」增加工作效率，減少工作人員的疲累。
　　預計設計比較簡單的工作流程拆解方法與web輔助，讓人比較方便使用，也比較容易大量生產。
（圖：分身伐樹）
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a8692fec0b7c2f8b1521f34863e0dc51)


## 二、參考範例：

（１）[\[逐字稿\] g0v緣起影片(完成) g0v](/x1vIIhs38Bx)
（２）[國會大代誌](http://ly.g0v.tw)
[http://ly.g0v.tw/sittings/08-04-IAD-18/video#2013-12-11T11:34:13](http://ly.g0v.tw/sittings/08-04-IAD-18/video#2013-12-11T11:34:13)
（３）[【政治獻金數位化】鄉民 OCR](https://plus.google.com/+g0vTW/posts/ATt8XFFaTS4)
[http://campaign-finance.g0v.ctiml.tw/](http://campaign-finance.g0v.ctiml.tw/)
（４）G8V.TV 第五權電視牆評台　　[使用說明](https://g0v.hackpad.com/G8V-JBDd9hvDt5f)
[http://hackfoldr.org/G8VTV](http://hackfoldr.org/G8VTV)
[http://a0000778.github.io/g8v/index.html](http://a0000778.github.io/g8v/index.html)



## 三、現成技術：

（１）YouTube 可以標記時間點。(t=?m?s，自動化切割 video)


## 四、挖坑：

（１）下載 Ustream 比較方便的工具，整理之後再重新上傳到 YouTube 。
（２）inLiveTW的直播列表，可以自動的讓文播的人知道，不必再用人工找Link。


### ＝＝　以上二～四，細部說明將在本行之下描述　＝＝


## 五、概念圖與說明

### 5.1.＜Summit　草創一個輸入頁面＞

－ Example Screenshot 2014/06/22 (還不是想要的功能，先建立雛型)
－ Find Source Code on GitHub: [https://github.com/suensummit/timeSlicer](https://github.com/suensummit/timeSlicer)
（樣圖）
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_133cca6295afa0af1af00f7826503de7)

### 5.2.＜關於二的１，只是使用hackpad＞

　　這是在沒有特殊工具之下，直接讓人取得「mp3聲音格式或影片格式」，然後直接每五分鐘切個段落讓人聽打。
　　最大的好處就是現成工具，不必弄其他程式設計，不過也就延伸出最大的兩個壞處︰
　　第一個壞處就是初步把它弄完，需要人工配對影片時間順序，以及之後的編輯排版，所以生產上還需要多幾道工序，其實使用網路工作的方式，人力不需要這樣安排。
　　第二個壞處就是hackpad本身的能力，很多人同時在一個頁面打字時，會有文字無法輸入現象，雖然理論上可以250人同時看同一份ＵＲＬ文件檔，可是之前其他人的實務上做不到，所以都反而是先在單機上輸入文字再貼上來。這樣子其實反倒不如直接用「Google 雲端硬碟」開個目錄，每個認領段落的人把自己的「txt檔」上傳上來就好，檔名有標準格式即可，最後再由整理的編輯來排版。
補充︰
　　至於說例外的情況，有人會惡意清空內文，開設該文件的人，可以有權限「一鍵還原」，做法如下：
　　1.在上方齒輪圖案，點 View History 裡面會有每個修改版本，
　　2.有 Rever to this 的超連結可以按下，就可以還原該存檔版本。
　　3.不過、如果不是 pad 的擁有者就沒有辦法維護了。


### 5.3.＜關於二的２，使用已經發展成熟的國會大代誌原始碼＞

　　感覺上這個比較省開發的力氣，只要事先把影片稍稍整理過（日期時間可以確定的先確定），先上傳到YouTube，就可以開始讓人標記時間段落。
　　之後再稍微把「5.1.」Summite 概念整理清楚，成為一個簡單扼要的網頁UI，這樣子大概可以完成以下這一個「連貫動作」︰
（圖︰連貫動作）
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_14edcbead658d9f6361cd960cf9e8dc5)

（圖︰參考範例／01_國會大代誌／.png）
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6837ef687ed759f7319ee1016cca6edd)


### 5.4.＜關於二的３，使用已經發展成熟的政治獻金數位化、拆豆腐原始碼＞

　　有請該專案的程式設計師協助了解本文件，看看如何改造原始程式，成為本需求的工作流程。

-->未來的計劃會像是切豆腐般，隨機跳出。
內容目前是預設輸入框＋影片（會直接設定好起始分秒，時間到也會強制停止），預設一段3分鐘，前後重疊15秒。然後頁面會支援影片快捷鍵。

輸入之後比照政治獻金，送出後資料直接進資料庫、排序。之後再人工整合、順文章、挑錯字。
資料庫會借別人的，對方已同意。


### 5.5.＜關於二的４，G8V電視牆的文播應用＞

[基本使用說明](https://g0v.hackpad.com/ep/pad/static/JBDd9hvDt5f)
    以下用實例說明文播應用
    - [香港立法會事件實況](http://j.mp/Uyr2jC)
        （直播時文播人員可一邊觀看實況，一邊於旁邊的 hackpad 文播）
        - [http://i.imgur.com/kJFi77O.png](http://i.imgur.com/kJFi77O.png)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_952202bb19826e900d502a911d6bb83e)
    - 如何[分段認領逐字稿工作](http://hackfoldr.org/G8VTV/http%253A%252F%252Fppt.cc%252FKRGU)
        - 將整段影音上傳至 youtube 播放清單
        - 直接於播放清單設定每段影音開始和結束時間
            - [http://i.imgur.com/jFQ3RZu.png](http://i.imgur.com/jFQ3RZu.png)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7249fdbd577d5494c5031935d13614f3)

            - [http://i.imgur.com/QTNaJSH.png](http://i.imgur.com/QTNaJSH.png)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5b2ffdc31a6d5aad37a76b9a5fa523ab)

        - 請文播人員認領要打清單中哪幾段，即可在下面的 hackpad 協作
            [http://i.imgur.com/I8qgO7y.png](http://i.imgur.com/I8qgO7y.png)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e2d3e714e4c0d6f9770cb45b97a1adaa)

### 5.41.＜關於四挖坑１、２點＞

＝＝節錄g0v IRC　[2014-06-25](http://logbot.g0v.tw/channel/g0v.tw/2014-06-25)＝＝
14:16:22 Michael_LI NewCliCker 就是前幾天我們在寫的hackpad，其中有談到要備份(非youtube)影片，有沒有好工具可用，或是得挖坑才行。
14:21:00 NewCliCker Michael_LI: 這個備份(非youtube)影片坑之前我有請教 venev 瑪麗亞，她指示了一條明路：「去找 yhsiang 就對了」。臉紅紅 ly 老師有寫立法院 ivod 上傳到 Youtube 的自動化工具，我想應該是可以比照辦理 XD
22:54:26 yhsiang
NewCliCker: 欸 我試的是youtube live stream, 影片上傳備份的話應該要問 kcwu

＝＝2014-06-26實驗＝＝
用G8V現有的功能，排版出一個「影片與資料的匯集頁面」，其中順便把hackpad涵蓋近來，把它當作秀出逐字稿、與相關影片配合的一個可能性。
　　張志軍來台，諾富特飯店破門事件，關鍵影片整理。（G8V.TV 電視牆）
[http://bit.ly/G8V20140625](http://bit.ly/G8V20140625)



## 六、試畫流程圖或UML、方便理解系統功能與流程

### 6.1.目前直播與文播的流程

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6f9d4603af8e36a6b028419918f27f50)


### 6.2.未來的流程　//正在製圖中…稍後




##  七～九、保留




## 十、自由討論

> 三、現成技術　那裡是指加在網址後面的嗎？加在網址後面的話是 [#t](https://g0v.hackpad.tw/ep/search/?q=%23t&via=ATtAnSyQnOM)=35m10s 這樣！
> [name=Yarrow C]

> 不過若是別的程式的話就是我誤會了哈哈
> [name=Yarrow C]

> （來自：[http://www.ptt.cc/bbs/Google/M.1261036814.A.F51.html](http://www.ptt.cc/bbs/Google/M.1261036814.A.F51.html)）
> [name=Yarrow C]

> 就只是這樣而已沒錯喔xDDD 不過youtube基本上好像也可以接受&t=?m?s的語法
> [name=Summit S]

> 我這邊只是希望把"每幾分鐘切一段"，"每段之間要有幾秒鐘的重疊緩衝(避免時間切割點剛好有人話講到一半被cut掉)"這部分自動化，不要由人工去做切影片的前置作業而已～
> [name=Summit S]

> 然後之後會借用政治獻金的技術！相關資料已補充在5.4～
> [name=淑華]

> 雖然不清楚技術難度，但如果之後有機會用到政治獻金專案的積分制度，有沒有可能擴大推廣到整個g0v甚至社運圈呢？所有需要群眾外包的專案都可以透過制定相應的貢獻點數來累積使用者的可信度。參考我草擬的[hackpad](https://g0v.hackpad.tw/--NY4jgrpicKE)
> [name=Rhozan]

> 我加上了G8V電視牆的文字轉播應用於 [二、參考範例](https://g0v.hackpad.tw/ATtAnSyQnOM#:h=二、參考範例：)，詳細說明放在 [5.5.＜關於二的](https://g0v.hackpad.tw/ATtAnSyQnOM#:h=5.4.＜關於二的4，G8V電視牆的文播應用＞)[5.5.](https://g0v.hackpad.tw/ATtAnSyQnOM#:h=5.4.＜關於二的4，G8V電視牆的文播應用＞)[4，G8V電視牆的文播應用＞](https://g0v.hackpad.tw/ATtAnSyQnOM#:h=5.4.＜關於二的4，G8V電視牆的文播應用＞)  **。**如果能幫上辛苦的文播人員，將是G8V電視牆專案的榮幸:satisfied:
> [name=NewCliCker]

> 當初決定讓電視牆能支援 IRC 聊天室、hackpad、google doc 等等就是想方便所有的文播和直播的工作。不過我也是鄉民，我也覺得像政治獻金那樣改成切聲音讓大家一起中文聽打然後累積 credit 會比較好玩，還可以開放給想學中文及打字的阿豆仔、補習班 (?) 一起協作:satisfied:
> [name=NewCliCker]

> 感謝_紐克_力提供G8V（G8TV公民電視台）的資料　　//G8TV是我自己加的文字
> [name=Michael_Li]

> 您客氣了:smiley:
> [name=NewCliCker]

> 請問要如何參與inLive和g8v的開發呢? 找到位置但不知如何加入
> [name=Bestian T]

> [https://github.com/inLiveTW](https://github.com/inLiveTW)
> [name=Bestian T]

> 我做過[農學地圖](http://g0v.github.io/farmer/)和[記者證產生器](http://g0v.github.io/reporter/)，會一點angular+angularFire+angularLeaflet，比較熟悉桌電使用的web介面，希望能貢獻一些在公民記者頻道的專案上
> [name=Bestian T]

> github id是  bestian
> [name=Bestian T]

> [Bestian Tang](https://g0v.hackpad.tw/ep/profile/vuj5N8pV6UZ) 大大，自從上次在萌典松向您介紹之後，我們 g8v 電視牆都還沒有開始動工地圖的功能 :satisfied: ，目前 Coding 都是靠 [a0000778](https://g0v.hackpad.tw/ep/profile/s8ZAuyblsAE) ( IRC、Github ID )，最近預計會先解決短網址和頻道 List 的功能。開發資料都集中在 [http://hackfoldr.org/G8VTV](http://hackfoldr.org/G8VTV) 、
> [name=NewCliCker]

> github repo：[https://github.com/a0000778/g8v](https://github.com/a0000778/g8v) ，我 [NewCliCker](https://g0v.hackpad.com/ep/profile/Aq3Xw5pjIMW) 和 [a0000778](https://g0v.hackpad.com/ep/profile/s8ZAuyblsAE) 都會常駐在IRC [#g0v](https://g0v.hackpad.tw/ep/search/?q=%23g0v&via=ATtAnSyQnOM).tw ，還請您多多指教 <(_ _)>。
> [name=NewCliCker]




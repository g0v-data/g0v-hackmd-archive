---
title: "[R2] 空調 / Ventilation @g0v Summit 2016"
tags: hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/DJ7foRA6AP8)

破解環境污染密碼，開源釋出好空氣 / Demystifying pollution: Transparency in the air
主持人: 黃雋

more info: [g0v Summit 2016 hackfoldr](http://beta.hackfoldr.org/g0v-summit-2016/)
現場直播網址 (live url) [http://summit.g0v.tw/2016/live](http://summit.g0v.tw/2016/live)

==↓文字轉播、線上討論↓==

## 空污資料搭配風場的內插與視覺化 / Interpolation and Visualization of Air Pollution based on Wind Fields


目標：PM 2.5, 風場, 內差

環保署視覺化的系統問題：
- 只針對 PSI（多種量測的組合，1989）沒有針對PM2.5
- 數值是移動平均，會有誤差
- 監測站分佈稀疏

民間的PM2.5監控系統：
- [http://env.g0v.tw/air/](http://env.g0v.tw/air/)
- [http://env.childgrowth.info/air/](http://env.childgrowth.info/air/)

風場資料 from [NCEP](http://www.ncep.noaa.gov/)
擷取的資料：風向資料與地形高度
檔案.grib2

Stationary Markov chain計算風場帶動污染物到臨近空間的機率
繪圖用webGL 方法(volume rendering
系統分為三部分: grib2檔 PM2.5粒子 空間(台灣島)
Scientific visualization硬要說的話跟空間上比較有關係，雖然都是視覺化。
Billboard根據使用者的視角，方向(風向?)會跟著做改變

同時考慮化學作用與物理作用下的空汙監測


[http://www.cmlab.csie.ntu.edu.tw/~ked](http://www.cmlab.csie.ntu.edu.tw/~ked)
中央大學鄭老師有一公里解析度的即時風場資料


## 社區科學與健康的環境 / Community science for healthy environments


Liz：這場演說會集中在開放原始碼來做資料的蒐集跟使用，並提倡依據當地的健康需求。開源資源對於當地市民來說是很重要的。我們目前深處在大數據的時代，我們衛星圍繞著地球，但是這些大數據卻很少用來治理當地環境。例如我們孩子在後院玩的資料。如果我們認為政府解決問題的速度太慢，很不幸的我得告訴你學術運作比政府動作更慢。科學家必須花好幾年來研究探討，所以我們現在很需要去研究影響我們健康的環境污染，而這些是尚未被學術研究覆蓋到，這是我們需要做的。我接下來要講三個專案，我幫助了兩個，一個是treekit，另一個是...。

[Treekit](http://treekit.org/)原本是一個公民的專案，現在已經變成公民與政府之間的合作了，這是關於都市之間的叢林與健康之間的影響。社區的民眾花很多時間照顧樹，促進健康品質。這是一個草根運動的基礎。先前有個市長想在紐約種一百萬棵樹，像是 Eva無法使用政府的資料，綠色的點是政府以為有樹的地方，但這都是錯誤的資料。但是Treekit可以標出正確的位置。我們怎麼做呢？你可以看到圖上的測量輪，這可以測出距離，比GPS更精確。過去四年來我們測量了許多樹之間的距離，這是一個草根的操作。紐約的公園樹是公園處的工作，他們也希望知道樹的位置與資料，因此政府與網路公司合作，將treekit做成一個行動網站。這並不只是群眾外包的計畫，長期來說更讓公民自己照顧樹，在2015年的時候，有數以千計的人記錄了紐約樹的位置，並顯示樹木的資料與維護活動，還有公民自己發起保養樹木的活動也都有在這個系統上紀錄，接下來是不太一樣的。我要用三個頭影片來說，我自己本身並無參與此活動，這在尼加拉瓜附近（BUCKET BRIGADE），許多人因為空污的原因生病了，許多人懷疑是附近的工廠原因。紅衣服的女性[Jackie James-Creedon](https://jackiejamescreedon.wordpress.com/)當時身體不舒服，跟全球社區監控者投訴。這組織設計了很多桶子可以監測空氣，裡面有一個袋子。可以做真空汲取外部空氣樣本，再將空氣樣本送回去州政府環保署檢驗，發現此區有很高的有害物質（苯），這數據往上通報後開始注意這邊的空氣品質，後來這個公司201ˋ4年定罪，2015年再上訴也敗訴，此公司被處以高額罰緩，被用於此區的空氣防制上面。這是美國空氣清淨法第二大勝訴，公民自己發起的上訴。

最後公共實驗室（[Public Lab](https://publiclab.org/)），這是我自己發起的實驗。讓環境變得更好。今天有人去參與氣球活動嗎？就像我們圖上所看到的，我們用便宜的照相機跟長長的線、風箏或氣球，就可以拍自己的空拍圖，並整合成地圖。地圖可以整合成同樣的模式，讓大家來用。這樣市民就可以參與活動，而不只是抱怨而已。對於公開街道的熱誠來說，可以直接將此圖上傳到OPEN STREET的網站。

這張圖片讓煤礦公司受罰，他沒辦法從同一個衛星得到這張照片。被罰鍰的其中一個條件是污染持續發生，透過風箏將圖片拍攝之後，我們看到尖尖的煤礦堆，並將公司繩之以法。

接下來我們有開源社群，這些人會協助當地居民處理資料或獲得資料，這組織的結合是草根運動的建置，此外我們也是經常性的網路社群，我們不止拍攝油污的照片，我們也會測試檢體，我們利用簡單的原則來檢測所知道的環境素質。一個簡單的觀察是，石油在陽光下發光，不同的油有不同的發光效果。這是根據實務經驗，可建立簡單的工具雷射，因此我們做了光譜儀及相機。因為我們是開源的方式，因此每次有人貢獻某些東西，我們都會將研究的連結或網址印製在盒子上面具體化。這是我們所做的油污測試工具組，各種不同的油會寄給世界上所有的人並附上實驗結果。我們會用那些實驗器具測試不同的油，我們進行不同規模的實驗。兩年前我做的工作坊，我們做了光譜儀，在此之後我們啟發了很多人去關懷食物安全這一塊，包括台灣。其他國家也測試了食物品質，來看食物當中有多少含量是橄欖油。我們希望有更多人來做這件事情。許多人也會辨識環境中不同油污油脂，像這是地溝油。

最後是我演講最後部分，我們是全球社群，但主要是英文、葡萄牙語及西班牙語等西方為主的國家；最近我們增加了一些華語的朋友。今天早上有人參加升上氣球的活動嗎？Kevin要聊聊這張照片嗎？他做的這件事很棒，他會開無人航拍機，並用此拍了油污滲透的問題。這是今天早上油污滲漏的狀況。2016年一月我跟shane一起出遊，一起去探索受污染水源的問題，此水源問題鄰近一個藥廠。我們做了很多實驗，包括飛風箏拍照，但那天風速太低。所隔天我們帶氫氣球並戴上空拍相機。我們就可以慢慢看到平地無法看到的地方。這空拍圖可以看到有魚貨死掉的地方，也看到附近工廠有污水儲存區。氣球愈來愈往上飛，我們看到綠色水田旁，污水處理廠跟污水處理區有黑色的水槽，且沒有看到他在運作。氣球繼續往上飛看到整個工廠運作的狀況。最後這些照片可以讓對環境議題關心的人們，可以用來提倡乾淨水的活動。

最後兩個投影片我想要邀請大家繼續參與這個對話。我們想問大家怎樣的資料是可以呈現於法庭使用的？在6月6日我們會有google hangout的活動，如果你是夜貓子的話可以加入我們，你們可以看投影片上的網址。接下來我想要邀請大家來參與[publiclab.org](https://publiclab.org/)或許你可以在上面問一些問題，很多人應該會很感興趣。這個QR code是微信的。我喜歡微信因為這有翻譯功能，我也會在上面參與討論。

**問：**您所做的事情是很成功的可以作為呈堂證供。你再將這些資料呈現給法院時有遇到什麼問題呢？
**答：**我介紹給大家的計畫是七八年前的，中間經過很多累積，才有今天的報告，具體的空氣與拍照資料才有具體的法律價值。我們會有環保的律師加入我們的團隊，你可以擁有許多學校的博士學位，但主要是律師對於此資料所說的話。科學家在法庭上不太有說話份量。所謂體制內的研究跟法律根本無法同拍。所以公民應該要來做這塊來讓公司負責，希望你可以一起加入我們解決問題。

**問：**最後的部分有一些中國當地運動份子的活動，我之前在中國工作，很難說服他們來參加活動，因為這是敏感的活動。而且可能會關係到企業的利益問題。根據你的想法，且你們有微信的帳號，你有什麼想法呢？在中國跟哪些社群合作？
**答：**很榮幸跟中國當地的環保運動人士合作，我們是一個全球性的社群，有一些當地的專家是在中國，他們在當地的社群當中看看四周有沒有一些可以用的點子。社群可以是全球的，我們可以加速知識的流動，但我們沒有辦法解決當地的問題。就像為什麼我們的 Logo 是一雙靴子，因為靴子是站在地上的，沒有人可以代替當地人解決在地的問題。對當地的人來說，他們可以採集當地的資料。

**問：**你可以多分享一些例子嗎？關於跟政府機關合作的例子？你有質疑關於體制下的研究，是否有方法能夠解決這問題？
**答：**體制內的科學家有在我們團隊做研究，體制內科學家加入我們是重要的。他們有自己的專業，可以幫當地的居民研發出他們自己的實驗或讓他們自己瞭解當地的狀況。或在什麼狀況下用低廉的價格做實驗。我們有一個詞叫做「公民科學」。公民科學就是參與式的科學，我們會自己問問題，不同專業的人都會貢獻，這是非常多樣化的社群。我們不常跟政府合作。我們計畫裡有很多協作者，這些協作者都是很有耐心的。我很少去跟政府部門開會。


## 綠盟兩岸環境資料透明與再應用專案 / Environment data transparency for cross-strait applications


### 洪申翰

大家好我是綠色公民行動聯盟洪申翰，等等會由我跟我同事曾宏文來跟大家做報告和討論，我們的題目是兩岸環境資料透明與在應用專案。

一開始會構思這個計畫有幾個原因，台灣接下來會面對很多框境的貿易，這二十年我們就不斷在經歷這些事情。這張圖顯示跟中國的貿易程度越來越高，不細講這個變化，兩岸之間跨境生產網絡成形產業界朋友非常熟悉，珠三角、蘇州、北台灣，跨境整合也引發了台灣社會滿大的焦慮，這照片是太陽花佔領立法院的照片，當時這個運動出來後也讓綠盟開始思考從環境組織角度該如何思考？包括這種經濟貿易整合下的環境問題，或更大的結構性問題。

所以我們開始關注一個主題，叫做「污染轉移」不會很難理解，透過供應鏈移動，過去二十年有非常多原本在台灣的生產企業、製造業轉移到中國大陸，生產轉移帶動的是污染行為的轉移，跟過去十五二十年相比，台灣沒有那麼多製造業，好像移過去了，看起來比較乾淨，實際上的污染都轉移到另一個地方去，這是環境運動很大的難題。

左邊例子，六輕本來要在宜蘭設置，因為宜蘭在地民間網絡和陳定南把六輕趕出去，最後到雲林麥寮。若從宜蘭角度看起來是環運勝利，成功阻止很大的污染物，可是從全台灣角度來看，這是環運的勝利嘛？好像比較難講，特別是移動的地方是民間監督力量比較弱、甚至財政比較差的地方會對環境污染產業有更大依賴，可能整體排放量更大，這可能是局部區域勝利，從更大幅度來看就不一定，環運很難處理這個問題。右邊大家都知道台灣有很多 IT 產業移到中國大陸後對長三角有很多污染，台資產業 hTC 和 Apple 有很多污染。

這是很多人知道的台塑在越南沿海造成大規模魚群死亡，發起兩起以上遊行抗爭在越南河內，鋼鐵和捕魚發展中選一個，這是台塑幹部講的，還在看這個污染是否的來自台塑，但因為聲名狼籍很直
觀就覺得是他。

作為一個台灣的環境組織，我們可以怎麼突破這個挑戰和困境？

就一個概念上來說生產資本會移出去，會不會移回來？其實也會，就像鮭魚返鄉也會移回來，當今天只有生產資本有能力做這樣移動，在地組織若把眼光放在島內邊界，有可能造成一個效果是資本只能移動，當要移回來時跟台灣政府開始問，中國大陸沿海省份給我優惠，台灣政府要給我什麼優惠？哪些可以更鬆可以讓我回台灣投資？意思是當只有資本有條件移動時，還是凝固附著在當地時，大家會向下競爭，特別我們對環境污染的管制，這是我們不樂見的。

很多台資企業去投資遇到的狀況是總公司在台灣，要制衡抗議要改善污染行為他不理，我們也聽到一些是兩岸關係，要要求台資企業改善時，中國大陸會說不要破壞兩岸和諧。

這邊是我們開始思考工作目標，想要以環境與污染資訊概念進一步開始建構這個計畫，第一個希望推動環境資訊公開，打造環境監督網絡，這個資料利用不是綠盟而已，而是環團可以一起加入。希望我們可以扮演這個角色，讓各地環境組織可以更有籌碼，兩三年前運動籌碼是身體，你不聽我就佔領你，資料有沒有可能是下一波籌碼？這是我們思考的。第二個協同機制，特別是跨境網絡。

大家需要什麼資料可以成為跨境資訊？跨境移動趨勢鮭魚返鄉是很明顯的，這狀況在兩岸社會造成影響，政府也強化open data這部分。

這段期間也認識綠色選擇聯盟，[公眾環境研究中心的馬軍](http://www.ipe.org.cn)  ，做很重要的是大規模統一收集企業監管資料，目前累積二十幾萬、三十萬的資訊
這資料主要來自環保部門資訊公開，也就是來自官方資訊，這樣應用比較安全

他們特色比較多要求品牌，大型品牌是重要茲點，ＮＧＯ公眾媒體透過對於品牌施壓倒逼回去供應鏈改變環境行為，供應鏈擔心品牌抽乾，所以像apple、非常多品牌開始「互動」的對象。

其中很重要的是在這邊，設定一個遊戲規則，台灣很常揭露之後後果不知道，但他們設定了第三方審核機制，有列入的企業或污染源必須透過綠色選擇聯盟的第三分審核機制，確認整改完成才拿掉，只要供應鏈在網路上有資料就要付出相應的社會責任，這帶來很大的效果。

這照片是我們有到當地昆山企業的鼎新電子，是做電路板的企業，旁邊河的污染狀況讓那個村便成癌症村，當時我們看到這個情景，居民說「你們可不可以管好你們的台資企業？」聽完之後覺得我們的責任滿重的。

透過品牌倒逼供應鏈，這是蘇州富士康，他本來很牛逼不太理你，但apple回去要求整改，就投入一兩億人民幣做這個工作。等於建立一套遊戲規則，逼的品牌要進來這個遊戲規則玩，去年狀況是一年促成將近七十個污染案件的整改，影響力是很大的。

幾個工作策略，要推動台灣環境資訊資料更全面與系統性的開放；民間環境與污染資料庫建置，發展民間環境資訊運用機制，跨境資料協同。

去年開始大動作行動是要求環保署、各地環保局公布，優先資料是水污空汙排放源，比如即時資料要公佈，中國大陸重點企業已經在公布這個資料了，對一般公民監督起很大效果，門檻大幅降低。再來是藉由污染裁處的記錄，目前只看得到違反法律，不知道違規事實，希望推動這部分公開。

下一個部分請虹文
> 請其他夥伴接手～～
> [name=Ann H]

> 我可以但網路有lag
> [name=Yu-Chi C]

> 這邊網路也會斷其實ＱＱ
> [name=Ann H]


### 曾虹文


請大家想像我們開始操作網站，希望可以從網站來落實民眾環境知情權，不管是民眾或在地團體都好，都可以查詢到周邊環境品質狀況，我們都希望可以在這個網站上看到。第一步就是要有這些資料，我們在政府網站找不到任一個企業的污染資訊，我們可以找到河川嚴重污染，但卻不知到沿岸有哪些工廠，或是污染物質有哪些。我們發現我們做網站時要什麼沒什麼，但就慢慢去要。我們現在在水污、空污目前都有慢慢的跟政府要資訊公開的進度。希望大家可以一起來關心要公開而未公開的進度。接下來我要開始實際操作網站。
> 網站是示意?
> [name=Mario C]

> 我也找不到網址
> [name=Weoi L]

> 應該還沒公開，只是先展示。記得她有說，請大家想像她在操作網站
> [name=Bear P]

> 初步建置 7/1上線
> [name=Weoi L]

因為要落實環境知情權，所以假設我是雲林麥寮人，我可以先在地圖頁面，輸入雲林縣麥寮鄉，地圖就會跳出麥寮周圍的環境品質狀況，圓點是空污，三角形是附近工廠。我們會想知道這彼此之間是否有關係。我們可以針對工廠做篩選，例如過去是否有污染違規，或是是否已經有即時監測資料。或是在三十天內是否有超標記錄。假設我們現在把游標從空品測站一到工廠，可以看到這是台塑麥寮廠，可以看到過去開罰記錄跟金額等，也可以再點進去看資訊。

還有其他搜尋方式是，我知道我家附近就有台塑，可以直接搜尋企業，可以直接這樣操作。若直接點進去企業名稱，可看到企業基本資料跟及時間監測資料，每根煙囪都可以看得到紀錄。繼續往下拉就可以看到五年內的違規開罰記錄。我們回到剛剛即時間側的部分。兩個重點是：環保署雖然一直有再開放資料，但這些資料都不是開放資料格式，沒有標準線。不知道是否已經超標。所以我們需要自己去把基準線找出來。但因為現在政府沒有開放資料，所以感謝g0v的將協助取資料。我們可以看到煙囪三十天，也可以看到24小時的紀錄。我們看到超標就想要檢舉，右上角紅紅的，會有分享跟檢舉的機制。點了分享之後，可以分享到臉書上讓更多人知道這件事情促成社會輿論。點了檢舉會直接進入到環保署公開陳情系統。如果是空污的話可以直接調記錄，兩小時內都超標就可以被開罰。水污比較麻煩，因為需要有稽查人員到現場。但我們仍可以繼續監測。

一個是地圖，一個是事業單位搜尋。我想知道台塑所有企業狀況，這裡輸入台塑，就會全部都列出來了。我如果直接點進去，一樣會跳到剛剛的頁面。如果不輸入台塑，也可以直接輸入產業別搜尋，例如半導體業，所有裁罰記錄就都會跑出來了。未來我們也會陸續補充資訊，像社會抗爭跟新聞報導也會陸續補進去。另外我們也放上一些環境小知識，像是常見的污染物等等。

網站還在建置中，預計七月一日上線，希望大家能給我們回饋與幫助。最後感謝Jimmy與團隊，他們很像建達出奇蛋，都會落實我們的願望。

這個資料庫是我們專案樞紐的核心，未來要發展成app或其他形式也都還在構想。坦白說這些資料也都可以公佈在這些平台上。政府若要做，很快就可以取代民間組織作這件事。所以民間組織可以做哪些事情是政府沒辦法作的？一是地方合作的網絡。二是跨地域資訊的整合，例如台資在中國的污染資料，也需要放入這個平台裡面，這個台資企業在中國表現如何，希望可以做資訊同步。第三、建立企業社會責任話語權，過去都是企業說的算，但我們認為這應該是ＮＧＯ跟在地組織和人民一起討論出來，不只看台灣本地，也應該把境外表現都納入。如果你是一個企業在中國或東南亞都有很多污染，我們應該要倡議政府不該在給此企業優惠。

環境資訊／料再應用的方向與機制
1.  與地方監察網絡充分合作，提高在地監督的籌碼與能力
2.  跨地域（兩岸或東南亞）資訊同步與協同
3.  介入企業社會責任話語權（ex.倡議海外環境表現納入企業治理評估機制）

第二個重點，這根煙囪可以看超標紀錄，點了分享之後可以分享到臉書上，引起輿論，點了檢舉之後會進入到環保署的系統。


### Q&A

Q1：我看到網站很不錯，需要進去才能看，如何用電腦自動寄檢舉信給政府？
A1（申翰）：我簡單回答，我們確實在這邊是有思考在地的監督網絡，不只是機器或電腦完成，特別是讓在地監測網絡過去不清楚排放多少，現在知道有沒有超標，可以檔一他去行動的門檻，沒有想到完全用機器讀取自動舉報。
虹文：現在台灣環保署公開陳情系統長這個樣子，你的需求是要跟g0v許願，看能不能做到這樣，開發app之後超標可能就震動，可是我們沒有辦法把這個訊息直接key進去，這個欄位還是要人工填寫，能夠做到的事提醒我們現在有哪些東西超標，要做到還是技術性問題往這邊，實際上很困難因為受限於系統。


## 從基礎工程到應用工程 g0v資料與其它資料庫的整併及後續應用 ─ 以環保署污染源與公司結構資料為例 / From infrastructure to applications Linking through g0v - a case study on the environmental agency and company registration data


Liz Barry 有講社區的部分，
要怎麼樣知道企業的來源？
模式分析有本講解答

我的研究方向是企業分析，主要談企業各種特徵和行為關係，其中重要行為是污染跟勞資爭議，這幾年是分析各種企業，g0v資料對我來說非常重要，但要變成我想要的資料或者有些給綠盟用，變成新的資料庫中間有非常多困難跟需要突破的點，分享這部分是如何一步步處理掉。

為什麼要用一個資料？這張圖可以看到企業結構跟上下關係是變動的，去年google就成立新的母公司 Alphabet，兩者之間的關聯？g0v基礎工程、公司結構應用、整併案例、解決方案

先用opendata倡議，四個部分是資料進用、分享與再使用、社會與商業價值、參與治理。

主要核心是放在再使用，g0v我要再使用出來，有很多方向與可能性，一個是商業價值廠商來用，在地的要是公共性和社會季札，再來可以參與治理，怎麼讓民眾看到之後可以動員組織。
我的目標是建立一個可以再使用的資料庫，第一個是g0v目前做到什麼？協作經驗累積，有後續應用的想像，公司資料非常重要也有實作案例，進一步要怎麼公共化？怎麼讓政府資料進一步完善話？裁罰記錄沒有更完整的記錄。最後怎麼達到參與治理。

為什麼要談公司資料？除了國家之外公司是影響力最大的組織，過去就有各種政府民間提供的資料庫，g0v資料重要事[rony](http://ronny.tw/data/)  爬了經濟部的商業司網站，把他爬下來後提取出來便成半結夠資料，簡易搜索不用驗證碼，商業司要，幾乎同步更新，每月十日更新，可以打包下載。可以進一步進行大規模分析。
> [http://company.g0v.ronny.tw](http://company.g0v.ronny.tw)
> [name=高餅倫]

可以看到公司資料兩面性，商業性質也有公共性質，目標不同有不同應用模式和授權、收費模式，商業性質有需求會賣很高，公共性質是希望達到社會監察效果，公司治理、學術研究，這些資料就會散佈不同地方。

分成兩種，一種是基本資料，可能有成立日期和董監事名單，資本額、員工數，行為資料，財經指標，獲利多少，或者營收，勞資爭議，違反勞基法幾次被罰多少錢，污染，逃漏稅，其他違法事項。

台灣目前重要資料庫有哪些？rony資料有董監事成立日期跟資本額，台灣經濟新報是最完整的，成立日期董監事污染逃漏稅都在CSR裡面但資料不完整，環保署污染資料有污染跟違法事項。各縣市政府都有定期公布違反勞基法的資料跟名單，但有些事pdf，有些csv，是很亂的。

現在要看的是如何把環保署資料整併為公司基本資料？跟rony整併出來，環保署2011年上線，把列管資料定期上網，以工廠為單位，日月光28家廠每季公布，七萬一千六百多家場，進入列管範圍才通報。「列管」二字非常重要，五個資料庫水污染、毒性化學物質.....，水污染可能懸浮物ph職，空汙pm2.5，廢棄物各種不同，有很多內部細節可以上去看。

環保署污染資料出發，可以在公共事務上發揮作用，我們有環保署污染源資料，過程是什麼？我的想像，第一個這是日月光排放廢水的場，我會希望把所有污染資料彙集，就知道有沒有改善，目前污染狀況如何，這是2014年各種數據，可以看到有少一點但還是繼續被裁罰。

黑心廠不夠，現在要抓日月光半導體製造股份有限公司在環保署污染源所有資料整併進來，要確定這幾個廠都是下屬廠，加起來空汙水汙廢棄物加總起來。要把所有日月光集團，不只半導體公司，這是整個祈團企業母公司到子公司的分布圖，剛有28家廠，透過不同路徑控股到中國、新加坡，入主開發，再出去，日月光有非常多公司，大陸有房地產公司，可以看到如何去佈局。

我要的是完整上下游公司列表，可以從最頂端控股公司到每個最細的末端。包括海外、國內註冊公司還有免稅天堂，每家在集團中的位置、上下游公司數、集團基本資料和結夠數據，這又可以變成新的資料庫讓大家利用，這東西是在環盟網站上，牽扯到他的行為污染，有人可能想做逃漏稅違法事項可以用這個數據去看大集團的為法事項是什麼。

整併過程、確認環保源、計算所屬公司數據、確認所屬集團、計算呈現新資料庫

他需要進入環保署污染源網站，這算是簡單，用R可以簡單挖出來，比較麻煩是環保署資料很糟糕，只有廠的管制編號，沒有這公司的統編，無法知道七萬多家list哪些屬於日月光，必須做資料清理，唯一方式就是名稱，把「日月光」的挖出來，模糊比對，三千多筆無法準確比對，必須人工比對。

環保署原始資料缺陷，剛那個圖二十幾家廠，還有很多未列管，從經濟部工廠資料，g0v他們開發出來的，總共43家，空汙22、水汙24.....，沒列管沒通報資料就是0。列管有資料的反而是少數。

牽涉到一個問題，g0v資料有限制，第一個是上下游公司認定，日月光半導體連上去，母公司新創投資連到華光電子，無法確認這個線該切到哪裡，資料挖出來會認定華光是子公司，無法確定企業邊界。再來是海外公司，只連到幾個點，可以把新加坡、大陸挖出來，目前經濟部沒辦法。

我的取巧手段是請朋友抓中華徵信資料庫，每個集團都有交叉持股列表，缺點是授權問題。最後就是整併，污染總值、集團董監事名單，還有社會網絡用的各點中心度、階層數。最後是污染呈現，資料輸出，問題列表歸納，有原始資料缺陷、有些有列管、有些有列管無資料，上下游、邊界、標準界定、授權問題。

歸納第一個是技術問題很好解決可以整併其他資料庫coding，第二是政治問題，政府資料欠缺需要民間倡議提案，再來是授權很麻煩，第三是專業問題，遠程框架問題，從g0v公司資料庫環保署資料庫到我的目標，遠程技術上遠程做到一步步推動，再來是標準建立，要採取什麼標準？董監事席位過半數？控制權？

這邊提出幾個點，比較重要的合作方式，這樣的計畫需要一個核心應用資料庫團隊，募款和整合角色，要能跟政府倡議。再來是學者記者，目的性很強需要去研究資料在哪，會提供框架建議，XBRL公開資訊觀測站推動要求上市櫃公司財務報表要用特殊語言輸出，但品質還不是很好，再來是巴拿馬文件，以後也許也可以併進來，再來是供應鏈，公司資料結構日月光集團可能ABC廠，可能A接apple單，B接dell單，要怎麼併進來，是以後分析公司行為重要的資料庫，還有租稅補貼，這應該最簡單拿到，日月光台積電拿了很多租稅補貼，但都藏在年報裡面沒有在公開資訊觀測站公開出來，需要大家要求證券交易所放在財報裡面，再來是工程師coding技術資源還有志工，很多需要手工人工清理。

各種方案像昨天談blupa可以慢慢評估每種不同資料庫應用性質組成方式到底哪種是我們跟政府要資料達到目的，可以知道每種方案效果如何，慢慢達到目的。


### Q&A

Q1：在這樣的資料結構下，除了企業與企業的連結外，是否有企業與各政府的關係做連結？
A1：提出框架，但資料在哪裡，例如監察院政治獻金資料庫，但沒有上網，要去挖他，他會呈現一部分你講的關係，遊說資料也可以，能並起來最好，要一步步去推，要求監察院上網，他現在只開放一台電腦去查。

Q2：整理資料時要揭露事情，有沒有可能整理正面表列的東西提供線索？例如有些電鍍方面處理非常好。
A2：企業社會責任排污優良廠商，有沒有一套第三方審核和大家信服方式去講這個實至名歸，認定CSR好不是現在這樣模式，而是有個客觀資料庫能夠被檢視挑戰、完善化，透過這個機制再去談誰是優良廠商。


Q3：大家說技術方面不是問題，提到的座談會提出 13 個部會要做整合，環境雲要做系統整合的話需要，大方向能不能整理出來給大環境？
是否能將資料開放進來？
A3：會希望這個資料庫跟你剛講的食安資料庫，我沒細看過不知道內容，至於倡議什麼的，目前重要工作是把相關問題列出來，把目前能夠在技術上合作上可以突破的點做出來，一步步問題推動，不一定要做很大倡議工作，倒是不用，這是我的想法。國外open copperation我看過但跟台灣不太一樣，台灣生產鏈位置有點複雜，他們表格我看就不對，也許我們可以私下討論。


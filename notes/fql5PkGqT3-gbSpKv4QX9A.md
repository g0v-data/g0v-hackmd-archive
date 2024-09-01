---
tags: GIS, Issue-Mapping, Open Street Map
---

# 哺乳地圖

> [點此觀看原始內容](https://g0v.hackpad.tw/O0rbl8VdqpC)


## 想做什麼

- 有個地圖給帶 baby 出門的人知道哪裡有方便哺餵小朋友的設施
- 2024.07 討論串 https://www.facebook.com/share/p/g79RP5UEa6LUS4kM/
- 2024.08 [北鼻趴趴走 Project](https://tree-cornflower-293.notion.site/3668351ca6464df887d1fbd6dbc3c0b6?pvs=4)

開了Notion，歡迎大家來協作

## 專案策略

- 地圖（由[飲水地圖](http://beta.hackfoldr.org/drinking-water)改為哺乳地圖）
    - 資料：衛服部的開放資料 --\> 投開票所 geocode轉碼工具 --> 群眾外包加入 OSM --> 使用者回報增點修正
    - 介面：使用者經驗出發的APP

- 遊戲

## 參與作法

- 飲水地圖：把資料放到 OpenStreetMap，用 drinkning.teia.tw 的程式或 App 呈現
    - OSM 有 babycare 相關 tag 可參考 [https://wiki.openstreetmap.org/wiki/Proposed_features/babycare](https://wiki.openstreetmap.org/wiki/Proposed_features/babycare)
    - 比較需要的 tag
        - baby_feeding=room（有哺乳室）
        - diaper=room（有換尿布室）
哺乳室適合的value可能是[diaper](http://wiki.openstreetmap.org/wiki/Key:diaper)=\* number for tables。台灣一般不會把尿布台做一個單獨隔間，而是常設置於廁所、哺乳室中的開放空間設施。
> 台灣一般換尿布台設置在廁所內，但幾乎都是女廁，男廁沒有尿布台，如果爸爸要換尿布，必須找無障礙廁所
> [name=YuHsin L]

        - stroller=yes（嬰兒車可進入）
        - level（所在樓層）
        - access（有沒有開放使用）
        - opening_hours（哪些時間開放）
```
       台灣公務機關的哺乳室，主要服務公務機關的員工，開放時間僅限平日的上班時間，週末去試往往碰壁
```
        - 另外獨立POI標註服務台位置[tourism](http://wiki.openstreetmap.org/wiki/Key:tourism)  [=  information](http://wiki.openstreetmap.org/wiki/Tag:tourism%3Dinformation) 因為常遇到要跟服務台拿哺乳室鑰匙才能使用的狀況。
        - 獨立標 POI (需要 proposal )
            - amenity = baby_feeding
            - baby_feeding = yes/room
            - access = yes/permissive/customers/key
> permissive也許能形容哺乳室常受管制的狀況，但我覺得這個更直覺：『[access=key ](http://wiki.openstreetmap.org/wiki/Zh-hant:Tag:amenity%3Dtoilets) 需先索取鑰匙才能進入』
> [name=Yaling P]

> 很適合台灣那些受管制的哺乳室，需拿鑰匙登記使用者的管理現況。
> [name=Yaling P]

            - drinking_water
                - drinking\_water:hot\_water
                - drinking\_water:warm\_water
                - drinking\_water:cold\_water
> drinking_water=yes 其實比較接近單純的「飲水點」 而非特指有冷熱水的飲水機？ 要如何標示台灣常見的冷熱水飲水機？ 因為哺乳室裡是否配置飲水機很重要，嬰幼兒照護常常需要使用熱水。 無論是要拿來清潔或泡配方奶或母奶隔水加熱。
> [name=Yaling P]

            - microwave = yes/no/fee 是否有微波爐
            - [water_tap](http://wiki.openstreetmap.org/wiki/Tag:man_made%3Dwater_tap) = yes 是否有洗手台 (可獨立標POI)
> 哺餵前都要先洗手，有肥皂可消毒更佳
> [name=Yaling P]

            - lock = yes/no
            - capacity = 1, 2, 3..
> 是指使用組數嗎？(單位是一組親子) 容量其實不太好估算，因為除了capacity = 1的空間容易辨識外，哺乳室空間一大，使用人數就會蠻彈性的。同一哺乳室，可能有媽媽正在哺乳、有其他媽媽在使用尿布台或其他設施。可能要發展成數字區間之類的標示，例如capacity = 2-4
> [name=Yaling P]

            - power\_supply:nema\_5_15 = yes/no  (插座)
            - supervised = yes/no (管理員)
            - fee = yes/no (收費)
            - operator =* (營運/維護單位)
            - ref =*
    - gov opendata
        - 依法應設置哺集乳室公共場所名單  [http://data.gov.tw/node/23750](http://data.gov.tw/node/23750)
        - 志願設置哺集乳室名單  [http://data.gov.tw/node/23858](http://data.gov.tw/node/23858)
        -
- 衛福部有「母乳一指通」App
    - [iPhone版](https://itunes.apple.com/tw/app/mu-ru-yi-zhi-tong-for-iphone/id578498751?l=zh&mt=8)
    - [Android版](https://play.google.com/store/apps/details?id=bhp.mohw.gov.tw)
    - App 的資料看起來有經緯度（不是只是所在建物或地址）、有樓層（可以從地址取得）、有開放時間（但是是文字描述）
    - 2016/1/8 update: 國健署釋出xls[有經緯度的資料](https://www.facebook.com/groups/odtwn/1406605286020552/)囉~ (感謝國健署認真同事)
- 官方集哺乳室地圖，衛福部孕產婦關懷網站 https://mammy.hpa.gov.tw/Map/BreastfeedingRoom
- 「友善新竹哺乳室」App
    - [iPhone版 ](https://itunes.apple.com/tw/app/you-shan-xin-zhu-bu-ru-shi/id976039615?l=zh&mt=8)
- 可以用類似投開票所 geocode 的方式 (現在爛掉中) # [http://comap.clkao.org/about](http://comap.clkao.org/about)
已經加到臺北捷運各車站了 [http://overpass-turbo.eu/s/bVe](http://overpass-turbo.eu/s/bVe)

## 工作討論記錄

### 10/24 g0v 第16次黑客松 討論記錄

- **（dir 依印象補記，有錯誤請幫忙補正）**
- 一般的列表不可以直接照抄進入OSM，但政府的OpenData平台上的資料可以。（授權問題）
- 政府OpenData平台上的兩個名單（依法應設置&志願）目前 的資料與「母乳一指通」App內的資料不同，Peggy會幫忙請政府相關單位校正。
> 2015/10/28 最新進展：[LINK](https://www.facebook.com/groups/odtwn/permalink/1351814758166272/)。重點如下：APP的資料上次更新是102年......所以data.gov上的資料才是對的，這邊資料每三個月更新一次 (data.gov資料連結：[依法應設置](http://data.gov.tw/node/23750) & [志願設置](http://data.gov.tw/node/23858))
> [name=羅佩琪]

> good news!!!
> [name=yellowsoar]


- Lucy 會幫忙收集終端使用者（主要是媽媽）對於哺乳室的的需求列表，整理完成後會提供給 Peggy 及 OSM 參考。
    - 需求列表例如：有沒有插座＼微波爐＼飲水機＼冷熱水，門可不可以鎖、有幾間（同時可有幾人使用）....等
    - 希望可以讓 Peggy 提供給政府w機關，理想目標是政府機關收集哺乳室資料時，順便就把細項都收集好。
    - 已完成，在哺乳室使用者經驗
- 目前首要目標是政府 OpenData  平台可以提供足夠正確度、品質的哺乳室資料，然後請OSM 高手幫忙轉入 OSM 。
- 等 OSM 端有資料後，可以包 APP ，APP打開才有第一批基礎資料，有了基礎資料後，做群眾編修才比較容易成功。
    - 第一階段：查詢所有哺乳室 （如果只做到這個階段，跟官方的「母乳一指通」差不多）
    - 第二階段：使用者可以新增哺乳室資料（使用者建立）
    - 第三階段：使用者可以修改哺乳室資料（使用者糾錯）
    - 第四階段：使用者可以刪除哺乳室資料（刪除不適當的資料）
        - 「修改」、「刪除」功能需要仔細討論清楚，避免使用者惡意破壞？


## 相關討論

### 臺乳協會討論

衛福部母法  [公共場所母乳哺育條例](http://law.moj.gov.tw/LawClass/LawContent.aspx?PCODE=L0070036)
施行細則
[http://www.hpa.gov.tw/Bhpnet/Web/HealthTopic/TopicArticle.aspx?No=201110070007&parentid=201110060009](http://www.hpa.gov.tw/Bhpnet/Web/HealthTopic/TopicArticle.aspx?No=201110070007&parentid=201110060009)

微波爐：理論上不適用於加熱母乳
溫奶器：理論上可以加熱母乳到常溫即可
尿布臺：需保護嬰兒小孩不墜落且方便更換尿布（理論上對外開放使用必備）
> 單獨標示的可能性？
> [name=yellowsoar]

推嬰兒車方便到達
冰箱：冰母奶專用（理論上對內員工使用必備）
哺乳、育嬰用品：溢乳墊、母乳袋（裝母奶用，比較厚，抗菌）、冰保（非食用級，保存母乳用）、尿布、
集乳器：電動設備，通常是對內使用才會配置。
空調
男性可否進入（台大醫院總院一樓哺乳室標示男性勿入）


洗手臺：老舊建築可能沒有辦法接水，或者要設置在廁所旁，但許多建築廁所處於陰暗人煙稀少處，部份以乾洗手代替。
收費：依中華民國法規，哺乳室不得收費。
飯店：部份飯店沒有設置哺乳室，但部份飯店允諾可無償出借房間供哺集乳使用。

還不錯的哺集乳室：新北市政府大樓（1樓為對外，13樓給員工使用，此兩間非常適合對照）、新北市中和稅捐稽徵處與地政處

哺集乳室認證：
台北市：[http://health.gov.taipei/Default.aspx?tabid=149&mid=1469&itemid=30107](http://health.gov.taipei/Default.aspx?tabid=149&mid=1469&itemid=30107)
新北市：[http://www.health.ntpc.gov.tw/information.aspx?uid=403&pid=4603](http://www.health.ntpc.gov.tw/information.aspx?uid=403&pid=4603)

### 以下為PTT Baby_Mother版上討論哺乳室的所有文章中提到的項目，可以做為欄位的參考:

位置:：地址　X樓XXX旁
功用：可哺乳/可集乳/皆可
使用方式 (要請服務人員開鎖/可自行進入/登記使用)
開放時段

主觀評價：
清潔度 （乾淨／髒）
整齊度
隱密性
安全感
安靜度（安靜／吵）

空調 （無／電風扇／冷氣／暖風機／空氣清淨機）
上鎖方式 （無／布簾／活動屏風／門／門+鎖）
空間（寬敞／窄小／可容納嬰兒推車）
數量 （只能一人使用／有X個隔間）
隔間方式（無隔間／用布隔／有實體牆）
座椅 （哺乳椅／沙發／有靠墊or餵奶枕／板凳／扶手／辦公椅）

電源插座 （這樣才有辦法使用電動集乳器）
尿布台 （有／無／數量／高度(方不方便把小孩抱到胸前洗)／乾淨度／柔軟度／可加溫／限重X公斤／有擦手巾）
洗手台／沖洗區 （熱水／洗手乳／擦手紙／奶瓶清潔劑／奶瓶刷／蓮蓬頭）
嬰兒床
飲水機（熱水／冷水／是否有定期換濾心）
吹風機
冰箱（用來暫時存放母乳）
置物櫃 （可放媽媽包）
全身鏡（方便哺乳完調整衣物）
兒童安全座椅（可以暫時困住小孩）
奶瓶消毒鍋（有／無／蒸汽消毒／紫外線消毒）
溫奶器 （又名調乳器）
微波爐
垃圾桶
親友等候區 （有椅子／書報雜誌）
集乳器 （品牌型號）
衛生紙 /紙巾 /濕紙巾
尿布（可索取／自取／販賣機）
痱子粉

### 需求表格整理（整理出上面那些攤開的item的重要程度）

[https://docs.google.com/spreadsheets/d/1t5Tuj9BQ4RZiwN3urHcKyochd7DW1nvzh85F7whkxRk/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1t5Tuj9BQ4RZiwN3urHcKyochd7DW1nvzh85F7whkxRk/edit?usp=sharing)

## 哺乳室使用者經驗


### by 彭小五 退役的哺乳媽媽、開放街圖圖客(OSM mapper)

心得分兩部份，前是哺乳室使用經驗，後半是圖客觀點

母乳地圖其實我蠻有興趣，因為我曾是經常性使用者。所以每次到室內的公共場合不免會側目注意一下哺乳室的所在位置，以免緊急時需要使用（或幫助其他慌張衝進來的媽媽）。
有時，立即找到哺乳室的急迫性類似尿急人找廁所的緊急性，因為常常是：
1.  哺乳媽媽漲奶急需要擠奶（可能是溢乳墊快爆炸，已經開始溼到衣服。或是漲奶漲到疼痛非常，需要擠出奶汁，舒緩乳腺壓迫）
2.  寶包正在大哭，急須喝奶（否則全場的人都會因嚎啕大哭的音量側目妳）
3.  寶包或幼兒尿布外溢或衣服吐溼，等等令人炸毛鳥事。
這些各種很緊急的事件發生時，我都是衝進確定有哺乳室的場合後，直接找櫃台詢問地點，因為有些哺乳室受管制需拿鑰匙開門，直接找服務台NPC可以一次解兩個任務1.知道地點2.獲得使用許可。
畢竟分秒必爭，在哺乳室前狂拉門把才發現又要跑去櫃台登記拿鑰匙真的超幹（尤其手上還拎著一個需要緊急處理的小人！）。
而對於有使用限制的哺乳室，在實際管理上，館方會在哺乳室門上貼告示知會使用者要去櫃台登記方能使用，所以通常是帶人又帶大包小包（重到可以砸死歹徒的育兒包）來到門前才知道被打槍。
所以mapping服務台也許是母乳地圖可以順帶推廣的？以我個人使用者的經驗來說，有其必要性。不過我的經驗不是現在式，也有可能現今已經慢慢開放，不再有那麼高比例的哺乳室需要得到許可？這點需要請參與者在與台灣母乳協會討論時，更新一下資訊。

（以下是mapping討論）

我之前思考過，覺得mapping哺乳室的困難點跟飲水機、AED、滅火器會遇到類似的問題：室內定位。從平面位置到垂直位置(樓層)，地圖上顯示的位置都不容易精確，偏偏又是很緊急需要立即知道明確地點並到達使用的設施(哺乳室、AED)。
如果建物只有單一樓層，地圖顯示就比較不容易照成誤會。但如果整棟好幾層樓，但設施只在某一樓呢？
還有哺乳室也會遇到AED一樣的問題：因為包含在某個機構室內，所以會有開放時間的限制。嚴謹的tagging方式是否需要以relation包入建物內呢(iD不好操作relation、學習josm又有進入門檻，會降低推廣效力)？還是個別tagging openinghours？先自首，我現在tagging以上室內設施，都沒實作那麼多啦XD 力求在建物平面內精準標出對應位置而已。

之前默默觀察過這些室內設施，在大型室內公共場所的分布位置：
- AED比較偏好設置於一樓，可能是利於支援戶外患者，而且一個建物可能只配一個設施。
- 但是飲水機就常遇到每層樓都在相同點配置的情況(分布跟廁所很像)
- 而哺乳室常會被塞到偏遠角落，所以遇到要使用時，真的要找、要詢問，有地圖會幫助到使用者，但又常被使用許可卡到(我支持同時tag服務台)。不過哺乳室我也遇過像廁所一樣，是在戶外獨立一間的。這種的在mapping上就不太用擔憂地圖上資訊呈獻的問題。
- 至於滅火器，我只有tag過掛在室外走廊的，還沒標住過室內的。

另外提供一個哺乳室的特殊案例：
一般都是一個場所配一個服務台，但有時也遇到N個服務台，而哺乳室鑰匙又單獨放在某櫃台。
- 實例：台中資訊圖書館的哺乳室設在兒童閱覽室(此非正式官方名稱，正名很難記XD)，但是鑰匙是要向兒童室借閱櫃台登記拿取，而非入門大廳的服務櫃台。

## OSM tagging schema

統整討論紀錄中哺乳室可能會有的項目，列出相對應的 OSM tag 以及不適合對應的 tag



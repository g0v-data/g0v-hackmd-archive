---
title: "村里長選舉資訊平台"
tags: hackpad
---

# 村里長選舉資訊平台

> [點此觀看原始內容](https://g0v.hackpad.tw/4dfOWQvbpgZ)


臉友Jevon Lee 提供的點子，大家來評估可不可行。

我建議板上可以做選區地圖，請有心人士幫忙製作

1.用地圖方式列出全台縣市→鄉鎮市區→村里

2.各位自行表明參選意願，經過團長審核(避免惡意亂入資料)，在該區標記有意參選人。若有政黨提名確定參選，也把這些資料一起列入(各位粉絲若有收到任何政黨提名消息，可以提供給團長，讓團長登錄資料)，大家比較能知道有多少對手。

參考格式：參選人姓名(政黨)

3.參選人可以簡單發表政見、理念與願景

4.該村里選區的粉絲可以對候選人按讚表示支持，可當作民調參考

這個選區地圖可以讓大家知道哪些村里已經有人表示參選，若同時存在多位有意參選人，參選人彼此可以政見交流

操作流程大致如下
1.一開始畫面是台澎金馬地圖
2.點選縣市，進入鄉鎮市區地圖
3.點選鄉鎮市區，進入村里地圖
4.點選村里，顯示自願報名/初選登記參選人和政黨，旁邊有粉絲數目和民調指數(換算成百分比)
5.點選或滑鼠移到參選人姓名，顯示政見、理念和願景

來源： [https://www.facebook.com/eeemmt/posts/237033213162434](https://www.facebook.com/eeemmt/posts/237033213162434)
討論： [http://community.g0v.tw/t/topic/126](http://community.g0v.tw/t/topic/126)

跳坑人士： [http://community.g0v.tw/users/kai_lin](http://community.g0v.tw/users/kai_lin), kiang

現有相關專案：
1.  [represent-boundaries](https://github.com/opennorth/represent-boundaries) \- 一個用 Django 呈現個別區域民意代表的程式
2.  [MyServant](https://github.com/sfhuang/MyServant) \- 根據選擇的行政區去找到對應的民意代表
3.
4.  [https://github.com/Hokila/TownCandidateMap](https://github.com/Hokila/TownCandidateMap)  \- 以 iOS 開發的村里候選人瀏覽介面 (alpha)

相關資料：
1.  [http://data.gov.tw/node/7440](http://data.gov.tw/node/7440) \- 全國村里界圖
2.  [http://cand.moi.gov.tw/of/ap/villmast_excel.jsp](http://cand.moi.gov.tw/of/ap/villmast_excel.jsp) \- 村里長一覽表
3.  [https://github.com/kiang/cunli](https://github.com/kiang/cunli) \- 村里資料展示
4.  [http://data.moi.gov.tw/MoiOD/Data/DataContent.aspx?oid=16DB45A1-37BD-478E-BEE1-E44088B54CF5](http://data.moi.gov.tw/MoiOD/Data/DataContent.aspx?oid=16DB45A1-37BD-478E-BEE1-E44088B54CF5) \- 單一年齡性別人口數
5.  [https://github.com/kiang/elections](https://github.com/kiang/elections) \- 2014 所有選舉資料平台，跟 [候選人政見專頁](https://g0v.hackpad.tw/SP93kHqeeFM) 有些相關性

比對了 "全國村里界圖102.05.21" 與 "單一年齡性別人口數 10304" ，發現了下面差異：
1.  臺中市龍井區(海) =\> 臺中市龍井區
2.  高雄市三民區 =\> (高雄市三民一, 高雄市三民二)
3.  高雄市鳳山區 =\> (高雄市鳳山一, 高雄市鳳山二)
4.  桃園縣蘆竹鄉 =\> 桃園縣蘆竹市
5.  新增 金門縣烏坵鄉 與 臺中市梧棲區
7.  少了 澎湖縣湖西鄉 與 澎湖縣白沙鄉


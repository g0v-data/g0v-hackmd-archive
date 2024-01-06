---
title: "1 月萌典松: moed8ct"
tags: event,moedict,hackpad
---

# 1 月萌典松: moed8ct

> [點此觀看原始內容](https://g0v.hackpad.tw/1-moed8ct)


時間：1/18 11am-9pm（歡迎遲到早退）
> 建議下次報名時新增「午餐算我一份（葷素忌）」check box，比較不會耽擱到 12:00 午餐時間
> [name=venev]

地點：[Bookshow.tw](http://bookshow.tw/traffic/) 基隆路一段 141 號 6 樓之 7（捷運市政府站步行三分鐘）
名額：35 人（[報名頁面](http://g0v-tw.kktix.cc/events/moedict-1-18)）
內容：比照[前七次萌典松](https://g0v.hackpad.com/8-moed5ct) ，採「併松」模式舉行，歡迎 g0v 各大小專案加**萌**參加。
費用：採量力而捐、自由贊助方式。如有剩餘，捐給下次黑客松。
直播：[https://www.youtube.com/watch?v=IZrsVQSL0ds](https://www.youtube.com/watch?v=IZrsVQSL0ds)
活動守則：[https://g0v.io/coc](https://g0v.io/coc)

流程：
- 11:30 專案、想法簡報介紹
- 12:00 自介、午餐、分組意見交流
- 13:30 十五分鐘短講
- 14:30 hack, eat, hack
- 17:00 第一次成果報告
- 17:30 hack, eat, hack
- 19:30 第二次成果報告

### 萌典相關開發項目

- 環境建置：加速 make offline 的時間
    - 接著 ly 的進度做好了 (572479f0)
- 環境建置：以阿美語 moedict-app 為例
    - miaoski + au 做了初步，在 docker hub miaoski/moedict_amis 繼續努力
    - 目前的 apk (with new icon) 在 [http://audreyt.org/newdict/amis-20150118.apk](http://audreyt.org/newdict/amis-20150118.apk)
- 合併 webpack branch，加上新的筆順動畫系統
    - 由 ly 遠端完成!
        - react-zh-stroker 已加入 deps （尚未進入 view.ls/main.ls）
> working on it XD
> [name=caasi H]

- [新台語運動](https://g0v.hackpad.tw/moed7ct-taigi-neologism)雛形開發（也許先做靜態的 [mockup](https://moqups.com/liz462/IMYHBVi5)，再整合到萌典界面中）
    - pm5 接坑，畫坑形中
    - 相關的：查不到詞時，跳入「建立新詞」界面

### 短講

- 談談「‧」間隔號（董福興）[zh-req上的討論](http://lists.w3.org/Archives/Public/public-zhreq/2014Dec/)
投影片：[middot.xul](https://www.dropbox.com/s/0a082odt26u1669/middot.xul?dl=0)（請用Firefox加上[Remote XUL manager](https://addons.mozilla.org/zh-tw/firefox/addon/remote-xul-manager/)套件開啟Local權限後就能看）

## 併松

> 歡迎把想做的專案/計畫列在這裡！
> [name=Audrey T]

超農域併松 [http://hack.g0v.tw/agriculture](http://hack.g0v.tw/agriculture)  (a0kman晚到，再請simon協助先開 <(_ _)>

~chewei>~
- [~古地名與災害~](https://g0v.hackpad.com/4rF7N2Ihf5r)
- [~地震災害列表~](https://g0v.hackpad.com/zEoZ8BiWkEE)
- [~NHK スペシャル震災 ビッグデータ~](https://g0v.hackpad.com/NHK--6R59i4HSsG8)

Liz>
新台語運動 [https://g0v.hackpad.com/moed7ct-taigi-neologism?r=0#](https://g0v.hackpad.com/moed7ct-taigi-neologism?r=0#)  （「系統概念」下有目前網站設計的概念）

Kirby>
- 今天簡報的題目
    - 全球飛機失事歷史紀錄整理, in geoevent format
        - Geoevent URL: [http://0media.tw/t/geoevent/](http://0media.tw/t/geoevent/)
        - List of Commercial Aircraft Accident
            - Wikipedia: [http://en.wikipedia.org/wiki/List\_of\_accidents\_and\_incidents\_involving\_commercial_aircraft](http://en.wikipedia.org/wiki/List_of_accidents_and_incidents_involving_commercial_aircraft)
            - Spreadsheet:
            [https://docs.google.com/spreadsheets/d/1weTyy3X52QginfNbrSmxjR8WpsAEgJSRjzzqBJ8RaXk/edit#gid=615981805](https://docs.google.com/spreadsheets/d/1weTyy3X52QginfNbrSmxjR8WpsAEgJSRjzzqBJ8RaXk/edit#gid=615981805)
            - Result:
                [http://0media.tw/t/geoevent/widget/?src=1weTyy3X52QginfNbrSmxjR8WpsAEgJSRjzzqBJ8RaXk&color=default&ratio=20](http://0media.tw/t/geoevent/widget/?src=1weTyy3X52QginfNbrSmxjR8WpsAEgJSRjzzqBJ8RaXk&color=default&ratio=20)
- 其他可能的題目
    - 台灣人口統計資料整理（初步盤點成果 [https://g0v.hackpad.com/xqnTZmdXJW5](https://g0v.hackpad.com/xqnTZmdXJW5) ）
    - 公眾人物關係圖

mrorz> [Political Promise Tracker](https://g0v.hackpad.tw/-Political-Promise-Tracker-4a31UkdBItq)
從 1 依序做到 5 ，可能只能做到 3 xd
    - [x] Livereload to make developing a happy process
    - [ ] Combine React.js mockup with mock data directly in React
    - [ ] Add React.router
    - [ ] Add Flux
    - [ ] Move mock data into in-memory database, serve from API.


## 紀錄

au> 開場
tkirby> [http://0media.tw/t/geoevent/](http://0media.tw/t/geoevent/)
- prototype demo
- 待辦：空難事件整理（八百筆），已開試算表，需要短名稱、死傷人數 parser
mrorz> mobile first web of  [Political Promise Tracker](https://g0v.hackpad.tw/-Political-Promise-Tracker-4a31UkdBItq)
- 智利的智能公民團體做了  [http://deldichoalhecho.cl/](http://deldichoalhecho.cl/)  、澳洲 abc news 推出[視覺化時間軸](http://www.abc.net.au/news/2014-07-27/75-million-to-increase-employment-participation-promise-check/5527164)將把自家的政治新聞脈絡串起來。 Political Promise Tracker 想做的則是crowdsourcing 版本的 promise tracker。
- Task 1: 看到新聞稿，可以新增政策的新聞來源
- Task 2:評定完成度
- 目前已有前端 mockup，後端 api 建置中
miaoski> 阿美語萌典坑: App, 阿美法語典
liz> 任何台語問題可以取得解決方式的網站
- 外來語進入語言當中，是一個約定俗成的過程，所以可以投票來加速過程的進行
- 新的講法可以寫「我要提供講法」，可以錄音把聲音放上去，再轉寫成台羅
- 需要：UI、UX、Mockup

13:37 短講時間
bobbytung > 談談「·」間隔號（董福興）[zh-req上的討論](http://lists.w3.org/Archives/Public/public-zhreq/2014Dec/)

17:05 成果報告
tkirby> 空難事件整理進度到達 30%，視覺化成果良好，其他打算下次大松繼續集氣
au> 阿美族萌典 Android Build 成功，但是 App 圖示不知道要放什麼... 之前用的單字圖示，「阿」好像是阿拉伯語，「美」好像是美語... 徵求設計想法
 How about the first picture on wikipedia?
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_65acb4b28badd994aa96c5d05ed00ccd)
[http://zh.m.wikipedia.org/wiki/File:Amis\_Alofo\_Pattern.svg](http://zh.m.wikipedia.org/wiki/File:Amis_Alofo_Pattern.svg)
> 小圖 (32x32) 好像會有點糊... 或是取中間的八卦部份？ Demo:
> [name=Audrey T]


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f407ad5eceffc3ce9da1f550fd61ad3f)
> 幫截: 128x128 + 64x64 + 32x32 + 16x16
> [name=Kirby W]

> ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7490af8889b43fc6ebc7460c88a8664e)
    
> [name=Kirby W]

> kirby++
> [name=Audrey T]

> 很漂亮哪 +1
> [name=venev]

> 現在才發覺其實好像還是有點糊, 重做了一遍 ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_30d5fa0441be2fa9eccddc0dea4aa786)
    
> [name=Kirby W]

> 族人 Wan Yi Mikasa 也設計了一個 App Store 用的大圖：
> [name=Audrey T]

> [https://play.google.com/store/apps/details?id=org.audreyt.dict.moe_p](https://play.google.com/store/apps/details?id=org.audreyt.dict.moe_p)
> [name=Audrey T]

> ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cbcdcec51e6b9782bea85c9045099920)
    
> [name=Audrey T]


19:35 成果報告 #2
au> gugod 新寫的拼音輸入在 mobile app context 的 demo（iOS/Android 即將更新）、阿美語 app 的新 icon，以及新 merge 的 webpack hot module replacement。
mrorz> [PPT 政治承諾追蹤網](https://github.com/g0v/PPT) 從靜態 mockup 變成 isomorphic loopback flux react app 了（而且也有 webpack hot module replacement!）
> 收播+晚餐，感謝大家~
> [name=Audrey T]


21:30 李維斌教授對台北市開放資料工作的初步想法
- 1 月底資料庫盤點回報
    - 包括所有的狀況和困難（法規及技術）
    - 有多少算多少
        - 重點是讓公務人員氣氛產生榮譽感
- 已有網址之資料，改為公開資料
    - 使用 CC BY 之類，容許加值的開放授權
    - 既有授權文字，例如社會局: [http://www.dosw.taipei.gov.tw/ct.asp?xItem=90621212&ctNode=75449&mp=107001](http://www.dosw.taipei.gov.tw/ct.asp?xItem=90621212&ctNode=75449&mp=107001)「(2)本網站上之資訊，可為**個人或家庭非營利**之目的而重製。」
        - 找到來源（研考會？），取得新的文字範本
        - 或是以行政解釋方式更改授權
- 局處長教育訓練，等 EY 宣教會之後再排時間
    - 鎖定特定局處，由價值較為明顯的局處開始
    - 建立各局處對資料要求的回應管道
- 3 月左右發起黑客松
    - 以開放資料為主題，但不限定使用台北市的資料
    - 題目是「對台北市民提供服務」

## 食物總務

飲料：咖啡、紫蘇梅汁、可樂
午餐：達美樂披薩
茶點：蛋塔、蒜味磚塊、Donuts
晚餐：開飯川菜
本次萌典松結餘 5,445 元（[收支明細](https://docs.google.com/spreadsheets/d/1JLdXfMQops2lBsgwpnQHE_L_S4yLi3yB4Y4yRuaYBd4/edit?pli=1)）


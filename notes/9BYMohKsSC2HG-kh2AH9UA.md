---
title: "立委投票指南-Iris"
tags: hackpad
---

# 立委投票指南-Iris

> [點此觀看原始內容](https://g0v.hackpad.tw/CaCooXMs28F)


## Android APP 提案

原本Android APP 專案: [https://github.com/HMW/g0v-twly-voter-guide-android](https://github.com/HMW/g0v-twly-voter-guide-android)
網頁版: [http://vote.ly.g0v.tw/](http://vote.ly.g0v.tw/)
Trello : [https://trello.com/b/laylhlfd/legislative-yuan-log](https://trello.com/b/laylhlfd/legislative-yuan-log)  (每周進度、代辦事項)
指導者 : 吳海明 (HMW)

email 討論過程節錄重點如下:u
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
_6/14  Iris_
    主要希望在這個app中可以多提供一些圖表的顯示，
    像以下這些統計的圖表 :
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_bb93bb59048cca2728e84a113695075d)


    還有找立委的部分:
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cbde572d5f8aa21e3905562349f729d7)


    目前覺得以上兩個部分手機使用者較常用到，
    感覺不適合放太多文字資訊在app上 (ex: "找法案")。

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
_6/14 HMW :_

    我先大概跟妳介紹一下我想要做的內容主要會分兩大部份
    分別是 **委員** 和 **議案**
    委員部份就是提供**基本資料**、出席率、政治獻金收入等等
    議案部份除了基本資料就是再來就是些表決紀錄
    以上除了底線標示出的部份   其他都還沒做 XD

    下面前兩張圖是和我公司裡一位負責做 art 的同事討論後
###     大概的UI的長相

    pic1 各個 fragment 裡的 UI
    pic2 navigation drawer
    pic3 則是現在唯一有內容的 **委員-基本資料** 頁面的長相
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c889a055bed27bd0083f46ae26a067e7)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_31fdedee1e1b266d6b831619f1190208)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b2bccbaeb25b2ad2ec3bae15b99d1379)

    然後我"個人"的想法
###     （project goal）

    會做這個 app 其實並不是要取代立委投票指南的網頁
    反而比較像是要推銷
    希望能夠在這個 app 提供一些立委投票指南的基本功能
    如果還想要了解一些更詳細的資訊
    再用電腦到網頁去看
###     （target user）

    然後這個 project （目前）唯一也是最重要的時間表就是要能夠在年底選舉的一個月前完成  ,目標使用者就是所有要投票的人

    所以因為主要是想要
    1)推廣立委投票指南 同時
    2)使用者又是所有成年的 android user
    這個 app 除了還要有一些例如從黨籍、縣市、選區等等的方式來搜尋這些資訊的方式
    我"個人"是覺得相較於能夠提供多少資訊，有好用簡潔的 UI 會是最重要的
    這週主要的工作會先和 art 討論一下看能不能先將 委員-基本資料 這頁的 UI 生出來

    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
_6/14  Iris _
        HW，謝謝你詳盡地提供資訊，我還滿贊同你的想法。 :)
        _"這個 app 其實並不是要取代立委投票指南的網頁，反而比較像是要推銷"_

        我對於UI設計可能比較沒有經驗，但大概知道使用者喜歡怎樣的操作畫面, 也許我們可以[參考這篇](http://www.inside.com.tw/2014/06/12/the-difference-between-single-function-and-multiple-functions-app) 來做設計。

        關於時程的部分，我這邊 6/20 前要先完成暑假的提案，
        我會希望暑假可以幫忙完成 :
###         （提案內容）

    1.  實做 app 委員部份的出席率、政治獻金收入等等圖表、數據資料呈現.  (應該可以做滿久  因為可能還要熟悉一下後端資料的抓取等等)
    2.  一起討論其他頁面 UI 設計的部分，規劃如何更 user-friendly.
    3.  可以看進度再做增加....

    希望我的投入能一起讓這個 project ，在年底選舉的一個月前完成上架，
    也非常謝謝你，希望之後合作開心 :D
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
_6/15  HMW:_

    clkao(高嘉良) 應該算是 **立委投票指南** 整個 project 的指導者
    johnny 則是 **立委投票指南** 網站的主要(唯一?)開發、維護者
    雖然他們兩位都異常的謙虛
    但無法否認他們都算是我個人在這個 android project 的指導者
    所以不論是**開發經驗**或是**相關的背景知識**他們絕對都比我要來得豐富
    同時
    就算妳指導者掛上他們的名字
    我也還是會盡我所能的幫妳完成這個比賽 這妳可以放八百萬個心 XD
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
_7/14  HMW:_

1.  之前妳有提到對 UI 的設計比較有興趣,  所以如果妳對於這個 app 的 UI 有任何的想法,  或許可以先簡單的畫一些流程圖(註1),  另外,  官方的文件也可以先翻一下(註2), 我覺得寫得相當完整也有很多圖片, 和 iOS、Windows 也有不小的差異
2.  我在這個 project 是用 Android Studio 開發,這個 IDE build 出來的 project structure 和 Eclipse 有點不太一樣,所以想請妳先研究一下如果要在 Eclipse build Android Studio 開的 project, 我還需要提供些什麼資訊或事先做什麼準備

註1 [http://developer.android.com/design/patterns/navigation.html](http://developer.android.com/design/patterns/navigation.html)
註2 [http://developer.android.com/design/index.html](http://developer.android.com/design/index.html)
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
_7/16  Iris:_
如果我也使用Android Studio 開發，對我們的整合是不是比較方便?

我目前有查了一些相關資料，對於簡單的專案轉換是OK,
但對於一些較複雜有引用外部的framework專案，可能會遇到比較多問題
我的想法是，如果我也改用Android Studio，雖然要再花點時間熟悉環境，
但之後我們比較不會有整合的問題，可以專注在開發上

我把github 上的 Android Studio 專案抓下來後，
找到方法把它成功移植到 Eclipse 了!!
方法在這裡: [http://stackoverflow.com/questions/16745793/how-do-you-open-an-android-studio-project-in-eclipse](http://stackoverflow.com/questions/16745793/how-do-you-open-an-android-studio-project-in-eclipse)
現在程式能正常地在我手機上面執行，所以目前移植這部分應該是ok的，

話說我也有載Android Studio 來用，但一直遇到
Failure \[INSTALL\_FAILED\_OLDER_SDK\] 的問題，目前還解不開><

接下來我也會研究一下UI設計的部分。
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
_7/17 HMW:_

在接下來這兩個月的實習中, 除了開發這個 app 之外,
我還會希望妳多學習 & 了解一些合作開發專案時應該要注意的事情.
以這次要求妳先研究 migrate 到 Eclipse 可能會遭遇的問題為例,
因為我們不可能去限制其他參與者使用的 IDE,
所以我們隨時都要確定在 github 上的 code 都能夠順利的在各個 IDE 上執行.
而這部份我之前比較偷懶,
設定好 git ignore 之後並沒有真的用 Eclipse 再開過一次,
所以感謝妳 & Good job！
也所以,
這和妳個人想要用那一套 IDE 來開發是沒有任何關係的.

其他針對這兩個月更詳細的規劃就等到週末再一併跟妳解釋,
也期待妳分享對 UI 的想法！

ps. 這個專案我有設定是 for Android 4.0 up
所以 Failure \[INSTALL\_FAILED\_OLDER_SDK\] 的問題不知道和這個有沒有關係
妳有抓 Android 4.0 (API 14) 的 SDK Platform 嗎？
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
_7/20 Iris: _
這幾張照片是我畫的兩個頁面. :)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_218a80714267f36187325544ce4d0b27)
> 下圖中的黨名也許可以用各黨黨徽的圖案取代
> [name=許雅婷]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_57448979163c98114aaecff43ef21561)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9cd280e4f5a0c1c72ac9c4ffeb75e68f)
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
_7/24 HM:_
我們之前用的 crash log 是 acra,
[https://github.com/ACRA/acra](https://github.com/ACRA/acra)

然後立委投票指南目前已經可以使用的 api 都列在這邊,
[https://twly.herokuapp.com/api/](https://twly.herokuapp.com/api/)
ex: 在網址加上 legislator 就能看到委員們的基本資料 [https://twly.herokuapp.com/api/legislator/](https://twly.herokuapp.com/api/legislator/)

所以可以先看一下想做的部份是不是已經有 api 可以使用了,
如果碰到在網頁上已經有的資料卻還沒有 api 可以使用的也可以先記起來,
我再去跟網站的作者反應
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
_7/26 Iris:_
**crash report 的部份**，我有個在KKBOX工作的好友推薦用"[Crashlytics](http://try.crashlytics.com/)" 這套 plugin.
我已經將 Crash report 的程式碼加到專案中，
[https://github.com/irisshu/g0v-twly-voter-guide-android/commits/master](https://github.com/irisshu/g0v-twly-voter-guide-android/commits/master)
我也有發出 Crashlytics 的邀請，你同意後應該就可以看到目前 app 的分析。

這就是那個有趣的App  : [Android UI Design](https://play.google.com/store/apps/details?id=com.boopathy.raja.tutorial&hl=zh_TW)  可以下載來玩玩看!
我有點想把它的"Arc Menu" 加進來，但目前還沒想到要應用在哪裡XD
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

_(經過一連串  pull request 與merge 的學習...)_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
8/7 Iris:
我有在profile page 加上ScrollView ，這樣資料太長時就不會看不到 :)
你之前想嘗試的"上下左右移動的方式"應該不會被影響到，
還是可以嘗試看看.

另外，spiderWebChart 旁邊的字好像有點太淡太小 XD
我下一步會把它弄得清楚一些，或讓整個畫面可以透過"雙指"來縮放 :)

我有發出 pull request，再麻煩你幫我看一下，
(其實我不太清楚你merge 完後，我要不要再把你那份 merge到我這邊? >< )
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
8/8 HM:

Git 我自己的使用方式大概是這樣,
1.  從本機端的 develop ( or master) 開一個 feature branch (ex:       feature/profile\_scroll\_view), 並在這個 branch 開始開發
2.  feature 完成後發 pull request, merge 到 Github 的 develop
3.  將 Github 上的 develop pull 回本機端的 develop (or master)
也就是 不在 develop (master) 上開發 並 保持 Github develop 和本機端同步
給妳參考
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
8/8 Iris:
最新頁面 :
(雷達圖數值尚未放入真實數據計算 )
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0bb99a46e3d5ac0be6e0a48c3cd97257)
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
8/20 Iris:
目前立委個人資料頁面，已可以將真實數據放入紅色雷達圖中，藍色的平均數值，還在蒐集資料中
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c1b449ab680693fdba50308d3a5aaff9)

APP 首頁: (照片來源: [http://farm9.static.flickr.com/8287/7850852366_b4f8229494.jpg](http://farm9.static.flickr.com/8287/7850852366_b4f8229494.jpg) ，之後會詢問看看作者是否願意授權給我們，如果不行，會再找其他圖片^_^)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_01a583188cdbd5214d30d0a593233066)
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
(感謝  Angie、Darlene、Victor、奕祺、HM 共同討論)
8/27 Angie整理 :

【做什麼】
專案想達成的目標是什麼？
1\. 確定使用者跟使用目的
比如說現況是有一部份人想理性投票沒工具，有一部份人不知道投票要理性，有一部份人根本不知道投票要幹嘛。
那我們想要讓『想理性投票的人』有工具可以用？或是讓『不知道投票要理性的人』了解理性的重要性？
確定目標之後就會有使用者調查方向、設計方向跟行銷方向。
2\. 功能的管理 / 數字管理
假設把目標訂在讓更多人知道怎麼選舉，也許可以為這個app訂一個數字目標，比如說Facebook like數比割闌尾粉絲頁多10%，或是50歲以上使用人數至少要有1萬人（Google Analytics有連動到分析）。這樣未來在調整功能時，可以清楚知道哪些功能的確會增加使用人數。
【如何做】
1\. 列出『理性投票』的因子
2\. 篩選目前資料庫中可以做到的因子
3\. 技術實現：目前以Android app為主，採open source，未來可以往網頁或是Facebook app發展。
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
2014-08-28
From HMW：
下個階段要做的會是幫使用者挑出和他立場相近的候選人
我目前想到的做法會是在 show 出候選人之前
會先列出幾個 **熱門 & 重大** 的議題 ( ex: web上表決裡的熱門議題)
讓使用者選擇 自己贊成 / 反對的項目 or 設定不同權重 ( 這部份我們還沒決定 )
不過現在的困難點就在
我要怎麼樣才能篩選出和這個使用者立場相同(近)的候選人呢?
以核四為例
立委投票指南的 web 上和核四相關的表決光是第八會期就超過 20 項
所以不知道你有沒有什麼建議的方法
能夠讓我們能夠從這幾**重大的議題**再去對應到幾個特定的**表決** 然後讓我們再去幫使用者挑出**相同(近)立場的候選人**
    johnny: 如果要從某議題中挑出特定表決，就須有"人"介入挑選是哪個表決，怕會影響客觀，當時的想法是，系統一樣列出含有該關鍵字的所有表決，由使用者決定要回答那些表決，每回答一個，匹配結果就隨之變動，但device畫面較小時，不知該怎麼呈現該議題所有表決??
    我這邊可以出api，client給我一串\[{"vote\_id": 1, "decision": 1}, {"vote\_id": 2, "decision": -1},...\]，server回最匹配的一串立委id
    HMW: 考量到 device 的螢幕尺寸，加上又有許多不同的議題，我也不覺得在 device 上列出每次表決的結果是個好的方式。我很贊成應避免人工介入，所以我是在想不知道有沒有辦法綜合參考每次的表決而得到(算出)各別委員對該議題的立場。
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
9/6 Iris:
可以選擇選區
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_dc87447011d21bf31b04c02a314d32ad)

9/14 Iris
準備將政治獻金的部分加入:
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1f5ca39b7ae185205ff7eb1d2cbb2612)
詳細的最新進展，請參考 trello
[https://trello.com/b/laylhlfd/legislative-yuan-log](https://trello.com/b/laylhlfd/legislative-yuan-log)
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
9/20
原本美美的圓餅圖:
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_32112b62d66a7b45724c05f5bc2ce9e6)

放真實數據之後就崩潰了: (正在修正或換library 嘗試中)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_36ef1bd5a2f6f4f3e4a9df6b2cef94a4)


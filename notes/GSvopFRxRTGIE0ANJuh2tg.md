---
title: "525 萌典併政治獻金松：實作提案"
tags: event,CY 零時監察院,hackpad
---

# 525 萌典併政治獻金松：實作提案

> [點此觀看原始內容](https://g0v.hackpad.tw/NxMrvI4uYcP)

[5 月萌典松: mo4dict](https://g0v.hackpad.tw/926nwUKC90j)：「開放政治獻金」要作什麼？有興趣參加者，請到 [KKTIX 報名](http://g0v-tw.kktix.cc/events/moedict-5-25)

## 攻城獅

OCR 功能新增或 debug；認領機制強化（[Finjon Kiang](https://g0v.hackpad.com/ep/profile/G4yGGowBe3x)  ~好像~在台南？）
- 進度視覺化（其實列表化或試算表化就好了）
    - 目前有[第八屆立委伐木任務包](https://drive.google.com/folderview?id=0ByObdQAbysqeQUE0UjMtUzVNLTg&usp=sharing)(13包)、[第七屆立委伐木任務包](https://drive.google.com/folderview?id=0ByObdQAbysqeM2tTekQ3RjI4QkU&usp=sharing)(14包)、[2012蔡英文伐木挑戰包](https://drive.google.com/folderview?id=0ByObdQAbysqeVG13eGhHNEI0Z2c&usp=sharing)(9包)，[99年五都直轄市議員](https://drive.google.com/folderview?id=0ByObdQAbysqeWTlLdl8wSHBnNU0&usp=sharing)(31包)，四個副本。
> [https://drive.google.com/file/d/0ByObdQAbysqeOVE2TnY2M1VuRm8/edit?usp=sharing](https://drive.google.com/file/d/0ByObdQAbysqeOVE2TnY2M1VuRm8/edit?usp=sharing)
> [name=Nicemaker]

> 可以將所有的擬參選人大頭照排好，遮住整個台灣，用透明度來表示「資料透明度」，未認領的是0.9，已完成是0.1
> [name=Nicemaker]

> 意思是在那些笑臉背後，到底藏了多少東西，擋住島嶼的光芒（好文意阿，請求美術獅救援）
> [name=Nicemaker]

> onmouseover可以將說明文字秀出「名字、進度」
> [name=Nicemaker]

> 當所有文件完成，就代表（至少第八屆立委）的黑幕已經被打開了
> [name=Nicemaker]

> 我到覺得不需要大頭照，密密麻麻都是人頭有點噁(真的，而且笑的都很惡心XD)
> [name=Moon C]

> 可以是黑幕，當滑鼠移過去的時候才會跳出相關資訊
> [name=Moon C]

> 透明度的IDEA很不錯!!可以顯示在上面，或是顯示目前需要的兵種(?
> [name=Moon C]

> 未完成的時候台灣會很像日蝕感覺(
> [name=Moon C]

> 我發現進度應該可以很快@@
> [name=Nicemaker]

> 感覺進度的部分最主要的應該要顯示目前的階段工作需要做什麼，像是目前需要調查兵或是說已經開啟鄉民的任務（雖然鄉民任務應該都秒殺哈哈
> [name=Moon C]

> 我正在打新的SOP，一個小時候可以幫忙美編嗎？
> [name=Nicemaker]

> 呃啊我現在才看到，不好意思＠＠這一兩天如果有空可以幫忙
> [name=Moon C]

> 新的sop也是在sop那個pad嗎？？
> [name=Moon C]

> 新的參戰sop [在這裡](https://docs.google.com/document/d/1zfBUMYoJNYj7RT_Ka8uTVoxlQyuaFuyQnfLDn9GFois/edit?usp=sharing) 還有[列印SOP](https://g0v.hackpad.tw/-SOP-dmcLmLXxXyw#:h=先-Copy-Paste，請原作者再整理)(在最下面)
> [name=Nicemaker]

> 問一下喔，我要做成文宣版還是網頁版(希望不要....我生不出來QQ)
> [name=Moon C]

> 有總比沒有好XD  
> [name=Nicemaker]

    - 列表：依選舉分類、時間排序
    - 每個任務包進度（給鄉民看的）
            1.  已認領（並需處理「認領後久未完成」的戶頭）~已完成監院影印、掃描圖檔並上傳
> 在追蹤上可能會併成一步，因為目前列印、掃描都外包給單一認領者，等到上傳後才能確定是否如期完成
> [name=venev]

            2.  _（3-1 已完成切豆腐、放出任務）完成OCR_
            3.  已確認可輸出
                1.  →用監院的總額合計確認，[這裡有](http://sunshine.cy.gov.tw/GipOpenWeb/wSite/sp?xdUrl=/wSite/PoliticAccount/PAQuery.jsp&ctNode=353)
                2.  還需要一個API把支出跟收入抓好總合，因為現在要假設資料是亂的（未分收支＆科目）
                3.  [那邊](http://sunshine.cy.gov.tw/GipOpenWeb/wSite/sp)有各科目總和，所以要一個API抓『選舉－人－各科目總和』來驗證數字欄是否正確
- OCR  批次功能
> 我發現鄉民速度遠大於影印速度= =  2小時的資料100分鐘就key完了...
> [name=Nicemaker]

    - 先大量篩選出「空白」「是」「匿名」「各項科目」
    - 大量校對功能：從「+1」開分流，一次輸出一頁為確認→改作業
> 這兩天人在台北，也許晚上有空可以來個松前松？找個咖啡店聊天？
> [name=Finjon K]


- [ ] 求救，監察院[這裡](http://sunshine.cy.gov.tw/GipOpenWeb/wSite/sp) 的資料Ronny只抓了「許可設立」那邊的List出來，而另一欄「會計報告書」下面有很多word檔，裡面格式都一樣，可以知道每一個帳戶的收入(支出)科目小計&總額，但 [立委投票指南](http://vote.ly.g0v.tw/) 好像只抓了第八屆立委。可以幫忙把所有的word檔轉成cvs檔嗎？我沒有開發環境QQ  只能一個一個下載....這樣才能核對目前ORC的數字是對還是錯。
> 因為里長有八成最後申報的收入跟支出都是0元。而在監察院現場要發現這件事要花薪台幣20元。而里長帳戶約有1000戶...
> [name=Nicemaker]


## 美術獅

人物設定之美術呈現：
- 調查兵團（感謝 [Moon Chang](https://g0v.hackpad.tw/ep/profile/s6B8KoJNpjo) 提供 SOP 宣傳圖）圖檔已上傳在此 [https://drive.google.com/](https://drive.google.com/#folders/0B0jawSySD8E3RUExTnVQdlhnMjQ)[#folders](https://g0v.hackpad.tw/ep/search/?q=%23folders&via=NxMrvI4uYcP)[/0B0jawSySD8E3RUExTnVQdlhnMjQ](https://drive.google.com/#folders/0B0jawSySD8E3RUExTnVQdlhnMjQ)
- OCR 大軍？鍵盤柯南？陽光監察娘？
    - 第一版監察娘 / 監察姐（ly: 御姐嗎） / 監察女王，左肩是眼神銳利的老鷹，左手是書（還是賬本？）
    - 第二版右手可能持手電筒（照亮）、狗鍊（管好你的政治人物），看子龍靈感怎麼發揮

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4772bd038dd43d9955c1827f5360f4f9)
塗色很隨意...


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1988423a7ba96cd60f1d54f6490e6dc4)
政獻娘在看你，他現在很火
好像更冷豔了（抖
> 在 [萌典松併松](https://g0v.hackpad.com/5-moed4ct--926nwUKC90j) 上拜見了超忙碌的 子龍設計師 [Moon Chang](https://g0v.hackpad.com/ep/profile/s6B8KoJNpjo) 的監察娘大作（上圖），由於當時現場也歡樂的討論起 傲嬌屬性+女王屬性，為了減輕設計師的負擔（冠冕堂皇的藉口），所以順手把最近看到類似概念的素材貼了上來（如下圖），純提供給設計師參考用，絕不是為了滿足私欲（遮臉），更無任何不良意圖。（越描越黑）
> [name=NewCliCker]

    - 監察女王元素_靈感參考_：IRC記錄 [http://logbot.g0v.tw/channel/g0v.tw/2014-06-17#29](http://logbot.g0v.tw/channel/g0v.tw/2014-06-17#29)
        [#這樣子的包青天沒問題嘛](https://g0v.hackpad.tw/ep/search/?q=%23%E9%80%99%E6%A8%A3%E5%AD%90%E7%9A%84%E5%8C%85%E9%9D%92%E5%A4%A9%E6%B2%92%E5%95%8F%E9%A1%8C%E5%98%9B&via=NxMrvI4uYcP)？ [https://i.imgur.com/euDK1cV.jpg](https://i.imgur.com/euDK1cV.jpg)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_614ab9d3f0a03a1754f9b9976f3ed5c0)
[http://i.imgur.com/n7fJDYY.png](http://i.imgur.com/n7fJDYY.png) 18+ 限制級梗（不解釋） 慎點
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_af9b27dc9bc4d2acdc07ce60eb961399)

- 劇本「大挖礦時代2014」全新副本：小豬撲滿、五都議員、利委傳奇、利委傳奇二。
> 那天我會去，有想法可以一起來角色設定什麼的～！
> [name=Moon C]

> 幫視覺化想辦法吧QQ　結合進度＆宣傳
> [name=Nicemaker]

> 喔耶～`
> [name=venev]

> 當天要吃中午喜酒@@ 五點到可以嗎？
> [name=Nicemaker]


- Moon Chang 跳坑，幫粉絲專頁（資料解讀、爆點文）製作 infographic

## 沒有人

討論專戶查詢、列印費用是否適合群眾募資？（扯到錢就好頭大啊）
- 新SOP！：[http://goo.gl/qbA8gD](http://goo.gl/qbA8gD)
> Nicemaker ++ will merge into the original file after Ronny's confirmation.
> [name=venev]

- 幫調查兵團省列印錢：縮小合併列印
    - 我有空再去試試A3行不行？答案是：不行。
    - **_但__一頁A4可以印9頁！_**
- 直接到 [這裡](https://g0v.hackpad.tw/-SOP-dmcLmLXxXyw#:h=先-Copy-Paste，請原作者再整理) 繼續
- 跟新[任務包](https://docs.google.com/document/d/1XGsUcZZBOzSI4n8YDe0ycho6feZPRP9J9frtBRrW0BI/edit?usp=sharing)
> 2014/7 更新：3x3 OCR 鄉民反映切歪、辨識度不佳，共識退回 2x2
> [name=venev]



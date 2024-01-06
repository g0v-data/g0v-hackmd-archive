---
title: "氣候選戰 Vote for Climate"
tags: g0v idea pool,環境,hackpad
---

# 氣候選戰 Vote for Climate

> [點此觀看原始內容](https://g0v.hackpad.tw/4ac9ap7zhrn)

> 如果是留 mail 的話請避免使用超連結。 ( hackpad 會對超連結加上 http://
> [name=lanfon]

> 善用==強調==的hackpad編輯功能( Ctrl + E )，參考：[hackpad 超新手教學](https://g0v.hackpad.tw/FPwfgwsjwdV)
> [name=lanfon]

> hackpad id 建議使用 英文 ，使用中文會無法 tag ( @ +id )
> [name=lanfon]

> 已先加進 idea pool 的 tag.
> [name=lanfon]

> [lanfon](https://g0v.hackpad.tw/ep/profile/FhF2TCnIycW)謝謝建議！我們對hackpad不是很熟還請多多指教...
> [name=Yingfan]

## 徵求協作者

發起人/拋磚人：陳膺帆(infantchen@gmail.com)、何沛怡（a41081legopeiyi@gmail.com）、悲羊
分工與成員
- [x] NeedsDesigner: 需要介面設計 [Ginger Chen](https://g0v.hackpad.tw/ep/profile/vq24JlPGJy5)
- [x] NeedsData: 需要資料（TWYCC提供）
- [ ] NeedsTech: 需要技術支援（程式、架站 etc)
    - [ ] 前端網頁架設
    - [ ] 後端資料庫建置

因為我們的網站需要比較多, 有前輩建議我們先從前端開始, 我們現在有些資料, 想請前端工程師先幫我們做出頁面, 之後再接後端。

## 專案簡介

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_495987a39f79f62e0358c638bab6c7c7)

### 專案說明


**發起人/拋磚人**：[台灣青年氣候聯盟 TWYCC](https://www.facebook.com/rocktwycc?fref=ts)
官方網站 [http://twycc.org.tw/](http://twycc.org.tw/)


1.  希望發起「氣候選戰」串連全台各校監督在地候選人之「環境政見」，在各校招募氣候選戰小組，議題由在地行動發起人自行設定(當地所關心的環境議題)。
2.  以網路平台做訊息、資源串連，提昇公民對於氣候環境政策之意識。
- 「擴大」希望讓更多人看見更多環境政見，鼓勵大家使用投票，決定環境未來
- 「培力」嘗試串起各校的環境青年據點
- 「政策」喚起大家對更多氣候政策（調適＋減緩）的重視

詳細Proposal：
[https://docs.google.com/document/d/1S4mrxlqBvZSXUV95XLbG8lPAA_R2LGwRVb9XXaaaBrs/edit](https://docs.google.com/document/d/1S4mrxlqBvZSXUV95XLbG8lPAA_R2LGwRVb9XXaaaBrs/edit)

## 目標與功能（什麼問題，要如何解決）

### 預定功能

- 社團以及在地環團行動串聯交流平台。
- 查詢相關環境行動的最新動態
- 監督候選人針對環境表態
- 公民監督相關新聞分享
> 有沒有想提出的議題？空氣汙染？氣候變化帶來的災難？之前g0v有作過環境儀表板有空污和雨量資料可以參考 [http://env.g0v.tw/air/](http://env.g0v.tw/air/)
> [name=ipa c]

> 我們目前的想法是，各地的議題由在地環保行動者自行提出，但主要還是與氣候變遷、環境議題相關。這個網站的功能之一是可以讓使用者自行新增和編輯內容，所以各地方會針對自己的區域選出最有利的行動策略與關注議題，所以我們只要建立讓大家都可以上傳行動、資料平台就可以了
> [name=Chui-Hsien L]


### 預定使用者

- 環保團體
- 在地氣候選戰小組
- 選民

## 要解決的好多問題

前端網站設計
後端架設及資料庫建置
上傳者的Facebook粉絲專頁貼文同步
網站上的貼文有Facebook分享功能
建立使用者用Facebook或Google登入網站的系統

授權方式
MIT, CC-BY

專案目前狀態：**要生網站!!**

網站架構：
各縣市→

    行動(監督候選人表態)→
        發佈
            更新後續消息(ex. 選民在「市長給問嗎?」提出問題，候選人之後的回應)
    參加(提供連結)
        捐款(僅提供連結)

    候選人(如果有)→
        政見→列出各候選人對於各在地環境議題的政策及立場

    新聞→
    媒體相關新聞報導
    使用者的訪調、觀察和評論


## 實作細節（非技術背景可跳填）

協作工具
- github repo：[https://github.com/g0v/VoteforClimate](https://github.com/g0v/VoteforClimate)

進度與 to-do
> 僅供參考
> [name=ET B]

- [ ] product planning（recommanded procedure from justin lee / 李易修）
    - [x] strategy
    - [x] scope
    - [ ] structure
    - [x] wireframe
    - [ ] visual
- [ ] web front-end
- [ ] web back-end
- [ ] ui / visual design

### 頁面


1.  **最新活動 (首頁)**
2.  **活動列表 (顯示多個活動)**

3.  **活動內容 (顯示單一活動下的PO文)**
4.  **候選人政見比較 **
    - ex: 比較胡志強、林佳龍 政見
5.  **文章 (新聞分享)**
6.  **新增政見內容**
7.  **FB登入**
    登入only： 新增政見內容

###  表單內容


活動 (has many messages)
    1.  活動名稱
    2.  發起人
    3.  聯絡方式
    4.  cover photo
    5.  活動簡介
訊息
    1.  標題
    2.  照片
    3.  活動
政見
    1.  候選人
    2.  政見內容
新聞
    1.  標題
    2.  連結 (顯示圖片)

## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）

==wireframe:====[https://drive.google.com/file/d/0B7mNkeigw1U1eEVTWXZ2SWg3Rm8/edit?usp=sharing](https://drive.google.com/file/d/0B7mNkeigw1U1eEVTWXZ2SWg3Rm8/edit?usp=sharing)==

(1)是首頁，可以用三種方式(5),(6)來檢視，(1-1)有列表
(2)是一個議題(ex:松煙護樹)，在這個議題下面有更新的post
(3)是post詳細內文
> [Ginger Chen](https://g0v.hackpad.tw/ep/profile/vq24JlPGJy5)  我想這裡的候選人政見比較表該乾脆就改成一個按鈕，可以連到(6)好了
> [name=Yingfan]

> OK
> [name=Ginger C]

(4)是行動串聯地圖，可以知道你家周圍有哪些環境行動，概念是從這裡發想：
[http://nonukeyesvote.tw/action.php](http://nonukeyesvote.tw/action.php)
(5)是從各個區域來看在地所關注的議題，你也可以藉此了解你們區域所關注的環境議題有哪些
(6)是各候選人對於這個議題是否有任何政見或看法(上面橫的那列可以切換左右不同議題。ex:核能,雪谷纜車,火力發電....)
> [Ginger Chen](https://g0v.hackpad.tw/ep/profile/vq24JlPGJy5)我覺得可以再加一頁以候選人連結議題(6這頁是議題連結各候選人)
> [name=Yingfan]

> 是說, 候選人有關注過的議題, 都列在這一頁嗎？
> [name=Ginger C]

(7)關於我們(可以列出以加入氣候選戰的NGO和社團)

## TWYCC網站建構 V1


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_26618d2c024f9a64471a1cfceefda31f)


## TWYCC首頁


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8e6d963743432286ee7edff4db753e98)

最上跑馬燈處跑最新環境相關新聞。下面各圖示放主要專案最新資訊，點進去可連到專案頁面(2)（目前專案有水水一百、Vote for Climate、COP20、綠色企業、政策研究）、次要專案連結（COYTW、綠色氣候基金、IPCC）。頁面底端放友好夥伴LOGO連結（連到official website)和贊助資訊。另外頁面其他空白區可放追蹤我們FB、youtube等圖示連結。
```
youtube 是有專屬頻道嗎？需要放連結上來喔！
```
> [Ginger Chen](https://g0v.hackpad.tw/ep/profile/vq24JlPGJy5) 有專屬頻道→[https://www.youtube.com/user/TWYCC?feature=watch](https://www.youtube.com/user/TWYCC?feature=watch)
> [name=Doris L]

```
Ginger Chen  需要修改的內容如下
```
===============================================================
- [x] 最上排Link文字更改：拿掉候選人有話要說，環境專案改為活動企劃、新增最新消息和認識氣候變遷
> 這裏認知最新消息就是下方跑馬燈, 訊息目的重複, 所以暫時先拿掉
> [name=Ginger C]

> OK
> [name=Doris L]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d47df3533aefb282c91791504d371d8d)
===============================================================
- [x] 上排跑馬燈：在跑馬燈右下角增加最新消息或More...的字樣，點此連結就可以連到所有文章或新聞的頁面
> 目前想法是, 點圖就可以直接連結到文章和頁面 [Doris Lo](https://g0v.hackpad.tw/ep/profile/xfucBVUPzJP)
> [name=Ginger C]

> 原先以為點圖只能連結到該文章，但如果點圖就可以連結到所有文章頁面，同時看到該文章和其他文章link就歐給。
> [name=Doris L]

- [x] 跑馬燈右下角FB、Youtube那排：新增[Peopo](https://www.peopo.org/twycc)
> [Ginger Chen](https://g0v.hackpad.tw/ep/profile/vq24JlPGJy5) 可否在peopo那排幫我新增FB [https://zh-tw.facebook.com/rocktwycc](https://zh-tw.facebook.com/rocktwycc)
> [name=Doris L]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cd2bdf42582a8bcda862516cb281e614)
===============================================================
下面活動企劃：八個專案縮減為五個→
- [ ]  氣候行動
> 氣候行動 ＝ vote to climate ? [Doris Lo](https://g0v.hackpad.tw/ep/profile/xfucBVUPzJP)
> [name=Ginger C]

> 兩個不同，vote for climate是氣候行動底下的行動專案之一 
> [name=Doris L]



- [x]  政策研究
- [x]  COP
- [x]  活動資訊
> 活動資訊和專案, 應該是不同型態的資料, 為什麼想放在這兒呢?
> [name=Ginger C]

> 因為照上面的link把環境專案給為活動企劃，想把其他不屬於任何專案的活動例如擺攤合作或演講等宣傳文章都放在這裡
> [name=Doris L]

> 因為這資訊會持續變動, 應該放在上面最新消息比較好喔！ [Doris Lo](https://g0v.hackpad.tw/ep/profile/xfucBVUPzJP)
> [name=Ginger C]

> 歐給
> [name=Doris L]

 綠色工作(Green Job)
> 不是綠色工作坊喔~英文的(Green Job)也放上去這樣比較好懂，因為是從英文翻過來的
> [name=Doris L]

> OK~
> [name=Ginger C]

- [x] 可否幫我把政策研究和氣候行動放在最上面兩個，這兩個目前是最重要的活動企劃 [Ginger Chen](https://g0v.hackpad.tw/ep/profile/vq24JlPGJy5)

[ Vote for Climate](https://g0v.hackpad.tw/4ac9ap7zhrn)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_16abe08879f89dcf37f525afda461692)
===============================================================
- [x] 現在就能支持我們：新增更多捐款辦法字樣，還有捐款方式圖樣→
- [x] 超商代碼捐款（小七圖樣）、
- [x] ATM轉帳（ATM圖樣）、
- [x] PayPal
- [x] 是否也要新增TWYCC匯款帳號?【匯款帳號】 華南銀行信義分行  (008) 匯款帳戶：119-10-0076721  戶名：社團法人台灣青年氣候聯盟
> 目前想法是, 點擊ATM後可以出現以下訊息, 請幫我補充 ibon 訊息, paypal 會直接轉跳
> [name=Ginger C]

> ibon還在申請中，我盡量在這禮拜處理完
> [name=Doris L]


> ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9321830de8c97ef6b2cb84a1bec172c9)
    
> [name=Ginger C]

> 所以是戳了ATM的button之後會浮出資訊的意思嗎？
> [name=詹皓詠]

- [x] 聯絡人改 秘書長 廖士婷
- [ ] [Ginger Chen](https://g0v.hackpad.tw/ep/profile/vq24JlPGJy5) 不好意思，我們秘書長改為許莞庭，再麻煩幫我更改一次，謝謝！
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_99f89d5c0a36e77eb357ccdfc19d5477)
===============================================================
- [x] 合作夥伴確認：
- [x] tcktcktck
- [x] 350.org
- [x] Unite for Climate
- [x] 立凱電
> 他們有Logo~[http://www.aleees.com/tw/](http://www.aleees.com/tw/)
> [name=Doris L]

- [x] AYCN
> 也有Logo
> [name=Doris L]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_eb2091822c44058a01f739a29cd61ef3)
> [Ginger Chen](https://g0v.hackpad.tw/ep/profile/vq24JlPGJy5) 麻煩再幫我新增環科工程顧問公司（ESTC) THX!!!![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c1eb9868d1c8cede378d6fff457da589)
    
> [name=Doris L]

> ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4e062d447aba8f2130378084f1d67813)
    
> [name=Doris L]


===============================================================
- [x] 網頁最最下面放©2013 Taiwan Youth Climate Coalition Organization operating as TWYCC, a non-profit organization. 字樣
> © 因為是用g0v資源做的, 所以...應該copyright 會是cc授權耶... [Doris Lo](https://g0v.hackpad.tw/ep/profile/xfucBVUPzJP)
> [name=Ginger C]

> 喔! 其實我不太確定這個，我是看官網有所以就放上來了XD，可以不要理我這個
> [name=Doris L]

> OK~
> [name=Ginger C]


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d94740dd18965178905222db47561d24)


## 活動企劃

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ccb8d1b0c518ea81fc47e9e71ebec81e)
- [x] 頂端放專案介紹文
- [x] _活˙動更新文_
- [x] 下方圖示以時間軸跑專案文章
> 嗨我是前端工程師，想問一下那個最上面的navigation bar在hover之後出現的選單啊，是只有在這個頁面的時候hover會有，還是在其他頁面的同一個link上hover也會出現?
> [name=詹皓詠]

> [Ginger Chen](https://g0v.hackpad.tw/ep/profile/vq24JlPGJy5) 再麻煩你回應~
> [name=Doris L]




## 認識氣候變遷


> 這裏要放什麼內容呢?
> [name=Ginger C]

> 這邊主要構想是介紹關於氣候變遷歷史
> [name=Doris L]

> 、現況、重大新聞和里程碑，還有相關的名詞解釋如氣候會議、氣候基金等。是說我們要先把內容條列給你，還是可以先幫我們設計一個頁面，之後我們慢慢加上去？
> [name=Doris L]

> 都是文字敘述嘛？我建議先將內容給我, 因為我擔心後續你們維護會有困難(目前還在想解法中) [Doris Lo](https://g0v.hackpad.tw/ep/profile/xfucBVUPzJP)
> [name=Ginger C]

> 基本上都是文字敘述，可以的話希望圖文搭配，恩...目前內容還沒想好，我看看這禮拜可否打上來
> [name=Doris L]

- [ ]



## Vote for Climate的候選人回應追蹤


> 這一部分還要嘛?
> [name=Ginger C]

> [Yingfan](https://g0v.hackpad.tw/ep/profile/A6BDvRZG9G5)
> [name=Doris L]

> 這一部分我想先不用了，之後有新的追蹤我們就用文章的形式呈現就好了
> [name=Yingfan]

> OK
> [name=Ginger C]


## 台灣地圖

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d58c468b8f4b62112dc4a7bbe5b9c9ef)

列出各縣市串連活動或各環團相關活動、演講
（不知是否可以與目前twycc的google calender結合）

## 關於我們頁面

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8aea94b3136f4195c2006d1b98dedb8e)
- [x] 我們是誰
> 我們還有影片~[https://www.youtube.com/watch?v=HmdVXkIspPk](https://www.youtube.com/watch?v=HmdVXkIspPk)
> [name=Doris L]

> [Ginger Chen](https://g0v.hackpad.tw/ep/profile/vq24JlPGJy5) 我們是誰 下面還有三個link→緣起、核心價值、目標（在原官網可以看到內容~）ex. 緣起[http://twycc.org.tw/about\_us/why\_youth/origin/](http://twycc.org.tw/about_us/why_youth/origin/)
> [name=Doris L]

- [x] 團隊介紹、
> [Ginger Chen](https://g0v.hackpad.tw/ep/profile/vq24JlPGJy5) 這裡廖士婷改為執行長，新增秘書長許莞庭，謝謝！
> [name=Doris L]

> 執行長 Executive Director 廖士婷 Shih-Ting Liao 
> [name=Doris L]

> 秘書長 Secretary Generay 許莞庭 Wan-Ting Hsu 
> [name=Doris L]


> ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f584489476dacb02d189115bdcc775a5)
    
> [name=Doris L]

> 麻煩再幫我增加一個成員！
> [name=Doris L]

> 籌募部長  Director of Finance and Sponsorship Department 程煒倫 
> [name=Doris L]


- [x] 大事紀、
- [x] 活動成果、
- [x] 聯絡我們、
- [x] 加入我們

> [Ginger Chen](https://g0v.hackpad.tw/ep/profile/vq24JlPGJy5)再幫我新增兩個
> [name=Doris L]

- [ ] 媒體報導
- [ ] 網頁導覽（這部分建議放在這頁面還是首頁上排link比較好?）

## TWYCC活動日曆

> 這裏要放google calender? [Doris Lo](https://g0v.hackpad.tw/ep/profile/xfucBVUPzJP)
> [name=Ginger C]

> 是的~
> [name=Doris L]








## 會用到的jQuery 技術

```
(一邊搜尋一邊設計, 找到適合就貼上來囉～)
```
首頁Header>[http://previous.themepunch.com/kenburner-responsive/](http://previous.themepunch.com/kenburner-responsive/)






## 接下來要做的事情

> 不知道怎麼上再來問我～
> [name=Ginger C]

前端上github   網址 : （不會同步更新，以Preview為主）
- Github Repo: [https://github.com/katrina376/VoteforClimate](https://github.com/katrina376/VoteforClimate)
- Preview: [http://homepage.ntu.edu.tw/~b00209023/twycc_beta/index.html](http://homepage.ntu.edu.tw/~b00209023/twycc_beta/index.html)
目的：讓大家可以幫忙除錯
1. 後端架設，目前是已有找到可以做後續內容修改的網管了。
2. RWD
3.




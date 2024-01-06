---
title: "HackStory共筆時間軸"
tags: hackpad
---

# HackStory共筆時間軸

> [點此觀看原始內容](https://g0v.hackpad.tw/6svktTYKVLb)


[#](https://g0v.hackpad.tw/ep/search/?q=%23HackStory%E5%85%B1%E7%AD%86%E6%99%82%E9%96%93%E8%BB%B8&via=6svktTYKVLb)[**Hack**](https://g0v.hackpad.tw/ep/search/?q=%23HackStory%E5%85%B1%E7%AD%86%E6%99%82%E9%96%93%E8%BB%B8&via=6svktTYKVLb)[**S**](https://g0v.hackpad.tw/ep/search/?q=%23HackStory%E5%85%B1%E7%AD%86%E6%99%82%E9%96%93%E8%BB%B8&via=6svktTYKVLb)[**t**](https://g0v.hackpad.tw/ep/search/?q=%23HackStory%E5%85%B1%E7%AD%86%E6%99%82%E9%96%93%E8%BB%B8&via=6svktTYKVLb)[**o**](https://g0v.hackpad.tw/ep/search/?q=%23HackStory%E5%85%B1%E7%AD%86%E6%99%82%E9%96%93%E8%BB%B8&via=6svktTYKVLb)[**r**](https://g0v.hackpad.tw/ep/search/?q=%23HackStory%E5%85%B1%E7%AD%86%E6%99%82%E9%96%93%E8%BB%B8&via=6svktTYKVLb)[**y**](https://g0v.hackpad.tw/ep/search/?q=%23HackStory%E5%85%B1%E7%AD%86%E6%99%82%E9%96%93%E8%BB%B8&via=6svktTYKVLb)[**共筆時間軸**](https://g0v.hackpad.tw/ep/search/?q=%23HackStory%E5%85%B1%E7%AD%86%E6%99%82%E9%96%93%E8%BB%B8&via=6svktTYKVLb)


## 專案簡介

[slide](https://docs.google.com/presentation/d/17chsTU6nYXHgtA03yz95kiE2ggmwkAgdrygiTXBqAwI/edit?usp=sharing)
github: [https://github.com/g0v/HackStory](https://github.com/g0v/HackStory)
source: [http://visjs.org/timeline_examples.html](http://visjs.org/timeline_examples.html)


### 緣由

不少工作坊跟會議都需要參與者共同整理出時間軸，不管是重建事件經過、未來情境推估或是統整眾人的認知。這通常需要透過現場有夠大白板跟牆面，加上一堆便條紙來達成。雖然本人對於寫字跟便條紙頗有好感，但是要做成紀錄的時候就非常痛苦，這時候就很想要一個數位化的工具啊！不管是在整理議題的來龍去脈、事件發生的經過、推估未來情境發展都會好用很多。


### 要解決的問題

要共同建立一套時間軸，現有方式遇到的問題如下：
1.  現場編撰：需要一定大小的空白牆面或白板，參與人數相對受限。缺乏數位化工具進行整理，事後編輯、保存與發布相對困難。
2.  數位工具：通常只能用文字表格或Google Sheet處理，而且時間刻度的設定相對侷限，無法自動調整間距，編輯上不夠直覺，視覺呈現不佳。


### 預定使用者

（成品要給誰用、在什麼場合用、怎麼用）
在工作坊或會議時，需要共同建立時間軸時，能夠讓參與者直接用手機或電腦直接


### 預定功能

#### 主要功能

- 以共筆方式做出時間軸，讓參與者共同標記事件對於進行意見標注或評論，也能夠顯示作者身份。
> 1\. 拿來給共識工作坊用
> [name=ddio J]

> 2\. 讓人可以投票（線上或線下）
> [name=ddio J]

> 3\. bonus, 可以設定分支，像是子事件，相關的事件，如 Linux Branch 
> [name=ddio J]

- 依照輸入的資料，自動調整時間刻度的間距，在視覺上表現出時間的間隔長度
> 「自動調整」：
> [name=Johnson L]

> 1\. 精細度希望到時、分
> [name=Johnson L]

> 2\. 希望省略沒有事件的時間刻度
> [name=Johnson L]

> 3\. 預設的時間軸刻度
> [name=ddio J]

- 多軸與歧出軸：可以同時有多軸，並且能夠從某一軸線中的一點，拉出延伸的軸線。
- 能夠輸出成圖片檔：方便嵌入網頁或其他用途（這點也許就需要連帶有橫軸到縱軸的轉換功能）
> 直軸 \- 手機瀏覽。但有兩種情境（最上面的最近 or 最上面的最久遠），可能需要可以切換。
> [name=Johnson L]

> 橫軸 \- 一般線下使用習慣是橫的時間軸。橫版也可以用於換頁印刷。
> [name=Johnson L]


#### 輸入資料方式

- 直接在時間軸上輸入
> 要填的東西：time, event / topic, effects
> [name=Johnson L]

> 其他互動 \- comments / +1：comments 與 +1 需要 user id
> [name=Johnson L]

> 其他互動未來可加上tag功能
> [name=Cheetah L]


- 問卷表單
    - 能夠從google spreadsheet或markdown文件讀取（如同timeline JS）

#### 專案初始設定

- 時間軸名稱
- 設定時間軸時間範圍，還有能否增加超出範圍的事件
- 設定時間刻度大小
- 設定分類、顏色，可以選擇之後是否開放新增分類

### 介面設定

- 介面單位名稱
    - 時間軸的集合：Board /Chart / Flow / 軸承bearing/ 線圈Coil
        - 時間軸Timeline
            - 事件Event

### 現有類似專案

（現成的是否可以直接使用？或者有什麼不足之處？國外專案可參考？）


####

[時間地圖(timemapper)](http://timemap.kuansim.com/)：強調時空的關係連結，將地圖與時間軸連結，需要以google sheet後台輸入。
[Timeline JS](https://timeline.knightlab.com/)：國外專案，單一軸線，以圖文呈現事件或人物的年表。
> 設計上似乎是以內容為主，時間軸只是一個用來串連各個時間的 navigation
> [name=Johnson L]

> 但此專案希望以時間軸為主。
> [name=Johnson L]


線上 Timeline - [http://www.tiki-toki.com/](http://www.tiki-toki.com/)
- 可分 timeline
- 可協作
- 可嵌入到其他地方
- 不開源的商用 web app

Visjs (比 timelinejs 更合用，也比較好 customize 的樣子)
Timeline: [http://visjs.org/timeline_examples.html](http://visjs.org/timeline_examples.html)
Repo: [https://github.com/almende/vis](https://github.com/almende/vis)
> 就決定是你了！
> [name=Cheetah L]


318 學運時用 Tumblr 整理時間軸：[http://ecfa.board.tw/](http://ecfa.board.tw/) （連結已失效）
Google Sheet 後來：
[https://docs.google.com/spreadsheets/d/1wYByB1HQ7F6zhFuyOGiYZ24tCs7DWY5ZSKfENfOW7xQ/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1wYByB1HQ7F6zhFuyOGiYZ24tCs7DWY5ZSKfENfOW7xQ/edit?usp=sharing)

### 相關專案

（衍生自某專案/衍生出某專案/API串接自某專案.）

### 授權方式

MIT / CC-BY

### 使用資料

（會使用到哪些資料來源、各是什麼授權）

### 專案目前狀態

（構想 / 規劃 / 雛形 / 實作）

### 利益揭露

（牽涉到哪些組織團體、有哪些已知的或潛在的金錢或物質或無形利益報酬）


## 徵求協作者


發起人/拋磚人：
- [ ] NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
- [ ] NeedsDesigner: 需要介面設計
- [ ] NeedsData: 需要資料（擷取、清理）
- [ ] NeedsTech: 需要技術支援（程式、架站 etc)
- [ ] NeedsProcess: 需要幫忙設計作業流程
- [ ] NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡


## 實作細節（非技術背景可跳填）


### 協作工具

- Github repo: [https://github.com/g0v/Hack](https://github.com/g0v/HackStory)[S](https://github.com/g0v/HackStory)[t](https://github.com/g0v/HackStory)[o](https://github.com/g0v/HackStory)[r](https://github.com/g0v/HackStory)[y](https://github.com/g0v/HackStory)
- Hackfoldr 工作資料夾網址：
- Google Drive: [https://drive.google.com/drive/folders/0B3WI0Q0DjiUfQUdZeWJmQkVtdVk?usp=sharing](https://drive.google.com/drive/folders/0B3WI0Q0DjiUfQUdZeWJmQkVtdVk?usp=sharing)
- Slack: [https://g0v-tw.slack.com/archives/hackstory](https://g0v-tw.slack.com/archives/hackstory)

### 測試檔案

[Sample檔案](https://docs.google.com/spreadsheets/d/164k1gVdRanZzlzWFB4tPxuaQ8I1tGcYesmlWv4ZlOqo/edit?usp=sharing)
[Sample spreadsheet](https://docs.google.com/spreadsheets/d/1E7TOSa_G2nFeXmMT7V4aIKlt1Ef2xjhYbHx_3WEcoNg/edit#gid=1614773175)
[Sample spreadsheet (同婚議題)](https://docs.google.com/spreadsheets/d/11hHSbluBcNfMYppvSMTfB9Pg4fHmJMvmduoaHFCXREE/edit#gid=0)

### 進度與 to-do

> 僅供參考
> [name=ET B]

- [ ] product planning（recommanded procedure from justin lee / 李易修）
    - [ ] strategy
    - [ ] scope
    - [ ] structure
    - [ ] wireframe
    - [ ] visual
- [ ] web front-end
- [ ] web back-end
- [ ] ui / visual design


### Function  List

第一階段：建立新故事、建立新軸線、建立事件、編輯事件
第二階段：多軸建立：建立多重軸線→軸線位置移動功能→軸線間關係圖示的功能→多軸線顏色自選與分束功能→基本功能完成
第三階段：優化工程：自適應時間間距、開放時間間距縮放→多軸合併顯示
第四階段：故事交織：軸線資料共享功能→軸線資料分類目錄
第五階段：行動閱讀



### Technical docs

- Timeline JS API [https://github.com/NUKnightLab/TimelineJS3/blob/master/API.md](https://github.com/NUKnightLab/TimelineJS3/blob/master/API.md)
- Google sheet API [https://developers.google.com/sheets/quickstart/js](https://developers.google.com/sheets/quickstart/js)


→
## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）

Prototype 網址：[https://g0v.github.io/Hack](https://g0v.github.io/HackStory/)[S](https://g0v.github.io/HackStory/)[t](https://g0v.github.io/HackStory/)[o](https://g0v.github.io/HackStory/)[r](https://g0v.github.io/HackStory/)[y](https://g0v.github.io/HackStory/)[/](https://g0v.github.io/HackStory/)

~使用 json file 製作 timelinejs3 timeline:~
- [~https://www.dropbox.com/s/fafdhr5pwcg2fgd/test1.json?dl=0~](https://www.dropbox.com/s/fafdhr5pwcg2fgd/test1.json?dl=0)
- [~https://www.dropbox.com/s/wmjn0xmmzmghy7z/use_json.htm?dl=0~](https://www.dropbox.com/s/wmjn0xmmzmghy7z/use_json.htm?dl=0)
使用 visjs 為基底發展 HackStory: [http://visjs.org/timeline_examples.html](http://visjs.org/timeline_examples.html)




![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_11fbbc0c3ad0ff3e589ac04fac7bc917)
圖一（圖示）




![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_695dadc5dc8378f736f0bccc13104831)
圖二（新增圖表）


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_69137667206300fbdd25703b4ed5d0c3)
圖三（填入圖表名稱、時間跨距、描述）



![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9ada1c5540b5082355b5c4002251736e)
圖四（主畫面：右邊有加入軸線與事件的選項、也有時間跨距縮放呈現的功能）
y



![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6f12d373beb1ea043d23e3b198137f0b)
圖五（建立時間軸：填入名稱、時間跨距與描述）



![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2d382530f51c42dcb75d8cf1888855a0)
圖六（第一條時間軸已經建立）


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4c4bf060493aee3ebeed36ddbcb5f02d)
圖七（新增事件：填入名稱、時間、所屬時間軸、標籤、描述）



![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c989e125f47fbbd77c5688bca91bd3a4)
圖八（軸線一已建立兩個事件，軸線二也被建立）


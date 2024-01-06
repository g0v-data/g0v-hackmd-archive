###### tags: `web3`
# da0 Shoutout 6/27 會議
## 會議記錄
[上次會議(6/20)](https://g0v.hackmd.io/mSYfxdb0SnqjKsYHzBDRXA?view)；[上上次會議(6/13)](https://g0v.hackmd.io/@da0/main/https%3A%2F%2Fg0v.hackmd.io%2F%40noahyeh%2FByb-tRSv2) ；[5/23 會議時列出SOP SPEC](https://g0v.hackmd.io/@noahyeh/HyPnZQqrn)

參與者：昶惟、珮杏、Matt、維人、Stanly

## 今日討論事項列表
1. 確認前後端目前進度
2. 討論7/1報告
3. 討論開源規劃
## 前端
1. 考慮調整：排五個名，由多到少- 先做字體由大到小
   - [x] 公共: The channel most frequently shoutouts-->排名
   - [x] 個人: Ppl who shoutout you the most-->排名
   - [ ] Ppl who recieve your shoutout the most-->排名
   (排名跟七天的換位子)
   - [x] 數字放大
   - [x] Shoutouts you sent 時間排序改由新到舊 
2. 碰到難題："我SO別人"是一整串文字，很難知道要抓多少字元，因為MATT前端目前沒有reciever的欄位
**解法：** 昶惟多兩欄篩選，把送給幾個人的名字realname 跟id篩出來，讓matt去抓，新增兩個array，包含real name and id

3. 手機板 多了一個收合功能

### 開源
:::info
**Matt補充：**
開源版，主要是讓他們能夠替換channel的api，以及channel的id，網頁的database目前是跟sob分開的，未來要用自己前端的人，他們也必須要有自己的主機（我們現在是放在picchu），logo也是存在主機，所以其他人要用就可以換掉就好，所以他們只需要有主機就行～～～

要自建前端，他們一定要有自己的主機，然後複製我們前端的code，改掉id那些，放上主機就可以運行了

目前so 跟 sob有關係的只有api，api是從sob的資料庫整理資料丟出來的，所以他們可以自己建後端資料庫，但前端也必須調整api參數，也就是說他們前端也要變成自己的
除非我so多加分頁就可以一樣用so，只是進去之後會分不同channel，抓不同的api
:::

7/1 可以先聊是否有技術能力，並且留資料，等後續有開源計畫再聯繫





---
## 後端
### 目前SOB概況
#### 昶惟畫新架構：
#### 名詞解釋
- SOB = shoutout bot
    - da0-SOB
使用SOB程式，並且使用原本da0在使用的slack app token
    - XX-SOB
使用SOB程式，但不使用原本da0在使用的slack app token，改為使用別的slack app token，也就是說，需要另建一個slack app
- SOD = shoutout database
    - da0 SOD
目前da0正在使用的database，使用da0-SOB將slack中的訊息篩選並且記錄
    - XX SOD
使用XX-SOB將slack中的訊息篩選並且記錄
- SOP = shoutout page
前端網頁頁面 (前端須有自己的主機)

#### 有什麼可以開源？
1. slack app操控需要slack app token，但是這個應該不能開源，因為這其中代表了g0v slack app的操作權力和各種g0v slack的資料，無法防止惡意操作

2. da0 SO database的讀取和寫入需要database URL，目前只要擁有這個URL就可以完全控制database，目前無法防止惡意操作，所以目前也不能開源。
==是否有方法讓人可以只讀取而不能刪除呢？==

`**目前唯一可以開源的就是SOB的程式，其中包含了如何收取訊息和篩選訊息、server的建立以及database的建立**`

#### 目前後續可以開放大家使用的方法：
1. SOB程式開源，讓大家在各自的slack work space裡面架設SOB
2. 在只有使用da0-SOB的情況下，這個工具只會顯示g0v slack裡面的資訊。
3. 在前端設置可點選的篩選，讓不同的坑來使用SOP時，可以篩選出自己的坑的資訊
4. 不設置篩選，顯示所有坑的資訊

#### 不建議使用的方式：
1. 在g0v slack中再安裝一個SOB，這樣就可以自己操作想要篩遠的訊息，以及新增功能。限制在於目前g0v slack可安裝的app欄位不足，無法新增app
2. 開放da0-SOB，會需要公開slack app token，因為無法切分使用權限，會影響到原本的da0-SOB使用
3. 開放da0-SOD，會需要公開database URL，資料可能被任意刪除或新增

#### 未來可能可以使用的方法：
1. da0 SO database的使用權限對外開放限定為只可讀取，讓其他坑可以自己讀取想要的內容，往後做其他的應用
2. 在SOP設置slack work space登入選項，登入後就會利用SOB抓取其work space中的SOD資料。未來如果新增這個work space功能，就會顯示各自XX-SOB所抓取的資料。目前SOP預設使用da0-SOB，顯示的是g0v中有安裝da0-SOB的所有SO資料

---

#### 統整
**基本原則：**
1. g0v work space，因為app欄位有限，建議只有一個SOB，就是 da0-SOB
2. da0-SOD管理權限維持在da0 (昶惟)
3. da0-SOP的database管理權限在da0 (Matt的主機picchhu)
4. 盡可能實踐各社群資料自主，有利日後維護資料庫

**一、使用da0-SOB**
**For 密切合作社群：**
後端：與da0共用da0-SOD
前端：與da0共用da0-SOP
* 未來：da0-SOP設置篩選功能(filter)，或是設置分頁

**For 外部社群：**
後端：先跟da0共用，昶惟提供API
~~2. 未來開發讀取功能?~~ 
前端：社群使用自己的主機，另建一個前端SOP+database
* 需要開源教學

**二、SOB程式開源**
1. 讓其他人能夠在不同slack work space架設SOB
2. 讓其他人在別的社群平台使用SOB，例如discord
==(問題：不同社群平台可以串進同一個SO的前端跟後端的database嗎？==

目前昶惟程式差不多ok，等寫文件

---
維人問：7/1 先加入的人，如果後續要走開源，要如何把目前試用的過程剪下帶走？
昶惟解：可以先人工設定時間標記、或製作頻道標籤，之後開源讓人好取用


----

## 7/1
### 定位：
1. 操作方法跟達成效果講得明確（即分享思維和運用經驗）
2. 但不直接推銷（~~不邀請加入da0版~~可先加入da0-SO試用
3. 如果有人問要怎麼應用，再根據對方需求來應對

* 先讓人加入，後續開源

### 討論開源可能性：
讓其他人可以來完善功能 或是 開發屬於他們的SO工具
1. 尋求小功能支援:
   - 如何操作database的資料，例如test紀錄，如何刪除這種資料
   
2. 討論需求
先確認對方社群需求，以及技術條件滿足幾項


現場先示範使用前端頁面

追蹤後續某個坑來用，後續他們的使用狀況
把人邀請進SO 或加入他們的坑

之後可以討論如何讓人更踴躍的使用
小活動 送禮物???????
例如逸晟有作一些周邊商品

社群動力

需要有人，不一定是坑主，也可能是成員，要有人主動使用工具

報告 幫忙寫程式，也可以說蒐集大家的經營坑的經驗、困難需求

3分鐘-



MATT 去年更早開始刀八貓(當時只有前端)
昶惟 12月開始寫SO程式


---
Stanley Leo晚上8:09
我是Stanley 
只是來旁聽沒有要發言
純粹想幫用力做事的人打氣~~

7/1會參加台中大松
7/2會留下來參加實驗教育論壇
你晚上8:10
謝謝Stanley Leo <3 <3 我們正在討論前端目前的進度等等換UPDATE後端，然後就會討論7/1
會議記錄
https://hackmd.io/5K9s3ghTSLONaapg8-Exfw?edit
Stanley Leo晚上8:13
我…..其實打開hacked 以後也看不懂…
不過還是會繼續熱血以及為熱血的人加油！
你晚上8:14
XDDD 沒問題 超級重要的打氣 感謝感謝！
劉維人晚上8:38
@SO matt 由大到小逆序字體的點子超讚
ROOOCK
Stanley Leo晚上9:10
剛剛斷線了可能是個sign…..
我要先告退了
大家加油
台中見啦！
你晚上9:10
沒問題~ 晚安~
Stanley Leo晚上9:10
晚安晚安💤
劉維人晚上9:12
晚安
Matt Lee晚上9:37
Ppl who shoutout you the most
好了～
cst-ozop-jrm~~




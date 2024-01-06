---
tags: web3
---

# da0 Shoutout 6/20 會議

## 會議記錄
[上一次會議(6/13)](https://g0v.hackmd.io/@da0/main/https%3A%2F%2Fg0v.hackmd.io%2F%40noahyeh%2FByb-tRSv2) 
[5/23 會議時列出SOP SPEC](https://g0v.hackmd.io/@noahyeh/HyPnZQqrn)

---
### 今日討論事項列表
1. 確認目前SOB 跟 SOP 的進度 @昶惟 @Matt
2. 確認[SO文件](https://g0v.hackmd.io/wRf3GRwsRdO0-8Vu6OEKaA?both)進度
- 未完成的PART的狀況如何
- 討論一下「閱讀對象」，是否調整版本
- 如果內容大致OK，會擷取出重點製作7/1台中報告內容
3. 討論一下7/1的目標、開源規劃 (哪部分是可以開放讓人加入完善功能，哪些部分是可以釋出讓人開發屬於他們的SO)

---
### 前端 @Matt
1. 目前已抓到資料、做好計算，下一步就是丟到網頁上。下週二就可以看到成果
2. 電腦畫面可能無法置中? 手機畫面尚未調整
3. Shoutout 時間戳記：先設定成顯示最新一筆so的時間
4. 先保留以下這串字，下週看效果。保留的原因是，這串字蠻清楚可以顯示目前so使用狀況。
"There're over
328
shoutouts from contributors of da0, for now."
5. SO對外文件的部分：
內部教學版目前沒有需要寫的，因為都是使用現成的東西。
[先補充登入步驟](https://g0v.hackmd.io/wRf3GRwsRdO0-8Vu6OEKaA?both#Getting-started-with-ShoutOut-frontend-%E5%89%8D%E7%AB%AF%EF%BC%9A%E9%83%A8%E7%BD%B2ShoutOut---Tim-Matt-%E2%87%AA613%E5%9B%9E%E4%BE%86%E7%9C%8B)，再請Matt確認~
未來開源版操作手冊可以等下週再來討論，例如怎麼抓api資料、怎麼顯示id

:::info
**Matt補充：**
開源版，主要是讓他們能夠替換channel的api，以及channel的id，網頁的database目前是跟sob分開的，未來要用自己前端的人，他們也必須要有自己的主機（我們現在是放在picchu），logo也是存在主機，所以其他人要用就可以換掉就好，所以他們只需要有主機就行～～～

要自建前端，他們一定要有自己的主機，然後複製我們前端的code，改掉id那些，放上主機就可以運行了

目前so 跟 sob有關係的只有api，api是從sob的資料庫整理資料丟出來的，所以他們可以自己建後端資料庫，但前端也必須調整api參數，也就是說他們前端也要變成自己的
除非我so多加分頁就可以一樣用so，只是進去之後會分不同channel，抓不同的api
:::

### 後端 @昶惟
1. 後端目前都做好了~
2. 使用者在使用上沒有改變。但後台流程完全不一樣，變成是會透過server做邏輯運算，然後進到database。接下來無論是寫入資料還是取出資料，全都在database。會讓未來開源可以更容易管理
3. 昶惟to-do:更新流程表

目前後台分成 程式、database

4. SO對外文件的部分： 
   1. 內部教學版: da0開新坑的設置步驟
      1. slack頻道裝上sob
      2. 填入g0v-tw.slack.com-->允許
      3. 開始使用
   2. 開源版: 再找時間處理。
討論如下
開源的部分或許可以請chatgpt寫，然後再修
       1. 請Tim幫忙確認後台程式架設在"railway"(一個方便讓大家開源的工具)
       2. 撰寫架設so的文件

--

**開源兩階段**

第一階段：7/1  讓人抄作業
- 安裝sobot
- 完整開源文件，設定跟架設，但會有自己database；前端???(問matt)



第二階段：完整後台工具+前端顯示的set
未來開源開發項目
"這樣未來會需要建立更好用的後台系統，讓各坑可以方便操作資料；以及前台（前端）系統，各坑會有各自的數據顯示和統計網頁"

大家要能管理自己的資料庫
更好用的後台工具: 完整工具 加入bot 資料就會上頁面
也可以刪除或新增資料的功能


---
### SO文件
- 待討論
1. 對象應分外部社群 & da0社群(+密切合作的群體)?
2. 部署shoutout
   - 開源版
   - 內部教學版
3. Lucky格式提醒
（1）各段落敘事的口吻一致（主要是noah的段落比較明顯）
（2）文件的目標在整份文件環環相扣（ex. 如果現階段最高的priority是讓g0v community都嘗試採用，我們可以微調每個段落的描述，讓整篇文章的意圖更確定。if not, we can ensure the article delivers it）與頭尾輝映（脈絡回顧 to closing thoughts）
（3）中英版分離

---
### 7/1目標
**定位**：
1. 操作方法跟達成效果講得明確（即分享思維和運用經驗）
2. 但不直接推銷（不邀請加入da0版
3. 如果有人問要怎麼應用，再根據對方需求來應對

**討論開源可能性：**
讓其他人可以來完善功能 或是 開發屬於他們的SO工具
當天尋求小功能支援:
1. 如何操作database的資料，例如test紀錄，如何刪除這種資料
2. 不同坑要架設自己sob，可能會碰到一個問題：因為g0v機器人有限，所以可能還是只能用da0-SOB。那如果其他坑也使用了da0-SOB，但不想要被收入da0的database的話，該怎麼辦? (目前資料庫會完整搜到g0v-tw這個workspace的資料)

目前昶惟做法是去搜g0v所有坑有裝sob的資料，可以限定在只搜da0的資料，但未來多一個坑，就要手動新增進蒐資料名單

如果昶惟先改成只搜da0，那前台就會只顯示da0的資料。
當天教學其他坑架設sob時，直接請他們只搜他們自己的坑 (但防止不了他們收入其他坑的資料)

原則上不需要去阻止別人搜da0的資料
是我們自己要設定邊界，就是da0只收da0的資料，前台只顯示da0的資料跟統計

==**這裡會碰到的問題是：**==

別的坑使用da0-SO時，也會顯示同一個SOB，SOB的按鈕點進查看成就背包，會進到da0的頁面，但如果da0-database限定只收da0的資料的話，那麼別的坑就會看不到該坑的資料
**所以: 該坑的sopage該怎麼呈現????**
要怎麼只顯示自己的資料，要看前端那邊有沒有方法可以做篩選

==**有沒有可能這麼做:**==
**前端**
先用目前da0頁面當成整個g0v的公開頁面(也就是把da0商標跟twitter刪掉?)
然後有兩個篩選做法
第一種：設定filter
第二種：設一個按鈕，點進去是未來各坑的專屬頁面
每個社群各有自己前端頁面顯示
這樣表示大家都要做到自己獨立的前端顯示功能

**database**
基本上還是蒐集所有g0v的資料，但是各社群可以設定只收自己社群的資料
昶惟圖示:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7aab9df1f4c7e9f39241ecabb37be738.jpg)

----

### ACTION ITEMS
1. 下週前端SOP會長好
2. SO對外文件整理


---
https://g0v.hackmd.io/@noahyeh/SJ4CZ-kun
你晚上8:05
https://g0v.hackmd.io/wRf3GRwsRdO0-8Vu6OEKaA?view
https://g0v.hackmd.io/wRf3GRwsRdO0-8Vu6OEKaA?view#Getting-started-with-ShoutOut-frontend-%E5%89%8D%E7%AB%AF%EF%BC%9A%E9%83%A8%E7%BD%B2ShoutOut---Tim-Matt-%E2%87%AA613%E5%9B%9E%E4%BE%86%E7%9C%8B
你晚上8:15
電腦 畫面可能無法置中?
手機畫面尚未調整
你晚上8:16
目前計算已算好，下周二可以上
後端:
你晚上8:18
使用上沒有改變。但後台流程完全不一樣，變成是使用者操作 會透過server做運算，然後進到database。無論寫入資料還是取出資料，全都在database。會讓未來開源可以更容易管理
會透過server做邏輯運算
昶惟會在更新流程表
傅昶惟晚上8:45
g0v-tw.slack.com
你晚上8:45
內部教學版: 要填入g0v-tw.slack.com
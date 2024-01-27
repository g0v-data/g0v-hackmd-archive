---
tags: web3, Shoutout
---

# da0 Shoutout 01/16 會議記錄
* 時間：2024/01/16 20:30
* 參與者：昶惟、Kay、Chubby、Stanley、Gim、Lilian、Lucky、Peixing
* [會議連結](https://meet.google.com/tpx-cukc-mfn)
* 上次會議紀錄：https://g0v.hackmd.io/JlOYixP1RROdLvi6pT0v1g#
* [SO Project Master Working Sheet](https://docs.google.com/spreadsheets/d/1TiLe2t5XUeXS1vE7gJmyeC8GRLaTwU0t_UstoFFrmaQ/edit#gid=1051831713)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f2b6885f9650b3b56e9f497d50ad1b34.png)


## 重要時程
```
例會相關時程
- 01/02：發散想法
- 01/09
    - 聚焦想法：共識出 SO vision/主要使用情境
    - 確認評估想法的框架：大家會後做 imapct & effort 評估
- 01/16
    - 評估想法：討論大家評估後的結果（e.g. 哪些項目不好評估，需要再拆更細或更具體）
    - 大松資金用途討論 & 多簽錢包實作
- 01/23：排序想法，共識出優先要做的項目
- 01/30：buffer week（如果需要更多討論，可利用這週進行）
- 02/06：專案流程優化
- 過年後的例會進行專案分工 & kick-off
```

## 例會議程
- 資金運用
- 實作評估結果討論

## 任務清單


## 會議紀錄
- 資金運用
    - 若支出是從 USDC 支出，支出金額可以同樣改成 USDC 幣種
    - 錄影功能：先比較 Chubby & Peixing 的錄影品質，再決定要使用哪個錄影工具
- 實作評估結果討論
    - 

## Action Items


## Kay 整理總結
Kay 1/17   晚上 11:36
Hi 大家，感謝 01/16 例會討論，再請參考以下重點記錄，謝謝！
1.重點事項
(1) 昶惟已協助將剩餘資金轉入專案多簽錢包，再請大家確認
(2) Lucky 已協助創建專案共用信箱，也再請大家提供三組 gmail 註冊 airtable（參考 Lucky 教學）
(3) 也請大家 1/23 例會前，針對例會的錄影方式，用 emoji 投票或分享其他想法
2.參考資料
(1) Shoutout 討論彙整
(2) 可至 [SO 專案總表 > Project Library tab](https://bit.ly/3S1LN6M) 找到專案相關資料連結

## 會後夥伴update
昶惟 1/17  中午 11:57
資金轉帳到公用資金池完成了:白色勾勾:再請大家確認
Gas fee也會紀錄進去，因為從主網轉OP的時候還滿高的

Lucky:說話泡泡:  凌晨 5:37
@頻道 重要資訊更新～！
（1）我設定了 shoutout2024@gmail.com 作為之後大家都可以登入的共用帳號，之後 
@昶惟 如果有些服務在特定需求下需要綁google SSO登入，可以用這個帳號，密碼我會再私給其他PM們
（2）我剛使用 shoutout2024@gmail.com 註冊airtable（沒綁定google SSO）的帳密，帳號同gmail、密碼我之後分享給會想一起協作airtable的社群成員，避免對airtable介面不熟悉不小心誤刪資料
（3）我用 shoutout2024@gmail.com 設定了未來我們共用的weekly meeting行事曆（可以刪掉原本的避免重複），並設置成公開、可供訂閱的calendar。新增到自己的行事曆的好處，是可直接在行事曆裡找到google meet連結：公開網址新增到自己的行事曆
（4）如昨天會議提到的，請大家 在下週二weekly前，我們每個人幫忙註冊3組gmail帳號，然後點入 shoutout2024@gmail.com 的邀請連結來註冊airtable，我們就有一年的付費功能權限可使用，請大家幫忙一下～～
流程我拍了3分鐘 短片 放這邊給大家參考
提醒：註冊gmail帳號後，請點 這個邀請連結 ，才會累積點數到 shoutout2024@gmail.com ，不要點錯哦～！
（5）最後，等 @Peixing 的影片上傳後，我們感覺一下畫質音質，一樣 下週二weekly前 確認一下是否花3300訂閱google錄影跟雲端空間的服務（私心是希望用這個懶人處理法XD）， 
@Kay@昶惟  ＆大家覺得這個關於資金使用的粗略共識是否如g0v的方式，在頻道po文後一定時間內沒有人異議就代表通過，或是投票率達到一定比例才通過？
Plus置頂的 Meet 連結、成員介紹與會紀錄 連結 皆已同步更新為 shoutout2024@gmail.com 重新設定後的版本～ 
@昶惟@Kay 提醒PMs～ (已編輯) 

Kay   10 天前 
另外感謝 @Peixing @Chubbytank 昨天協助使用 OBS & windows 內建錄影功能協助錄影，兩部影片如下：
Peixing 協助：https://drive.google.com/drive/folders/1SrgLFFau3QzA-2_-OTBMvAONvegpQfLV?usp=drive_link
Chubby 協助：https://youtu.be/VGKr75EeVJA

我的想法是在可見未來，server 維運是一筆必要支出，目前資金比較緊的情況下，可能需要優先給 server 維運。因此也和大家討論以下方案：
背景：昨天@昶惟 有提到考量 DC server 費用較高，因此在接下來三個月會嘗試透過 DC SOB code 重構 or 自架 server 的方式來壓低 server 費用
解法：我想也許能先等三個月後的 DC server 費用優化狀況，來看是否有額外金費能支出 google one 年費。在這三個月期間，我們可能先用 OBS or mac quicktime 來錄影，然後將影片檔存在專案 Gmail 雲端或 YT
補充：理解上述解法會需要比較多人工來進行錄影 & 處理/整理影片，我這邊能協助@Lucky 一起做錄影 & 影片整理
總的來說，錄影這塊目前有下述方案，大家可以用 emoji 投票看是要 #1 or #2
#1：現階段花 3300 年費訂閱 google one
#2：視三個月後 DC server 費用優化情況，決定是否訂閱 google one，在這三個月中，先用 OBS or mac quicktime 來錄影
tag 主要參加 SO 例會的朋朋@Lucky@Peixing@昶惟@Lilian Wang@Chubbytank@Stanley@gim/dpupperr@Danny ( D大叔@Kevin 歡迎大家在 1/23 例會前點點 emoji 投票或分享其他方案，謝謝！
:二:6:一:1

Kay  10 天前
@Lucky 另外這個我想可以在某場例會和大家討論下～感謝 Lucky 提出！我先記下，可能下下下週 Lucky 較方便參與的例會我安排成一個議程來討論～ 「是否如g0v的方式，在頻道po文後一定時間內沒有人異議就代表通過，或是投票率達到一定比例才通過？」
:愛心2:1:good:1也已經傳送至頻道


Kay  9 天前
感謝 @Lucky 幫忙創專案的信箱帳號，我也將專案用的表單 ownership 轉移到 shoutout2024@gmail.com。可到 Library 查看哪些文件的所有權已轉移，謝謝～
:愛心2:3也已經傳送至頻道

Kay  9 天前
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_49bfae781ab392ef04c7e0265e6001ad.png)
:愛心2:1

Kay  4 天前
Hii @Lucky, 今天例會也有和大家討論錄影方式，目前多數人覺得可以先走 #2，看 Lucky 這邊是否 ok~ 感謝！cc @昶惟
https://g0v-tw.slack.com/archives/C046ZFGTWQK/p1705504668004769?thread_ts=1705441057.542429&cid=C046ZFGTWQK
若 Lucky ok，考量 #2 需要比較多人工處理流程，Lucky 可以再看哪部分需要我幫忙，謝謝！


## Reference


## Meet開會文字頻道
PT Chiu晚上8:33
剛到家 居然剛好
Lucky Chen晚上8:36
我另一個開會正在收尾不好意思先沒辦法說法
Peixing Liao晚上8:37
嗨~~
筆記: 舊電腦也可以當SERVER 但不能關機 也不能掛掉
Lucky Chen晚上8:38
我回來了
Peixing Liao晚上8:39
STANLEY: 參加gitcoin每三個月一次，獲得小額資金
引出資金池的配捐金額
Peixing Liao晚上8:40
舉手問: 好像可以，不過實際上參與過程是怎麼樣，還不是很清楚，只是一直看到fabdao在玩
Peixing Liao晚上8:42
Stanley: 成為被資助的專案，似乎門檻不高，好像把目標講清楚即可。不過需要跟web3有關，要跟鏈有一點關係
PT Chiu晚上8:42
WOW
playground的經費第一年就燒完啦
Peixing Liao晚上8:42
上次你聊到的免費軟體，好像真的很需要來用用
好啊你開開
Peixing Liao晚上8:43
ㄟ 原來 我以為是車子XD
Stanley Leo晚上8:45
我以為是血輪眼….
（想說會不會是動漫迷XD)
Peixing Liao晚上8:49
昶惟:折衷作法，先延續既有作法三個月，再看後續要換成哪一個方案
１．　自架
２．　程式改架構（主要是Praise比較貴，slack比較少，程式需求記憶體量不一樣)
Peixing Liao晚上8:50
給 kevin 目前在聊server費用

筆記
你晚上8:49
昶惟:折衷作法，先延續既有作法三個月，再看後續要換成哪一個方案
１．　自架
２．　程式改架構（主要是Praise比較貴，slack比較少，程式需求記憶體量不一樣)
Kevin晚上8:51
Ok謝謝
Lucky Chen晚上8:51
我跟chubby一樣
Peixing Liao晚上8:52
chubby: 如果要有繼續推廣，目前架構確實不太適合(貴)
Peixing Liao晚上8:53
三個月金額就是 1/4 ，如果未來要再追加就在從多簽提
Peixing Liao晚上8:55
不確定是什麼問題，不過就最近我大量做訪談，用windows的錄影都蠻清楚的~
Stanley Leo晚上9:01
Ok
Peixing Liao晚上9:02
筆記: 先確認錄影品質，再來選擇~
Peixing Liao晚上9:04
lucky: AT不花錢的作法~ 例如用帳號來累積使用時間~
PT Chiu晚上9:08
能省就省XD
Peixing Liao晚上9:10
超級專業
PT Chiu晚上9:13
那就用gmail拋棄式地址解決吧
省事
Peixing Liao晚上9:13
怎麼做? 我有點煩惱，申請帳密我最不擅長 QQ
PT Chiu晚上9:15
https://fomol.pixnet.net/blog/post/18772464
Peixing Liao晚上9:15
XDDD
Lilian Wang晚上9:15
學習了ＸＤ
Peixing Liao晚上9:16
還是要再說一次，超強大表格 XD
Lucky Chen晚上9:17
真的
覺得FAB DAO的人都好會做表格...
PT Chiu晚上9:21
0x55F16e16FCBA8B18E3c2032a68cA863cd85a90f2
PT Chiu晚上9:23
https://app.safe.global/address-book?safe=oeth:0x55F16e16FCBA8B18E3c2032a68cA863cd85a90f2
Peixing Liao晚上9:24
筆記: 交易所是好的跨鏈工具

## AI 逐字稿
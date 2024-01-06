[< 回EchoMori專案首頁](https://g0v.hackmd.io/OAq3-ouBTBScLk7TOYCQtg)
# EchoMori 設計師專區

## [Site Map](https://drive.google.com/file/d/1IKpr8RVOqJTj1_ESLAfr-stIYW4rx2JB/view?usp=sharing)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7c5f61b0adf0de5f06556a81e43c47be)

## 遊戲說明
[Brainstorm過程](https://g0v.hackmd.io/m55UNGNhQ9SaoAcqBnSw-g?both)
勇者不斷在地圖上挑戰新關卡，每個關卡要超過80分才算過關，80分獲得一顆星，90分獲得兩顆星，95分獲得三顆星。獲得12個星星才能解鎖新的地圖。
解鎖關卡之後會獲得金幣，可以用金幣買裝備，裝飾自己的森林，像是：種子、屋子、城堡、水池、木頭、動物...等等。種子有不同的等級和成長時間（強迫使用者要固定回來看樹長成怎樣）。
有些關卡解鎖之後會獲得寶箱，開啟寶箱隨機抽獎獲得新的裝備。
每張地圖可以蒐集不同的東西，不一定是星星。可以是散落在各地的書頁、花朵、齒輪之類的，增加故事性。
未註冊的使用者只能試玩前三個關卡，如果要繼續則必須登入。

## Wireframe
[Steph's Sketch file](https://drive.google.com/file/d/1AswGhlnoXwCF-d3B2WNR2Yug5Gq26JDu/view?usp=sharing)
* [首頁](https://g0v.hackmd.io/m55UNGNhQ9SaoAcqBnSw-g)：(Story point: 13 / Designer: Steph)
    * 任務地圖：每個區塊表示一個主題，完成類別中的單元挑戰之後可以拿獲得的金幣種樹。
    * 全站排行榜：依照積分、練習時間、內容貢獻
    * EchoMori Challenge：這裡在遊戲邏輯上做了一些改變。將系統default關卡當作是關卡選項之一，使用者可以點選獨角獸，瀏覽、選擇、切換到不同關卡![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cf16e7fcbeb82b58df257db06c29bed9)

    * Custom Challenge: Switch to custom view -> Browse and select the unit -> See the challenges -> Change the unit ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1090d1627d409ef84ed3b3155d0ac7f4) ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_efd87acbb3b37ec2e46f0b5acc3abff7)


> 
> [name=zucci]"完成Level 1的所有主題（種滿樹）之後可以移動到下一張地圖" < 是移動到下一個 Level的意思嗎? 在不了解使用者程度前，讓使用者可以自由移動到下一張地圖會不會比較好?     
> [name=steph]"希望在等級和分類完善之後可以讓使用者先完成測驗，再提供相應等級的地圖。在尚未完善前可以一律從初階開始。"
  
* 類別挑戰：點選首頁地圖上的單元類別後進入挑戰(Story point: 8 / Designer: Steph)
    * 顯示單元句子列表
        * 第一次練習：點選關卡進入練習 ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_886120ed7cf11006a9abb8b51c33e194)![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d94637d9fd08a12d44a538f9fe420169)


        * 第二次練習 ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_51083ebbcbcb74aa55b8bb489cec984f)



    * 練習畫面
        * 移除按著才能講的功能，改為自動開始，但如果收不到音則顯示：「請再說一次。」![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e2aec14aa8651abe301a57344bd4bc22)


        * 將評分改為顯示在系統這一邊，並加上機器人表示為系統回應 ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d57e7ce550e66a973cb1ec3d59c5e867)



    * 調整練習模式
        * 移除meaning mode & interpreter mode，因為 google 不支援中文的台灣口音。![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_93a67ea84ddfa3cab648a142df73407e)

    * 練習結果（包含得分、結果分析、獲得金幣、獲得積分）（Action: 繼續挑戰、分享結果）
        * ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c78b7de2b8a2226dd54756349a6579f1)

>[name=Awan]
>- user story 上面的分享，其實那時想的是分享關卡。(像 youtube 的 share) 給其他人挑戰，而不是想分享結果。
> - 現在不會做聲調的判斷。
> 
>[name=Steph]保留分享結果的功能，增加EchoMori的曝光度

* 個人客製化單元：點選首頁地圖上的客製化類別後進入(Story point: 8 / Designer: steph)
    * 個人客製化單元列表 ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a22fb16486c533174ffcc1de2757c793)
    * 建立新單元頁面 ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_444aa4247340c9be7669f5e683ff34ca)![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6d2d3ee7546b5e6469fa7747b3019bb9)

    * 單元詳情（創建者可以編輯、刪除或選擇分享該頁面，邀請別人加入挑戰。）![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_99ef9dc64de53ff4578cb5d67c84852f)

    * 單元內句子詳情 ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0ef68e2174e86ebbdbb32503b6751864)


    * 打開別人分享的單元連結後的畫面：選擇「開始挑戰」之後回到首頁，並且切換至該選擇的單元 ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3fe57bce8b6608b25279a358ca320b66)




* 個人資訊頁面：點選首頁右上方的icon進入(Story point: 13 / Designer: stella)
    * 積分/時數趨勢圖/目標達成進度
    * 練習歷史（顯示單元/句子/結果）（選擇句子重新練習）
    * 徽章/頭銜/等級
    * 設定目標
    * 更改密碼/頭像
    * ~~調整default練習設定~~ -> 改成在練習頁面修改設定(Steph 8/20)
* 通知：點選首頁右上方的icon進入(Story point: 3 / Designer:)
    * 顯示所有通知（系統通知、好友升級/頭銜/徽章）
* 註冊/登入(Story point: 3 / Designer:Steph)
    * 登入![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6deb637f5d3bd7cb883ef00d3aeb19e0)

    *  未註冊或登入前，每個單元最多只能練習到1-3。如要繼續則需註冊![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3fa740db7b0c5933c7adcca6fe506334)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2db12010170191508e05639ede87091b)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0449e96d3c9d591681fe6f4be499ae99)![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a301f27d7fc704b2baf2f5292d487c8f)
    

## [視覺設計靈感專區](https://g0v.hackmd.io/pPmSUZ-TRQ2IGJZH3cVVsA)

## [Backlog](https://g0v.hackmd.io/y6QV3v9vSi6e30giIvICDA)

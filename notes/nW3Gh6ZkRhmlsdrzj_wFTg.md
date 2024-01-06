# OBS 直播 - 基本操作

## 前置作業

準備好視訊鏡頭。

## 新增來源、調整來源

1. 加入媒體來源
    - 在下方 [來源] 欄位 **[右鍵]** > **[新增]**，在這邊可以加入各種媒體來源。選擇 **[視訊媒體裝置]** 來做示範教學。
    
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_26e9068b552633bf29f5b11e8fcab7fa.png)

2. 在 **[來源]** 或 **[畫布]** 上 **[右鍵]** 剛才加入的視訊擷取裝置，

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1454344849c14b9a46542c851197c542.png)

3. 在這邊可以調整關於這個視訊鏡頭的設定。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_34c0153d889c81b9d7e1b23fd731a1f5.png)

4. 以下為常用的幾個設定：
    - **停用/啟動**
    :::info
    有時候視訊來源會卡住，可以透過這個按鈕先停用再啟用後來重新抓取訊號。（Reset 萬解）。
    :::
    :::warning
    視訊鏡頭一次只能對一個程式傳送畫面。如果你的 OBS 程式已經在用這顆視訊鏡頭了，那你線上會議的軟體就會抓不到視訊鏡頭。
    :::
    
    - **設定視訊**
    一般來說視訊鏡頭會自動調整焦距跟色澤，但你也可以透過**設定視訊**自己調整焦距、亮度或對比。
    
    - **解析度/FPS 類型**
    通常不會選擇**裝置預設值**而改成**自訂**，來調整自己想要的解析度，現在直播通常會選 1920x1080
    
5. 最後調整視訊來源在畫布的位置，除了可以直接從畫布上拖拉之外，也可以透過 **[右鍵]** > **[變形]** 裡頭的選項快速調整位置。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b5708d10eeb9313dc135e64856540ec0.png)

5. 調整來源的設定選擇 **[屬性]**，調整來源的呈現則選擇 **[濾鏡]**，在濾鏡裡頭有很多效果可以使用，最常使用的功能是 **[剪裁/填充]** 跟 **[色彩校正]**，用來調整你希望的大小跟色彩。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4d3afab8336180359a2ffcc8163786f8.png)

6. 來源的種類很多，每個來源新增後都可以透過 **[屬性]** 跟 **[濾鏡]** 做設定調整。
    - 視訊擷取裝置：攝影機/視訊的畫面。
    - 圖片：加入單一個圖片。
    - 投影片放映：加入多個圖片輪播，可以透過屬性調整輪播的速度。
    - 媒體來源：加入單一個影片。
    - VLC視訊來源：加入多個影片輪播。
    - 視窗擷取：擷取電腦上單一個程式的畫面。
    - 文字：如題，可以在 **[屬性]** 中調整大小、字體；字加上 **[外框]** 避免融入背景看不清楚。
    - 擷取音訊輸入：麥克風的聲音。
    - 擷取音訊輸出：電腦的聲音。
    
    :::info
    聲音的大小可以在 OBS 正下方的 **[音效混音器]** 欄位調整。
    
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2b187aa235813487c53d35f1a2d277c1.png)
    :::

## 新增場景、場景轉換

1. OBS 的左下方欄位 **[場景]** > **[右鍵]** > **[新增]**，取好場景名稱後就新增了一個場景。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fa595c541ac38064aedb592966a70fa3.png)

2. 點選不同的場景即可切換過去。

    :::info
    正式直播時會先確認畫面沒問題再轉過去。所以正式直播時會使用 **[工作室模式]** 。(按鈕在 OBS 右下角的 **[控制項]** 欄位)，開啟工作室模式後會有左邊一個預覽畫布，右邊一個正式畫布，點選兩個畫布中間的 **[轉場特效]**、**[直接轉場]** 就可以將預覽的畫面轉到正式畫布。
    
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cbb426a28ffd87d3825fb9e20b23e534.png)
    :::
    
## 直播設定、開始直播

1. 在 OBS 視窗上方的控制項選擇 **[檔案]** > **[設定]** 中，可以在新視窗左側清單找到 **[串流]**。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ae18c9516d4eaadbf32b1b7051cf0a4d.png)

2. **[串流]** 中可以在 **[服務]** 選擇要在 YouTube、FB、還是 Twitch 直播； **[伺服器]** 這個選項通常不用調整；最後貼上串流金鑰（不可以給別人知道以免被駭），金鑰會在你想直播的平台上設定好後取得。
3. 通常在直播前要確認一下輸出的解析度，在 **[設定]** 右側的清單，選擇 **[影像]**，可以調整解析度，一般來說來源跟輸出都會設定成 1920x1080，常用 FPS 為 30 或 29.97 就很足夠，60 FPS 雖然很清楚但會很明顯增加電腦的負擔。
4. OBS 視窗的右下方 **[控制項]** 點選 **[開始串流]**，Happy on air

    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2c948a1a0d736f1c4ca04eb839d1597f.png)

5. 按 **[開始錄製]** 的話則是錄成影片存在電腦裡，存檔路徑可以在 **[設定]** > **[輸出]** > **[錄影]** > **[錄影路徑]** 上找到。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d199cdc21e0d2de0104721ce784b5460.png)

6. 在希望直播的平台建立直播，取的直播金鑰。
    - 通常建議取消「串流影片停止播放時結束直播視訊」個選項

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c22a18fde38bf635b11bc933d7249896.png)

> 教學：如何在 YouTube 建立一個直播（[YouTube 影片](https://www.youtube.com/watch?v=Pvmt42GZnUg)）
> 一個 YouTube 帳號第一次要直播通常要先審核一天。
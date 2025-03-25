# 腦震盪 Concusion For iPad

https://hackmd.io/YXyG4ZIuQXiZ0Lf-tHtMQA

> 2025/2/23
> Replace Pico with ipad for using eye-tracking in ios
> then we will have both platform for eye-tracking
::: info
此專案前人開發的時候沒把沒用到的部分刪掉，逐漸積累下來越來越多垃圾在裡面，如果你看到沒用到的東西就勇敢刪除，刪過頭就回來重clone
> 要不是那兩個急著要去美國demo 我也不用這個急著生出這個專案，這專案很多寫很醜的地方，你有那個心可以鍛鍊一下自己如何寫出clean code
:::

:::danger
目前這個專案有兩個問題

1. 現行眼動數據不準
受限於使用的基礎是ARkit而不是ios 18自己推出的eye tracking(這東西在我開發的時候還沒開放API給開發者)
`不準確的原因我覺得是ios eye tracking有兩個，分別是他們有用機器學習以及他們的雙眼注視座標是screen space`
計算眼動數據在`Concussion_BrainBit\Concussion_brainbit\Assets\Scripts\Eye\EyeTracker.cs`
如果你未來有開發到有用的眼球校正，那就更新
2. 無法上傳數據
受限於iOS安全性問題，我們無法直接將數據上傳到http當前綴的網址，若使用https我們必須要有domain name來取得ssl，又或是你們開發出ios interface那就可以上AIOT
:::

## 架構說明

此專案包含兩個 unity 專案，分別為Concussion_brainbit & 分別為Concussion_brainbit_control

1. Concussion_brainbit 是我們程式主要跑的地方
2. Concussion_brainbit_control 則是因為原專案收案時需要同時使用頭帶及vr，而在進行校正電阻時候測試人員無法看到受試者VR內的情況下進行校正，故另外使用**平板**先進行校正

> 如果你是使用ipad的話，使用及開發用Concussion_brainbit就好

## 眼動數據說明

### 左右眼

ARkit 當中有提供雙眼各自的位置以及看的方向，資料型態皆Vector3
也有提供眼睛的閉合程度，0~1之間變動
> 0為睜眼 1為閉眼

### 雙眼合併

使用ARface.fixation進行，fixation是ARface中表示雙眼注視的位置( 世界座標 )
我們在開發iPad這種2D的介面不能直接取，你得轉換到screen space上才行

### 朝向的方向

遊戲中這種資訊會是一個三維數據，你可以透過這個方向發出去的射線去跟場景中的物件做互動
我是用fixation.forward來替代

## 遊戲流程

### 場景介紹

這專案主要使用四個場景

1. MainUI：
    a. 功能：button到腦電確認、跳轉到VEP、判斷腦電有沒有連線(綠色有灰色沒有)、
    b. 主要scripts：MainMenuController.cs
2. VEPTest：
    a. 功能：就是讓玩家看著閃爍的黑白格子，這邊收的是腦電的資料，閃爍完就會前往下一個scene
    b. 主要Scripts：VEP_Task.cs
3. FixationTest1：
    主要眼動的地方，也是整個專案的重點，這邊提到有關數量的都是因為我們計算特徵的時候有規定，所以如果你確認哪個特徵計算沒有規定或是有更改特徵計算，你盡量別動那個數量要求
    > 這邊有前面人開發時亂取名的東西，我盡量在這邊說明，可能還是會遺漏
    a. 流程：分成兩個任務進行，分別是注視(fixation)以及掃視(saccade)其中會搭配英文語音解說，兩個任務都是透過注視螢幕上的點去消除標靶只是差在注視所需的時間
    > fixation 在 遊戲中取名叫做 fixation task 1，saccade叫做fixation task 2
    b. fixation：遊戲會先秀出一個標靶讓受試者進行測試，只要受試者可以注視兩秒就可以消掉，只要消滿10個就可以前往下一關
    c. saccade：遊戲一開始會秀出40個標靶，玩家就全部消除就可以結束遊戲
    > 照理來說遊戲結束要開網頁看成果如何，但問題回到readme開頭那邊
4. brainbit：我忘了叫什麼名字，就是確認腦電阻抗有在固定值以下

### 必定要常存的東西

1. saveLocal(Prefab)：這用來存資料的
2. brainbitcontroller：這會在main ui 時候設置為`DontDestroyOnLoad(GameObject.Find("BrainBitController"))`，

> 這個寫法不是很好，你在開發的時候有遇到的話就知道了

## ios build 過程

> 有鑑於ios 不像 android 或是 windows一樣是直接拉執行檔案進去，故寫這個來用
1.建置的時候不會是執行檔，而是一整個資料夾，所以你要先選個地方存
2.接下來將建置好的資料夾傳到具有apple developer(這個要花錢買)帳號的mac上面 `我們實驗室用在名叫陳宇揚的帳號`
> 看你要怎麼傳直接傳輸線或是壓縮後上傳到實驗室的雲端(nas or google drive)
3.成功用到電腦上開啟資料夾，用xcode開啟專案

4.應該會出現以下畫面 (沒的話就點左欄的Unity-iPhone)

5.出現的時候在 `sign & capabilities` 選擇chen yu yang(如果其他帳號有apple developer也可以)，並勾選上圖寫的
6.最後按下左上的播放鍵(build)，注意如果xcode有更新位置可能變

> 你當然要在上排的裝置選擇建置到哪個裝置

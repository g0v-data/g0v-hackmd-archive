# 腦震盪 Concussion

## :male_mage:  負責人員

- **2024**
  - (研) 蔡宇傑、詹偉裕
  - (專)

- **2023**

  - (研) 黃鵬緒
  - (專) 無
- **2022**
  - (研) 謝兆峰
  
  - (專) 無

## :link: 相關連結

### 原始碼連結

- 腦電使用ganglion版本 :

[gitea 連結](http://140.115.54.26:4000/ccisd/concussion/src/branch/WmlabAIOT/Concussion)

- 腦電使用BrainBit版本:

[gitea 連結](http://140.115.54.26:4000/113522054/Concussion_BrainBit/src/branch/master)

#### 收案說明文件

[文件連結](https://hackmd.io/YXyG4ZIuQXiZ0Lf-tHtMQA?view#%E7%B3%BB%E7%B5%B1%E5%92%8C%E8%A8%AD%E5%82%99-System-and-Equipment)

#### 執行檔連結

#### 計畫書

<!-- 
- {連結} 
-->

#### 專題生專題競賽海報

<!-- 
- ({年份}) {專題生名稱} {專題海報標題} {連結}
-->

#### 相關論文

<!-- 
- ({年份}) {作者} {論文題目} {連結}
-->

## :page_facing_up: 專案文件

### 遊戲架構說明

![image](https://hackmd.io/_uploads/BJSZfj6FJx.png)
此專案透過測試三種任務時所蒐集到的腦電訊號和眼動資料，來計算和推測遊玩者有沒有腦震盪跡象。
腦電蒐集的方式分為兩個版本:

1. 使用openbci ganglion
2. 使用BrainBit

### 操作說明

#### Main menu

![image](https://hackmd.io/_uploads/B18AxjatJx.png)
進到遊戲後請先將腦電開啟並連接，若連接成功，上面的提示文字會消失，且腦電的圖案會顯示綠色。
:::warning
若腦電沒有連接是無法開始遊戲的!
:::

> **Setting**：點擊按鈕會跳轉到wifi連接畫面
> **Calibration**：點擊按鈕會跳轉到眼動校正畫面
> **BrainBit**：點擊按鈕會跳轉到確認腦電電阻畫面

點選 **PLAY** 按鈕可開始遊戲

#### 確認電阻畫面

![image](https://hackmd.io/_uploads/SyelBi6tJl.png)
當腦電成功連上時，要先確認電阻值是否降到特定的數值以下。

- Ganglion版本:
電阻30歐姆以下
  - BrainBit版本:
電阻1M歐姆以下([官方建議](https://sdk.brainbit.com/device-recommendation/))

#### 任務

1. SSVEP任務
此任務需要持續注視螢幕中的黃點，在這期間就會不斷的收集腦電的資訊，經過30秒後即結束此任務。
![image](https://hackmd.io/_uploads/B13MUi6Kyl.png)

2. Fixation任務
此任務需要完成10次注視標靶，當眼睛注視在標靶上持續兩秒可以消除標靶，完成10次後即結束此任務。
![image](https://hackmd.io/_uploads/HklscIopYyl.png)

3. Saccades任務
此任務需要將畫面上的標靶全部消除，將眼睛注視在標靶上即可消除標靶，當標靶全部消除後即結束此任務。
![image](https://hackmd.io/_uploads/B15QPspFJg.png)

完成以上三個任務後遊戲會自動結束，資料會儲存在pico的頭盔裡面。

### 程式相關

- 腦電使用Ganglion版本:
使用 Unity 2020.3.33f1 開發
- 腦電使用BrainBit版本:
使用Unity 2021.3.8f1、BrainBit NeuroSDK2 1.0.10 開發

#### 重要 C# Scripts

##### UI

- MainMenuController.cs
  - MainUI 場景（主畫面）的運作。
- BrainBitCheckController.cs
  - 確認BrainBit腦電電阻場景的code。
- UIController.cs
  - 這是Ganglion版本用來確認腦電電阻的code。

##### GanglionSDK

- BrainBitController.cs
  - 用來控制BrainBit腦電頭戴的code。
- GanglionController.cs
  - 用來控制Ganglion腦電的code。

##### LocalSave

- SaveLocalFile.cs
  - 將收集到的腦電和眼動資料儲存到pico頭盔中的code
  - 資料會存放在/Pico Neo 3 pro Eye/內部儲存空間/LabData/concussionPico/ForSand/

##### Tasks

- GameTaskController.cs
  - 控制兩種注視遊戲的流程
- VEP_Task.cs
  - 控制SSVEP任務

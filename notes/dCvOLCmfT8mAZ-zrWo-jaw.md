# 助教課

# 雲端資料夾

[課程素材庫](https://drive.google.com/drive/folders/1HzvexBlurS1gE15yS91XBQlEzpq2Qfa9)
[Google Drive: XRCamp_UnityTutorial_魷魚遊戲](https://drive.google.com/drive/folders/1DO6T4LYf76ZNJaC66JMGpSdPp59T9s7d?usp=drive_link) -- 待更新

# 目錄
1. [創建URP專案](#1-創建URP專案)
2. [匯入場景、道具](#2-匯入場景、道具)
3. [Post Processing 提升畫面氛圍](#3-Post-Processing-提升畫面氛圍)
4. [匯入可操作的角色](#4-匯入可操作的角色)
5. [產生中文字幕](#5-產生中文字幕)
6. [整理 Heirachy 視窗](#6-整理-Heirachy-視窗)
7. [與物體互動](#7-與物體互動)
8. [場景(Scene)切換](#場景(Scene)切換)
9. [自主練習](#9-自主練習)
    A. 為遊戲添加音效
---
(以下為舊版，待更新)
10. [VR遊戲 vs 3D遊戲](#1-VR遊戲-vs-3D遊戲)
11. [Unity VR設定](#2-Unity-VR設定)
12. [3D to VR](#3-3D-to-VR)
    12.1. [角色控制 (Camera、Hands、Move、Turn)](#31-角色控制)
    12.2. [場景互動 (Hover、Grab)](#32-場景互動)
    12.3. [UI](#33-UI)
    12.4. [VR Raycast](#34-Raycast)
    12.5. [Feedback (Vision、Haptic)](#35-Feedback)
13. [為遊戲加分 (美術、音樂組同學注意！！！)](#4-為遊戲加分-美術、音樂組同學注意！！！)
    13.1. [為遊戲添加音樂吧！](#41-為遊戲添加音樂吧！) 
    13.2. [為場景增加一個會動的NPC吧！ (內含Sketchfab及Mixamo教學)](#42-為場景增加一個會動的NPC吧！)
    13.3. [Particle System (粒子系統)–最近怎麼一直下雨啦](#43-Particle-System-粒子系統–最近怎麼一直下雨啦)
14. [其他 (內有Plastic SCM)](#5-其他)
15. [注意與建議](#6-注意與建議)


# 2024/02/27 Unity (3D) 魷魚遊戲

## 目標

從頭開始，完整製作出一個 XR project。

預設已經先行完成Unity Learn - Misson 1，對Unity有基礎的認知。

TARGET： [魷魚遊戲：123木頭人](https://www.youtube.com/watch?v=J7FqiKJmwEI)

![美術圖 (1)](https://hackmd.io/_uploads/rkd4S369Jl.png)

先試著構想心智圖吧！

![image](https://hackmd.io/_uploads/ry7X1hT91g.png)

## 所使用到的素材

1. [XR Camp Utilities](https://drive.google.com/drive/folders/1cN4LKXDMaVtaXzZxrDOUkjezCA6RT8QD?usp=drive_link) -- 其中包含助教寫好，常用到的Script和工具
2. [SquidGameAsset & Script](https://drive.google.com/drive/folders/1DO6T4LYf76ZNJaC66JMGpSdPp59T9s7d?usp=sharing) -- 包含場景、人物模型和腳本
3. [StarterAssets - FirstPerson](https://assetstore.unity.com/packages/essentials/starterassets-firstperson-updates-in-new-charactercontroller-pac-196525) -- 簡易的第一人稱角色控制器
4. [FREE Skybox Extended Shader](https://assetstore.unity.com/packages/vfx/shaders/free-skybox-extended-shader-107400) -- 天空盒材質
5. [Sketchfab for Unity](https://assetstore.unity.com/packages/tools/input-management/sketchfab-for-unity-14302) -- Sketchfab Plugin
6. [Copilot on VSCode](https://github.com/features/copilot) -- 給不是程式專業的你^^

## 上課內容紀錄 (持續更新...)

:::success 
請善用瀏覽器的關鍵字搜尋功能：```Ctrl+F```
:::
  
### 1. 創建URP專案

* **創建專案**
    打開Unity Hub，建立一個空的3D (URP) Unity專案，版本請選擇最新的LTS版，並按下Create Project：
    ![image](https://hackmd.io/_uploads/BJj2ourTa.png)

    如欲使用版本控制，請勾選右下角的"Use Unity Version Control"。

### 2. 匯入場景、道具

* 課程資源、網站介紹
    * 課程Discord頻道中的"資源分享"欄位底下，有這門課[過去所購買的諸多素材](https://drive.google.com/drive/folders/1FFOdh6Hl0fuGalCv6iOCogKh9CX823TN?usp=share_link)供同學免費使用，同時也提供了許多免費資源連結，請多加利用。
    * 這堂課所使用到的所有素材，都已列在[#所使用到的素材](#所使用到的素材)底下
* 將材質(Material)轉換成URP格式
    1. 當匯入的物件呈現粉紅色(無法正確顯示材質)，
    2. 請前往 Window -> Rendering -> Render Pipeline Converter
    3. 全部勾選，並點擊 Initialize And Convert
    
    ![image](https://hackmd.io/_uploads/BJFcPpbTp.png)


### 3. Post Processing 提升畫面氛圍

* Volume
    1. 創建一個空的GameObject
    2. 在Inspector介面中，點選"Add Component" -> "Volume"
    3. 創建一個新的profile
    4. 點擊"Add Override"，為其添加各種濾鏡
    
    ![image](https://hackmd.io/_uploads/BkAiLnTqJg.png)

* Local Volume
    1. 為這個GameObject添加一個Box Collider，限定濾鏡作用範圍
    2. 將"Volume"底下的Mode欄位，改為"Local"即可
    
    
### 4. 匯入可操作的角色

* Main Camera
    遊戲畫面
* Player Follow Camera
    Main Camera 會跟隨player capsule

1. 匯入[StarterAssets - FirstPerson](https://assetstore.unity.com/packages/essentials/starterassets-firstperson-updates-in-new-charactercontroller-pac-196525)
2. 將StarterAssets/FirstPersonController/Prefabs/NestedParent_Unpack.prefab 拖曳至Heirachy視窗中
3. 右鍵點擊NestedParent_Unpack，點擊"Prefab" -> "Unpack"
4. 取出MainCamera、PlayerFollowCamera、PlayerCapsule即可，其餘物件可以刪除


### 5. 產生中文字幕

1. 創建一個UI->Text
![image](https://hackmd.io/_uploads/BkxmRmjp6.png)
2. 自行上網下載字體 (Windows預設字體在C:\Windows\Fonts)
3. 前往 Window -> Text Mesh Pro -> Font Asset Creator 產生客製化的字形圖檔。
![image](https://hackmd.io/_uploads/B1xdUTbap.png)
4. 將生成的檔案，丟入Text的"Font Asset"欄位中
![image](https://hackmd.io/_uploads/ryFcAQspT.png)
   
   
### 6. 整理 Heirachy 視窗

* 雜亂的Heirachy不利於開發。
* 請善用Empty GameObject為其命名當作「抽屜」，將不同功能的GameObject分類以方便管理。
![image](https://hackmd.io/_uploads/HyMzInp51x.png)

### 7. 與物體互動

我們的目標是實現以下兩個情境：
1. 被看到時動作、判定Loss
2. 抵達終點、判定Win

### 7.0. XRCamp_Utilities部分功能介紹 (請先將 XRCamp_Utilities 匯入專案中)

> **XRCamp_Utilities中，包含了三種讓玩家與物體互動的方式：**
> * **TriggerOnClick**
    點擊滑鼠左鍵時，朝玩家畫面(MainCamera)面向方向射出一道射線，射線接觸到物體時觸發動作。
> * **TriggerOnCollision**
    物體與對應Layer的其他物體碰撞時觸發動作。
> * **TriggerOnKeyPress**
    玩家按下特定按鍵時觸發動作。
> 
> 以上互動的方式皆透過 Unity Event/Game Event觸發動作。

### 7.1. [補充] Unity Event vs. Game Event

#### Unity Event 使用方法：

1. 點擊Unity Event()底下的+號，即可添加要執行的動作即可。
![image](https://hackmd.io/_uploads/SJSD_Miaa.png)


#### Game Event 使用方法：

1. 先於Project視窗底下點擊右鍵，創建一個GameEvent
![image](https://hackmd.io/_uploads/ryNTtzsaa.png)
2. 在Heirachy中創建一個空的GameObject，為其添加"GameEventListener.cs"的Script。
![image](https://hackmd.io/_uploads/HkUq2fsTT.png)
3. 將創建的GameEvent拖曳至"On Event"欄位中，並於底下的Response添加想觸發的動作。 GameEventListener會監聽對應的GameEvent，並於GameEvent觸發時執行底下的動作。
![image](https://hackmd.io/_uploads/SJH1sfipT.png)

### 8. 場景(Scene)切換

1. 創建一個空物件"SceneManager"，並為其加上Script "Scene Transition"
![image](https://hackmd.io/_uploads/ryb_DQs6T.png)
2. 創建一個空物件"MoveToNextScene"，為其添加"Box Collider"、"Trigger On Collision"
    * Box Collider裡面的"Is Trigger"需要打勾
3. 使用"Trigger On Collision"，觸發SceneManager的轉場指令。
    * "GoToSceneAsync"所輸入的數字，為Scene在"File"->"Build Settings"中，Scenes in Build底下的數字編號。
    ![image](https://hackmd.io/_uploads/rJfHumoTT.png)
4. 為玩家人物"PlayerCapsule"創建一個新的Layer名為"Player"，以此作為Target Layer Mask。
5. 將MoveToNextScene移動到門的後方，使玩家走出門後觸發轉場。


### 8.1. [補充] 轉場淡入/淡出

我們可以透過淡入/淡出的特效，緩和場景轉換的突兀感。
1. 首先將XRCampUtilities/Prefab/FadeScreen.prefab放入MainCamera底下，並調整z軸，使屏障覆蓋相機。
![image](https://hackmd.io/_uploads/SkcE9QiTa.png)
2. MainCamera中，"Camera"底下有一個"Clipping Planes"，代表畫面只會顯示在距離相機如此範圍內的物體。我們只需將FadeScreen的z軸設得比"Near"的0.2大一些即可。
![image](https://hackmd.io/_uploads/r1xV4omjap.png)
3. 將FadeScreen物件拖曳至SceneManager底下的"Fade Screen"欄位中。 如此，轉換場景時就可以看到淡入淡出的特效了。

        
### 9. 自主練習
    
>**A. 為遊戲添加音效**
>
>* 為物件添加AudioSource，嘗試使用先前的方式觸發音效！
>* 為遊戲加入一個不斷重播的BGM！

# 2024/03/13 Unity (VR&MR)魷魚遊戲

## 目標

承續上週的3D魷魚遊戲，教學如何快速轉換成VR版本與MR版本，並介紹Unity更多有用功能；也會提及美術組與音樂組同學如何協助程式組同學，使專案更加分！

## 所使用到的應用程式、素材與連結

1. [Oculus](https://www.meta.com/zh-tw/help/quest/articles/headsets-and-accessories/oculus-rift-s/install-app-for-link/) -- 使用Oculus頭盔需安裝
2. [Plastic SCM](https://www.plasticscm.com/download) -- Unity專案合作開發需安裝
3. [XRCamp_UnityTutorial_for VR](https://drive.google.com/file/d/1HezLkv2iCJn2gruFJNYR3uj6G1DjMolT/view?usp=drive_link) -- 雲端資料夾。包含助教寫好、VR常用到的Script和工具，以及上課會使用到的音樂素材
4. [Lets Make a VR Game](https://drive.google.com/file/d/1B5qxgxok_B-kHy8oZSXuYUtrMea-BA1t/view) -- 其中包含寫好的VR手部Prefab
(XRCamp_UnityTutorial_for VR已有包含到這包。參考自：[Valem Tutorials](https://www.youtube.com/watch?v=pm9W7r9BGiA&t=614s))
5. XR Interaction Toolkit (包含starter asset)

![image](https://hackmd.io/_uploads/r18mh6Hpa.png)

![image](https://hackmd.io/_uploads/ryiInTHTT.png)

6. [Sketchfab SDK](https://assetstore.unity.com/packages/tools/input-management/sketchfab-for-unity-14302) -- 可以將從Sketchfab上下載之GLTF檔直接匯入Unity的工具

## 上課內容紀錄

### 1. VR遊戲 vs 3D遊戲
* **沉浸感**—360全景、120FOV，遊玩時有「空間感」
* **人機互動**、互動**反饋**
* **不同視角**的體驗 (沙盒、上帝視角等等)
* 更多想像空間 (魔法、劍技、溶解等等)

### 2. Unity VR設定
* 下載Oculus並link至電腦

![image](https://hackmd.io/_uploads/S1Oxg4JRa.png)

* 下載XR Plugin Management

![image](https://hackmd.io/_uploads/r1ThcTHp6.png)

* 使用OpenXR (支援oculus&steamVR)

![image](https://hackmd.io/_uploads/SJ1fjar6T.png)

* Fix/Edit All warning rules

![image](https://hackmd.io/_uploads/HkCFiaBpT.png)

* 選擇使用的裝置Profiles (基本上這堂課是HTC vive/Oculus Touch)

![image](https://hackmd.io/_uploads/HJxKl4JRp.png)

* Package Manager>Unity Registry> **XR Interaction Toolkit** >Install，順便也Import **starter asset**

### 3. 3D to VR

自學/課前：
* [Valem Tutorial](https://youtu.be/HhtTtvBF5bI?si=NWnIc_W4n0ZivR9H)
* [Make Hands in VR](https://www.youtube.com/watch?v=pm9W7r9BGiA&t=614s)
* [Physics in VR](https://www.youtube.com/watch?v=6TW9N7Ie8tA)
* **TextMeshPro Bug：**![image](https://hackmd.io/_uploads/ByfCa8JAT.png)

0314課程紀錄：

### 3.1. 角色控制
1. Camera
    * 右鍵Create-> XR-> XR Origin

    ![image](https://hackmd.io/_uploads/SkLA1PWRp.png)
    * Camera tracking mode: "floor"

      ![image](https://hackmd.io/_uploads/S15jV0B6a.png)

2. Hands(Controller)
    * 設置Controller Profile

    ![image](https://hackmd.io/_uploads/SySBevW0p.png)

    * 把跟Raycast相關的Components從Controller上拔掉

    ![image](https://hackmd.io/_uploads/HJ2jlDb0T.png)

    * 將Oculus Hands(已製作好捏、握的手勢動作)放到Controller底下，使玩家的Controller有模型

    ![image](https://hackmd.io/_uploads/HJI8-vbRp.png)

    * 上述步驟請在Left、Right Controller各做一次
3. Move
    * 在XR Origin的Inspector中新增：
        1. Locomotion System
        2. Character Controller(記得去調整角色的Height喔)
        3. Continuous Move Provider(**Action-based**)
           * 將**Use Gravity**打勾
           * Mode選用**Immediately**
           * Move Speed調至2~4左右即可(視人物、場景大小)
           * 在想給予移動功能的Hand上勾選Use Reference，並在下方貼入**XRI/Hand/Locomotion/Move**之Reference

    ![image](https://hackmd.io/_uploads/BkhsfwZRp.png)
4. Turn
    * 分為連續轉動(Continuous turn)與間斷轉動(Snap turn)，因現實世界的玩家都是使用連續轉動的關係，在遊戲中若使用Continuous turn的話容易導致動暈症的產生(轉動速度不一致)，因此會建議大家以Snap turn為主
    * 與新增Move的方法相似，新增**Snap Turn Provider(Action-based)**
    * 在想給予移動功能的Hand上勾選Use Reference，並在下方貼入**XRI/Hand/Locomotion/Snap turn**之Reference即可

    ![image](https://hackmd.io/_uploads/H1-s4w-06.png)
5. Jump
    * 在VR遊戲中不是那麼建議讓玩家有太過劇烈的動作(避免動暈)，因此Jump的功能在一般**VR劇情遊戲的專案內不會推薦**給大家使用。
    * 但若之後會想製作動作類型的VR遊戲的話，這邊助教有提供一個腳本方便同學製作跳躍的功能。
        1. XRCamp_UnityTutorial_for VR > Script > **Jump Provider**
        2. 將地板(踩的地方)設定一個新Layer，並設定在Ground Layer Mask中
        3. Jump height設定跳躍高度(預設為1)
        4. 自製Reference並放到Jump Action中
        ![image](https://hackmd.io/_uploads/SkOcPPbR6.png)


    ![image](https://hackmd.io/_uploads/BynqUDb0a.png)
    
### 3.2. 場景互動
1. 先介紹一下，在VR遊戲中，互動功能需要兩個角色--
    * Interactor：互動方，在XR Origin中便是兩個Controller(手)
    * Interactable：可被互動方，通常有XR Simple Interactable(**Hover、Select、Activate**)、以及XR **Grab** Interactable
2. 互動時，**會動的一方需要有Rigidbody**(剛體)，**雙方都要有Collider** (碰撞箱/偵測箱)
3. 先新增XR Direct Interactor、Sphere Collider至我們兩個Controller上，並**把Sphere Collider的Is trigger打開**(變成觸發箱而非碰撞箱)


4. 將XR Grab Interactable新增到我們場景中的物件上
(要記得把物件Rigidbody的Use Gravity打開喔，不然拿起放開後會飄來飄去XD)

    
5. [Movement type](https://fistfullofshrimp.com/unity-vr-grab-interactables/)
    * Instantaneous(較常用)：**無視物體的Rigidbody**，且**會穿透任何物體**，會一直黏在手上直到放開為止。
    * Kinematic ：會**有些許的延遲**(不會完全貼在手上)，且會被手的物理性質影響，**會穿透只要是沒有Rigidbody的物體**
    * Velocity Tracking(較真實)：**模擬真實**在拿物體的現象，且會與沒有Rigidbody的物體進行碰撞(也就是說**除了自己額外設定的物體以外都會進行碰撞**)、**不會穿透過去**。

6. 好啦！到目前為止，目前VR場景就有一個可以移動的玩家，以及一個可以拿起來丟來丟去的物件囉~ 
   如果還有時間的話，可以試試看把場景中的其他物件也變成可以互動的物件喔~ (**記得把static關掉**^^)

7. Q. 在互動中如何觸發event?
   A. 
   第一種方式，即是在Interactable Component底下的Interactable Events中，有Hover(碰觸)、Select(捏)、Activate(握)、Focus等等放Event的地方，也就是在物件上觸發。
   
   第二種方式，即是在Controller的Interactor上觸發，那就多了Haptic Event(震動反饋)可以設定。
   
   第三種方式(給那些Coding比較強，想自由一點的同學)，你當然可以使用OntriggerEnter、OnCollisionEnter等方式，利用Hand Contrller的Sphere Collider與物件的Collider碰撞時觸發Script自訂的程式。

    ![image](https://hackmd.io/_uploads/SJ1H3DW0p.png)

    ![image](https://hackmd.io/_uploads/r1PkkO-0a.png)

    ![image](https://hackmd.io/_uploads/HJHopPZRp.png)
### 3.3. UI
1. UI在VR專案中，基本上我們**不會將其放在頭盔眼前顯示**(像是3D遊戲，UI為Screen Space)，一方面是因為控制字幕、圖片在頭盔眼上的清晰度這件事是非常麻煩，每個人的感覺也差很多。
2. 另一方面也是因為使用者在遊玩的時候，頭盔會一直跟著玩家移動、旋轉，若視野底下一直有字幕等UI出現，會使**動暈症**的發生更加容易，體感變差。
3. 因此助教這邊推薦大家使用的是**World Space**的UI，透過有背景顏色的Panel、Image或是特效，上面附有你想要呈現的字幕，在VR頭盔中呈現的感覺會好很多 (記得Canvas的大小要重新設定，通常會小很多)

    ![image](https://hackmd.io/_uploads/HJc3eOZCa.png)

4. 取消原有的Graphic Raycaster，新增**Tracked Device Graphic Raycaster**，使UI在VR空間中能被使用者互動到(例如Button)

    ![image](https://hackmd.io/_uploads/HyezEbdb0T.png)

5. **VR專案中透過World Space的UI去提示玩家目前該怎麼做、要去哪裡，是很重要的元素喔！**


### 3.4. Raycast
1. XR > **Ray Interactor(Action-based)**，新增兩個(左、右)並取名

    ![image](https://hackmd.io/_uploads/H1WhbuWA6.png)

2. 一樣要設定兩隻手分別的Preset
3. 目前兩隻手的Ray便可顯示在我們的VR頭盔中，隨著我們的Controller移動，並也可以使用此Ray interactor來與場景得interactable物件互動喔！
4. Q. 如何讓我們的Raycast在想顯示的時候顯示呢? (加分項目)
   比方說按下Activate(捏，食指按紐)來打開Raycast，其他時候隱藏，使遊戲更完整
   A.
   * 增加Ray Able Controller至XR Origin中
   * 並把XRI/Hand/Activate(兩手)分別放到兩個Action Reference中
   * 將剛剛Create的兩個Ray Interactor放入Left Ray及Right Ray中即可

    ![image](https://hackmd.io/_uploads/B1ADzuWR6.png)

### 3.5. Feedback
1. Vision
    * 上週的fadein/fadeout，也是在VR專案中常常使用在轉場動畫上的一個技巧
    * 一樣將上週製作的FadeScreen加在XR Origin>Main Camera底下就好，然後要記得把FadeScreen的Shader改成**URP/Lit**喔！

    ![image](https://hackmd.io/_uploads/rygTqNubRT.png)

2. Haptic
    * 助教有提供Haptic Interactable的腳本，方便同學使用震動反饋來添增VR遊戲的互動性！
    * 使用方式：添增Script至兩個Controller上，貼好Controller Reference後便可在Game Event或是Unity Event使用此腳本的**HapticActiveOnce**函式來觸發震動
    * 若同學好奇在程式中是怎麼觸發的話，都可以點進去C#檔案查看腳本內容喔~
      助教提供的都是很基礎、常用的C#、Unity語法，特別是程式組的同學可以參考一下！

    ![image](https://hackmd.io/_uploads/H1QdtObAp.png)

    ![image](https://hackmd.io/_uploads/ryCcqd-RT.png)

### 4. 為遊戲加分 (美術、音樂組同學注意！！！)

自學/課前：
* [Mixamo](https://www.mixamo.com/#/)
* [AI: Text to Speech](https://elevenlabs.io/)
* [Particle System](https://www.youtube.com/watch?v=SrWrUN56UWU)

---

### 4.1.  為遊戲添加音樂吧！
1. 音效在Unity中主要是兩個角色在作用
    * Audio Listener：聆聽者，通常會自動加在Main Camera中
    * Audio Source：音源，可放入Audio Clip並調整類似音樂軟體的相關設定，也有空間音效(3D)的多項設定可以設置
2. 注意！！！ Unity基本上只接受**Mp3**以及**Wav**喔
3. 添加BGM (2D音效)
    * 在場景Manager物件中新增Audio Source的Component，並將你的Mp3/Wav放到Audio Clip裡面
    * 將Play On Awake、Loop打勾，遊戲中就有開啟時自動播放且循環播放的背景音啦！

    ![image](https://hackmd.io/_uploads/rkPR6_Z0T.png)
4. 添增音效 (3D音效)
    * 在想要產生聲音的物件(例如麥克風)上加上Audio Source，一樣將音檔放入Audio Clip中
    * 將Spatial Blend設為1，此時這個音源便是一個3D空間音效
    * 3D空間音效在Unity有幾個常用的設定：
        * Volume Rolloff：距離與聲音大小的關係式，預設是對數下降，其他也有像是線性下降的關係是可以選擇
        * Min Distance & Max Distance：Min~Max中間的空間則是可以聽到聲音的範圍，要注意這些數值會跟物體大小有關，因此物件若要有3D音效的話都要親自去做調整

    ![image](https://hackmd.io/_uploads/rymilFZ0p.png)

    * 在Scene視窗中也可以看到Min/Max Distance的範圍，如下圖即為(0.5 ~ 2)

    ![image](https://hackmd.io/_uploads/HyzcMKWCT.png)

    * Q. 如何在Unity Event中觸發音效播放?
      A.
      * 在Unity Event加入Animator.Play()的函示即可，若想在Script裡面控制播放Audio Clip的話，同樣也是使用Animator.Play()喔

      ![image](https://hackmd.io/_uploads/HkpH0Kb06.png)

         
>             public AudioClip[] ballClip;
>             public AudioSource ballSource;

>             ballSource.clip = ballClip[1];
>             ballSource.Play();

### 4.2.  為場景增加一個會動的NPC吧！
1. Sketchfab in Unity
    * 先去下載 [Sketchfab for Unity](https://assetstore.unity.com/packages/tools/input-management/sketchfab-for-unity-14302)
    * 在Unity即可直接載入GLTF模型檔 (若跳出Plugin Update就不用理他，直接關掉該提醒視窗就好)

    ![image](https://hackmd.io/_uploads/r1LnmYbAa.png)

2. Mixamo
    * 找到GLTF匯入Unity後檔案中的模型fbx檔，或是直接在Sketchfab上下載fbx也可(要人形完整的)
    * 匯入[Mixamo](https://www.mixamo.com/#/)

    ![image](https://hackmd.io/_uploads/Hyb8NYbAT.png)

    * 製作完動畫後，匯出成fbx，直接丟進去Unity就大功告成！(可以在匯入的model底下找到剛剛的Animation Clip)

    ![image](https://hackmd.io/_uploads/ryvTNYWCp.png)

3. Model
    * 大小-- 匯入的模型檔太大的話，可以改Scale Factor(先改這個為主，不要直接改場景的Scale，不然Scale數值會太大或太小)

    ![image](https://hackmd.io/_uploads/rJKrHtW0T.png)

    * 材質-- 若發現材質消失的話，可以試試看Use External Material或是Use Embedded Material，再不行的話就直接在Unity內創幾個Material然後重貼進來(適用在模型Material算少的時候)

    ![image](https://hackmd.io/_uploads/SJ1gUt-0a.png)

    * 動畫-- 通常fbx附加的動畫都不是Write able，所以要編輯Animation的一些性質，例如looping、Curve等等簡單的設定可以直接從這邊設定

    ![image](https://hackmd.io/_uploads/SkfYIKZ0a.png)

4. Animation (若同學是在Blender中製作後再匯入Unity的就可以先跳過^^)
    * 在Unity中，產生Animation主要也有兩個角色(怎麼都是兩個XD)--
        * Animation：包含整個動畫內容，時間軸上每個物件的屬性變化、時間軸上的事件觸發等等

        ![image](https://hackmd.io/_uploads/H1PX_YW0T.png)

        * Animator：包含Layer(同時執行不同的動畫流程，一心二用的感覺)、Parameter(控制流程的變數)、流程圖(包含Animation、Transition、Condition)等等

        ![image](https://hackmd.io/_uploads/Byv2dKWCT.png)

    * 把剛剛fbx底下的Animation Clip放入場景中的人物模型上，Unity就會自動生成Animator，並設計好遊戲開始變自動播放該Animation囉！

    ![image](https://hackmd.io/_uploads/SJdaDFW0p.png)
    
    {%youtube xX4DYjD0U8M %}

    * Q. 如何在Unity Event中觸發動畫播放?
      A.
      * 跟Audio source很像，加入Animator.Play()的函示即可，Play的名稱即為想播放的Animation名稱(在流程圖上的，非Clip名稱)

        ![image](https://hackmd.io/_uploads/rJxIKtZA6.png)

      * 設計簡單的流程圖，讓角色觸發完後回到原本的行為動畫

        ![image](https://hackmd.io/_uploads/BJue9Y-Aa.png)

     * **更多有關Animation、Animator的製作，在3/23的Unity工作坊時講師也會介紹喔！**
### 4.3. Particle System (粒子系統)--最近怎麼一直下雨啦
* 透過Light、PostProcessing、Model、UI的場景創建下，我們可以讓EndScene看起來更有憂愁的感覺

    ![image](https://hackmd.io/_uploads/Byy3cKZR6.png)

* 適時增加點天氣效果，例如下雨、迷霧、打雷等等的特效，會使作品更加分！

    ![image](https://hackmd.io/_uploads/H1pgiYWRp.png)

* 大家可以從XRCamp_UnityTutorial_for VR那一包裡面找到下雨的Particle System，直接放入場景就可以用囉！

    ![image](https://hackmd.io/_uploads/BJl2witWCp.png)

* 配合自己的場景大小以及所需的雨量，可以分別在Emission以及Shape的Radius中調整喔

    ![image](https://hackmd.io/_uploads/HkZaitZCT.png)

* **更多有關Particle System的功能介紹，在3/23的Unity工作坊時講師也會介紹喔！**

### 5. 其他

自學/課後：
* [Quest Quick Build (Newest)](https://www.youtube.com/watch?v=paVX3Pm4Yq4)
* [Oculus Gesture](https://www.youtube.com/watch?v=Lc1PuEatrCA)
* Body Skeleton
  若**還有時間**則可以去研究一下身體的部分，有身體的虛擬角色會更有帶入感！
        [Valem Tutorial](https://www.youtube.com/watch?v=tBYl-aSxUe0&list=PLrk7hDwk64-ZRB5lz-xJhgH7Lp6MIRcHJ&pp=iAQB)
* Final IK
  這個Package是包含手、手指以及身體等的終極Module，如果你是**高手的話**則可以嘗試一下！ 
        [Unity Asset Store](https://assetstore.unity.com/packages/tools/animation/final-ik-14290)
* [Multiplayer](https://doc.photonengine.com/fusion/current/tutorials/host-mode-basics/1-getting-started)
---
* Plastic SCM
    * 注意：在製作新進度前、或Push之前要先Pull！！！
    * 建議：Comment最好簡潔有力(寫重點)，也可以再標記一次push的時間點
    * 建議三人分別是兩位程式、一位美術來使用Plastic SCM
    * Q. 如果不只三個人想合作撰寫怎麼辦？
      A. 如果是美術或音樂組的話，程式組可以先生出一個prototype讓他們測試(例如模型大小、整體空間等等是可以先決定的)，製作好模型、場景、動畫或音樂後則可包成Unity Package後匯入到有連結到Plastic SCM的專案中
    * 功能(有學過Git概念的可以自行跳過)
      1. Pull
      **注意：在製作新進度前、或Push之前要先Pull!!!**
      自動Merge其他更變集的資料，如有衝突的話則可能使用到以下兩種情況：
        * choose from Origin  Master : 選擇以本機的更變集為主
        * choose from resources : 選擇以目的地的更變集為主
      請自行與其他組員協調好再執行Pull的動作，否則更變集被覆蓋有時會很難救回來的！
      2. Push
        * 建議每次上傳都打個簡短明瞭的註解
        * Unity會先進行Check in的動作
        * Push前如果想恢復某個物件或檔案修改前的版本，Undo即可
      3. Branch
        * 假設今天非主要開發人員想進行測試或開發新功能，會建議在新的場景或另一個Branch製作
        * 好處是別人不會Pull到你的Branch的東西，也就是沒有Merge或是Unity設定被覆蓋的問題
      4. Switch to workspace
        可以在Plastic SCM應用程式的更變集介面中右鍵某個更變集，並按下Switch to workspace則可將目前的專案還原到當時的版本
        * 還原前必須先將當下的變更Push上去
        * 若確定要還原到該變更，則需把該更變集之後的更變集**全部刪除**！
    * 創建
      1. 下載Plastic SCM雲端版
         [https://www.plasticscm.com/download](https://)
         限制：三人、5Gb內免費
         ![image](https://hackmd.io/_uploads/BkOeTpH6p.png)

      2. 至Plastic SCM網頁版，使用Unity ID登入後，創建一個新的組織並創建Unity Repo
         * 先去Unity Dashboard新增Project
         [https://cloud.unity.com/](https://)
         ![image](https://hackmd.io/_uploads/B1FYAprTp.png)

         * 再到Plastic SCM Dashboard、進入Cloud
         [https://www.plasticscm.com/dashboard](https://)
         ![image](https://hackmd.io/_uploads/BksTppSaT.png)

         * 有出現專案畫面的話就代表專案建立成功囉！
         ![image](https://hackmd.io/_uploads/B186kASTa.png)

         * 現在就可以打開剛下載好的Plastic SCM，確認存儲庫是否有該專案啦


      3. 開啟你想同步的Unity Project，並到Unity Version Control的介面
      4. 填寫相關資訊，包含repo名稱，即步驟2.的專案名
      5. 出現類似下面畫面後則代表你成功了！
      
      ![image](https://hackmd.io/_uploads/HyD86uZ06.png)

      7. 最後一步啦！ 寫下你的第一則Comment、Check in changes並Push就大功告成啦！
    * 邀請
      1. 到Plastic SCM Cloud，點選組織的設定成員功能

         ![image](https://hackmd.io/_uploads/B1IF1CBTT.png)
      3. 利用Gmail邀請你的成員加入組織後，他們就可以在Plastic SCM的應用程式中選擇該組織並找到你的repo進行共編啦！

### 6. 注意與建議

:::success 
注意事項！ 製作專案前有空看看吧！小心踩到這些地雷喔~ (是教授會注意的點^^)
:::
* 避免**動暈症** (順移時角度變化過大、角色旋轉方式、急速移動)

* 畫面過於炫彩(特效、顏色、燈光)，導致**視覺疲乏**

* 遊戲**元素過多**，無法呈現遊玩特色或故事主軸
     (也會使專案loading變重)

* 美術**風格相斥或過多**、與音樂不搭

* 隨時注意遊戲時的fps (最好能維持在**60Hz以上**)

* 若角色有全身的話(除了頭以外)，記得把**影子**拿掉！
    (mesh renderer>lightning

* 有導引玩家的提示會更好！

:::success 
建議です！ 學長姐們修課經驗談~
:::
* **遊戲的操作自由度越大越好、操作方式越少越好、越有創意越好**

* 在VR世界中因場景很大的關係，有時候不會選擇切換整個scene，而是在不同地區使用不同模型、不同效果渲染+fadein/fadeout來轉場。(善用VR世界的環境)

* 美術的部分，要注意素材不要選擇過度high poly的模型，會導致幀數下降，particle system在VR作品中也要慎用

* 一個專案的美術風格盡量維持一~兩種就好，且不要極端
   (lowpoly+highpoly就會很怪)

* 配音的部分，由於同學們並非專業配音員，容易因為聲音含糊或收錄到環境音，而導致玩家出戲、甚至聽不清內容。建議同學可以多加利用免費的 AI文字轉語音工具(TTS)，如： [Elevenlabs](https://elevenlabs.io/)、[ttsmaker](https://ttsmaker.com/zh-hk)、[edge-tts(需使用python，可調性較大)](https://pypi.org/project/edge-tts/)等等。

* VR遊戲中，使用[空間音效(Audio Spatializer)](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)，可以讓玩家透過聲音，定位視野外的物體，為你的故事/玩法創造更多可能性！

* 使用好音樂/音效，可以大幅提升玩家的沉浸感、改變故事的氛圍、甚至可以用來引導玩家以推進劇情！

* 專案到後面script、prefab、package各類檔案會越來越多，記得隨時整理「需要」的檔案，並命名分類，分裝至不同資料夾中。


# 番外篇1. 連結VR頭盔與突發狀況解決方法

* Oculus Quest 2 / 3
    1. Oculus Link (有線)
        步驟1. 下載[Oculus](https://www.meta.com/zh-tw/help/quest/articles/headsets-and-accessories/oculus-rift-s/install-app-for-link/)應用程式並開啟
        步驟2. 頭盔啟用Usb外部存取權(有出現的話)
        步驟3. Enable Oculus Link
        (插上數據線的時候應該會出現，沒有的話去選單手動點選或切換有無線幾次)
        步驟4. 到了白色的大廳就代表成功囉！
        
        ![image](https://hackmd.io/_uploads/S1Oxg4JRa.png)
    2. Air Link（無線）
        步驟1. 下載[Oculus](https://www.meta.com/zh-tw/help/quest/articles/headsets-and-accessories/oculus-rift-s/install-app-for-link/)應用程式並開啟
        步驟2. 將電腦與頭盔連線至同樣網路(電腦分享也可)
        步驟3. 到選單切換成Air Link模式、點選自己電腦的名稱並連線
        步驟4. 連線成功後按下Enable Link
        步驟5. 到了白色的大廳就代表成功囉！
    3. 突發狀況
       * 連線至白色大廳的途中一直轉圈圈進不去
         **解決方法**：頭盔斷開重連，再不行就重新開機
       * 線插進去了卻沒接到Oculus Link
         **解決方法**：頭盔重新開機，電腦將Unity關閉、去系統管理員把所有有關Oculus的程序關閉
         (起碼比電腦重開來得好==)
       * 進入大廳後或是測試途中開始閃爍或卡卡的
         **解決方式**：盡量使用有線的方式Link、或拔掉重連

# 番外篇2. 好用資源及連結

*  專案流程、組內分工/討論工具
    * 約? [約時間網站](https://www.when2meet.com/)
    * 專案流程分工? [Trello](https://trello.com/zh-Hant)
    * 討論工具(圖像式)? 
        1. [Milanote](https://milanote.com/)
        2. [Excalidraw](https://excalidraw.com/)

*  資料與連結整理
    *  程式組
        1. [Unity 論壇](https://forum.unity.com/)
        2. [Unity Document- Script](https://docs.unity3d.com/ScriptReference/)
        3. [Unity 常用語法(較友善XD)](https://www.gameislearning.url.tw/article_content.php?getb=2&foog=9997)
        4. [Steven Hu](https://steven-net.medium.com/)
    *  美術組
        1. [Sketchfab](https://sketchfab.com/feed)
        2. [SpeedTree](https://store.speedtree.com/)
        3. [去背神器](https://www.remove.bg/zh-tw)
        4. [UI Icon](https://www.flaticon.com/)
        5. [Quadspinner](https://quadspinner.com/)
        6. [Pinterest](https://www.pinterest.com/)
        7. [ArtStation](https://www.artstation.com/?sort_by=community&dimension=all)
        8. [Quixel](https://quixel.com/)
    *  音樂組
        1. [小森平：常用音效](https://taira-komori.jpn.org/game01tw.html)
        2. [甘茶音樂工坊：BGM](https://amachamusic.chagasi.com/music_uchiagehanabi.html)
        3. [Text-to-Speech: Elevenlabs](https://elevenlabs.io/)
        4. [音檔裁切](https://mp3cut.net/tw/)
        5. [背景降躁](https://products.aspose.app/audio/zh-hant/remove-background-noise/mp3)

*  Youtube超好用教學
    * Unity基礎 
        1. [Brackeys](https://www.youtube.com/@Brackeys)
        2. [米飯教學室](https://www.youtube.com/watch?v=OZH7GSsLgaE)
        3. [阿空](https://www.youtube.com/@RemptyGame/videos)
    * VR基礎 
        1. [Valem Tutorial](https://www.youtube.com/@ValemTutorials)
        2. [Valem](https://www.youtube.com/@ValemVR)











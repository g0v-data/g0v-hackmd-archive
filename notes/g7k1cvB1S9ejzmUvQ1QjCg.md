# Unity筆記

## 前置

在project settings將coding偏好改visual studio
給手機用的話要在Build setting切換平台(Build Setting還可以為scene增加編號)
切換後在game view裡面去調整鏡頭的長寬(1920x1080)

## 父子物件
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7fc952484739e66d35dcc8139fe6a46e.png)
magic circle & Image是子物件，背景則是父物件
```csharp=
transform.GetChild(0).GameObject
```
將程式碼貼在父物件下表示第一個子物件(由上面例子就是指magic circle)
## GetComponent
```csharp=
GameObject game;
Animator ani;

ani = game.GetComponent<Animator>();
```
這樣就可以將game裡面的animator屬性做事情(播放 停止或是直接改裡面的數值)

## Particle System
render是直接改噴的方式以及粒子材質

得增加新的camera才能避免particle system被canvas擋住，或是改變Order in layer這個數值(改到比canvas大就好了)

Particle System也可以呈現出各種形狀的(圓形)，透過這樣可以比原本放圖片多了一些其他特效(燈光造成的明暗、旋轉)


## Collider&Trigger

依照形狀去選適合的collider，兩者相撞的條件在於**正在動那一方**要有rigid body，rigid body 有三種屬性(static、dynamic、kinematic)，用dynamic要注意重力係數要調0不然會自然往下掉
isTrigger開了之後會穿透，但不會出現碰撞導致的位移
```csharp=
private void OnTriggerEnter2D(){
    ...
}
```

## 淡入淡出(未嘗試)
透過animation的圖片透明度
## 動態模糊(未嘗試)
shader、post-processing profile


## Cinemachine(from package manager)
    camera的一種，可以透過這種方式做到多鏡頭，例如角色在走道某個位置後會切換鏡頭去拍其他地方，或是可以做到第一、二、三人稱視角跟隨(virtual camera)

在這次我是想有震動效果，原先震動效果是透過對canvas進行animation，也就是製作上下左右的快速移動來達到震動的效果，但這會切到你的畫面所以canvas要多預留空間，這次是透過設置cinemachine中的virtual camera去做到，裡面有個叫noise屬性
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1e2211501d1ae9378b039084817a5e42.png)
將noise profile調為6D Shake，amplitude gain是震度，除此之外我也沒動什麼，有其他的方法可以達到震動效果(impulse listener)。
cinemachine有些scripts是內建的，像是cinemachine impulse source就是在震動上會用到的。
這次遇到的問題我沒找出原因。

    依上述步驟設置virtual camera，但卻沒有達到想要的效果，先說解決辦法:改了canvas的render mode從原先的screen space Camera變World space。
    
    不知道是什麼原因但只要將canvas關掉照原本的設置還是可以看到game view裡面有在震動所以可能是canvas 的設定之類的
    
    但在其他專案我用screen-space camera是沒問題的
    
## Audio

## 貝茲曲線


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d1bd1c5f8db1b0210eaf563179933b66.png)


### gizmos(繪製輔助線


### struct vs foreach


### switch-case vs if-else

### codeGPT

### ObjectPool
instantiate & destroy 會太消耗電腦的效能
所以用上object pool去做到預先存取但這個也只是沒有銷毀而是存在scene中
### 匯出匯入
有時會遇到project setting 內的scene編號消失，還有遇到tag消失但某個記錄檔的tag還有所以我認為是我哪邊忘了
如果只是要匯出某個prefab unity會幫你找好它所需的所有asset

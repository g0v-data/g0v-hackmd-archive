# Develop journal

## 分工
- 架構
- Plant
- Npc
- UI (menu?), sound, image

## Bug
- DuckEgg 與 NpcComponent的collision
- Egg可以是負數
- Animal沒有Attack animation
- Gameover判定

## 紀錄
[2021/6/28 15] 初建架構 
[2021/6/28 16] 進行分工工作
[2021/6/28 17] 建立規格
[2021/6/29 16] BlueBird 可以生蛋了！
[2021/6/30 0] BirdHunter 出現了

### 架構
- Entity 定義在 ```AnimalVsNpcType.java``` 裡面
- ```Config.java``` 裡面定義 Npc spawn 座標，以及背景中各個格子的座標位置
- ```AnimalVsNpcApp```裡面先把所有 texture 都load進來，未來要 spawn 的時候再傳進去當參數
- 如果要加入新的 component 可以在 ```initGame()``` 裡面進行初始化
- ```animalComponents``` 儲存所有可以建造出來的 animal 種類
- ```initUI```裡面的 for loop 會把 animal 的圖片並排放在上方的 memu bar
- ```setOnMouseClicked```那邊是設定我們點到上面的ui時會把 selected 設定成某個animal，接下來點擊下方的草地就會把 selected spawn 在那邊
- ```eggs```這個變數宣告在 ```initGameVars()```那邊，用```getip("egg")```可以取得```eggs```這個變數，```bind()```的意思是這個UI會隨時觀測 ```eggs```這個參數的數值，他是javafx內建的 property 的概念，當```eggs```的值改變時會同步顯示在UI
- 我把週期性的動作寫在 ```UnitComponent```裡面了 
- ```@Override
    public void onUpdate(double tpf) {
        if (timer.elapsed(CD)) {
			performAction();
			timer.capture();
		}
	}
	abstract public void performAction();```
- 要繼承```UnitComponent```就需要Override掉 ```performAction()```

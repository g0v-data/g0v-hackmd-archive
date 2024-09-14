# My first HackMD note (change me!)

###### tags: 機器學習演講心得

> 

## :memo: 大分類

### AR/VR/MR

-  VR-影像都假的
-  AR-實體影像裡面有虛擬物體
-  MR-跟AR類似但虛擬物體非常擬真


### Show real player in virtual environment(pose entination)

-  如何在影像裡面找到人物的骨架?
    
    難點在於不知道有多少人，以及每個人的姿勢不同難以辨別
-  demo 1: (2D)套用yolo模型的類神經網路找到人，以深度學習的方式猜到節點高機率存在的點，再猜關節點間如何相鄰以區分每個人，架設圓形場景以紅外線攝影機鎖定位置。
-  demo 2: (3D)同樣用深度學習的方式(CNN)

    CNN的概念:找error function的最小值，解theta，但要解決overfitting的問題

    overfitting原因:資料會有noise
    
    training process: 
    - 假設一個不那麼複雜的模型
    - 把data分成train 跟 test
    - 選擇一個複雜度的模型，去最佳化

- 類神經網路:把訊號一層一層的放進去，每一層的node會找到特徵並以非線性的方式傳遞訊號，最後會把資料分成n類。現在的理論認為深度學習是特徵擷取器，只要結果正確就不用特別定義

- 因為運算需求太大，可以把類神經網路的節點當成眼睛，每個節點只會專注在自己專注的那個區塊(local CNN)，現在我們認為每個節點專注的地方(重要性)會一樣，可以share。

- 例子:裁判手勢預判練習
- 例子2(AR):招牌中的連鎖店招牌判斷，相對CNN，FCN還會還原座標標註出照片中的位置
- Data Augmenatation: 把data微調變成更多可以training的資料

- content creation:玩家可以自己編輯場景
- 4D是場景會動

- 用triplet CNN，input 三個東西: (1) 原物件 (2)合的物件 (3)不合的物件
- 人工智慧開創工人智慧的機會(標記Training data 就填問卷)
- google autodraw:有限制東西都在database，所以他們要doodle master美化塗鴉，生成新的圖片(在database跟現在塗鴉中間取平衡)
- gan模型:兩邊互相對抗，生成完有判別器去測試，再生成更厲害的圖片
- Cross modol:圖片生成聲音或反過來


> Drag-n-drop image from your file system to the editor to paste it!

### Step 3: Invite your team to collaborate!

Click on the <i class="fa fa-share-alt"></i> **Sharing** menu :arrow_upper_right: and invite your team to collaborate on this note!

![permalink setting demo](https://i.imgur.com/PjUhQBB.gif)

- [ ] Register and sign-in to HackMD (to use advanced features :tada: ) 
- [ ] Set Permalink for this note
- [ ] Copy and share the link with your team

:::info
:pushpin: Want to learn more? ➜ [HackMD Tutorials](https://hackmd.io/c/tutorials) 
:::

---

## BONUS: More cool ways to HackMD!

- Table

| Features          | Tutorials               |
| ----------------- |:----------------------- |
| GitHub Sync       | [:link:][GitHub-Sync]   |
| Browser Extension | [:link:][HackMD-it]     |
| Book Mode         | [:link:][Book-mode]     |
| Slide Mode        | [:link:][Slide-mode]    | 
| Share & Publish   | [:link:][Share-Publish] |

[GitHub-Sync]: https://hackmd.io/c/tutorials/%2Fs%2Flink-with-github
[HackMD-it]: https://hackmd.io/c/tutorials/%2Fs%2Fhackmd-it
[Book-mode]: https://hackmd.io/c/tutorials/%2Fs%2Fhow-to-create-book
[Slide-mode]: https://hackmd.io/c/tutorials/%2Fs%2Fhow-to-create-slide-deck
[Share-Publish]: https://hackmd.io/c/tutorials/%2Fs%2Fhow-to-publish-note

- LaTeX for formulas

$$
x = {-b \pm \sqrt{b^2-4ac} \over 2a}
$$

- Code block with color and line numbers：
```javascript=16
var s = "JavaScript syntax highlighting";
alert(s);
```

- UML diagrams
```sequence
Alice->Bob: Hello Bob, how are you?
Note right of Bob: Bob thinks
Bob-->Alice: I am good thanks!
Note left of Alice: Alice responds
Alice->Bob: Where have you been?
```
- Auto-generated Table of Content
[ToC]

> Leave in-line comments! [color=#3b75c6]

- Embed YouTube Videos

{%youtube PJuNmlE74BQ %}

> Put your cursor right behind an empty bracket {} :arrow_left: and see all your choices.

- And MORE ➜ [HackMD Tutorials](https://hackmd.io/c/tutorials)

# LNA note 

###### `Pipi Chen's note`

## :memo: 共源級(Common-Source Stage)
> :+1:輸入Gate端in，輸出從Drain端出來。相較於其他架構具有較低NF(noise Figure)、較高的Gain與容易進行阻抗匹配
> :-1:電路線性度差、具有High Gain同時輸入的頻寬較窄(narrow band)
>![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_486cfda8d1d5cc307d0757719a5ecac9.png)
>右圖的輸入阻抗為
$$
 Z_{in}= {1 \over sC_{gs}}
$$
可以從上式發現輸入阻抗在低頻時很高，但是隨著頻率增加，阻抗會隨之下降，又可以從上式發現 $C_{gs}$ 為G&D端的寄生電容，可知輸入阻抗被此主宰。
>頻率不變下，改變電晶體AREA :arrow_right:控制輸入阻抗 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_518bba5e535fb544fe6d5a3382b2f859.png)
CS-amp的輸出增益為
$$
Gain=-g_mR_D
$$
>把 $g_m$ 控制在0.2ms :arrow_right:輸入阻抗50 $\Omega$ 






## :memo: 源極退化電感(Source Degeneration)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7298d006169c286cab7fe2ed21694066.png)
>Source Degeneration架構的輸入阻抗與Gain分別為
$$
Z_{in}={{1 \over sC_{gs}}+sL_s}
$$
$$
Gain={-g_mR_D \over 1+sL_sg_m}
$$
>由上述可知，雖然增益下降了1 + $𝑠𝐿_𝑠𝑔_𝑚$倍，但是輸入阻抗增加了
$𝑠𝐿_𝑠$，讓我們可以更容易實現輸入阻抗匹配，也可以補償在高頻時輸入阻抗的衰減

## :memo: 共閘級(Common-Gate Stage)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_80aaa2f9940ddc8b095e99d30a835dbf.png)
















### Step 1: Change the title and add a tag

- [x] Create my first HackMD note (this one!)
- [ ] Change its title
- [ ] Add a tag

:rocket: 

### Step 2: Write something in Markdown

Let's try it out!
Apply different styling to this paragraph:
**HackMD gets everyone on the same page with Markdown.** ==Real-time collaborate on any documentation in markdown.== Capture fleeting ideas and formalize tribal knowledge.

- [x] **Bold**
- [ ] *Italic*
- [ ] Super^script^
- [ ] Sub~script~
- [ ] ~~Crossed~~
- [x] ==Highlight==

:::info
:bulb: **Hint:** You can also apply styling from the toolbar at the top :arrow_upper_left: of the editing area.

![](https://i.imgur.com/Cnle9f9.png)
:::

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

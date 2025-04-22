---
tags: edu
---

# Vue 上課4/22

### 安裝

```python
1. 網路如果太慢, 陸續裝完即可
npm install npm -g
npm list -g
npm install -g @vue/cli
npm install -g serve

if hang, click ctrl+c

npm list -g
+-- @vue/cli@5.0.8
+-- npm@11.3.0
`-- serve@14.2.4

2. http://firebase.google.com/
用gmail登入(即可)

3. 安裝vscode extension
Name: Vue - Official
Id: Vue.volar
Description: Language Support for Vue
Version: 2.2.8
Publisher: Vue
VS Marketplace Link: https://marketplace.visualstudio.com/items/?itemName=Vue.volar


Name: HTML Boilerplate
Id: sidthesloth.html5-boilerplate
Description: A basic HTML5 boilerplate snippet generator.
Version: 1.1.1
Publisher: sidthesloth
VS Marketplace Link: https://marketplace.visualstudio.com/items/?itemName=sidthesloth.html5-boilerplate
```

### 創建第一個程式
```htmlembedded=
index.html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <title></title>
        <meta name="description" content="">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <link rel="stylesheet" href="">
    </head>
    <body>
        <label for="plan">plan</label>
        <input type="text" id="plan">
        <button>Add a plan</button>
        <ul>
            <!--content will be added here-->
        </ul>
        <script src="app.js" async defer></script>
    </body>
</html>

```

```javascript=
// get button
const button1 = document.querySelector('button')
const input1 = document.querySelector('input')
const list1 = document.querySelector('ul')
function addPlan() {
    const v = input1.value
    const i = document.createElement('li')
    i.textContent = v
    list1.appendChild(i)
    input1.value=''
}
button1.addEventListener('click', addPlan) // function name, not exection result
```
```java 
執行 找到cmd後 輸入
serve .
    
記住要是cmd模式 而非Power Shell
```


### 創建第一個VUE程式
```htmlembedded=
index.html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <title></title>
        <meta name="description" content="">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <link rel="stylesheet" href="">
    </head>
    <body>
        <label for="plan">plan</label>
        <input type="text" id="plan">
        <button>Add a plan</button>
        <ul>
            <!--content will be added here-->
        </ul>
        <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script> <!-- -->
        <script src="app.js" async defer></script>
    </body>
</html>




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

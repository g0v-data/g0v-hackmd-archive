# Vue 上課4/23

### 效能不佳的方法


```htmlembedded=
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title></title>
    <meta name="description" content="">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="">
    <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
</head>

<body>
    <section id="app">
        <input type="text" v-bind:value="issue" v-on:input="setIssue">
        <p>你要處理的是:{{issue}}</p>
        <button v-on:click="resetIssue">clear issue</button>
        <hr />
        <input type="text" v-model="task">
        <p>你的任務是:{{task}}</p>
        <button v-on:click="resetTask">clear task</button>
        <hr />
        <p>counter:{{counter}}</p>
        <button @click="increase">+1</button>
        <hr />
        <h3>顯示變數</h3>
        <p>{{outputIssue()}}</p>
    </section>

    <script src="app.js" async defer></script>
</body>

</html>

```


v-on:click 和 @click 的差別：

✅ 兩者的功能完全一樣！
它們都是 綁定點擊事件 的方法，差別只在於語法上的「簡寫與否」。
```javascript=
const app = Vue.createApp({
    data() {
        return {
            issue: "default issue",
            task: 'learn vue',
            counter: 0
        }
    },
    methods: {
        setIssue(event) {
            this.issue = event.target.value
        },
        resetIssue() {
            this.issue = ''
        },
        resetTask() {
            this.task = 'learn vue'
        },
        increase() {
            this.counter += 1;
        },
        outputIssue() {
            console.log("output called, issue=", this.issue)
            if (this.issue === "") {
                return "";
            }
            return "!!" + this.issue
        }
    }
})

app.mount('#app')

```
這邊的 outputIssue() 是一個函式調用，而不是像 {{ issue }} 這樣單純綁定變數。

💡 Vue 的模板是 reactive 的
每當 Vue 偵測到任何 依賴的資料有變動（例如 issue、counter 之類的）時，它就會重新執行 template 裡所有的函式調用，來重新渲染畫面。

🔁 所以發生了什麼？
你按了 +1，呼叫了 increase()。
counter 改變，Vue 偵測到資料變動。
Vue 重新 render 整個 <section id="app">。
在 render 過程中，會執行 {{ outputIssue() }}。
所以你看到 console.log("output called, issue=", this.issue) 又印出來了！
    
再補充
🔁 {{ outputIssue() }}：自動執行，因為是函式調用（函式被當成內容）
🖱️ <button v-on:click="resetIssue">clear issue</button>：不會自動執行，因為是事件綁定
    
使用computed
```javascript=
    computed:{
        outputIssue() {
            console.log("格式化issue=", this.issue)
            if (this.issue === "") {
                return "";
            }
            return "!!" + this.issue
        }
    }
需要注意 Html也要改 沒有括號
       <h3>顯示變數</h3>
        <p>{{outputIssue}}</p>
```
    
使用watch來做監聽
```htmlembedded=
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title></title>
    <meta name="description" content="">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="">
    <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
</head>

<body>
    <section id="app">
        <input type="text" v-bind:value="issue" v-on:input="setIssue">
        <p>你要處理的是:{{issue}}</p>
        <button v-on:click="resetIssue">clear issue</button>
        <hr />
        <input type="text" v-model="task">
        <p>你的任務是:{{task}}</p>
        <button v-on:click="resetTask">clear task</button>
        <hr />
        <p>counter:{{counter}}</p>
        <button @click="increase">+1</button>
        <hr />
        <h3>顯示變數</h3>
        <p>{{formatIssue}}</p>
    </section>

    <script src="app.js" async defer></script>
</body>

</html>
    
```
    
```javascript=
const app = Vue.createApp({
    data() {
        return {
            issue: "default issue",
            task: 'learn vue',
            counter: 0
        }
    },
    methods: {
        setIssue(event) {
            this.issue = event.target.value
        },
        resetIssue() {
            this.issue = ''
        },
        resetTask() {
            this.task = 'learn vue'
        },
        increase() {
            this.counter += 1;
        },
    },
    computed: {
        formatIssue() {
            console.log("格式化issue=", this.issue)
            if (this.issue === "") {
                return "";
            }
            return "!!" + this.issue
        }
    },
    watch: {
        counter(v) {
            console.log(`new counter set as ${v}`)
            if (v > 10) {
                this.counter = 0
                console.log("counter reset")
            }
        }
    }
})

app.mount('#app')
```
一直按下increase後連續加10次
counter 會被歸零 記得在watch內要用this
    

### 使用css
```css=
.demo {
    width: calc(80% - 32px);  /* 修正：加上空格 */
    height: 80px;
    margin: 12px;
    border: 4px dashed #DDD;
}
    
```
```htmlembedded=
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title></title>
    <meta name="description" content="">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="styles.css">
    <!~-在這import-->
    <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
</head>

<body>
    <section id="app">
        <div class="demo" style="border-color:green;" @click="divSelect(1)">Mountain</div>
        <div class="demo" style="border-color:blue;" @click="divSelect(2)">Ocean</div>
        <div class="demo" style="border-color:red;" @click="divSelect(3)">Sun</div>
    </section>
    <script src="app.js" async defer></script>
</body>

</html>
```
    
```javascript
const app = Vue.createApp({
    data() {
        return {
            div1Selected: false,
            div2Selected: false,
            div3Selected: false
        }
    },
    methods: {
        divSelect(divId) {
            if (divId === 1) {
                this.div1Selected = true;
            } else if (divId === 2) {
                this.div2Selected = true;
            } else if (divId === 3) {
                this.div3Selected = true;
            }
        }
    }
})

app.mount('#app')
```
這個一開始沒有click也是會變色的原因是
為什麼會一開始就變色？
在你的情況中，CSS 應該是在點擊後動態更新邊框顏色，但因為 div1Selected, div2Selected, div3Selected 這些變數的初始值為 false，Vue 的 響應式系統會在頁面渲染時自動處理綁定的樣式。具體來說，你在模板中對 divSelected 這些屬性進行條件綁定樣式，當它們是 false 時，會顯示預設的顏色，這就導致了「畫面一開始就顯示顏色」的情況。
    
之後要換這種寫法 才會改成點一下才變色
```htmlembedded
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title></title>
    <meta name="description" content="">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="styles.css">
    <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
</head>

<body>
    <section id="app">
        <div class="demo" :style="{borderColor: div1Selected?'green':'#DDD'}" @click="divSelect(1)">Mountain</div>
        <div class="demo" :style="{borderColor: div2Selected?'blue':'#DDD'}" @click="divSelect(2)">Ocean</div>
        <div class="demo" :style="{borderColor: div3Selected?'red':'#DDD'}" @click="divSelect(3)">Sun</div>
    </section>
    <script src="app.js" async defer></script>
</body>

</html>
```
    
解決方法：
1. 預設顏色設置：
你需要確保初始時邊框顏色是黑色，然後在點擊時才會變色。

2. 動態綁定邊框顏色：
利用 Vue 的 動態綁定來控制每個 div 的邊框顏色。你可以根據 div1Selected、div2Selected、div3Selected 的狀態來決定每個 div 的顏色。

    
### 用class來判斷 
有點的時候 給兩個class屬性is1Selected和demo
沒點的時候是只有demo
有點擊時做divSelect(1)
```htmlembedded
        <div  :class="div1Selected? 'demo is1Selected':'demo'" @click="divSelect(1)">Mountain</div>
        <div  :class="div2Selected? 'demo is2Selected':'demo'" @click="divSelect(2)">Ocean</div>
        <div  :class="div3Selected? 'demo is3Selected':'demo'" @click="divSelect(3)">Sun</div>


```
    
VS 
```htmlembedded
        <div  :class="{demo:true,is1Selected:div1Selected}" @click="divSelect(1)">Mountain</div>
        <div  :class="{demo:true,is2Selected:div2Selected}" @click="divSelect(2)">Ocean</div>
        <div  :class="{demo:true,is3Selected:div3Selected}" @click="divSelect(3)">Sun</div>
```
第一種寫法（條件運算符寫法）較簡潔，適合簡單的條件判斷。
    
第二種寫法（物件寫法）更具靈活性，適合條件較多的情況，可以控制更多的 class。
    
維護性上較優 不過如果判斷簡單 可以用第一種
第一種寫法簡潔明瞭，適合簡單的條件判斷，對於只有一個條件的情況來說非常直觀。
    
第二種寫法可能稍微冗長一些，但如果你有多個條件來控制類名，它會變得更具可讀性和維護性。
在第二種寫法中，{ demo: true, is1Selected: div1Selected } 表示你不僅要控制 is1Selected 是否應用，還可以靈活地控制 demo 類名的應用，這對於複雜的邏輯來說會更加方便。

    
### 想做到一直點就能變色
```htmlembedded
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title></title>
    <meta name="description" content="">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="styles.css">
    <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
</head>

<body>
    <section id="app">
        <div  class="demo" :class="{is1Selected:div1Selected}" @click="divSelect(1)">Mountain</div>
        <div  class="demo" :class="{is2Selected:div2Selected}" @click="divSelect(2)">Ocean</div>
        <div  class="demo" :class="{is3Selected:div3Selected}" @click="divSelect(3)">Sun</div>
    </section>
    <script src="app.js" async defer></script>
</body>

</html>
```

```javascript
const app = Vue.createApp({
    data() {
        return {
            div1Selected: false,
            div2Selected: false,
            div3Selected: false
        }
    },
    methods: {
        divSelect(divId) {
            if (divId === 1) {
                this.div1Selected = !this.div1Selected;
            } else if (divId === 2) {
                this.div2Selected = !this.div2Selected;
            } else if (divId === 3) {
                this.div3Selected = !this.div3Selected;
            }
        }
    }
})

app.mount('#app')
    
```
    
![](https://g0v.hackmd.io/_uploads/r1g5aSJIylx.png)
這樣的寫法不好需要computed幫忙



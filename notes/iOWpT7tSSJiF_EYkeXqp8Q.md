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
counter 會被歸零 記得在watch內要用this.counter
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
這樣的寫法不好 需要computed幫忙
    
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
    },
    computed: {
        div1Classes() {
            return { is1Selected: this.div1Selected }
        },
        div2Classes() {
            return { is2Selected: this.div2Selected }
        },
        div3Classes() {
            return { is3Selected: this.div3Selected }
        }
    }
})

app.mount('#app')
```
    

### v-if的用法
```htmlembedded
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
        <input type="text" v-model="courseContext" />
        <button @click="addCourse">add a course</button>

        <p v-if="courses.length === 0">No course</p>
        <ul v-else>
            <li>course</li>
        </ul>

    </section>
    <script src="app.js" async defer></script>
</body>

</html>
    
```
```javascript
const app = Vue.createApp({
    data() {
        return {
            courses: [],
            courseContext: ""
        }
    },
    computed: {},
    methods: {
        addCourse() {
            this.courses.push(this.courseContext)
        }
    }
})
app.mount('#app')
```
可以改用v-show
```htmlembedded
<p v-show="courses.length === 0">No course</p>
        <ul v-show="courses.length > 0">
            <li>course</li>
        </ul>
    
```

### v-for的用法

```htmlmixed=
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
        <input type="text" v-model="courseContext" />
        <button @click="addCourse">add a course</button>

        <p v-show="courses.length === 0">No course</p>
        <ul v-show="courses.length > 0">
            <li v-for="(c,idx) in courses">{{c}} at location {{idx}}</li>
        </ul>
        <hr/>
        <ul>
            <li v-for="v in {name:'poop',duration:35}">{{v}}</li>
        </ul>
        <hr/>
        <ul>
            <li v-for="(v,k) in {name:'poop',duration:35}">
                key={{k}},value={{v}}</li>
        </ul>

    </section>
    <script src="app.js" async defer></script>
</body>

</html>
    
```
這邊介紹了兩種用法 一種是一般迴圈一種是增強行迴圈
兩種寫法各有不同

    
### 使用splice刪除陣列
```htmlmixed=
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
        <input type="text" v-model="courseContext" />
        <button @click="addCourse">add a course</button>

        <p v-show="courses.length === 0">No course</p>
        <ul v-show="courses.length > 0">
            <li v-for="(c,idx) in courses"
            @click="removeCourse(idx)">{{c}} at location {{idx}}</li>
        </ul>
        <hr/>
        <ul>
            <li v-for="v in {name:'poop',duration:35}">{{v}}</li>
        </ul>
        <hr/>
        <ul>
            <li v-for="(v,k) in {name:'poop',duration:35}">
                key={{k}},value={{v}}</li>
        </ul>

    </section>
    <script src="app.js" async defer></script>
</body>

</html>
    
```
```javascript=
const app = Vue.createApp({
    data() {
        return {
            courses: [],
            courseContext: ""
        }
    },
    computed: {},
    methods: {
        addCourse() {
            this.courses.push(this.courseContext)
            this.courseContext = ""
        },
        removeCourse(idx) {
            console.log(111);
            this.courses.splice(idx, 1)
        }
    }
})
app.mount('#app')
    
```
    
### 怎樣不要隨意觸發
假設文字旁邊多一個輸入視窗 我們想要保留數出視窗不要刪掉
使用stop
```htmlmixed=
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
        <input type="text" v-model="courseContext" />
        <button @click="addCourse">add a course</button>

        <p v-show="courses.length === 0">No course</p>
        <ul v-show="courses.length > 0">
            <li v-for="(c,idx) in courses"
            @click="removeCourse(idx)">{{c}} at location {{idx}}
        <input type="text" @click.stop/></li>
        </ul>
        <hr/>
        <ul>
            <li v-for="v in {name:'poop',duration:35}">{{v}}</li>
        </ul>
        <hr/>
        <ul>
            <li v-for="(v,k) in {name:'poop',duration:35}">
                key={{k}},value={{v}}</li>
        </ul>

    </section>
    <script src="app.js" async defer></script>
</body>

</html>
```
    
### 再次練習使用v-for讀取資料
```htmlmixed=
<ul>
            <li>
                <h2>POOP</h2>
                <button>show details</button>
                <ul>
                    <li>Python OOP</li>
                    <li>35</li>
                </ul>
            </li>
            <li>
                <h2>BDPY</h2>
                <button>show details</button>
                <ul>
                    <li>Python and big data</li>
                    <li>35</li>
                </ul>
            </li>
        </ul>
    
=>
        <ul>
            <li v-for="course in courses" :key="course.id">
                <h2>{{course.id}}</h2>
                <button @click="toggleCourseDetail">show details</button>
                <ul v-if="detailsVisible">
                    <li>{{course.name}}</li>
                    <li>{{course.duration}}</li>
                </ul>
            </li>
        </ul>
```
但這樣點及按鈕時會有問題，因為click事件觸發時會統一進行(物件同樣)
需要建立不同物件，故要學習使用Component
    
### Component的使用
    
```htmlembedded=
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
    <title>Document</title>
</head>

<body>
    <section id="app">
        <ul>
            <course-content></course-content>
            <course-content></course-content>
            <course-content></course-content>
            <course-content></course-content>
        </ul>
    </section>
    <script src="app.js" async defer></script>
</body>

</html>
    
```
```javascript=
const app = Vue.createApp({
    data() {
        return {
            courses: [
                { id: "POOP", name: "Python OOP", duration: 35 },
                { id: "BDPY", name: "Python and big data", duration: 35 }
            ],
            detailsVisible: true
        }
    },
    methods: {
        toggleCourseDetail() {
            this.detailsVisible = !this.detailsVisible
        }
    }
})
app.component("course-content", {
    template: `
<li>
    <h2>{{course.id}}</h2>
    <button @click="toggleCourseDetail">show details</button>
    <ul v-if="detailsVisible">
        <li>{{course.name}}</li>
        <li>{{course.duration}}</li>
    </ul>
</li>
    `,
    data() {
        return {
            detailsVisible: true,
            course: { id: "POOP", name: "Python OOP", duration: 35 }
        }
    },
    methods: {
        toggleCourseDetail() {
            this.detailsVisible = !this.detailsVisible
        }
    }
})
app.mount('#app')

```
    
### vue-cli安裝
```shell=
vue create lab10_vue3_cli_component
mirror (Y)
Default vue3

code lab10_vue3_cli_component
npm run serve
```
    
### vue-vite安裝
```shell=
cd C:\Users\Admin\Desktop\vue_lab_0422

npm init vue@latest
cd lab10_vue3_vite_component
    
```
![](https://g0v.hackmd.io/_uploads/r1wq-XLJge.png)

    
![](https://g0v.hackmd.io/_uploads/Sye1pZmIklx.png)
    
### 創建第一個cli程式
```javascript=
<template>
    <div>
        <h1>課程簡介</h1>
    </div>
</template>

<script>
    export default {
        
    }
</script>

<style lang="scss" scoped>

</style>
    
```
同理可以新增Coomputeo的模式
```javascript=
新增CourseIntro.vue
<template>
    <div>
        <h1>課程簡介</h1>
    </div>
</template>

<script>
    export default {
        
    }
</script>

<style lang="scss" scoped>

</style>
```
改成這樣呼叫
```javascript=
      <h1>課程列表</h1>
      <course-intro></course-intro>
      <course-intro></course-intro>
      <course-intro></course-intro>
```
main.js也需要修改
```javascript=
import { createApp } from 'vue'
import App from './App.vue'
import CourseIntro from './CourseIntro.vue'

const app = createApp(App)
app.component("course-intro", CourseIntro)
app.mount("#app");
```
    
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


### 創建第一個VUE3程式
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
    <div id="myapp">
        <label for="plan">plan</label>
        <input type="text" id="plan" v-model="value">
        <button v-on:click="addPlan">Add a plan</button>
        <ul>
            <li v-for="plan in plans">{{plan}}</li>
            <!--1lIO0-->
            <!--content will be added here-->
        </ul>
    </div>
    <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
    <script src="app.js" async defer></script>
</body>

</html>

```

```javascript
Vue.createApp({
    data() {
        return {
            plans: [],
            value: ''
        }
    },
    methods: {
        addPlan(){
            this.plans.push(this.value)
        }
    }
}).mount('#myapp')

Vue.createApp的結構().mount()
初始化Option API
data=> reactive 的Object
methods=> 成員函數
之後就會創造一個VUE物件

```
![](https://g0v.hackmd.io/_uploads/H1WVoKNklg.png)


![](https://g0v.hackmd.io/_uploads/S1lEUstN1gx.png)


### 創建第一個VUE2程式
HTML的寫法一樣 只是改src import的部分
Create Vue的方式不同

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
</head>

<body>
    <div id="myapp">
        <label for="plan">plan</label>
        <input type="text" id="plan" v-model="value">
        <button v-on:click="addPlan">Add a plan</button>
        <ul>
            <li v-for="plan in plans">{{plan}}</li>
            <!--1lIO0-->
            <!--content will be added here-->
        </ul>
    </div>
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <script src="app.js" async defer></script>
</body>

</html>
```

```javascript
var vue = new Vue({
    el: '#myapp',
    data() {
        return {
            plans: [],
            value: ''
        }
    },
    methods: {
        addPlan() {
            this.plans.push(this.value)
            this.value = ''
        }
    }
})

```


### VUE3 綁定變數名稱

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
        <section id="my-planner">
            <h2>Yearly plan</h2>
            <p>{{primaryGoal}}</p>
        </section>
        <script src="app.js" async defer></script>
    </body>
</html>
```

```javascript
const app = Vue.createApp(
    {
        data: function () {
            return {
                primaryGoal: "Have a happy life!"
            }
        }
    }
)
app.mount('#my-planner')

```
在my-planner底下，建立VUE的時候回傳物件primaryGoal
{{ }} VUE會看得懂

#### 超連結


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
        <script src="app.js" async defer></script>
    </head>
    <body>
        <section id="my-planner">
            <h2>Yearly plan</h2>
            <p>{{primaryGoal}}</p>
            <p> goto: <a v-bind:href="plainLink">{{plainLink}}</a></p>
        </section>
        
    </body>
</html>
```
```javascript
const app = Vue.createApp(
    {
        data: function () {
            return {
                primaryGoal: "Have a happy life!",
                plainLink: "http://www.uuu.com.tw"
            }
        }
    }
)
app.mount('#my-planner')

```


比較
```htmlembedded=
<p> goto: <a href >{{plainLink}}</a></p> 純粹文字顯示
<p> goto: <a href="plainLink">{{plainLink}}</a></p> 雖然有超連結 但只是連結到字串 "plainLink"
<p> goto: <a v-bind:href="plainLink">{{plainLink}}</a></p>
正確寫法 連結到data bind
```

#### 呼叫方法
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
        <section id="my-planner">
            <h2>Yearly plan</h2>
            <p>{{primaryGoal}}</p>
            <p> goto: <a v-bind:href="plainLink">{{plainLink}}</a></p>
           <!-- <p> goto: <a href="plainLink">{{plainLink}}</a></p> -->
           <p>{{3+3}}</p>
           <p>{{ getNumber() }}</p>
           <p>{{ outputMessage() }}</p>
        </section>
        <script src="app.js" async defer></script>
    </body>
</html>
```
{{}}內可以執行一些方法
3+3 可以執行指令但不能做判斷式
呼叫app的getNumber outputMessage 方法

```javascript
const app = Vue.createApp(
    {
        data: function () {
            return {
                primaryGoal: "Have a happy life!",
                plainLink: "http://www.uuu.com.tw"
            }
        },
        methods: {
            getNumber() {
                return 7
            },
            outputMessage: function () {
                const number1 = Math.random();
                if (number1 < 0.5) {
                    return 'work hard'
                } else {
                    return 'work harder'
                }
            }
        }
    }
)
app.mount('#my-planner')

```

#### 使用this存取變數 以及在裡面用html語法

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
        <section id="my-planner">
            <h2>Yearly plan</h2>
            <p> goto: <a v-bind:href="plainLink">{{plainLink}}</a></p>
            <p>{{3+3}}</p>
            <p>{{ getNumber() }}</p>
            <p>{{ outputMessage() }}</p>
            <p v-html="outputMessage()"></p>
        </section>
        <script src="app.js" async defer></script>
    </body>
</html>
```

```javascript
const app = Vue.createApp(
    {
        data: function () {
            return {
                primaryGoal1: "Have a <em>happy</em> life!",
                primaryGoal2: "Have a <em>health</em> body!",
                primaryGoal3: "Have a <em>strong</em> mind!",
                plainLink: "http://www.uuu.com.tw"
            }
        },
        methods: {
            getNumber() {
                return 7
            },
            outputMessage: function () {
                const number1 = Math.random();
                if (number1 < 0.3) {
                    return this.primaryGoal1
                } else if (number1 < 0.6) {
                    return this.primaryGoal2
                } else {
                    return this.primaryGoal3
                }
            }
        }
    }
)
app.mount('#my-planner')

```
直接用產出的文字會失敗，需要v-html
![](https://g0v.hackmd.io/_uploads/BJxGU3NJll.png)


#### 使用ON事件
這個寫法不好 因為在html內使用的程式加減 建議挪去APP做事
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
    <script src="app.js" async defer></script>
</head>

<body>
    <section id="lab4">
        <button v-on:click="counter1++">+1</button>
        <button v-on:click="counter1--">-1</button>
        <p>Result:{{counter1}}</p>
    </section>

</body>

</html>
```

```javascript
const app = Vue.createApp({
    data(){
        return {counter1:0}
    }
})

app.mount('#lab4')

```
比較好的寫法是方法放在app內
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
    <script src="app.js" async defer></script>
</head>

<body>
    <section id="lab4">
        <button v-on:click="increase1()">+1</button>
        <button v-on:click="decrease1()">-1</button>
        <p>[3]Result:{{counter1}}</p>
    </section>

</body>

</html>
```

```javascript
const app = Vue.createApp({
    methods: {
        increase1() {
            setTimeout(() => {
                this.counter1 = this.counter1 + 1
            }, 1000)

        },
        decrease1() {
            this.counter1 = this.counter1 - 1
        }
    },
    data() {
        return { counter1: 0 }
    }
})

app.mount('#lab4')

```
increase1 和 decrease1也可以傳入參數



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
    <script src="app.js" async defer></script>
</head>

<body>
    <section id="lab4">
        <button v-on:click="increase(1)">+1</button>
        <button v-on:click="decrease(1)">-1</button>
        <button v-on:click="increase(2)">+2</button>
        <button v-on:click="decrease(2)">-2</button>
        <p>[3]Result:{{counter1}}</p>
    </section>

</body>

</html>
```

```javascript
const app = Vue.createApp({
    methods: {
        increase(step) {
            setTimeout(() => {
                this.counter1 = this.counter1 + step
            }, 100)

        },
        decrease(step) {
            setTimeout(() => {
                this.counter1 = this.counter1 - step
            }, 100)
        }
    },
    data() {
        return { counter1: 0 }
    }
})

app.mount('#lab4')

```
#### 使用ON事件來聆聽input事件
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
    <section id="lab4">
        <button v-on:click="increase(1)">+1</button>
        <button v-on:click="decrease(1)">-1</button>
        <button v-on:click="increase(2)">+2</button>
        <button v-on:click="decrease(2)">-2</button>
        <p>[3]Result:{{counter1}}</p>
        <hr />
        <input type="text" v-on:input="setTodo">
        <p>What do you expect to do? {{todo}}</p>
    </section>
    <script src="app.js" async defer></script>
</body>

</html>
```
同樣todo為app的變數直接使用

```javascript
const app = Vue.createApp({
    methods: {
        setTodo(event) { 
            this.todo = event.target.value
        },
        increase(step) {
            setTimeout(() => {
                this.counter1 = this.counter1 + step
            }, 100)

        },
        decrease(step) {
            setTimeout(() => {
                this.counter1 = this.counter1 - step
            }, 100)
        }
    },
    data() {
        return {
            counter1: 0,
            todo: ''
        }
    }
})

app.mount('#lab4')

```
event.target.value 是標準寫法
event: 使用者觸發的事件物件（像是點擊、輸入等等）
target: 事件發生的那個 DOM 元素（也就是哪個元素觸發了事件）
value: 那個元素的「值」，例如 <input> 裡面的文字


#### 傳入多個變數
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
    <script src="app.js" async defer></script>
</head>

<body>
    <section id="lab4">
        <button v-on:click="increase(1)">+1</button>
        <button v-on:click="decrease(1)">-1</button>
        <button v-on:click="increase(2)">+2</button>
        <button v-on:click="decrease(2)">-2</button>
        <p>[3]Result:{{counter1}}</p>
        <hr />
        <input type="text" v-on:input="setTodo($event, 'I want to:')">
        <p>What do you expect to do? {{todo}}</p>
    </section>

</body>

</html>
```
這句話可以翻譯成：
當使用者在這個輸入框打字時（input 事件），執行 setTodo 這個方法，並把兩個參數傳進去：
$event：事件物件（包含觸發事件的元素、輸入的值等等）
'I want to:'：你手動傳入的字串
```javascript
const app = Vue.createApp({
    methods: {
        setTodo(event, greeting) { 
            this.todo = `${greeting},${event.target.value}`
        },
        increase(step) {
            setTimeout(() => {
                this.counter1 = this.counter1 + step
            }, 100)

        },
        decrease(step) {
            setTimeout(() => {
                this.counter1 = this.counter1 - step
            }, 100)
        }
    },
    data() {
        return {
            counter1: 0,
            todo: ''
        }
    }
})

app.mount('#lab4')

```
從 event.target.value 取得使用者輸入的文字
把 greeting（你手動傳的字串）加在前面
設定到 Vue 組件裡的 todo 變數


#### FormSubmit

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
    <script src="app.js" async defer></script>
</head>

<body>
    <section id="lab4">
        <button v-on:click="increase(1)">+1</button>
        <button v-on:click="decrease(1)">-1</button>
        <button v-on:click="increase(2)">+2</button>
        <button v-on:click="decrease(2)">-2</button>
        <p>[3]Result:{{counter1}}</p>
        <hr />
        <input type="text" v-on:input="setTodo($event, 'I want to:')">
        <p>What do you expect to do? {{todo}}</p>
        <hr />
        <form v-on:submit="submitForm">
            <input type="text">
            <button>log in</button>
        </form>
    </section>

</body>

</html>
```

```javascript=
const app = Vue.createApp({
    methods: {
        submitForm() {
            alert('已經提交了')
        },
        setTodo(event, greeting) { 
            this.todo = `${greeting},${event.target.value}`
        },
        increase(step) {
            setTimeout(() => {
                this.counter1 = this.counter1 + step
            }, 100)

        },
        decrease(step) {
            setTimeout(() => {
                this.counter1 = this.counter1 - step
            }, 100)
        }
    },
    data() {
        return {
            counter1: 0,
            todo: ''
        }
    }
})

app.mount('#lab4')

```
如果不想要重刷畫面 有
  e.preventDefault()
和<form v-on:submit.prevent="submitForm2"> 兩種方法


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
    <script src="app.js" async defer></script>
</head>

<body>
    <section id="lab4">
        <button v-on:click="increase(1)">+1</button>
        <button v-on:click="decrease(1)">-1</button>
        <button v-on:click="increase(2)">+2</button>
        <button v-on:click="decrease(2)">-2</button>
        <p>[3]Result:{{counter1}}</p>
        <hr />
        <input type="text" v-on:input="setTodo($event, 'I want to:')">
        <p>What do you expect to do? {{todo}}</p>
        <hr />
        <form v-on:submit="submitForm">
            <input type="text">
            <button>log in</button>
        </form>
        <form v-on:submit.prevent="submitForm2">
            <input type="text">
            <button>Sign Up</button>
        </form>
    </section>

</body>

</html>
```

```javascript=
const app = Vue.createApp({
    methods: {
        submitForm(e) {
            console.log(e)
            e.preventDefault()
            alert('已經提交了')
        },
        submitForm2() {
            alert('已經提交了2')
        },
        setTodo(event, greeting) { 
            this.todo = `${greeting},${event.target.value}`
        },
        increase(step) {
            setTimeout(() => {
                this.counter1 = this.counter1 + step
            }, 100)

        },
        decrease(step) {
            setTimeout(() => {
                this.counter1 = this.counter1 - step
            }, 100)
        }
    },
    data() {
        return {
            counter1: 0,
            todo: ''
        }
    }
})

app.mount('#lab4')

```
右鍵click事件
```htmlembedded=
       <button v-on:click="increase(1)">+1</button>
        <button v-on:click="decrease(1)">-1</button>
        <button v-on:click="increase(2)">+2</button>
        <button v-on:click="decrease(2)">-2</button>
        <button v-on:click.right="increase(3)">+3</button>
        <button v-on:click.right="decrease(3)">-3</button>
```


 
 輸入和ENTER事件
 ```htmlembedded=
        <input type="text" v-on:input="setUrgent" 
               v-on:keyup.enter="commitUrgent">
        <p>current urgent issue:{{urgent}}</p>
        <p>committed Urgent Issue:{{checkedUrgent}}</p>
```
 
<input type="text" v-on:input="setUrgent" v-on:keyup.enter="commitUrgent">

是指輸入的時候觸發 setUrgent 方法
然後按鈕按下ENTER後觸發commitUrgent 方法

```javascript=
const app = Vue.createApp({
    methods: {
        submitForm(e) {
            console.log(e)
            e.preventDefault()
            alert('已經提交了')
        },
        submitForm2() {
            alert('已經提交了2')
        },
        setTodo(event, greeting) {
            this.todo = `${greeting},${event.target.value}`
        },
        increase(step) {
            setTimeout(() => {
                this.counter1 = this.counter1 + step
            }, 100)

        },
        decrease(step) {
            setTimeout(() => {
                this.counter1 = this.counter1 - step
            }, 100)
        },
        commitUrgent() {
            this.checkedUrgent = this.urgent
        },
        setUrgent(e) {
            this.urgent = e.target.value
        }
    },
    data() {
        return {
            counter1: 0,
            todo: '',
            urgent: '',
            checkedUrgent: ''
        }
    }
})

app.mount('#lab4')
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
    <link rel="stylesheet" href="">
    <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
    <script src="app.js" async defer></script>
</head>

<body>
    <section id="lab4">
        <button v-on:click="increase(1)">+1</button>
        <button v-on:click="decrease(1)">-1</button>
        <button v-on:click="increase(2)">+2</button>
        <button v-on:click="decrease(2)">-2</button>
        <button v-on:click.middle="increase(3)">+3</button>
        <button v-on:click.middle="decrease(3)">-3</button>
        <p>[3]Result:{{counter1}}</p>
        <hr />
        <input type="text" v-on:input="setTodo($event, 'I want to:')">
        <p>What do you expect to do? {{todo}}</p>
        <hr />
        <form v-on:submit="submitForm">
            <input type="text">
            <button>log in</button>
        </form>
        <form v-on:submit.prevent="submitForm2">
            <input type="text">
            <button>Sign Up</button>
        </form>
        <hr />
        <input type="text" v-on:input="setUrgent" v-on:keyup.enter="commitUrgent">
        <p>current urgent issue:{{urgent}}</p>
        <p>committed Urgent Issue:{{checkedUrgent}}</p>
        <hr />
        <p v-once>initial value={{counter2}}</p>
        <p>current value={{counter2}}</p>

        <button v-on:click="increase2(4)">+4</button>
        <button v-on:click="decrease2(4)">-4</button>
    </section>

</body>

</html>
  ```
 ```javascript=
 const app = Vue.createApp({
    methods: {
        submitForm(e) {
            console.log(e)
            e.preventDefault()
            alert('已經提交了')
        },
        submitForm2() {
            alert('已經提交了2')
        },
        setTodo(event, greeting) {
            this.todo = `${greeting},${event.target.value}`
        },
        increase(step) {
            setTimeout(() => {
                this.counter1 = this.counter1 + step
            }, 100)

        },
        decrease(step) {
            setTimeout(() => {
                this.counter1 = this.counter1 - step
            }, 100)
        },
        commitUrgent() {
            this.checkedUrgent = this.urgent
        },
        setUrgent(e) {
            this.urgent = e.target.value
        },
        increase2(step) {
            this.counter2 = this.counter2 + step;
        },
        decrease2(step) {
            this.counter2 -= step;
        }
    },
    data() {
        return {
            counter1: 0,
            todo: '',
            urgent: '',
            checkedUrgent: '',
            counter2: 666
        }
    }
})

app.mount('#lab4')
  ```
 
 
✅什麼是 v-once？
v-once 告訴 Vue：「這個元素只渲染一次，初次掛載時拿資料，之後即使資料變了，也不要更新它」。
適合用在你只想顯示「初始資料」的情況，例如 loading 前的靜態畫面、初始狀態快照等等。
 
 
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
            <input type="text" v-on:input="setIssue">
            <p>你要處理的是:{{issue}}</p>
        </section>
        
        <script src="app.js" async defer></script>
    </body>
</html>
 ```
 
```javascript=
   const app = Vue.createApp({
    data() {
        return {
            issue: ""
        }
    },
    methods: {
        setIssue(event) {
            this.issue = event.target.value
        }
    }
})

app.mount('#app')
   ```
   
複習時間: 我的html呼叫setIssue沒有event傳入
但app.js的第8行需要EVENT 為什麼這樣可以
✅ Vue 的自動行為：事件物件會自動傳入

但如果你的方法是
```javascript=
<!-- 這樣就不能自動傳 event，必須自己寫 $event -->
<input @input="handleInput('hello')" /> <!-- 這裡 event 不會自動傳！ -->

<!-- 正確的做法應該是 -->
<input @input="handleInput($event, 'hello')" />
```
 
 #### 使用V-MODEL
 
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
            task: 'learn vue'
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
        }
    }
})

app.mount('#app')
```
使用V-MODEL的好處就是不用自己在寫Set值的方法
就是這麼乾淨俐落 ✨

Vue 會自動幫你：
綁定 input 的值（value）到 message
監聽 input 事件
在使用者輸入時自動更新 message 這個變數


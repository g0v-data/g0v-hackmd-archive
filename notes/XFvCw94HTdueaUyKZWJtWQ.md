# Vue 上課4/24

### Import components

局部註冊：你可以完全不在 main.js 做任何事情，只在 App.vue 中註冊組件 A 和 B。這樣做是可以的，但只會在 App.vue 或其子組件中有效。

全局註冊：如果你希望組件 A 和 B 在應用的任何地方都能使用，則應該在 main.js 中進行全局註冊。這樣可以避免在每個需要使用這些組件的地方重複 import 和註冊。

App.vue 是單一的組件，它的組件和註冊的組件只會在這個文件中有效。因此，如果你在 App.vue 中引入並註冊了 A 和 B，它們只會在 App.vue 和其子組件中有效。

main.js 是整個應用的入口文件，它用來設置和初始化應用，包括全局註冊組件、插件、路由等等。如果你選擇不在 main.js 做任何事，那麼你就無法在其他組件中全局使用 A 和 B，只能在 App.vue 中使用它們。

![](https://g0v.hackmd.io/_uploads/HJjq7fDkeg.png)

可以在Main註冊全局


```javascript=
import { createApp } from 'vue'
import App from './App.vue'
import CourseIntro from './components/CourseIntro.vue'

const app = createApp(App)
app.component("course-intro", CourseIntro)
app.mount("#app");
```
引用的時候CourseIntro吃到全局
ContactInfo是局部
```javascript=
<template>
  <div>
      <h1>課程列表</h1>

      <CourseIntro></CourseIntro>
      <CourseIntro></CourseIntro>
      <hr/>
      <ContactInfo></ContactInfo>
  </div>
</template>

<script>
import CourseIntro from '@/components/CourseIntro.vue';
import ContactInfo from '@/components/ContactInfo.vue';

export default {
  components: { CourseIntro,ContactInfo }
}
</script>

<style>
#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

#app li {
  width: 50%;
  max-width: 40rem;
  text-align: center;
  border-radius: 5px;
  box-shadow: 0  4px 8px rgba(0,0,128,0.26);
}
</style>
```


在CourseIntro.vue的上方有li ul button的tag
然後app.vue就會吃到

```javascript=
<template>
    <li>
        <h2>{{ course.id }}</h2>
        <button @click="toggleCourseDetail">show details</button>
        <ul v-if="detailsVisible">
            <li>{{ course.name }}</li>
            <li>{{ course.duration }}</li>
        </ul>
    </li>
</template>

<script>
export default {
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
}
</script>

<style lang="scss" scoped></style>
```

原本的資料大家都一樣用props幫忙SET值

```javascript=
<template>
    <li>
        <h2>{{ id }}</h2>
        <button @click="toggleCourseDetail">show details</button>
        <ul v-if="detailsVisible">
            <li>{{ name }}</li>
            <li>{{ duration }}</li>
        </ul>
    </li>
</template>

<script>
export default {
    props: ["id", "name", "duration"],
    data() {
        return {
            detailsVisible: true,
        }
    },
    methods: {
        toggleCourseDetail() {
            this.detailsVisible = !this.detailsVisible
        }
    }
}
</script>

<style scoped></style>
```

![](https://g0v.hackmd.io/_uploads/Hk8R4XDJgx.png)

    
### Props 可以給型別跟檢核
```javascript=
props: { id: String, name: String, duration: Number, current: Boolean },
```
```javascript=
<template>
    <li>
        <h2>{{ id }}--[isCurrent-->{{ isCurrent }}]</h2>
        <p>[current -->{{ current }}]</p>
        <button @click="toggleIsCurrent">toggle isCurrent</button>
        <button @click="toggleCourseDetail">show details</button>
        <ul v-if="detailsVisible">
            <li>{{ name }}</li>
            <li>{{ duration }}</li>
        </ul>
    </li>
</template>

<script>
export default {
    props: {
        id: { type: String, required: true },
        name: { type: String, required: true },
        duration: {
            type: String, required: true, validator: function (v) {
                return parseInt(v) > 7;
            }
        }, current: { type: String, required: false, default: "false" }
    },
    data() {
        return {
            detailsVisible: true,
            isCurrent: this.current // current是isCurrent的初始值
        }
    },
    methods: {
        toggleCourseDetail() {
            this.detailsVisible = !this.detailsVisible
        },
        toggleIsCurrent() {
            this.isCurrent = !this.isCurrent;
        }
    }
}
</script>

<style scoped></style>
```
在app.vue中如果有人設定成5，會報錯
```javascript=
        <CourseIntro duration="5"></CourseIntro>
```

![](https://g0v.hackmd.io/_uploads/SyiFdXPyxg.png)

### 可以用v-for來傳遞資料

```javascript=
<template>
  <div>
      <h1>課程列表</h1>
      <course-intro v-for="c in courses"
      :key="c.id"
      :id="c.id"
      :name="c.name"
      :duration="c.duration"
      :current="c.current">
      </course-intro>
      <hr/>
      <ContactInfo></ContactInfo>
  </div>
</template>

<script>
import CourseIntro from '@/components/CourseIntro.vue';
import ContactInfo from '@/components/ContactInfo.vue';

export default {
  components: { CourseIntro, ContactInfo },
  data() {
      return {
          courses: [
              { id: "poop", name: "python oop", duration: 35, current: true },
              { id: "bdpy", name: 'python and big data', duration: 35, current: false }
          ]
      }
  }
}
</script>

<style>
#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

#app li {
  width: 50%;
  margin: 1rem auto;
  max-width: 40rem;
  text-align: center;
  border-radius: 5px;
  box-shadow: 0 4px 8px rgba(0, 0, 128, 0.26);
}

#app button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #FF0077;
  background-color: #c0ffee;
  color: black;
}
</style>
```

### 在子元件的直無法改變 要用emit
```javascript=
  <div>
      <h1>課程列表</h1>
      <course-intro v-for="c in courses"
      :key="c.id"
      :id="c.id"
      :name="c.name"
      :duration="c.duration"
      :current="c.current">
      </course-intro>
      <hr/>
      <ContactInfo></ContactInfo>
  </div>

```
雖然可以顯示 但子元件並無法改變 需使用emit事件觸發

![](https://g0v.hackmd.io/_uploads/Hyl-nxVPkgl.png)

1. 當點擊按鈕觸發時觸發click事件去做toggleIsCurrent
2. 因為送了emit事件 會再去觸發toggle-current
3. toggle-current設定會去用toggleCurrent
4. toggleCurrent就會去改動
5. 要注意toggleCurrent需要的傳入參數就是emit時要傳入的

```javascript=
<template>
    <li>
        <h2>{{ id }}--[isCurrent-->{{ current }}]</h2>
        <button @click="toggleCurrent">toggle isCurrent</button>
        <button @click="toggleCourseDetail">show details</button>
        <ul v-if="detailsVisible">
            <li>{{ name }}</li>
            <li>{{ duration }}</li>
        </ul>
    </li>
</template>

<script>
export default {
    props: {
        id: { type: String, required: true },
        name: { type: String, required: true },
        duration: {
            type: Number, required: true, validator: function (v) {
                return v > 7;
            }
        },
        current: { type: Boolean, required: false, default: false }
    },
    data() {
        return {
            detailsVisible: true,
        }
    },
    methods: {
        toggleCourseDetail() {
            this.detailsVisible = !this.detailsVisible
        },
        toggleCurrent() {
            this.$emit('toggle-current', this.id)
        }
    }
}
</script>

<style scoped></style>
```

```javascript=
<template>
  <div>
      <h1>課程列表</h1>
      <course-intro v-for="c in courses" :key="c.id" :id="c.id" :name="c.name" :duration="c.duration"
          :current="c.current" @toggle-current="toggleCurrent">
      </course-intro>
      <hr />
      <ContactInfo></ContactInfo>
  </div>
</template>

<script>
import CourseIntro from '@/components/CourseIntro.vue';
import ContactInfo from '@/components/ContactInfo.vue';

export default {
  components: { CourseIntro, ContactInfo },
  data() {
      return {
          courses: [
              { id: "poop", name: "python oop", duration: 35, current: true },
              { id: "bdpy", name: 'python and big data', duration: 35, current: false }
          ]
      }
  },
  methods: {
      toggleCurrent(id) {
          //alert(`toggle fired with id=${id}`)
          const c = this.courses.find(c => c.id === id)
          c.current = !c.current;
          console.log(`now ${id} course current status:${c.current}`)
      }
  }
}
</script>

<style>
#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

#app li {
  width: 50%;
  margin: 1rem auto;
  max-width: 40rem;
  text-align: center;
  border-radius: 5px;
  box-shadow: 0 4px 8px rgba(0, 0, 128, 0.26);
}

#app button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #FF0077;
  background-color: #c0ffee;
  color: black;
}
</style>
```

### 使用mitt
![](https://g0v.hackmd.io/_uploads/rkFQvNwkxl.png)

一個用來傳遞害修改物件的套驗
需要再main.js初始
```javascript=
import { createApp } from 'vue'
import App from './App.vue'

import mitt from 'mitt'
const emitter = mitt()
const app = createApp(App)
app.config.globalProperties.emitter = emitter;
app.mount('#app')
```

```javascript=
<template>
  <div>
      <h1>課程列表</h1>
      <course-intro v-for="c in courses" :key="c.id" :id="c.id" :name="c.name" :duration="c.duration"
          :current="c.current" @toggle-current="toggleCurrent">
      </course-intro>
      <hr />
      <ContactInfo></ContactInfo>
  </div>
</template>

<script>
import CourseIntro from '@/components/CourseIntro.vue';
import ContactInfo from '@/components/ContactInfo.vue';

export default {
  created() {
      console.log("App created, prepare mietter")
      this.emitter.on("togget-current", (idx) => {
          console.log(`${idx} will change status`)
      })
  },
  components: { CourseIntro, ContactInfo },
  data() {
      return {
          courses: [
              { id: "poop", name: "python oop", duration: 35, current: true },
              { id: "bdpy", name: 'python and big data', duration: 35, current: false }
          ]
      }
  },
  methods: {
      toggleCurrent(id) {
          //alert(`toggle fired with id=${id}`)
          const c = this.courses.find(c => c.id === id)
          c.current = !c.current;
          console.log(`now ${id} course current status:${c.current}`)
      }
  }
}
</script>

<style>
#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

#app li {
  width: 50%;
  margin: 1rem auto;
  max-width: 40rem;
  text-align: center;
  border-radius: 5px;
  box-shadow: 0 4px 8px rgba(0, 0, 128, 0.26);
}

#app button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #FF0077;
  background-color: #c0ffee;
  color: black;
}
</style>
```

### 比較原本的方法和mitt
```javascript=
      <button @click="toggleCurrent">emit Current</button>
        <button @click="mittCurrent">mitt Current</button>

emit工作原理要看上面的解說
        toggleCurrent() {
            this.$emit('toggle-current', this.id)
        },
            
        mittCurrent() {
            console.log("mitt send a event")
            this.emitter.emit('toggle-current', this.id)
        }
```
### 可以自己多定義emit的方法
```javascript!
export default {
    //emits:['toggle-current'],
    emits: {
        "toggle-current": function (id) {
            if (id) {
                return true;
            } else {
                console.warn("id is missing")
                return false;
            }
        }
    },


```

### 新增元件按鈕實作

```javascript=
app.vue多了
<new-course></new-course>
然後再多一個
import NewCourse from './components/NewCourse.vue';

裡面是
<template>
    <form>
        <div>
            <label>id</label>
            <input type="text"/>
        </div>
        <div>
            <label>name</label>
            <input type="text"/>
        </div>
        <div>
            <label>duration</label>
            <input type="text"/>
        </div>
        <div>
            <button>Add a course</button>
        </div>
    </form>
</template>

<script>
    export default {
        
    }
</script>

<style scoped>

</style>
```

但這樣子很醜 可以針對from再給css
```javascript=
#app li, #app form {
    width: 50%;
    margin: 1rem auto;
    max-width: 40rem;
    text-align: center;
    border-radius: 5px;
    box-shadow: 0 4px 8px rgba(0, 0, 128, 0.26);
}
```
先在NewCourse給定框架

```javascript=
<template>
    <form>
        <div>
            <label>id</label>
            <input type="text" />
        </div>
        <div>
            <label>name</label>
            <input type="text" />
        </div>
        <div>
            <label>duration</label>
            <input type="text" />
        </div>
        <div>
            <button>Add a course</button>
        </div>
    </form>
</template>

<script>
export default {
    emits: ["add-course"],
    data() {
        return {
            inputId: '',
            inputName: '',
            inputDuration: ''
        }
    },
    methods: {
        submitData() {
            this.$emit("add-course", this.inputId, this.inputName, this.inputDuration)
        }
    }
}
</script>

<style scoped></style>
```

同理可用alert確認傳入參數是否有近來
```javascript=
      submitData() {
            alert(this.inputId + this.inputName + this.inputDuration)
            this.$emit("add-course", this.inputId, this.inputName, this.inputDuration)
        }
```

綁定方法
```javascript=
    <new-course @add-course="addCourse"></new-course>
```

```javascript=
<template>
    <new-course @add-course="addCourse"></new-course>
    <course-intro v-for="c in courses" :key="c.id" :id="c.id" :name="c.name" :duration="c.duration" :current="c.current"
        @toggle-current="toggleCurrent">
    </course-intro>
    <hr />
    <ContactInfo></ContactInfo>
</template>

<script>
import CourseIntro from '@/components/CourseIntro.vue';
import ContactInfo from '@/components/ContactInfo.vue';
import NewCourse from './components/NewCourse.vue';

export default {
    created() {
        console.log("App created, prepare mietter")
        this.emitter.on("toggle-current", (idx) => {
            console.log(`${idx} will change status`)
            const c = this.courses.find(c => c.id === idx)
            c.current = !c.current;
        })
    },
    components: { CourseIntro, ContactInfo, NewCourse },
    data() {
        return {
            courses: [
                { id: "poop", name: "python oop", duration: 35, current: true },
                { id: "bdpy", name: 'python and big data', duration: 35, current: false }
            ]
        }
    },
    methods: {
        toggleCurrent(id) {
            //alert(`toggle fired with id=${id}`)
            const c = this.courses.find(c => c.id === id)
            c.current = !c.current;
            console.log(`now ${id} course current status:${c.current}`)
        },
        addCourse(id, name, duration) {
            const newCourse = { id, name, duration, current: false }
            this.courses.push(newCourse)
        }
    }
}
</script>

<style>
#app ul {
    margin: 0;
    padding: 0;
    list-style: none;
}

#app li,
#app form {
    width: 50%;
    margin: 1rem auto;
    max-width: 40rem;
    text-align: center;
    border-radius: 5px;
    box-shadow: 0 4px 8px rgba(0, 0, 128, 0.26);
}

#app button {
    font: inherit;
    cursor: pointer;
    border: 1px solid #FF0077;
    background-color: #c0ffee;
    color: black;
}
</style>
```

### 新增刪除方法
先在CourseIntro.vue新增框架
```javascript=

        "delete-current": function (id) {

            if (id) {

                return true;

            } else {

                console.warn("id is missing");

            }

        }

        deleteCourse() {

            this.$emit("delete-current", this.id)

        }
```

在app.vue呼叫 刪除該ID
```javascript=
       deleteCourse(id) {

            this.courses = this.courses.filter((c) => c.id != id)

        }
```
完整
```javascript=
<template>
    <new-course @add-course="addCourse"></new-course>
    <course-intro v-for="c in courses" :key="c.id" :id="c.id" :name="c.name" :duration="c.duration" :current="c.current"
        @toggle-current="toggleCurrent" @delete-current="deleteCourse">
    </course-intro>
    <hr />
    <ContactInfo></ContactInfo>
</template>

<script>
import CourseIntro from '@/components/CourseIntro.vue';
import ContactInfo from '@/components/ContactInfo.vue';
import NewCourse from './components/NewCourse.vue';

export default {
    created() {
        console.log("App created, prepare mietter")
        this.emitter.on("toggle-current", (idx) => {
            console.log(`${idx} will change status`)
            const c = this.courses.find(c => c.id === idx)
            c.current = !c.current;
        })
    },
    components: { CourseIntro, ContactInfo, NewCourse },
    data() {
        return {
            courses: [
                { id: "poop", name: "python oop", duration: 35, current: true },
                { id: "bdpy", name: 'python and big data', duration: 35, current: false }
            ]
        }
    },
    methods: {
        toggleCurrent(id) {
            //alert(`toggle fired with id=${id}`)
            const c = this.courses.find(c => c.id === id)
            c.current = !c.current;
            console.log(`now ${id} course current status:${c.current}`)
        },
        addCourse(id, name, duration) {
            const newCourse = { id, name, duration, current: false }
            this.courses.push(newCourse)
        },
        deleteCourse(id) {
            this.courses = this.courses.filter((c) => c.id != id)
        }
    }
}
</script>

<style>
#app ul {
    margin: 0;
    padding: 0;
    list-style: none;
}

#app li,
#app form {
    width: 50%;
    margin: 1rem auto;
    max-width: 40rem;
    text-align: center;
    border-radius: 5px;
    box-shadow: 0 4px 8px rgba(0, 0, 128, 0.26);
}

#app button {
    font: inherit;
    cursor: pointer;
    border: 1px solid #FF0077;
    background-color: #c0ffee;
    color: black;
}
</style>
```

------------------
### composition API

第一個範例使用了 選項式 API (Options API)：
```javascript=
<template>
    <div>
        <h1>options ==> composition</h1>
        <p>{{ userName }}</p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            userName: "Mark Ho"
        }
    }
}
</script>

<style scoped></style>
```
第二個範例使用了 組合式 API (Composition API)，並透過 setup 函式來實現：
setup 函式是組件邏輯的入口點。你可以在 setup 函式中定義並暴露組件所需的響應式資料、計算屬性、方法和生命週期鉤子。最後，你需要明確地回傳一個包含你想在模板中使用的值的物件。

```javascript=
<template>
  <div>
    <h1>(options) ==> composition</h1>
    <p>{{ userName }}</p>
  </div>
</template>

<script>
export default {
  setup () {
    const userName = "Kevin Lee"
    return { userName }
  }
}
</script>

<style lang="scss" scoped>

</style>

```

ref 是 Vue 3 組合式 API 中一個非常重要的工具，它用於創建一個響應式的資料持有者
```javascript=
<template>
    <div>
        <h1>(options) ==> composition</h1>
        <p>{{ userName }}</p>
    </div>
</template>

<script>
import {ref} from 'vue'
export default {
    setup() {

        const userName = ref("Kevin Lee")
        console.log("userName=", userName.value)
        setTimeout(() => {
            userName.value = "Min-Che Lee"
            console.log("userName=", userName.value)
        }, 5000)
        return { userName }
    }
}
</script>

<style lang="scss" scoped></style>
```

1.import { ref } from 'vue'： 這行程式碼從 vue 模組中引入了 ref 函式。

2.const userName = ref("Kevin Lee")：

你呼叫了 ref 函式，並將初始值 "Kevin Lee" 傳遞給它。
ref 函式會回傳一個物件，這個物件被賦值給 userName 變數。
這個 userName 物件並不是直接儲存字串 "Kevin Lee"，而是擁有一個 .value 屬性，而這個 .value 屬性才是真正儲存 "Kevin Lee" 的地方。更重要的是，當 .value 的值發生改變時，所有在模板中綁定到 userName 的地方都會自動更新，這就是「響應式」的意義。
console.log("userName=", userName.value)：

3.這段程式碼設定了一個在 5 秒後執行的非同步操作。
在回調函式中，你將 userName.value 的值修改為 "Min-Che Lee"。


### reactive
對於單個基本類型值（例如數字、字串、布林值），通常使用 ref。
對於物件或陣列，如果你希望直接響應式地存取和修改其屬性，那麼使用 reactive 會更方便。當你使用 ref 包裹一個物件或陣列時，你需要透過 .value 來存取這個物件或陣列本身，然後再操作其屬性或元素。

### 沒用reactive
```javascript=
<template>
    <div>
        <h1>(options) ==> composition</h1>
        <p>{{ userName }}</p>
        <p>age={{ age }}</p>
        <hr/>
        <p>{{ course }}</p>
    </div>
</template>

<script>
import { ref } from 'vue'
export default {
    setup() {
        const userName = ref("Kevin Lee")
        const age = ref(19)
        console.log("userName=", userName.value)
        const course = {front:'vue',backend:'spring boot'}
        const reactiveCourse = ref(course)
        setTimeout(() => {
            userName.value = "Min-Che Lee"
            console.log("userName=", userName.value)
            reactiveCourse.value.front = 'vue 3.5'
            setTimeout(() => {
                age.value += 1
                reactiveCourse.value.backend = 'spring boot 3.4'
            }, 3000)
        }, 3000)
        return { userName, age, course:reactiveCourse }
    }
}
</script>

<style lang="scss" scoped></style>
```

### 有用
```javascript=
<template>
    <div>
        <h1>(options) ==> composition</h1>
        <p>{{ userName }}</p>
        <p>age={{ age }}</p>
        <hr />
        <p>{{ course }}</p>
        <p>不建議==>{{ course.front }}/{{ course.backend }}</p>
        <p>not reactive==>{{ frontEndTech }}/{{ backEndTech }}</p>
        <p>{{ instructor }}</p>
        <p>{{ instructor.firstName }}/{{ instructor.lastName }}</p>
    </div>
</template>

<script>
import { ref, reactive } from 'vue'
export default {
    setup() {
        const userName = ref("Kevin Lee")
        const age = ref(19)
        console.log("userName=", userName.value)
        const course = { front: 'vue', backend: 'spring boot' }
        const reactiveCourse = ref(course)
        const instructor = { firstName: "Mark", lastName: "Ho" }
        const reactiveInstructor = reactive(instructor)
        setTimeout(() => {
            userName.value = "Min-Che Lee"
            console.log("userName=", userName.value)
            reactiveCourse.value.front = 'vue 3.5'
            reactiveInstructor.firstName = "Meng-Hang"
            setTimeout(() => {
                age.value += 1
                reactiveCourse.value.backend = 'spring boot 3.4'
                reactiveInstructor.lastName = "何"
            }, 3000)
        }, 3000)
        return {
            userName, age, course: reactiveCourse,
            instructor: reactiveInstructor,
            frontEndTech:reactiveCourse.value.front,
            backEndTech:reactiveCourse.value.backend
        }
    }
}
</script>

<style lang="scss" scoped></style>
```

### setup 和 setup script
```
<script setup> 是 Vue 3 推薦的組合式 API 使用方式，因為它提供了更簡潔、
更符合直覺的語法，減少了樣板程式碼，並提高了開發效率。
它在功能上與傳統的 setup 函式完全相同，只是在語法層面上進行了優化。
在新的 Vue 3 專案中，通常會優先使用 <script setup>。
```
    
```javascript=
<template>
    <div>
        <h1>options ==> (composition) script setup</h1>
        <p>{{ userName }}</p>
        <p>age={{ age }}</p>
        <hr />
        <p>{{ reactiveCourse }}</p>
        <p>不建議==>{{ reactiveCourse.front }}/{{ reactiveCourse.backend }}</p>
        <p>{{ reactiveInstructor }}</p>
        <p>{{ reactiveInstructor.firstName }}/{{ reactiveInstructor.lastName }}</p>

    </div>
</template>

<script setup>
import { ref, reactive } from 'vue'
const userName = ref("Kevin Lee")
const age = ref(19)
console.log("userName=", userName.value)
const course = { front: 'vue', backend: 'spring boot' }
const reactiveCourse = ref(course)
const instructor = { firstName: "Mark", lastName: "Ho" }
const reactiveInstructor = reactive(instructor)
setTimeout(() => {
    userName.value = "Min-Che Lee"
    console.log("userName=", userName.value)
    reactiveCourse.value.front = 'vue 3.5'
    reactiveInstructor.firstName = "Meng-Hang"
    setTimeout(() => {
        age.value += 1
        reactiveCourse.value.backend = 'spring boot 3.4'
        reactiveInstructor.lastName = "何"
    }, 3000)
}, 3000)

</script>

<style scoped></style>
```
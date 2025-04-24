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
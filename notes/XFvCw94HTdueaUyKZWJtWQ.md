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

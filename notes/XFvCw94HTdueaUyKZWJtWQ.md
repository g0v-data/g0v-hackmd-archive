# Vue 上課4/23

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
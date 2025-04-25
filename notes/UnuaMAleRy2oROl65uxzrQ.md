# Vue 上課4/25

### reactive的用法 續
```javascript=
<template>
  <div>
      <h3>{{ course }}</h3>
      <button @click="course.duration = course.duration + 7">加課</button>
  </div>
</template>

<script>
import { reactive } from "vue"
export default {
  setup() {
      const course = reactive({ name: "POOP", duration: 35 })
這一行做的事是：
建立一個物件 { name: "POOP", duration: 35 }
用 reactive() 包起來
所以 course 變成一個「可被追蹤改變的物件」
      return { course: course }
  }
}
</script>

<style lang="scss" scoped></style>

```
🔁 為什麼不用 ref()？
Vue 3 裡還有另一種做響應式的方式叫 ref()，那是用來包「原始型別」資料（像是 number、string 等）。
如果你只需要一個簡單的數字：
const duration = ref(35)
但如果你是像你這樣的複合物件（object），就建議用 reactive()：
const course = reactive({ name: "POOP", duration: 35 })
這樣才能讓整個物件每個屬性都能被追蹤。

如下面    const price = ref(24000) 就直接用ref變成物件
按按鈕後課程跟錢都增加
```javascript=
<template>
    <div>
        <h3>{{ course }}</h3>
        <h3 v-once>原本價錢:{{ price }}</h3>
        <h3>目前價錢:{{ price }}</h3>
        <button @click="extendOneDay">加課</button>
    </div>
</template>

<script>
import { reactive, ref } from "vue"
export default {
    setup() {
        const price = ref(24000)
        const course = reactive({ name: "POOP", duration: 35 })
        function extendOneDay() {
            course.duration = course.duration + 7
            price.value += 5000
        }
        return { course: course, price: price, extendOneDay: extendOneDay }
    }
}
</script>

<style lang="scss" scoped></style>
```

### 複習event
```javascript=
<template>
    <div>
        <h3>{{ course }}</h3>
        <h3 v-once>原本價錢:{{ price }}</h3>
        <h3>目前價錢:{{ price }}</h3>
        <h3>{{ courseDisplayName }}</h3>
        <button @click="extendOneDay">加課</button>
        <hr />
        <input type="text" @input="setCourseId" />
        <input type="text" @input="setCourseFullName" />
    </div>
</template>

<script>
import { reactive, ref, computed } from "vue"
export default {
    setup() {
        const courseId = ref("")
        const courseFullName = ref("")
        const courseDisplayName = computed(
            function () {
                console.log("calculate course display name",courseId.value,courseFullName.value)
                return courseId.value + ' ' + courseFullName.value
            }
        )
        const price = ref(24000)
        const course = reactive({ name: "POOP", duration: 35 })
        function extendOneDay() {
            course.duration = course.duration + 7
            price.value += 5000
        }
        function setCourseId(event) {
            courseId.value = event.target.value;
        }
        function setCourseFullName(event) {
            courseFullName.value = event.target.value;
        }
        return {
            course: course, price: price, extendOneDay: extendOneDay,
            courseDisplayName: courseDisplayName, setCourseId: setCourseId, setCourseFullName: setCourseFullName
        }
    }
}
</script>

<style lang="scss" scoped></style>

```
這邊的envet之前有教過 可以不用寫
```javascript=
<input type="text" @input="setCourseId" />
function setCourseId(event) {
    courseId.value = event.target.value;
 }
可以改成
<input type="text" @input="setCourseId($event)" />
function setCourseId() {
    courseId.value = event.target.value;
}
```
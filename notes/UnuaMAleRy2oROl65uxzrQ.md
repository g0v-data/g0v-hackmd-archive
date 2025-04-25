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

### 改用v-model

🔄 雙向綁定超直觀
用 v-model 就是 Vue 提供的「雙向綁定語法糖」，會自動幫你綁定：
:value（讀取資料）
@input（更新資料）

```javascript=
<template>
    <div>
        <h3>{{ course }}</h3>
        <h3 v-once>原本價錢:{{ price }}</h3>
        <h3>目前價錢:{{ price }}</h3>
        <h3>{{ courseDisplayName }}</h3>
        <button @click="extendOneDay">加課</button>
        <hr />
        <input type="text" v-model="courseId" />
        <input type="text" v-model="courseFullName" />
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
                return courseId.value + ' ' + courseFullName.value
            }
        )
        const price = ref(24000)
        const course = reactive({ name: "POOP", duration: 35 })
        function extendOneDay() {
            course.duration = course.duration + 7
            price.value += 5000
        }
        return {
            course: course, price: price, extendOneDay: extendOneDay,
            courseDisplayName: courseDisplayName, 
            courseId:courseId,courseFullName:courseFullName
        }
    }
}
</script>

<style lang="scss" scoped></style>

```
### 使用watch
🧠 watch() 是什麼？
Vue 3 的 watch() 是用來「監聽 reactive 的資料變化」，當資料改變時會自動觸發對應的 callback。

```javascript=
<template>
  <div>
      <h3>{{ course }}</h3>
      <h3 v-once>原本價錢:{{ price }}</h3>
      <h3>目前價錢:{{ price }}</h3>
      <h3>{{ courseDisplayName }}</h3>
      <button @click="extendOneDay">加課</button>
      <hr />
      <input type="text" v-model="courseId" />
      <input type="text" v-model="courseFullName" />
  </div>
</template>

<script>
import { reactive, ref, computed, watch } from "vue"
export default {
  setup() {
      const courseId = ref("")
      const courseFullName = ref("")
      const courseDisplayName = computed(
          function () {
              return courseId.value + ' ' + courseFullName.value
          }
      )
      const price = ref(24000)
      //watch([price, courseDisplayName]現在的寫法是同時監聽兩個值
      //只要 price 或 courseDisplayName 有任何變化，就會觸發這個 callback 函式
     //watch([...])	可監聽多個 ref/computed，陣列寫法一次搞定
      watch([price, courseDisplayName], function (newValue, oldValue) {
          if (oldValue[0] !== newValue[0]) {
              console.log(`price goes from ${oldValue[0]} to ${newValue[0]}`)
          }
          if (oldValue[1] !== newValue[1]) {
              console.log(`display full name goes from ${oldValue[1]} to ${newValue[1]}`)
          }
      })
      const course = reactive({ name: "POOP", duration: 35 })
      function extendOneDay() {
          course.duration = course.duration + 7
          price.value += 5000
      }
      return {
          course: course, price: price, extendOneDay: extendOneDay,
          courseDisplayName: courseDisplayName,
          courseId: courseId, courseFullName: courseFullName
      }
  }
}
</script>

<style lang="scss" scoped></style>
```

### 改用 ref + DOM控制
## ✅ 比較總表

| 比較項目              | `v-model` 寫法                           | `ref` + DOM 控制寫法                          |
|-----------------------|------------------------------------------|-----------------------------------------------|
| **資料同步**          | 雙向綁定，Vue 自動同步                  | 手動取值、手動更新資料                        |
| **簡潔程度**          | 超簡潔，推薦預設用法                   | 稍複雜，需要 `.value.value`                   |
| **可維護性**          | 高，容易理解                            | 中，易出錯或多寫程式碼                        |
| **適用場景**          | 表單、即時資料綁定                     | DOM 操作（聚焦、捲動、特定操作）              |
| **整合 computed/watch** | 很容易整合                            | 不太適合整合 computed，需額外邏輯處理         |

```javascript=
<template>
    <div>
        <h3>{{ course }}</h3>
        <h3 v-once>原本價錢:{{ price }}</h3>
        <h3>目前價錢:{{ price }}</h3>
        <h3>{{ courseDisplayName }}</h3>
        <button @click="extendOneDay">加課</button>
        <hr />
        <input type="text" v-model="courseId" />
        <!-- <input type="text" v-model="courseFullName" /> -->
        <input type="text" ref="courseFullNameInput" />
        <button @click="setCourseFullName">set course full name</button>
    </div>
</template>

<script>
import { reactive, ref, computed, watch } from "vue"
export default {
    setup() {
        const courseId = ref("")
        const courseFullName = ref("")
        const courseDisplayName = computed(
            function () {
                return courseId.value + ' ' + courseFullName.value
            }
        )
        const price = ref(24000)
        watch([price, courseDisplayName], function (newValue, oldValue) {
            if (oldValue[0] !== newValue[0]) {
                console.log(`price goes from ${oldValue[0]} to ${newValue[0]}`)
            }
            if (oldValue[1] !== newValue[1]) {
                console.log(`display full name goes from ${oldValue[1]} to ${newValue[1]}`)
            }
        })
        const course = reactive({ name: "POOP", duration: 35 })
        function extendOneDay() {
            course.duration = course.duration + 7
            price.value += 5000
        }
        //
        const courseFullNameInput = ref();
        function setCourseFullName() {
            // reactive ==> html element ==> element value
            courseFullName.value = courseFullNameInput.value.value;
        }
        return {
            course: course, price: price, extendOneDay: extendOneDay,
            courseDisplayName: courseDisplayName,
            courseId: courseId, courseFullName: courseFullName,
            setCourseFullName:setCourseFullName,
            courseFullNameInput:courseFullNameInput
        }
    }
}
</script>

<style lang="scss" scoped></style>

```
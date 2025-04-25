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
### 複習props + computed
```javascript=
<template>
    <div>
        <h3>{{ course }}</h3>
        <h3 v-once>原本價錢:{{ price }}</h3>
        <h3>目前價錢:{{ price }}</h3>
    </div>
</template>

<script>
export default {
    props: ["courseId","courseFullName", "price"],
    computed: {
        course(){
            if (!this.courseFullName) {
                return `[${this.courseId}]`;
            }
            return `[${this.courseId}]${this.courseFullName.value}`
        }
    }
}
</script>

<style scoped></style>

```

這邊寫法有問題
```javascript=
 return `[${this.courseId}]${this.courseFullName.value}` // ❌ 不應該這樣寫
 
 return `[${this.courseId}]${this.courseFullName}`
```
✅ 原因解析
🧠 背景知識：Vue 的 props 自動解包
如果你使用的是 Options API（你這邊就是），並且透過 props 傳入資料，

Vue 會自動幫你解開 ref() 的 .value
所以在 this.courseFullName 中，其實就已經是你傳進來的「值」，不是 ref 本身


### ✅ Options API vs Composition API 差異比較表

雖然功能表面看起來一樣，但在邏輯、擴充性與可控性上仍有不少差異，以下是清楚的比較：

| 項目                         | 第一段：Options API                              | 第二段：Composition API（`setup()`）               |
|------------------------------|--------------------------------------------------|----------------------------------------------------|
| **API 風格**                 | 傳統 Options API                                 | 現代 Composition API（需要 `setup()`）             |
| **變數宣告位置**            | `computed` 寫在 `computed:{}` 裡                 | `computed()` 寫在 `setup()` 裡                     |
| **取得 props 的方式**       | 透過 `this.courseId` / `this.courseFullName`     | 透過 `props.courseId` / `props.courseFullName`     |
| **reactive 支援**           | Vue 自動 unwrap props，取值簡單                  | 需要從 `props` 手動取值                            |
| **彈性與可讀性**            | 結構清楚、簡單，適合小元件                       | 更具彈性，適合大型應用、可拆分功能                 |
| **可擴充性（例如 watch）**  | 擴充性較低，如要加 `watch` 得另開 options 區塊   | 擴充性高，可在 `setup()` 裡做任何操作              |
| **Vue 3 標準推薦**          | 支援，但不再是推薦主流（偏向過渡）               | ✅ Vue 3 推薦使用方式，尤其配合 `script setup`     |

Options API
```javascript=
<template>
    <div>
        <h3>{{ course }}</h3>
        <h3 v-once>原本價錢:{{ price }}</h3>
        <h3>目前價錢:{{ price }}</h3>
    </div>
</template>

<script>
export default {
    props: ["courseId","courseFullName", "price"],
    computed: {
        course(){
            if (!this.courseFullName) {
                return `[${this.courseId}]`;
            }
            return `[${this.courseId}]${this.courseFullName}`
            
        }
    }
}
</script>

<style scoped></style>
```
Composition API
```javascript=
<template>
    <div>
        <h3>{{ course }}</h3>
        <h3 v-once>原本價錢:{{ price }}</h3>
        <h3>目前價錢:{{ price }}</h3>
    </div>
</template>

<script>
import { computed } from "vue"
export default {
    props: ["courseId", "courseFullName", "price"],
    setup(props) {
        const course = computed(function () {
            if (!props.courseFullName) {
                return `{[${props.courseId}]}`;
            }
            return `{[${props.courseId}]}${props.courseFullName}`

        })
        return { course: course }
    }
}
</script>

<style scoped></style>
```
### provide
🧠 provide / inject 是什麼？
簡單來說：

provide 讓「父元件」提供資料，inject 讓「子元件」使用這些資料，不用透過 props 傳遞一層一層傳下去。

✨ 使用時機
當你有以下需求時很適合用：

✅ 多層元件需要共用同一份資料
✅ 不想一層一層地用 props 傳值
✅ 某些資料是「context」類型（例如：使用者資訊、主題色、語言設定等）

## ✅ 比 props 的優點？

| 比較項目           | `props` 傳值                         | `provide` / `inject`                        |
|--------------------|--------------------------------------|---------------------------------------------|
| **傳遞方式**       | 一層層向下傳                          | 可直接在任一子元件拿到                      |
| **可維護性**       | 多層嵌套時會變麻煩                    | 比較乾淨、不重複                            |
| **元件耦合程度**   | 耦合高（要寫在 `props`）              | 耦合低，子元件不需要知道上層細節           |
| **可讀性**         | 較高（資料流明確）                   | 較低（需查是哪個元件 `provide` 了資料）     |

```javascript=
<template>
    <div>
        <CourseIntro :course="course" :courseFullName="courseFullName" :courseId="courseId"></CourseIntro>

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
import CourseIntro from "@/components/CourseIntro.vue"
import { reactive, ref, computed, watch, provide } from "vue"
export default {
    components: { CourseIntro },
    setup() {
        const courseId = ref("")
        const courseFullName = ref("")
        const courseDisplayName = computed(
            function () {
                return courseId.value + ' ' + courseFullName.value
            }
        )
        const price = ref(24000)
        provide('price', price)
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
            setCourseFullName: setCourseFullName,
            courseFullNameInput: courseFullNameInput
        }
    }
}
</script>

<style lang="scss" scoped></style>

```

-------
### lifecycle
這些是 Vue 3 中 生命週期鉤子（Lifecycle Hooks） 的一部分，通常用來控制元件在不同階段的行為。

在 Vue 的生命週期中，元件會經歷從「創建」到「銷毀」的一系列階段，而這些鉤子函數會在特定的階段自動被調用。你提供的這些鉤子是與元件的創建與銷毀有關的生命週期鉤子。

Options API	的寫法
```javascript=
<template>
    <div>
        <h1>Options API 元件</h1>
        <p>{{ counter }}</p>
        <button @click="increaseCounter">+1</button>
    </div>
</template>

<script>
export default {
    data() {
        return { counter: 0 }
    },
    methods: {
        increaseCounter() {
            console.log("before +1, counter=", this.counter)
            this.counter += 1
            console.log("after +1, counter=", this.counter)
        }
    },
    beforeUpdate() {
        console.log("before update has been called")
    },
    updated() {
        console.log("component updated")
    },
    beforeCreate() {
        console.log("component before created")
    },
    created() {
        console.log("component created")
    },
    mounted() {
        console.log("component mounted")
    },
    beforeUnmount() {
        console.log("component will be removed")
    },
    unmounted() {
        console.log("component removed")
    }

}
</script>

<style scoped></style>
```

Composition API的寫法
```javascript=
<template>
    <div>
        <h1>Composition元件</h1>
        <p>{{ counter }}</p>
        <button @click="increaseCounter">+1</button>
    </div>
</template>

<script>
import { onBeforeUnmount, onMounted, onUnmounted, ref, onBeforeUpdate, onUpdated } from 'vue'
export default {
    setup() {
        const counter = ref(0)
        function increaseCounter() {
            console.log("[c]before update value")
            counter.value += 1
            console.log("[c]after update value")
        }
        onBeforeUpdate(()=>{console.log("[c]before update UI")})
        onUpdated(()=>{console.log("[c]before update UI")})
        console.log("[c]prepare composition api")
        onMounted(() => {
            console.log("[c]component mounted")
        })
        onBeforeUnmount(() => {
            console.log("[c]component will be removed")
        })
        onUnmounted(() => {
            console.log("[c]component removed")
        })
        return { counter, increaseCounter }
    },

}
</script>

<style lang="scss" scoped></style>
```

### form

```javascript=
<template>
    <form @submit.prevent="submitForm">
        <label for="course-id">course id</label>
        <input name="course-id" type="text" />
        <br />
        <label for="course-name">course name</label>
        <input name="course-name" type="text" />
        <br />
        <label for="course-duration">course duraion</label>
        <input name="course-duration" type="number" />
        <br />
        <label for="category">category</label>
        <select id="category">
            <option value="java">java</option>
            <option value="C#">C#</option>
            <option value="python">python</option>
        </select>
        <br />
        <p>need equipment</p>
        <input id="arduino" type="checkbox">
        <label for="arduino">arduino</label>
        <input id="webcam" type="checkbox">
        <label for="webcam">webcam</label>
        <input id="internet_access" type="checkbox">
        <label for="internet_access">internet access</label>
        <br />
        <p>location</p>
        <input id="taipei" type="radio" name="location">
        <label for="taipei">taipei</label>
        <input id="hsinchu" type="radio" name="location">
        <label for="hsinchu">hsinchu</label>
        <input id="taichung" type="radio" name="location">
        <label for="taichung">taichung</label>
        <input id="kaohsiung" type="radio" name="location">
        <label for="kaohsiung">kaohsiung</label>

        <br />
        <button type="submit">Save</button>

    </form>
</template>

<script>
export default {
    methods: {
        submitForm() {
            console.log("form submitted")
        }
    }
}
</script>

<style scoped></style>
```


### form包值
在 Vue 中，Vue 並不會自動幫你「打包整個 <form> 成物件」。
你看到的 v-model 綁定，其實是你在 data() 裡自己定義的變數，Vue 幫你「資料雙向綁定」而已，但「打包成表單物件」這件事，還是要你手動寫。
```javascript=
<template>
    <form @submit.prevent="submitForm">
        <label for="course-id">course id</label>
        <input name="course-id" type="text" v-model="courseId"/>
        <br />
        <label for="course-name">course name</label>
        <input name="course-name" type="text" v-model="courseName"/>
        <br />
        <label for="course-duration">course duraion</label>
        <input name="course-duration" type="number" v-model.number="courseDuration"/>
        <br />
        <label for="category">category</label>
        <select id="category" v-model="category">
            <option value="java">java</option>
            <option value="C#">C#</option>
            <option value="python">python</option>
        </select>
        <br />
        <p>need equipment</p>
        <input id="arduino" type="checkbox" value="arduino" v-model="equipment">
        <label for="arduino">arduino</label>
        <input id="webcam" type="checkbox" value="webcam" v-model="equipment">
        <label for="webcam">webcam</label>
        <input id="internet_access" type="checkbox" value="internet_access" v-model="equipment">
        <label for="internet_access">internet access</label>
        <br />
        <p>location</p>
        <input id="taipei" type="radio" name="location" value="taipei" v-model="location">
        <label for="taipei">taipei</label>
        <input id="hsinchu" type="radio" name="location" value="hsinchu" v-model="location">
        <label for="hsinchu">hsinchu</label>
        <input id="taichung" type="radio" name="location" value="taichung" v-model="location">
        <label for="taichung">taichung</label>
        <input id="kaohsiung" type="radio" name="location" value="kaohsiung" v-model="location">
        <label for="kaohsiung">kaohsiung</label>

        <br />
        <button type="submit">Save</button>

    </form>
</template>

<script>
export default {
    data() {
        return {
            courseId: "",
            courseName: "",
            courseDuration: null,
            category: "java",
            equipment: [],
            location: "",
            rememberMe: false

        }
    },
    methods: {
        submitForm() {
            const course = {
                id: this.courseId,
                name: this.courseName,
                duration: this.courseDuration,
                category: this.category,
                equipment: this.equipment,
                location: this.location,
                rememberMe: this.rememberMe
            }
            console.log("form submitted as:", course)
            this.courseId = "";
            this.courseName = "";
            this.courseDuration = null;
            this.category = "java";
            this.equipment = [];
            this.location = "";
            this.rememberMe = false;
        }
    }
}
</script>

<style scoped></style>
```
🧠 要怎麼「打包成物件」？
你要自己在 methods.submitForm 裡整理好：
如上面58~66行 

### 多了驗證版本
```javascript=
<template>
    <form @submit.prevent="submitForm">
        <label for="course-id">course id</label>
        <input name="course-id" type="text" v-model="courseId" @blur="validateId" />
        <p v-if="idValid === 0">course id can not be empty</p>
        <br />
        <label for="course-name">course name</label>
        <input name="course-name" type="text" v-model="courseName" />
        <br />
        <label for="course-duration">course duraion</label>
        <input name="course-duration" type="number" v-model.number="courseDuration" />
        <br />
        <label for="category">category</label>
        <select id="category" v-model="category">
            <option value="java">java</option>
            <option value="C#">C#</option>
            <option value="python">python</option>
        </select>
        <br />
        <p>need equipment</p>
        <input id="arduino" type="checkbox" value="arduino" v-model="equipment">
        <label for="arduino">arduino</label>
        <input id="webcam" type="checkbox" value="webcam" v-model="equipment">
        <label for="webcam">webcam</label>
        <input id="internet_access" type="checkbox" value="internet_access" v-model="equipment">
        <label for="internet_access">internet access</label>
        <br />
        <p>location</p>
        <input id="taipei" type="radio" name="location" value="taipei" v-model="location">
        <label for="taipei">taipei</label>
        <input id="hsinchu" type="radio" name="location" value="hsinchu" v-model="location">
        <label for="hsinchu">hsinchu</label>
        <input id="taichung" type="radio" name="location" value="taichung" v-model="location">
        <label for="taichung">taichung</label>
        <input id="kaohsiung" type="radio" name="location" value="kaohsiung" v-model="location">
        <label for="kaohsiung">kaohsiung</label>

        <br />
        <input type="checkbox" v-model="rememberMe" id="remember" />
        <label for="remember">remember me</label>
        <button type="submit">Save</button>

    </form>
</template>

<script>
export default {
    data() {
        return {
            courseId: "",
            courseName: "",
            courseDuration: null,
            category: "java",
            equipment: [],
            location: "",
            rememberMe: false,
            idValid: -1
        }
    },
    methods: {
        validateId() {
            if (this.courseId.trim() === "") {
                this.idValid = 0;
            } else {
                this.idValid = 1;
            }
        },
        submitForm() {
            const course = {
                id: this.courseId,
                name: this.courseName,
                duration: this.courseDuration,
                category: this.category,
                equipment: this.equipment,
                location: this.location,
                rememberMe: this.rememberMe
            }
            console.log("form submitted as:", course)
            this.courseId = "";
            this.courseName = "";
            this.courseDuration = null;
            this.category = "java";
            this.equipment = [];
            this.location = "";
            this.rememberMe = false;
        }
    }
}
</script>

<style scoped></style>
```
```vue
<input name="course-id" type="text" v-model="courseId" @blur="validateId" />
<p v-if="idValid === 0">course id can not be empty</p>
```
會在欄位 失去焦點（blur）時做檢查。
如果是空的，就會提示錯誤訊息。
類似「前端驗證」的初階做法。
    
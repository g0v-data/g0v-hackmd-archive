# Vue.JS 課程


## 特性
*關注點分離: 開發者只需專注在畫⾯面元素，及其對應的資料
變化即可。*

## 漸進式框架

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8702f79e85008b191d0b0be949135c93)

##  MVVM ( Model-View-ViewModel )

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8c98af7d3caa0e00a6c6585c70ce14e4)

##  元件系統簡介

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0d08d1ea6ca8972c560953d536f2faa6)




```
new Vue({
      el: '#app',
      components: {
        CustomMain,
        CustomHeader,
        CustomAside
      }
    });
```

##  透過 CDN 載入 Vue

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_aa73221ad3d9b755eb28b898c12e5525)


##  透過 Vue-CLI 建置專案

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f08fa3228db7bf5654f7eaaa1332305d)



##  Vue 實體

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9e35a0179cdcbea61458d08f6a800577)


## Vue 元件實體生命週期
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fb4ed239c303e209a9b45d84f1ea0d61)

##  Vue 實體基本屬性

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ce039b50776988e690883e6c3da633e9)



##  computed 與 methods( ) 的差異

偵測到變化時
computed() 只會跑一次
methods() 會跑三次資料

效能上的差異

##  computed 屬性的 set 與 get


##  過濾器 Filter
mustache{{ }}以及v-bind的表達式，以
「 | 」(pipe) 符號來來表⽰示。

### Vue filter 與 methods 的差別?


## 指令
v-text
v-html (會有xss攻擊, 不建議用)
v-show
v-if

v-on 事件處理
v-bind 綁定事件
(找data要 找compuntent)
v-model
v-pre
v-cloak
v-once 只更新一次

##  表單修飾子 v-model + Modifiers
.trim 可略掉空白
.lazy 需要離開輸入框才顯示
..number 轉換成數值

##  事件修飾子 v-on + Modifiers
.once 只觸發一次

##  條件判斷 (區塊) - v-if + template
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_36b652541d645819b1a160d9013ed0b9)


template 無法與 v-show 共⽤用。

##  列表渲染 v-for + range

最常用在頁籤
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1ba435c77b10d81edd9931ac6f487151)




vue
Vue無法建立巢狀結構
例如:
<div>
{{text}}
  <div>
   {{text}}
  </div>
</div>
Vue只能綁定一個元素所以建議使用id但也能使用class
Vue可以建立兩個應用程式



顯示綁定資料
<div>
{{ text }}//顯示"這是一段話"
</div>
建立一個Vue應用程式

let app = new Vue({
el:"#app",
data:{
text:"這是一段話"
}
})


雙向資料綁定v-model
<div>
{{message}}輸出結果為"哈囉"
<div v-html="message"></div>//可以插入html標籤 輸出結果為"哈囉"
<div v-text="message"></div>
<input type="text" v-model="message">//透過input修改model的資料內容 data的message對應到model的message 輸出結果為"哈囉"
</div>


let app = new Vue({
el:"#app",
data:{
message:"哈囉"
}
})

Vue.js是以資料狀態操作畫面


指令
v-bind 更新HTML屬性
<div id="app">
<img v-bind:src="imgSrc" v-bind:class="className" alt="">
</div>



let app = new Vue({
el:"#app"
data:{
imgSrc:XXXXXXXXXX,
className:"img-fluid"//此方法為bs4語法,用來使圖片的寬度限制在100%以內
}
})


v-for

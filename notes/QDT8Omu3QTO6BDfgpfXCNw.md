# 情侶紀錄ＡＰＰ

* 登入功能
google連動
https://developers.google.com/identity/sign-in/web/sign-in
介面
https://ant.design/components/form/
https://ant.design/components/drawer/

* font awesome
```
<!-- Font Awesome icons (free version)-->
<script src="https://use.fontawesome.com/releases/v5.13.0/js/all.js" crossorigin="anonymous"></script>
```

* 動畫效果
愛心
https://www.npmjs.com/package/react-animated-heart
筆記感
https://medium.com/frontend-digest/how-to-animate-text-decorations-with-gatsby-js-and-rough-notation-cc349d86603
* 桌布
    * https://www.pinterest.com/pin/39758409198905144/
    * https://www.pinterest.com/pin/844493668367266/
    * https://www.pinterest.com/pin/431782683029208885/
    * http://www.designlovefest.com/2017/01/dress-your-tech-175/ (藍色的)

* 書react
https://nodlik.github.io/react-pageflip/
* 記帳
金額 項目（分類）誰付的 誰應付
最後要算誰欠誰
參考資源
android app
https://github.com/fcamel/Go-Go-Dutch
web react
https://github.com/7070587/Accounts--React
圓餅圖
https://reactjsexample.com/customizable-circular-svg-progress-bar-component-for-react/
https://reactjsexample.com/tag/chart/
tag

* 日誌
https://reactjsexample.com/a-hooks-to-svg-drawing/
https://reactjsexample.com/a-react-emoji-picker-for-use-with-emojione/
* pictures
http://motion-layout.com/

* 行事曆
hackathon1 時間 Google map
https://ithelp.ithome.com.tw/articles/10186932
https://fullcalendar.io/docs/event-object
https://fullcalendar.io/docs/react
https://codepen.io/pen/?&editors=001
React使用範例：
https://github.com/fullcalendar/fullcalendar-example-projects/blob/master/react/src/DemoApp.jsx
官網document
https://fullcalendar.io/docs
event structure format
https://fullcalendar.io/docs/event-parsing
event addEvent 把它傳進 addform
https://fullcalendar.io/docs/Calendar-addEvent
event eventAdd 會自動啟動在做addEvent之後
https://fullcalendar.io/docs/eventAdd
select setState 範例
https://codesandbox.io/s/fullcalendar-functional-430-mydrf?file=/src/App.js
useEffect函式
https://ithelp.ithome.com.tw/articles/10224270
eventChange
https://docs.mongodb.com/manual/reference/operator/aggregation/replaceRoot/#pipe._S_replaceRoot
eventDrop
https://fullcalendar.io/docs/eventDrop
list event
https://fullcalendar.io/docs/list-view
modal example
https://hugh-program-learning-diary-js.medium.com/react-中如何實作的彈出視窗-48935aee5183
modal doc
https://react-bootstrap.github.io/components/modal/
* 回憶
上傳相片
```
<form action="/somewhere/to/upload" enctype="multipart/form-data">

<input name="progressbarTW_img" type="file" accept="image/gif, image/jpeg, image/png">

</form>
```
文字 GoogleMap
時間軸 https://ant.design/components/timeline/

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8024947e67f38235f56235423a9410a1.png)

### 注意事項
* 要使用`yarn server` & `yarn start`之前
先打`npm install react-router-dom`
* websocket 使用
https://medium.com/enjoy-life-enjoy-coding/javascript-websocket-讓前後端沒有距離-34536c333e1b
* MonogooseSchema
https://stackoverflow.com/questions/33049707/push-items-into-mongo-array-via-mongoose

### 現在問題
1. 怎麼分開管理不同database?
2. 怎麼用database紀錄誰欠誰
3. 怎麼畫圓餅圖
https://github.com/tomlinNTUB/HTML5/blob/master/13-2%20Chart.js-%E5%9C%93%E9%A4%85%E5%9C%96.md

沒辦法load events

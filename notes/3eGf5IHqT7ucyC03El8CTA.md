# 說明
* 新加入的程式碼會像這樣前面有一點
```
程式碼會像這樣下面有灰灰的
```
然後旁邊可以留言---------------------->
有不看不懂的再來問我


# 1.	新增color.css
  ```html
 :root{
      --color-primary-0 : #EAD9B7  ;
      --color-primary-1 : #FFD78A  ;
      --color-primary-2 : #FFE2A9  ;
      --color-primary-3 : #9E9686  ;
      --color-primary-4 : #575757  ;
      }
```
---
:root{}        廣域變數(root為根目錄)
--廣域變數名稱 : 變數值 ;

將main.css中的 background:#000; 改為
background: var(--color-primary-2);




# 2.加入newsbar
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9c44f81182cdef54adb618651362a33a)
## index.html
### -->在content的文章中加入以下程式碼
> 
```html
<div class="newsbar">
<div class="news"></div>
<div class="news"></div>
<div class="news"></div>
</div>
```
---

## main.css
### -->在main.css中加入以下程式碼(在content下方)
### 1.

```html
div.news{
    height: 300px;
    width: 220px;
    background:var(--color-primary-3);
}
```
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_68a995beeed82b0db419e6aa75cdcfd8)


---

### 2.


```html
div.news{
    height: 300px;
    width: 220px;
    background:var(--color-primary-3);
```
 *     float: left;  
```html
}
```

> **block:** 直的排
> **inline:** 衡的排


加入 *flot:left;* 將newsbar 變成 inline

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4266cc82108677faa036eecf51b99f8d)

---
### 3.
以下功能跟上次的clear一樣
```html
div.newsbar:after{
    display: block;
    content: ' ';
    clear: both;
}
```
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0574b1f3d567043ebf79271044a7a096)

---
### 4.
```html
div.news:nth-child(1),
div.news:nth-child(2){
    margin-right: 30px;
}
```
```html
div.news:not(:last-child){
    margin-right: 30px;
}
```
以上兩段功能一樣
都是將三塊"news"中加入30px的間隔
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c092febd9272a5fcf69057e1f41cf1c9)


---

# 3.在newsbar 加入圖片
## index.html
```html
<div class="newsbar">

    <div class="news">
```
*         <img src="imgs/1.jpg">
*         <center><h3>IU </h3></center>
```html
    </div>
    
    <div class="news">
```
*         <img src="imgs/2.jpg">
*         <center><h3>李知恩 </h3></center>
```html
    </div>

    <div class="news">
```
*         <img src="imgs/3.jpg">
*         <center><h3>이지은 </h3></center>
```html
    </div>

</div>
```



上面這些表示 將 **圖片** 放在和 **文字** 放在
**newsbar** 裡的 **news** 裡


---

## main.css
```html
div.news{
    width: 220px;
```
*     height: 220px;
```html
background:var(--color-primary-3);
float: left;
}
```
將高改成220px

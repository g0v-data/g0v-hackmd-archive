---
tags: vtaiwan 
---
# vTaiwan Luma 活動頁設定教學
最後更新時間：2025/04/23 

目前vTaiwan 是使用Ghost作為部落格使用 
未來如果要直接用在vTaiwan新官網是可以直接把code貼在網站上的

# 如何在Blog文章中嵌入活動
### 1.嵌入程式碼在哪？ 
在你發布的活動中，點擊「更多」
![](https://g0v.hackmd.io/_uploads/H1KIjuIygl.png)

在「更多」頁面，找到嵌入活動頁，點選後複製下面的程式碼
![](https://g0v.hackmd.io/_uploads/By1oidUkex.png)

### 2. 貼上程式碼
如果不要求自適應，在編輯文章的時候，點選+ 
找到HTML Block之後，將下方的程式碼貼入Block中
![](https://g0v.hackmd.io/_uploads/HJl4a6dIyeg.png)

這樣就完成了! 
記得要publish出去，才看得到
Draft模式下只會顯示「embeded iFrame」

---

### 3. 自適應的調整
但為了讓嵌入漂亮一點，我有做一些調整 
我在Ghost的 Code Injection裡面貼上了這段CSS
這樣未來的人也不需要自己調整CSS
基本上不用理會這一段
``` css
<style> /*這是調整lu.ma的 css injection*/
  .luma-event {
    width: 100%;
    max-width: 100%; 
    margin: 0 auto;
    display: flex;
    justify-content: center;
  }
  
  .luma-event iframe {
    width: 800px;
    height: 380px; 
    border: 1px solid #bfcbda88;
    border-radius: 4px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  }
  
  @media (max-width: 850px) {
    .luma-event iframe {
      width: 100%;
      min-height: 700px; 
    }
  }
</style>

```

### 4. 修改iframe
把剛剛複製到的iFrame程式碼中的src，複製到下方的src中
![](https://g0v.hackmd.io/_uploads/HJhvgF8yex.png)

``` html 
<div class="luma-event">
  <iframe
    src="https://lu.ma/embed/event/test/simple"
    frameborder="0"
    allowfullscreen=""
    aria-hidden="false"
    tabindex="0"
  ></iframe>
</div>
```

再將修改好的程式碼用
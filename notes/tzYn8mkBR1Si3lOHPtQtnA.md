# DOMContentLoaded時間優化

Html的外部腳本 VS 內聯腳本
---
- 外部腳本
```
   <script >
        let script = document.createElement('script');
        script.defer=true;
        script.src = '../../test.js';
        document.body.appendChild(script);
    </script>
```

- 內聯腳本
```
   <script defer src= '../../test.js'></script>
```


- 差異
<外部>
腳本的加載，並不影響DOMContentLoaded的時間，做完Html的內容跟Css的內容後，便完成DOMContentLoaded事件。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2503f336502d77762925e659d74bf3ce.png)
<內聯>
腳本的加載，除了做完Html的內容跟Css的內容後，還要完成便完成DOMContentLoaded事件。



所以因為需求是

Themes
---
- [Dark theme](/theme-dark?both)
- [Vertical alignment](/theme-vertical-writing?both)

###### tags: `DOMContentLoaded` `Html`

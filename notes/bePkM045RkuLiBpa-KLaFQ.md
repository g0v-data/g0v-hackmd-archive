# WebAPIs//筆記
### 6 hour /18 Hour


---

取消HTML5內建的驗證
form 元素的 novalidate 屬性
Submit 按鈕的 formnovalidate屬性

這邊不會有驗證


---


### Drag and Drop 拖放
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_42b14ff02d03656cf3cda5ef59cd3c00.png)
"draggable = true"
要加上這個屬性才能讓目標被拖移
但是 "a" 跟 "img" 是預設就可以被拖移的

drag事件主要有三個

舉起來-dragstart
    透過dragstart取得目標值
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1262c0f1633ed3600d10d958b73449f6.png)
    紅色-對這個div內的東西被拖動時加上一個dragstartHandler
    橘色-就是dragstartHandler
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6ad2ee449964c01534f8511d581e216c.png)

    
    
    
搬運-dragover
    這邊是針對指定區域
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_47e09876fa1983bf59dbb8fc79c22e72.png)
    
這邊就是這裡的每個zone
 紅色這個
 zone.addEventListener('dragover', event => event.preventDefault());
 這個是讓他可以接受被拖移的目標,預設是不接受


放下來-drop
    橘色就是當zone裡面有物件drop時觸發
    event.preventDefault(); - 阻止預設事件發生
    event.stopPropagation(); - 停止事件在DOM樹中的傳播
    這兩條起手式
    
這邊是

取出放進DataTransfer物件中的ID
const sid = event.dataTransfer.getData("text/plain");

根據ID找到指定的標籤
const source = document.querySelector(`#${sid}`);

將標籤移動到放下的區域中
event.target.appendChild(source);

這邊全部就是
拖移
移動
放下來
    
    

---


### 拖移檔案上傳

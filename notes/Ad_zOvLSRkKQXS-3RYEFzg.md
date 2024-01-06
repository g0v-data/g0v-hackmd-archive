# [C#] 讓程式以系統管理員身分執行

1.找到方案總管的專案下面的方案項目。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cf55bf9ee33aa579bd997830fb13d1b9.png)
 
2.右鍵>加入>新增項目
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_191b0e304ec4b437c7ed2add853ced01.png)

3.左邊選擇 "一般"。中間選擇 "應用程式資訊清單" 。之後新增。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d30fcde1f01c5431d7e82cbd44155d5d.png)

4.新增完後左方的方案管理員內會出現一個 "app.manifest" 的文件
視窗內會多出一大串程式碼(如圖)。
找到 <requestedExecutionLevel level="asInvoker" uiAccess="fal
se" />
將 "asInvoker" 替換成 "requireAdministrator"
如下程式碼
<requestedExecutionLevel level="requireAdministrator" uiAccess="false" />
即可。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1b2d1c4a11d0a47ac12a112c69271a61.png)

5.建置>重建方案

6.成功後到輸出資料夾看。
編譯後的 檔案是否多了個盾牌
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bc11a64c5fd230eb7418fc59c55611c2.png)

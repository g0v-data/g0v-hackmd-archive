# 掃臉工具 Frida 環境設置教學
## Frida 簡介
Frida是讓銀行APP到掃臉的步驟可以自動掃臉個工具，Frida 環境是需要安裝在電腦上的，請各人員必須學會設置
目前支援的銀行有
* MB -- 可用
* ACB -- 更新中
* VPB -- 更新中
* VIB -- 更新中

## Frida 環境設置
### 安裝包載點
Frida 執行檔可以在公司的[Google Drive](https://drive.google.com/drive/u/2/folders/1Om1-a16EqEqbeE8Sw7Q0abb0NwwL0dXe)上下載到，如果沒有權限TG上的小秘笈也有。

### 設定流程
解壓縮完後，會得到這些檔案
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1a22cbb0546c5977995ade9e20da6d17.png)

1. 第一步，先點 setting.bat 右鍵，點"以系統管理員身分執行"，因為點下之後不會跑出任何視窗或訊息，所以只要確認有點就可以了。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7ed6df4e49659fc7d3064c23aa7838bb.png)

2. 第二步，右鍵點擊 config.yml ，選擇開啟檔案，使用WordPad 或是 記事本，開啟檔案。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_26dee8d7d8636f482f7eeb1145daf77c.png)

3. 第三步，進入 config.yml 檔，會有像圖片中一樣的文字，這邊我們需要改掉"phoneaddr"、"device"、"account"、"bank"
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a89731c30e815260508ab680e85efde8.png)

    3.1 修改 phoneaddr -- 這個欄位可以在設定 >> 網路與網際網路 >> 選擇連接的網際網路 >> 點設定 >> IP位置
    設定，接著把"phoneaddr"的IP換成手機上的IP位置即可。
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_57eba7a404c7fa67126827c023ad561f.png)
    
    網路與網際網路
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_484e84bf64963ef9da3a07ecfb7fccd7.png)
    
    選擇連接的網際網路
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2751963a1f0a6a9235d6751b7582f42a.png)
    
    點設定(小齒輪)
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_31e5a77962dd62b25a98da4c6f781074.png)
    
    IP位置(往下拉)
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ee4fdeab32390b3e880ed266153dc16e.png)
    
    3.2 修改 device -- 可以直接從投影軟體上看設備號，不過只要"Phone-"後面的部分就好。
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e2a9171c1e8ded3201d4736d71555cf5.png)
    
    3.3 修改 account -- 詢問站點，現在連接的設備使用的是哪個卡主，請他們提供當初拍掃臉影片時的帳號或VCODE
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_75b128247a1ec2abf0b1ac7f2b4aed19.png)
    再從他們提供的帳號或VCODE去後台找到相對應的帳號，這邊用"test11111"舉例
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1c92e0357ed1cd7d15c2d3141906ff21.png)
    如果帳號是"test11111"就把config.yml檔內的"account"改成 "test11111"
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0c8b7049df0ac7a2e123d6b89ba3035d.png)
    
    3.4 修改 bank -- 依照使用的銀行名稱來改，固定為小寫。
    如果是MB設備的話就改"mb"，VPB設備的話就改"vpb"，以此類推
    
    3.5 全部改完，存檔就可以了

4. 第四步，點 "downloadFile0_1.exe" 下載卡主的照片
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_64a6efcb2e1b73c1aeea738af95e4c9d.png)
下載成功，會多一個該銀行的資料夾，裡面就是卡主的照片
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f0f317578d0febdd07b09a5efd42cdb8.png)

5. 第五步，點 "firstFrida.exe" 啟動 Frida 程式
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_43b15973acd437868d472a8b011f5ee1.png)
如果正常啟動，會跑出比較ㄉㄨㄛ
    
    5.1 如果 "firstFrida.exe" 啟動失敗，請先執行一次 "clearFridaServer.exe" 再重新執行 "firstFrida.exe" 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4d24b75c9c296b01be69990125712271.png)











    


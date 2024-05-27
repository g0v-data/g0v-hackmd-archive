# 計算機概論 

* ## 我們選擇yolo的原因
* ##  我們怎麼做的
1. 收集照片
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d98de5e208c2ab3b1f39c677a499dd0a.png)
.
.
.
前面都跟影片差不多 
只是我們是照片不是影片
.
.
.
每張照片都標好後
開始訓練模型
把照片跟文字檔分成images 跟 labels再細分成train 跟 val檔


建立一個名為test.yaml的檔案
主要是用來讀取學習資料的路徑
0、1為他的類別
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_98a369ba7e939974cfe519665abf4c49.png)

修改yolov5檔案中的train.py 檔
這檔案主要是拿來做模型訓練
修改第518行 將路徑改為test.yaml檔案的路徑(把修的地方劃出來)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c6d19e44745cf8b34518c23bd409e83e.png)

開始運行
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5d6540af7488c16f1f8a001a58494345.png)

數值正常
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3fb6d827dd85d17d076c1cba810088eb.png)
開始學習


* ##  DEMO



* ## 過程中遇到的問題
1. 照片讀不到
原因:因為圖片中含有中文字
解決方法: 將所有的圖片名稱改成單純數字










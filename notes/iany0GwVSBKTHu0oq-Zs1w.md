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
2. 沒辦法訓練
原因:GPU記憶體不足
解決方法:將默認值從16改為8
原代碼:parser.add_argument("--batch-size", type=int, default=16, help="total batch size for all GPUs, -1 for autobatch")

改後的:parser.add_argument("--batch-size", type=int, default=8, help="total batch size for all GPUs, -1 for autobatch")
這句代碼是在使用Python中的argparse模塊，用於添加命令行選項以便在執行程序時可以設置參數。具體到這行代碼：

parser.add_argument("--batch-size", type=int, default=8, help="total batch size for all GPUs, -1 for autobatch")
這樣解釋：

--batch-size：這是一個命令行選項，用戶可以在命令行中使用這個選項來指定一個整數值。
type=int：指定這個選項的值必須是整數類型。
default=8：如果在命令行中沒有提供--batch-size選項，則其值默認為8。
help="total batch size for all GPUs, -1 for autobatch"：提供了這個選項的說明信息，告訴用戶這個選項是用來設定所有GPU的總批次大小，如果設置為-1，則表示自動批次，即程序會根據可用的記憶體和其他條件自動選擇批次大小。
這行代碼使得用戶可以通過命令行來靈活控制程序中批次的大小，非常適用於需要在不同運行環境或根據不同硬件配置調整批次大小的情況。

我將16改成8改變了什麼

如果你將命令行參數 --batch-size 的值從 16 改為 8，這會對你的程序或模型訓練有以下幾個可能的影響：

減少記憶體使用：每個批次的數據量減少，因此每次迭代消耗的GPU記憶體也會減少。這對於解決內存不足的問題非常有幫助。

訓練速度：通常情況下，較小的批次大小可能會導致訓練過程中每個epoch的時間增加，因為需要更多的迭代來處理相同量的數據。

模型性能：批次大小會影響模型訓練的結果。較小的批次通常可以提供更好的泛化性能，但也可能導致訓練過程更加不穩定。相對地，較大的批次可能提供更穩定的梯度估計，但有過度擬合的風險。

梯度更新：每個批次的梯度更新頻率會增加，因為每次處理的數據量減少了。這可能會導致模型學習的路徑更加多變，特別是在梯度下降過程中。

能耗與效率：較小的批次大小可能會影響整體的計算效率，有時可能導致GPU資源的利用率不是最優化，從而影響能源消耗和訓練時間。

總之，批次大小的調整是機器學習和深度學習中一個重要的超參數，需要根據具體的應用場景和硬件條件來適當調整。在許多情況下，找到最佳的批次大小需要通過實驗來確定。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e17bb7ebbd4af0e0ca09091a59bd9fe3.png)

3. 判斷不夠精確
推測原因:樣本數不夠










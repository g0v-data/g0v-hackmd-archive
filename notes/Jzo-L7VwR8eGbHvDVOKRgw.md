# Readme
**資料放置路徑**
data資料夾為Simple dataSet
資料集下需要有real(真實資料)、drop(缺失資料)
資料集的csv需對應(例如:real0.csv需對應drop0.csv)
> 資料集/real/*.csv
> 資料集/drop/*.csv

調整Config.py來設定以下各種參數
```python
# For Train
use_cuda = torch.cuda.is_available() #判斷是否可以啟用GPU
epochs = 10000    #訓練次數
batch_size = 16  #batch size設定
drop_percent = 90 #丟失資料
epoch2save = 5   #經過多少epoch後儲存
file_keep = 1    #需保留多少模型檔案(-1為無限制)
model_path = './model/' #儲存模型的路徑
nowusedata = 'data'  #使用的資料集的key

# For Predict
model_path_pre = './model/model.pt' #載入模型路徑
output_path = './output' #預測後要輸出路徑
predictdata = 'data' #使用的資料集的key
png_num = 10 #熱力圖輸出張數
```

資料集路徑設定
```python
# 資料集設置 "key":對應路徑
# EX: 'data':'./data'
# 'data_test':'./data/test'
data_class = {
    'data':"data/train",
	'data_test':'./data/test'
}
```

Training Model
```bash
python train.py
```

Predict Model
```bash
python predict.py
```
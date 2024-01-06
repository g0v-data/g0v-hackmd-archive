# Data mining
## Project2 -  Classification
* 郭昱辰
* N96091148
## Enviroment
* Windows 10
## Prerequisite
* Python 3.5.0
## File Structure
* CNB.py
* CNB_result.jpg
* DATA.py
* DT.jpg
* project2.py
* SVM.jpg
* SVM.py
* SVM_result.jpg
* Test_train.csv
* Test_val.csv
* TREE.py
* Tree_result.jpg

## DATA
* 本次project使用資料是以英雄聯盟電競選手校園海選的情境做分類，定義age(年齡)、experience(遊戲經驗)、rank(牌位)、rate(勝率)、pool(角色池)、potential(潛能)六種屬性分類，各種分類狀況如下:
    * age : 0~30歲(16以下無法參加)
    * experience : 0~10年(5年以上屬於資深玩家)
    * rank : Master以下、Master、ELITE(Master以上才夠格)
    * rate : 0~100%(55%以上才有資格)
    * pool : 0~110隻遊戲角色(至少需要專精70隻才組已成為選手)
    * potentioal : 0~10(8分以上可視為未來之星)
* absolutely right 定義如下:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9a16c66dbb9ce75817f3a311061ee0f7.jpg)

 Training data: 5000筆
 Testing data: 100筆

## Result
* Decision Tree : Accuracy = 1.0
|--- experience <= 4.50
|   |--- rate <= 54.50
|   |   |--- pool <= 69.50
|   |   |   |--- rank <= 0.50
|   |   |   |   |--- class: 1.0
|   |   |   |--- rank >  0.50
|   |   |   |   |--- potential <= 7.50
|   |   |   |   |   |--- class: -1.0
|   |   |   |   |--- potential >  7.50
|   |   |   |   |   |--- class: 1.0
|   |   |--- pool >  69.50
|   |   |   |--- class: 1.0
|   |--- rate >  54.50
|   |   |--- class: 1.0
|--- experience >  4.50
|   |--- rank <= 0.50
|   |   |--- class: -1.0
|   |--- rank >  0.50
|   |   |--- rate <= 54.50
|   |   |   |--- pool <= 69.50
|   |   |   |   |--- potential <= 7.50
|   |   |   |   |   |--- class: -1.0
|   |   |   |   |--- potential >  7.50
|   |   |   |   |   |--- class: 1.0
|   |   |   |--- pool >  69.50
|   |   |   |   |--- class: 1.0
|   |   |--- rate >  54.50
|   |   |   |--- class: 1.0

* ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8028e9ce6d1ae94454dbc28567141c3c.JPG)

* SVM : Accuracy = 0.948
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1e1c3c59baf9991396d350e092e442a8.JPG)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_098dac9964fded7ed80b90d63cef45e2.JPG)


* Categorical Naive Bayes : Accuracy = 0.808
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e2f32eda2e05ab8b78700d9d93e77d61.JPG)

## Conclusion
不論Decision Tree、SVM、Naive Bays各有不同的分類方法，對於不同的資料採用不同模型會有不同的結果。例如Descision Tree方法與結構最為簡單，但出來的效果仍然很好，因此若要訓練一未知的資料進行分類，應嘗試各種不同的模型，再做選擇。

##Author
Kuo Yu-Chen
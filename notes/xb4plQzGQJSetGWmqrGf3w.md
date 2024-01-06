# ***專題共筆***

每星期天討論這星期讀了什麼，
以及下個星期預計要讀什麼

---
# *padding 參數意義*
Feature map寬高會依據kernel size縮小一點(「padding = ‘VALID’」)或Feature map寬高不變(「padding = ‘SAME’」)

而padding會依據kernal(filter) size
不同而有所不同

利用zero padding
kernel size是3的時候，你希望卷積後圖的寬高不要變，pad就要設定為1
kernel size是5的時候，你希望卷積後圖的寬高不要變，pad就要設定為2
kernel size是7的時候，你希望卷積後圖的寬高不要變，pad就要設定為3
參考網址：https://medium.com/@chih.sheng.huang821/%E5%8D%B7%E7%A9%8D%E7%A5%9E%E7%B6%93%E7%B6%B2%E8%B7%AF-convolutional-neural-network-cnn-%E5%8D%B7%E7%A9%8D%E8%A8%88%E7%AE%97%E4%B8%AD%E7%9A%84%E6%AD%A5%E4%BC%90-stride-%E5%92%8C%E5%A1%AB%E5%85%85-padding-94449e638e82

# *Deep Learning    machine learning techniques*

*         Deep Neural Network
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_21d8324670efd1730a94170dc076bc4f)
meaning of each layer : simple to complex features
challenges and Key for Deep Learning:

**1.difficult structural decisions:**
validation(general),subjective with domain knowledge(CNN for images)下一層的神經元不一定連到上層的每個神經元(離太遠的pixel毫無關聯)

**2.High model complexity:**
no big worries if big enough data
regularization towards noise-tolerant:
dropout(tolerant when network corrupted 神經元壞掉)
denoising(tolerant when input corrupted 模擬輸入不正常時)

**3. Hard optimization problem**
careful initialization to avoid bad local minimum:pre-training

**4. Huge computational complexity**
novel hardware/architecture.Like mini-batch with GPU

**Regularization & Initialization are Key techniques!!**
**Simple techniques:**
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_960bf889d09dabf8e4f0dee9ba8e3cce)
-->上圖說明一個Initialization的方式，我們先決定input到第一層的weights(how)，固定下來之後再來決定2到3，再固定，再慢慢找出全部weight
(一次決定全部太多了)
-->進一步訓練

*         AutoEncoder
HOW TO PRETRAIN!?

meaning of weights? feature transform. 或是說我們如何把資料換成另一種表現形式(encoding)

good weights:information-preserving encoding! next layer contains same info with different representation.
(每層都保有特徵 但只是更加精煉)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b16493b8c4176da8dbde7485ad4156ad)
//你可以透過phi 1,2,3 重建回原始資料 1(表示資訊損失少)//
**Information-Preserving Neural Network**
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0773b9cbc45005bba9ed84f13121fc5c)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_42d726f3cf4f9c8724b7a7f10b645dbd)
**Why Identity Function?**
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5c3b457f0e03351dd0afd0ae7548adcb)
supervised:這些潛藏的結構可以作為一個不錯的transform!
(以手寫辨識數字來說 即是phi 1,2,3那三種筆畫)

unsupervised:
1.判斷是否稠密:資料密度高的地方 還原做得比較好
2.outlier detection:不合群的資料 還原做的比較差!
=>於是可以挑出那些是典型的資料!

auto-encoder:representaion learning through appoximating identity function!
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_770a5c0579afb8ead1925850def7f9ab)
有時候編碼以及解碼的weights會限制相同作為regularization，但這會提升backprop難度。
於是前面的一層一層pretrain的方式就決定了
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1681131bfc24a0b83c623f9517dcd8f3)
以上層的輸出 做為要輸出的對象。


*         Denoising Encoder
Initialization is done.How about regularization?
Why overfitting? data size,noise,excessive power...
if data size and model(power) are fixed...=>deal with noise
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_eb726f839efc30b907dd4bfcb7287046)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_409ff9b45e26c8d6897692da469ff6c8)
=>給有雜訊的資料 仍能輸出正確的資料
=>某種程度上限制了g
=>artificial noise/hint(指引應該將哪種資料做得更好) as regularizer


*         Principal Component Analysis
linear dimension reduction:compress to a smaller dimension
Lagrange multiplier
太多細節就不記了
    (筆記後續補上 2019.7.2    22:30)
# *Radial basis function network    machine learning techniques*
* RBF Network Hypothesis
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_607f63b89f67d503fd34fe368ad8fc2e)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6c8ae805eee35f130c62130c27e57c33)
=>guassian svm:linear aggregation of selected radial hypothesis
**RBF network:linear aggregation of radial hypothesis**
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d39dab72cda472bfa01b94f46f36879c)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cd7b449fe2a100386100f9dd3e352c65)
um: center bm:weight
now given rbf and output. decide the weight  and support vector(center) of each rbf!(idea from gaussian svm)
kernel: similartity via z space inner product.
similarity is a good thing to determine our feature transform.similarity is not just distance!
RBF network:distance similarity-to-centers as feature
(利用到中心點距離的相似性來做特徵轉換)
* RBF Network Learning
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a5653b9374f34328175e7aa717235db7)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5f5ef9125653f2fa1b15c800937392e8)
aggregate with same votes,every data point can express their opinion,and the voting result is weighted by distance.
full RBF network:a lazy way to decide centers
**Nearest Neighbor**
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4e95284f758eab2ee7b1547ed9d48334)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f4f6c7a1cc1704463b75c51dad8da31b)
idea : we only find the maximum one! or to say,the nearest. =>this is selection .Nearest Neighbor Model
**Fewer Centers as regularization**
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4f63e0a324498893e67ed07f87d59c16)
like svm,we choose less centers.找出幾個點當代表
then how to find prototypes?
* k-means algorithm
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3594e00c0432cbb330f8c20f500fe644)
找出一個好的代表(prototype)...WHY?資料分群!若兩筆資料相近，則它們的RBF很相近!不需要有相同的的意見，僅須有一個代表!
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_036ad17ef8dd14d242c7bab7364bb5e6)
↑cluster error with square error measure. Goal : minimize this
但很難同時最佳化(組合&數值最佳化)，考慮分別最佳化(fix one of them)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f2405c417f62ac0df714665d5f8cef65)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9cf2874b2d389ec3baaad913e904828d)
固定partition的話，是一個無條件最佳化問題! 直接微分
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7674672c0415a19caefbeecb484a1730)
隨意選k個資料作為一開始的代表。收斂直到s1,s2...sk(分群內的成員)不再改變為止，並保證收斂(交互最佳化過程會使Ein減少並有一個下限)
k-means:popular through alternating minimizing.
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_134aea411ff8a5aab756b15a45d73463)
同樣使用非監督式學習(k-means)來幫助特徵轉換，需要決定M(prototype)以及RBF。
* k-means and RBF network in Action
k-means: sensitive to k and initialization!
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6c465c9f7c800553ce58e962f708fcfc)
RBF network with k-means: good performance with proper centers
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3026062e2ff18c19b48e93c83acb24e1)
Full RBF network:
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c2995a1b38d733f28606cd1c5f439be5)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c2cba31bde9e9feafd26cef34eba7d6f)
# Matrix Factorization
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6d5e971cbfa06d3b237bf3262644d8b6)
categorical features:抽象的特徵 難以建立線性模型，不太有任何數值上的關聯或意義。
need: encoding(transform) from categorical to numerical.
但有些也會使用categorical .like decision tree.
**Feature Extraction from encoding vector**
BinaryVectorEncoding:僅使用0,1作為向量中各維度的值，藉以將類別資料轉換為數值資料。現在我們用類神經網路來擷取向量(使用者)中的特徵。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2d2d357907f6bcaf10f94e4a06982e5f)
為了簡化，我們先忽略常數項。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ee5148c33e13d6ceb12035f1cc9a5369)
now learn V&W !



















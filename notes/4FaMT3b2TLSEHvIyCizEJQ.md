# PR Midterm Note

### 配分
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8803841499ba042e43f2763238f7da31.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3939ab410eb4939e96bfb7e0d81a4f3d.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_60e5f2d843d2561a8f87d191eb0d0fb6.png)


### 觀念題

#### 1. 分類器的不同

**貝氏分類器**
>當資料分布與統計機率一樣時，則以統計學概論來說，沒有比「貝氏分類器」更好的方法

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_79f2cb81ed0147684e6a7590555059db.png);![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8f38ed62cd2189f60e2bb695f96ee497.png)**為先驗機率**; ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d3a1f5edc219aed8b0b7bd4a5c4e9895.png)**為Likelihood**


Likelihood 
: 在已知道類別的情況下，你的特徵的機率分布。
以上圖為例子，在知道母數C類別的情況下，D會出現的機率分佈是![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0ec61dfb59a854b5dc8247d3eed86dbe.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f6ce1288e26cb374707bb6409c3c4c4e.png)
*Likelihood與先驗機率的相乘占了很重要的一部份去決定後驗機率*




**Neural Network**
>Neural Network相比統計方法在學習時，不會先給Training Data做假設(如:高斯分佈)，所以學習成效通常比統計來得好，**因為Normal Pattern 不會跟Training Data給定的假設一樣**

Neural Network Learning 具有 Generalization

#### 2. 分類器的名詞介紹 (包括訓練方式、特性)

Generalization 
: 從Training Data學習到一條Decision Boundary，如果在Normal Pattern時，表現得也不錯，則稱這方法Generalization好


Supervised V.S Unsupervised classification
: 不解釋

Parametric classification (必考)
: 可以用一種用參數型的密度函數(Density Function)來設計分類器
如 Hypothesis testing & Bayes classifier
 

Nonparametric classification (必考)
: 可以用一種非結構化的方法(unstructured approach)來設計分類器
The estimates is far less reliable with larger bias and variance than the parametric counterpart.(這句不懂 考試有考建議寫英文)
因為偏差與方差較大，預估較不準確 (KYU)
如 Statistical approaches & Neural networks

Hughes Phenomenon
: 模型的預測能力隨著特徵數量的增加會先升後降 (overtrain)
特徵overlap容易發生Hughes Phenomenon

Bayes Decision Rule
: Decide W1 if P(W1|x) > P(W2|x); otherwise decide W2
P(error|x) = min[P(W1|x),P(W2|x)]
Decide W1 if p(x|W1)P(W1) > p(x|W2)P(W2); otherwise decide W2

Likelihood ratio
: ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_17d4e3886ceb8b72c01c0da4205f2230.png)

Likelihood ratio test
: ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d1755bfd6934d18c32f2fc10993ba19f.png)

Bayes Decision Rule for Minmum Error
: Example x超過t x就判定屬於w2
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_210c4e968f918b38cb4a97f4b3d58b50.png)


最小Error等於
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_836c9f5a20a049173009e7096a28d4ed.png)

PR07.pdf  考Covariance Matrix 跟 Mean Vector 運算
: [Covariance Matrix介紹](https://www.youtube.com/watch?v=152tSYtiQbw)
**ALL Covariance Matrices are Symmetric**

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_886f592a0d005b4b3f44dbe0b68d3021.png)


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3fb331e682ac48de4f2f0c7a7bc0279c.png)

下面這2張會考!!!
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_39ee8cce03807807a5c4e80e03432634.png)


#### 3. BackProgation (期末考會考的??不確定期中會不會考)
影片 考怎麼算出W <-- Neural Network 的 Edge
: [BackProgation介紹](https://www.youtube.com/watch?v=ibJpTrp5mcE)
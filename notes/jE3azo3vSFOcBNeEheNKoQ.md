# 資料科學

1. reference 標出處
2. 要註解(怎ㄇ用，用自己的想法描述而不是翻譯)
3. 時間複雜度(vip)


------------------

1. training set : 建Model用
2. validation set : 用來調整Model參數，提高準確度
3. test set : 做最後測試，結果即最終Model準確度
**永遠不能重疊這三種資料**

---
* 在相同的validation set中，使用不同比例的training set
* 使用多重交叉驗證消冗資料的變異性
* 如何表達資料、照什麼當依據皆會影響之後的訓練

# High-quality Dataset
A few things to keep in mind when searching for high-quality datasets:

1. A high-quality dataset should not be messy, because you do not want to spend a lot of time cleaning data.(不能太亂

2. A high-quality dataset should not have too many rows or columns, so it is easy to work with.(不要有太多欄位)

3. The cleaner the data, the better — cleaning a large dataset can be incredibly time-consuming.

4. Your end-goal should have a question/decision to answer, which in turn can be answered with data.

**Imbalanced Dataset：不平衡資料集**
-
定義：
指資料集中的類別>=2個者，其分布比例不平均，若資料比例相差不大，對之後的預測造成的影響可能不大，但若資料及比例相差懸殊，會造成後續再做預測時，準確度看似很高，但其實並不是好的model
# 

# ----------------(洽)了解各演算法對imbalance datasets的作用及成效----------

# 變異數    參考影片:變異數與標準差的概念及其範例https://www.youtube.com/watch?v=FNgbhAuvyPQ
->所有跟(平均數的差)做平方再做平均

# 標準差
->變異數開根號

# SMOTE    參考網站:https://www.itread01.com/content/1543288145.html 
->對少數類樣本進行分析並根據少數類樣本人工合成新樣本(衍生新樣本)，新增到資料集

SMOTE Border Line
->邊界的少數樣本容易跟多數樣本混合在一起造成雜訊，

# 夾角餘弦    參考網站:同上
->範圍[-1,1]，2個向量方向重疊時相當於夾角0˙=1，反之，當2個向量方向完全相反相當於夾角180˙=-1，由此可得知，夾角之餘弦越大代表2個向量的夾角越小。

# k-means    參考網站:https://medium.com/@chih.sheng.huang821/%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92-%E9%9B%86%E7%BE%A4%E5%88%86%E6%9E%90-k-means-clustering-e608a7fe1b43
->白話:一個班上都會有幾個群體，大家會因為這個群體裡的老大而聚在一起，這些群體在k-means裡也就是k群，老大就是"群心"，在群體還沒穩定前老大都有可能換人當，所以需要一直更新，也就是換掉"群心"。
每個data都會有k個群心，以歐式距離做計算將每筆資料分配給離它最近距離的群心，在這過程中都會一直有新的資料被分配過來，一直更新直到所有群心不再有太大變動即為"收斂"
問題:k-means概念懂，可是它底下"ADASYN"應用k-means原理做imbalance datasets的方法看不懂

# undersampling 2個分支:EasyEnsemble、BalanceCascade
->

# 下採樣
->將多數樣本中不具代表性的資料去除以避免造成雜訊。
  讓多數樣本的數量減少至與少數樣本的數量一致(縮小樣本)
缺點：過擬和，沒有鑑別度的data也被模型考慮進去，等於是餵分類器吃了垃圾
解法：
Tomek Link，假設a,b兩點各別為多數資料集和少數資料集中一筆data，去計算a,b間的距離d，這時去找第三個樣本點c，若找不到這點c的距離<a,b間的距離，則代表a,b屬於Tomek Link對有2種做法：
1.under sampling：將Tomek link對中屬於多數類的樣本剔除
2.數據清洗：將Tomek link對中的兩個樣本都剔除

# 泛化能力
->演算法對新資料的適應能力

# 上採樣
->將少數樣本用某種方式重複抽樣或合成新樣本(ex.SMOTE)。
解法：
Borderline-SMOTE：為周圍被被大眾樣本包圍的小眾樣本生成新樣本，因為這些小眾樣本通常都是邊界樣本，但若k附近都是大眾樣本則捨棄那筆小眾樣本

# 代價矩陣(不知道怎麼做，只知道他的概念)
->研究者們針對不同的learning model如感知機，SVM，decision tree，神經網路等提出各別的代價敏感版本
解釋：在現實生活中每個情況的判斷錯誤所造成的損失都有不同，例如一個人到醫院做檢查，檢查結果出來他可能患有癌症，那這位病人需再額外進行更深入的健康檢查，請可能對他造成一些心理壓力，但若是對真正患有癌症的病人檢測結果判斷他為健康，那可能造成這位患者延誤就醫最後喪命，這一前一後的差別所造成的代價即可以代價矩陣做

# k-fold cross-validation(dataset平衡才可做)

# 混淆矩陣
->True Positive 真陽性 : 實際上是正樣本且被預測為正樣本
  True Negative 真陰性 : 實際上是負樣本且被預測為負樣本
  False Positive 假陽性 : 實際上是負樣本但被錯誤預測為正樣本
  False Negative 假陰性 : 實際上是正樣本但被錯誤預測為負樣本
  
  accuracy = (TP+TN) / N(全部樣本)
  precision = TP / (TP+FP)被電腦預測是正樣本的總數
  recall = TP / (TP+FN)正樣本總數
  F1-score調和平均數 = 

---

# algorithm
**1、 分類器整合方法**
Chen等 提出了平衡隨機森林的方法 ,該方法對正類和反類分別進行重取樣, 重取樣多次後採用多數投票的方法進行整合學習.Chawla等人將boosting演算法與 SMOTE算法結合成SMOTEBoost演算法,該演算法每次迭代使用SMOTE生成新的樣本 ,取代原有 AdaBoost演算法中對樣本權值的調整,使得Boosting演算法專注於正類中的難分樣本

**2、 代價敏感方法**
在大部分不平衡分類問題中 , 稀有類是分類的重點 .在這種情況下 , 正確識別出稀有類的樣本比識 別大類的樣本更有價值 .反過來說 , 錯分稀有類的樣 本需要付出更大的代價 .代價敏感學習賦予各個類別不同的錯分代價 , 它能很好地解決不平衡分類 問題 .以兩類問題為例 , 假設正類是稀有類 , 並具有 更高的錯分代價 , 則分類器在訓練時 , 會對錯分正類 樣本做更大的懲罰 , 迫使最終分類器對正類樣本有更高的識別率 .如 **Metacost** 和 **Adacost** 等演算法。

代價敏感學習能有效地提高稀有類的識別率 . 但問題是 , 一方面 , 在多數情況下 , 真實的錯分代價 很難被準確地估計.另一方面,雖然許多分類器 可以直接引入代價敏感學習機制 , 如支援向量機和 決策樹 , 但是也有一些分類器不能直接使用代價敏感學習 , 只能通過調整正負樣本比例或者決策閾值間接的實現代價敏感學習，這樣不能保證代價敏感學習的效果。

**3、 特徵選擇方法**
特徵選擇方法對於不平衡分類問題同樣具有重要意義 .樣本數量分佈很不平衡時,特徵的分佈同樣會不平衡.尤其在文字分類問題中,在大類中經常出現的特徵,也許在稀有類中根本不出現 .因此 ,根據不平衡分類問題的特點 , 選取最具有區分能力的特徵 ,有利於提高稀有類的識別率 .

通過採用特徵選擇來解決不平衡分類問題主要 
集中於自然語言處理領域 .Cardie和 HoweOptimally combining positive and negative features for text categorization 
以基於**事例學習 (casebasedlearning)** 的框架為基礎,提出了一種與測試樣本相關的動態特徵加權方法 .該方法首先利用訓練集得到一棵決策樹, 然後計算每個測試樣本在測試路徑上的資訊收益, 並以此計算每個特徵的權值, 最後 , 從訓練集中挑選 k個與測試樣本最接近的樣本 ,並對他們測試類別進行投票 .該方法在提高正類樣本準確率的同時確保了總的準確率不下降

**4、其他演算法**
Wu和 Chang KBA: kernel boundary alignment considering imbalanced data distribution 提出了一種修改支援向量機核 
**函式矩陣 (kernelmatrix)** 方法 , 該方法通過將核函式 矩陣進行保角變換(conformaltransformation), 擴大 稀有類特徵向量處的邊界 , 從而增加正負類樣本的 分離度 , 減少大類的支援向量數目 , 起到降低不平衡 度的效果 .理論分析和模擬試驗結果表明 , 該方法在 一些不平衡資料集上有比較好的效果 .

**一 類 學 習 (one-clas slearning)** Estimating the support of a high-dimensional distribution也 被 用 於 處 理 不平衡問題 .當樣本數量不平衡時 , 並且當特徵空間 中混雜有大量噪音特徵時 , 基於學習單一稀有類樣本的產生式模型 , 相比於學習兩類問題的判別式模型具有更好的效能.

# 準確度悖論：
面對非均衡資料集時，準確度這個評估指標會使模型嚴重偏向佔比更多的類別，導致模型的預測功能失效。

# kaggle (男:1、女:2)
身高、體重、iq亂填的->男生，少數女生也有這個現象
算BMI判斷男女
最後一欄intro(重要但有點難，有些中文是亂碼)->有些從敘述中就會有說他是男生還女生，但，需用中文、英文的自然語言處理去分析
睡意欄位->大部份3分以上的高機率是男生(55%)
training dataset iq、yt各有2格遺漏值(皆在女生列)
testing dataset沒有遺漏值
關於遺漏值填補：
因為觀察到這2筆遺漏值皆為女生，其上下2筆也為女生且iq & yt所填的值皆在合理範圍內，故將遺漏值填上其他同為女生所填之值iq = 100、yt = 2
法1：去計算詞頻，比較某個詞被男生還女生用的機率最大，之後若再出現這個詞就提升這筆data為該性別的機率
特徵值判斷順序：intro -> BMI -> iq
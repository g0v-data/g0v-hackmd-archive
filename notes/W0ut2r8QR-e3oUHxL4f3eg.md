統計學期末筆記
===
###### tags: `統計`
CH12
---
1. *前言*

>這章節都在講跟多個母體作比較，比一些咚咚像是比例、適合度、獨立性，阿也因為有比較就有差值、所以我們會用平方去算統計量，也因為這樣我們都用卡方檢定去判斷。
2. *啥是卡方檢定*

>卡方檢定通常是為了處理類別變數(Categorical Varirable)的資料像是職業(教師、工程師...)，在CH12裡面的data就是用類別根各母體組成的table，像這樣
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2446b6b1201e8e459189277dc932f2e1.png)
row就是類別變數column則是各母體
3. *卡方用途*
>在CH12我們會討論三個主要用途
>>1. **多比例(齊一次檢定)**:檢定多個互相獨立的母體，其中只涉及1個類別變數。
>>舉例:有三間店，麥當掉、肯德不到、摩斯漢人(後面舉例都用這三間了)，而row就是好吃、不好吃跟沒意見，然後我們就會去討論"認為麥當掉好吃的比例" 和 "認為肯德不到好吃的比例" 和 "認為摩斯漢人好吃的比例"   是否相等(Ho)
>>2.    **適合度檢定(Goodness of Fit Tests)**:是用來了解單一母體而類別變數會是分成好幾類，我們會要特定的分類有特定的比例，像是麥當掉(單一母體)的好吃比例=0.5、不好吃的比例=0.2跟沒意見的比例=0.3(這就是Ho)
>> 3.**獨立性檢定(Independence Tests)**:為了瞭解單一母體，2個類別變數之間是否獨立，可以用高中學到的機率去看，$p(x|y)=p(x)$   $p(x,y交集)=p(x)*p(y)$ 算出來後的數字只是期望值。 




CH12補充
---
懶得打上去了
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_59a39d8e3da16f813774a3c978150d51.jpg)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4b9157cf923c2746b0703d3945e6f2e7.jpg)


### 配適度檢定


多了平均跟標準差要估計所以從k-1變k-3



## CH13變異數分析
---
第13章討論的是關於自變數跟應變數的關係，對於自變數的分類還可以分成三種來討論，因為是討論各自變數是否會影響應變數，所以Ho假設都會是判斷是否相等，另外這章節會出現許多的新名詞。

data都是離散變數(相反的是連續變數)，因為這種變數才可以推測因果關係，連續也不是不行啦，只是要切，而CH13會教三種類型的
1. 一因子分析(a compelety randomized design)
2. 一因子區集分析(a randomized block design)
3. 二因子分析(a factorial experiment)

對於我們想討論的因素我們會稱他為因子，不想要討論的我們會稱他為

h0:每個母體的平均數相等
ha:reject h0


>大家都是相同的常態分配，下圖是符合H0
>>![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1d841bb2bac63c1a8da0f4829dacbcf7.png)
>他們的散的不開

>但如果是符合Ha，就會顯得分很開
>>![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d0c8cddaaff47fc983dcf3e7dd171f03.png)


從以上我們可以知道要判斷ho&ha是看他們離散的程度，而散的程度可以看標準差 || 變異數，所以這章才叫變異數檢定，而也因為我們看的是差距程度所以都會是右尾檢定



MSE:誤差變異數(處理內變異數)


為什麼SSTR+SSE=SST?公式推導


LSD:(t-distribution)
hypothese:
這次沒有加絕對值
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8c52f5cce065d546126e83ffc4bfea8f.png)
Ho可以寫做是否相等


統計量:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_672906fac1f9d3879d05f591845e0848.png)
第十章有教過

CH13-B
假設化學實驗有兩個因素分別為濃度跟溫度會影響實驗結果
二因子分析(Factorial):就是將兩種都納入考量
一因子區集(Randomized Block Design):就是將另一種固定只考慮一種


ANOVA Procedure:
SST = SSTR(處理變異) + SSBL(區集變異) + SSE(誤差變異)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9386e7b7d6edf835ea879604060b37a4.png)


因為MSBL本來就不在討論範圍內，所以在算F分配時沒有MSBL

二因子分析(Factorial Experiment)
---

SST = SSA(A變異) + SSB(B變異) + SSAB(交互變異) + SSE(誤差變異)

/*A&B分別為兩個因子的代號*/

整理如下:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fdcfd90ab4476187330a252ad0c5ade2.png)

有三個檢定分別檢查A、B跟AB對應變數的影響

.i. .j.





CH14
---
>**簡單線性回歸(simple linear regression)**
>>這是在去找變數間的關係，而他們的公式長這樣
>>![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b09417bf1a26a8eefea7c73f493d2728.png)
>>sigma 比較像是修正用的，通常是沒在看的，簡稱垃圾
>>


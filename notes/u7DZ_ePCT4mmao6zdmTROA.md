# ADA-Introduction
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_90b8bc331548f205ad90883ab9096cce.png)
---
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_acbff0f17f323abeaab3e300cdc5a73c.png)
---
### 平攤分析 Amortized Analysis
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_de9d6ffc5ebe77c4ccc9dd80c8ca28bd.png)

算法分析中，平攤分析尋找在**最壞情況下的操作序列中每操作的平均耗費時間**。這個方法需要知道操作序列中可能發生的每個操作。通常應用在操作間存在狀態的資料結構中。基本思想是，一個最壞情況操作會改變狀態而不會在一段時間內再次出現，因此「平攤」它的耗費。

例如：動態數組中，我們在每次數組溢出時增長數組的長度至原來的兩倍。因此需要數組空間分配，在**最壞情況下一個插入操作需要O(n)的時間。但是，一個 n 個插入的操作序列仍然可以在 O(n) 的時間內完成**，因為剩下的插入可以在常數時間內完成，因此 n 個插入可以在 O(n) 的時間內完成。因此**每操作**的平攤耗費為 **O(n) / n = O(1)**。

---
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a2467113f5b87add81354f33b6e219bf.png)
---
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7daff3ac2b6447aa20f3da384bdd2313.png)
* f(n)=O(g(n)) doesn't imply 2^f(n) = O( 2^g(n) )
//why?
---
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_185be991bba6fc25e463bd2d133c7f27.png)

### Goal:Finding the Hardness
* Focus on worst-case complexity
 “**average-case**” analysis requires the assumption about the **probability distribution of problem instances**
>  Using 𝑂 to give upper bounds on the worst-case time complexity of algorithms
> Using **Ω** to give lower bounds on the **worst-case** time complexity of algorithms
> 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8cfb025a2b437d375242bf5f5dc0586a.png)

### Algorithm Comparison
Q: can we say that Algorithm 1 is a better algorithm than Algorithm 2 if
* Algorithm 1 runs in 𝑂(n) time
* Algorithm 2 runs in 𝑂(n^2) time

A: No! The algorithm with a **lower upper bound** on its worst-case time **does not necessarily have a lower time complexity.**

### Comparing A and B in terms of TIME complexity
* Algorithm A is **no worse than** Algorithm B in terms of worst-case time complexity if there exists a positive function 𝑓(𝑛) s.t.
    * Algorithm A runs in time 𝑂(𝑓(𝑛)) &
    * Algorithm B runs in time Ω(𝑓(𝑛)) in the worst case
* Algorithm A is **(strictly) better than** Algorithm B in terms of worst-case time complexity if there exists a positive function 𝑓(𝑛) s.t.
    * Algorithm A runs in time 𝑂(𝑓(𝑛)) &
    * Algorithm B runs in time 𝜔(𝑓(𝑛)) in the worst case
or
    * Algorithm A runs in time 𝑜(𝑓(𝑛)) &
    * Algorithm B runs in time Ω(𝑓(𝑛)) in the worst case
    
### Time Complexity of a Problem
We say that the (worst-case) time complexity of Problem P is Θ(𝑓(𝑛))) if:
1. The time complexity of Problem P is 𝑂(𝑓(𝑛))
    * There exists an 𝑂(𝑓(𝑛))-time algorithm that solves Problem P
2. The time complexity of Problem P is Ω(𝑓(𝑛))
    * **Any** algorithm that solves Problem P **requires** Ω(𝑓(𝑛)) time

> **漸進最優** (Asymptotically **optimal algorithm**)
> 在計算機科學中，漸進最優一詞用以評價算法的效率。如果已經證實一個問題需要使用Ω(f(n))的資源來解決，而某個算法用O(f(n))的資源來解決這個問題，則該算法就是漸進最優的。 
# ADA-Divide and Conquer(1)
## What is Divide and Conquer?
1. Divide the problem into a number of subproblems that are smaller instances of the same problem
2. Conquer the problem by solving them recursively
> Recursive Solution: Clear Structure and **Poor Efficiency**
> 
3. Combine

## Hanoi Tower
* Algorithm
```
Hanoi(n, src, dest, spare)
    if n==1 // base case
        Move disk from src to dest
    else // recursive case 
        Hanoi(n-1, src, spare, dest)
        Move disk from src to dest 
        Hanoi(n-1, spare, dest, src)
```

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ea6067a5f5e0f1f60488acc88534efa9.png)


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_af14aa20427db1ecd07a9117c9e728f7.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ba3f94c144af9968d9946271fb6df975.png)

---
##  Merge Sort
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_28a67ddec313e46d9e67349c316269da.png)
```
 MergeSort(A, p, r)
    // base case
    if p == r
        return
    //recursive case
    
    //divide
    q = [(p+r-1)/2]
    
    //conquer 
    MergeSort(A, p, q) 
    MergeSort(A, q+1, r) 
    
    //combine
    Merge(A, p, q, r)
}
```

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_65ea4a57c2951d126eb4ef4f8e49fb78.png)

---

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2bcc31f0d3b9480b31526131688746fd.png)

---
### 解題step1: 用替代法求得時間複雜度
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_41a445194c57cc693444f4b4580eeffc.png)

### 解題step2: 根據前面找到的線索，找出正確的假設
前面得T(n) <= T(1)* n + c * nlog(n)
故假設T(1) = a, T(n) <= a * n + 2b * nlog(n)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f5ab642d835d85757eb0f210914636f7.png)

##  Bitonic Champion Problem
 
Problem:
給定一個bitonic sequence，求最大值？
> The bitonic sequence means “increasing before the champion and decreasing after the champion” (冠軍之前遞增、冠軍之後遞減)
### 法一： 沒有使用到bitonic sequence性質的寫法：
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5ba67f140f323740fb26b2bd354f7eb0.png)

---
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_440f77ff4bed2343520782dae4de6f6b.png)

### 法二： 有使用到bitonic sequence性質的寫法：
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f7a2c374b5cebba47d0d14b463a620bd.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b5c2fc1a51e170ab65511e3a3225b50b.png)
* My Answer:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_404aa3f1e476c67d575423375da972dd.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_34af52cdbdfe920f38fa992cac9cb832.png)

## Maximum Subarray
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8cfc7b61a900a85ddbff3fe0c04431aa.png)

---

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_404890409e7f5f0e69b13fff8f12cffb.png)

### Divide and Conquer Algorithm
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_48f803bcc414e86b9cc377117a9be995.png)

---

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4cc1dc118f0ffcf205805d29f15165eb.png)


---

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f9b72879062fef296fd53bda285d6373.png)


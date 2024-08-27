# Back Track 
### 通常都是用來解組合的
### (leetcode 39、40、46、47、78、90)
####  基本模版
>需要base case(終止條件)
>遍歷題目給的input
>把遍歷的值暫存到list
>call Recursive (遞迴)
>把暫時的list最後一個pop掉，給新值留空間

# Leetcode 39
題目主要是dfs，把他想成樹的樣子，若變成-1就返回上一層，這樣target就會回復到上一層的樣子，比較可以接受

`使用 candidates = [2, 3, 6, 7] 和 target = 7作為範例，並使用樹狀結構來圖像化表示DFS的遞迴過程，了解如何「展開所有組合型態」，以找出正確組合。`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b554a6c0850e6f9134a65d8ac0f27da4.png)



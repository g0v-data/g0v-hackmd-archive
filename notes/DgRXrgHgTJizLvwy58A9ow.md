# 作業研究共同筆記
## simplex
1. 找出standard form
    - 非負RHS
    - 非負變數
    - 限制式均為等號
    - 範例![](https://i.imgur.com/l8aSeIs.jpg)
    - standard form也可以被表示為矩陣
![](https://i.imgur.com/a5VhUZt.jpg)![](https://i.imgur.com/2JpW0wQ.jpg)
2. 找出Basic solutions
    - 假設n為變數數量，m為限制式數量，則(n-m)為nonbasic variavles的數量，m為basic variable的數量。
    - 範例![](https://i.imgur.com/TVmszo6.jpg)![](https://i.imgur.com/ZCE9Jyy.jpg)
    - BFS是滿足條件的Basic solutions
    - 當一個解是extreme point of feasible region時，他必定是LP的BFS。
    - 如果一個LP有最佳解，那他必定有optimal BFS。(?
    - 範例![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_50db8b236a0ebf4c5f4163463661f50d)
    - extreme point是在"幾何上"的定義，而bfs是在"代數上"的定義。
3. simplex method
    - 不停的改變basis直到找到最佳解的basis
    - 使用tableau的範例:
    ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7f54480ead097ab6e15486f0e1eb65d0)
    - 原則上為找出ratio最小的開始(除非題目有指定)。
    - 當還沒找到optimal(0th尚未解決)時，ratio已經全部為非正數，則為unbounded LPs。
4. Two-phase implementation
    - phase 1，新增一個artificial variable![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d9041bc5dccd803da1c10332698ae065)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_474e1b8192a189ee3e7ac974a8be2aab)
    - 然後進行row operation![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_71b039aae1ef53b1f17491dee5460fc3)
    - phase 2，

## LPapp
1. Material blending
2. Linearizing maximum/minimum functions
    - 將不是linear的公式改為linear
    - 


# 2022.04.25 觀念題

---

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f62b174546513a731b788dc565a27502.png)
> int取整數，直接計算 val = 3/2 + 4/3 + 5/3

---
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d9af5aef2649419a0eb40332b959f8b0.png)
```
1.G(3)帶入→return K(a, 3)
2.if (n>=0)→return(K(a, 3-1)+a[3]) →a[3]值為2 = K（a, 2) + 2
3.n依然>=0 繼續計算，重複上述步驟
4.  K(a,2)=K(a,1)+a[2]=K(a,1)+3
    K(a,1)=K(a,0)+a[1]=K(a,0)+4
    K(a,0)=K(a,-1)+a[0]=K(a,-1)+5
    K(a,-1)=0，return 0
5.G(3)=14
```

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_911903d0f05f85c1cd9304889ce7c375.png)
```python=
"""
這個函式的中止條件會return 1

然後題目給的參數傳入值是7，回傳值是12

那麼就是
7 > 5 + 4
                                                     ( 7 )
5 > 3 + 2                                         ( 5 ) ( 4 )
4 > 2 + 0                                    ( 3 )( 2 ) ( 2 )( 0 )
                                          (1)( 0 )                                          /-------------------(7)
3 > 1 + 0              假設a<3才終止的話，就是1 + 1  + 1  + 1   + 1  = 5       /-------------(5)            /------(4)
2 > 0 + -2                                                         /------(3)          /--(2)       /--(2)    /-(1)
                                                               /-(1)    /-(0)      /-(0) (-1)   /-(0) (-1) (-1)(-2)
1 > -1 + -2                                                 (-1)(-2) (-2)(-1)   (-2)(-1)     (-2)(-1)
0 > -2 + -3                            假設a<0才終止的話，就是   1 + 1  + 1 + 1    + 1 + 1  + 1 + 1 + 1  + 1  + 1 + 1 = 12
"""


a = 7   # 試著填入各種不同數值
def f(a: int):
    if a < 3:
        return 1
    else:
        return f(a-2) + f(a-3)

print(f(a))

```
---
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_70ec6f20d0161f3869c9f8cbf113493a.jpg)

## 先進第一個Loop:
* i = 0時
```python=
tmp = a[0] = 1
a[0] = a[9-0-1] = a[8] = 2
a[8] = tmp = 1 #a[0]與a[8]互換
```
* i = 1時
```python=
tmp = a[1] = 3
a[1] = a[9-1-1] = a[7] = 4
a[7] = tmp = 3 #a[1]與a[7]互換
```
* i = 2時
```python=
#a[2]與a[6]互換
```
* i = 3時
```python=
#a[3]與a[5]互換
```
* i = 4時
```python=
#a[4]與a[4]互換
```
* i = 5時
```python=
#a[5]與a[3]互換
```
* i = 6時
```python=
#a[6]與a[2]互換
```
* i = 7時
```python=
#a[7]與a[1]互換
```
* i = 8時
```python=
#a[8]與a[0]互換
```
### 所以可以得知此陣列互換後又換回來，是不變的!
## 再來進第二個Loop:
* i = 0時
```python=
#印出a[0]、a[8]
```
* i = 1時
```python=
#印出a[1]、a[7]
```
* i = 2時
```python=
#印出a[2]、a[6]
```
* i = 3時
```python=
#印出a[3]、a[5]
```
* i = 4時
```python=
#印出a[4]、a[4]
```
### 就可得到答案：1 2 3 4 5 6 7 8 9 9
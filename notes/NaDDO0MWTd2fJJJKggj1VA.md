# 2022.05.02 觀念題作業
### 請把你的解題方式(內容)寫下來，並加註自己的名字

---
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6ef99087d7db505706cdb5664f608133.png)
若以 F(5,2)呼叫上述 F()函式，執行完畢後回
傳值為何?
A)1   
B) 3  
C) 5
D) 8
### 完成後請點選上列"**一**"圖示插入水平線
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_432d3f06db4ed9f89a889e54b5e95100.png)



---
## Jesse
* F(5, 2): F(3, 2) + F(1, 2)
    * F(3, 2): F(1, 2) + F(-1, 2)
        * F(1, 2): F(-1, 2) +F(-3, 2)
            * F(-1, 2): 1
            * F(-3, 2): 1
        * F(-1, 2): 1
    * F(1, 2): F(-1, 2) +F(-3, 2)
        * F(-1, 2): 1
        * F(-3, 2): 1

* A: C) 5（以下附上Python詳解，運行程式碼即可）
```python=
print("請計算共有幾次x<1，以獲得解答: ")


def F(n: int, x: int, y: int):
    print(f"{'  ' * (n-1)}第{n}次呼叫F函式: x={x} y={y}")
    if x < 1:
        return 1
    else:
        return F(n + 1, x - y, y) + F(n + 1, x - 2 * y, y)


print(f"                          A: 回傳值為{F(1, 5, 2)}")
```
---
## 宇岑
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_44027f261e041096ae5eb8fff4796ea1.jpg)
## code
```python=
def F(x,y):
    if (x < 0):
        return 1
    else:
        return (F(x-y,y) + F(x-2*y,y))

ss = F(5,2)
print(ss)
```
---

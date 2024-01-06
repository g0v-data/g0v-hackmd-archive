# 2022.03.28 作業a044

#Please paste your code and follow the following rules:)
#Name / Question No. 
#code，code內容請反白後點選上列**</>**圖示
#之後在ˋˋˋ後加上python= 

For example:
```python=
#Aaron / a003 
#Example text
```
---
## 完成後請點選上列"**一**"圖示插入水平線
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_432d3f06db4ed9f89a889e54b5e95100.png)

## [a044題目連結](https://zerojudge.tw/ShowProblem?problemid=a044)
---
## 夏羽綾理
```python=
while True:
    try:
        d = int(input())
        pmqy = 2
        dcs = 1
        kjqy = 2
        for i in range(d-1):
            dcs += 1
            kjqy += pmqy
            pmqy += dcs
        print(kjqy)
    except:
        break
'''
 _________________________________      
| |             |  |            | |
| |             |  |            | |
|  |            |  |            | |
|  |            |  |            | |  要
|  |            |  |            | |  不
|   |           |  ,-+--,       | |  要
|   |           | /|     \      | |  吃~
|   |           || |_    -      | |
|    |          |\   \__/       | |  哈
|    |          | `-,   (_      | |  密
|    |           | |_\    i     | |  瓜~
| |   |          | ||      \    | |
| |   |          | ||       |   | |
| |   |        <eee/        |   | |
|  |   |       +```+        \   | |
|  |   |      (WMWMW)        |  | |
|  |   |       +,,,+         )  | |
|   |   |         --,,,,..--`   | |
|   |   |           |        |  | |
|   |   |           \        |  | |
|   |   |           |\       |  | |
|    |   |          | |      |  / |
|    |   |          | \      | /  |
|    |   |        .  | \     |/   |
|    |   |      ,/|  |  \    \    |
|     |   |   ,/  |  |  ||    |   |
|     |   |  /   ,/  |  | |   |   |
|     |   |  | ,/    |  | |   |   |
|_________________________________|
'''
```
---
## HungYuNung / a044(無公式) / 2022.03.28
```python=
def arithmetic_progression(time):
    """_arithmetic_progression(time)_
    Args:
        time (_int_): _int(input(line))_
    Returns:
        _int_: _index_
    """
    square = [2]
    index = 2
    for i in range(0, time-2):
        square.append(square[i]+i+2)
    for j in square:
        index += j
    return index
        
while True:
    try:
        line = int(input())
        if line == 1:
            print(2)
        else:
            print(arithmetic_progression(line))
    except EOFError:
        break
```
---
## HungYuNung / a044(公式版) / 2022.03.28
```python=
def cut(square):
    """_cut(square)_
    Args:
        square (_int_): _int(input())_
    Returns:
        _type_: _int_
    """
    return (square**3 + 5 * square + 6) // 6
while True:
    try:
        line = int(input())
        print(cut(line))
    except EOFError:
        break
```
---
## 黃品誠
```python=
while True:
    try:
        a = int(input())
        p = 1
        d = 0
        l = 2
        for i in range(a-1):
            d += 1
            p += d
            l += p
        print(l) 
    except:
        break

```


---
## 何咏謙's code
```python=
while True:
    try:
        n = int(input())
        print((n**3+5*n+6)//6)

    except:
        break
```
---
## albert's code
```python=
while True:
    try:
        n=int(input())
        a=int((n**3+5*n+6)/6)
        print(a)
    except:
        break
```
---
## Jesse's code
```python=
'''
參考資料: https://dreamisadream97.pixnet.net/blog/post/165781698-n%E5%80%8B%E5%B9%B3%E9%9D%A2%E6%9C%80%E5%A4%9A%E5%8F%AF%E5%88%87%E5%87%BA%E5%B9%BE%E5%80%8B%E7%A9%BA%E9%96%93
'''
import sys

# 公式版
try:
    for n in sys.stdin.readlines():
        n = int(n)
        print(int((n*(n*n+5)/6)+1))
except ValueError:
    pass


# 遞迴版 （會TLE)
def cut3D(n):
    if n == 1:
        return 2
    return cut3D(n - 1) + cut2D(n - 1)


def cut2D(n):
    if n == 1:
        return 2
    return cut2D(n - 1) + n


try:
    for n in sys.stdin.readlines():
        print(cut3D（int(n)）)
except ValueError:
    pass

```
---
## peggy'code
```python=
while True:
    try:
        a = int(input())
        print((a**3+5*a+6)//6)
    except:
        break
```
---
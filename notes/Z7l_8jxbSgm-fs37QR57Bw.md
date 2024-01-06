# 2022.03.28 課堂a042

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

## [a042題目連結](https://zerojudge.tw/ShowProblem?problemid=a042)
---


## 夏羽綾理
```python=
while True:
    try:
        d = int(input())
        quyushu = 2
        dcs = 0
        for i in range(1,d):
            dcs += 2
            quyushu += dcs
        print(quyushu)
    except:
        break
'''
(想不到吧~Python是個好用的工具www)
   (  `--v-. \     \`-.      \
   `+       \----,-         \
  \          ) `         `+
  | \*    o `,   \      ,   \
   \    ,* \  --*+*`         \
    +00+>,       \   \        )
  \EE(*_    ``` \ |   \     `+
 \EEEA    (<ee >  |    *-<,,  \
 |EEE\*      ,\  \        \*  |
 |EEE\\o    >   \         \   |
 ,\EEE,+`   o *,          |   |
  v\EEEEE\** ,            | ``|
    E^E--A               \  \ |\
    . .                  ( +\ ||
                         | -, \
                         | |_
                         | |
                         ,v,
   樓  下  的  寫  的  不  錯  ~  XD
'''
```
---
## Jesse's code
```python=
import sys

while True:
    try:
        n = int(sys.stdin.readline()[:-1])
        print(n**2 - n + 2)
    except ValueError:
        break
```


---

## 黃品誠
```python=
while True:
    try:        
        a = int(input())
        ans = 2
        n = 0
        for i in range(a-1):
            n += 2
            ans += n
        print(ans)
    except:
        break

```
---
## Dino's code
```python=
while True:
  try:
    n = int(input()) 
    print(n**2-n+2)    # 公式
  except:
    break
```
---


## albert's code
```python=
while True:
    try:
        n=int(input())
        a=n**2-n+2
        print(a)
    except:
        break
```
---
## 周旻儀s code 
```python=
while True :
    try:
        a = int(input())

        s = (((2+(2*a-2))*a)//2)-(a-2)
        print(s)
    except:
        break
```
---
## peggy'code
```python=
while True:
    try:
        a = int(input())
        print(a**2-(a-2))
    except:
        break
```
---
## 宇岑's code
```python=
while True:
    try:
        n = int(input())
        a = (2+(((2*n-2)/2)*n))
        print(int(a))
    except:
        break
```
---
## 聖偉/a065/0328
```python=
try:
    while True:
        f=int(input())
        an=2
        for i in range(f):
            an+=(2*(i))
        print(an)
except EOFError:
    pass
```
---
## 何咏謙's code        
```python=
while True:
    try:
        n = int(input())
        print(n*n - n +2)

    except:
        break
```
## 蕭亦峰        
```python=
while True:
    try:
        a = int(input())
        print(a ** 2 - a + 2)
    except:
        break
```
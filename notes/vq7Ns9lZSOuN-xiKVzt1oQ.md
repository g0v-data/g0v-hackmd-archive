# 2022.05.02 作業c294

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

## [題目連結](https://zerojudge.tw/ShowProblem?problemid=c294)



---
## albert's code
```python=
a=int(input())
b=int(input())
c=int(input())
if a+b <= c:
    print("No")
elif a*a+b*b  < c*c:
    print("Obtuse")
elif a*a+b*b  == c*c:
    print("Right")
elif a*a+b*b  > c*c:
    print("Acute")
```
---
## 宇岑's code
```python=
abc = list(map(int, input().split()))
temp = 0

abc.sort()

a = abc[0]
b = abc[1]
c = abc[2]
print(a,b,c)

if a+b <= c:
    print('No')
else:
    if a*a+b*b < c*c :
        print('Obtuse')
    if a*a+b*b == c*c:
        print('Right')
    if a*a+b*b > c*c:
        print('Acute')
```
---
## Jesse's code
```python=
import sys


def identify_triangle(three_number):
    numbers_list = list(map(int, three_number.split()))
    numbers_list.sort()
    a = numbers_list[0]
    b = numbers_list[1]
    c = numbers_list[2]
    if a + b <= c:
        res = "No"
    elif a * a + b * b < c * c:
        res = "Obtuse"
    elif a * a + b * b == c * c:
        res = "Right"
    elif a * a + b * b > c * c:
        res = "Acute"

    print(a, b, c)
    print(res)


identify_triangle(sys.stdin.readline())
```
---
## 夏羽綾理
```python=
d = input().split()
for i in range(len(d)):
    d[i] = int(d[i])
d.sort()
a,b,c = d[0],d[1],d[2]
def txb():
    return a*a+b*b
def zdb():
    return c*c
for i in range(len(d)):
    print("%d"%(d[i]),end=' ')
print("")
if a+b <= c:
    print("No")
else:
    if txb() < zdb():
        print("Obtuse")
    elif txb() == zdb():
        print("Right")
    elif txb() > zdb():
        print("Acute")
```
---
## 聖偉/c294/0518
```python=
F=map(int,input().split())
F=sorted(F)
print(*F)
a=int(F[0])
b=int(F[1])
c=int(F[2])
if a+b<c:
    print("No")
elif (a*a)+(b*b)==(c*c):
    print("Right")
elif (a*a)+(b*b)<(c*c):
    print("Obtuse")
elif (a*a)+(b*b)>(c*c):
    print("Acute")
```
---
## 何咏謙's code
```python=
while True:
    try:

        x = list(map(int, input().split()))
        
        x.sort()
        a = x[0]
        b = x[1]
        c = x[2]
        A = a*a
        B = b*b
        C = c*c
        D = A+B

        print(a,b,c)
        if ((a+b) <= c):
            print("No")
        elif (D == C):
            print ("Right")

        elif (D > C):
            print("Acute")

        elif (D < C):
            print("Obtuse")

    except EOFError:
        break

```
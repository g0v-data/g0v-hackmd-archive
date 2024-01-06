# 2022.03.07 課堂解題a005

#Please paste your code and follow the following rules:)
#Name / Question No. / Date
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

## [a005題目連結](https://zerojudge.tw/ShowProblem?problemid=a005)
1. 本題解法綜合a003.a004.a053
2. 第一行是數列的數目t（0 <= t <= 20）。 以下每行均包含四個整數，表示數列的前四項。 約定數列的前五項均為不大於105的自然數，等比數列的比值也是自然數。
3. 需要先處理第一行輸入的"列數(值)"之後再進入迴圈
4. 再次處理輸入的"數列"，進行分割split()
5. 之後將list裡的內容轉為值(int())進行計算
6. 用if判斷
---
## Peggy's code

```python=
a = int(input())
if 0 <= a <=20:
    for b in range(a):
        c = list(map(int, input().split(" ")))
        if c[1]-c[0] == c[3]-c[2]:
            e = c[1]-c[0]+c[3]
            c.append(e)
            print(*c)
        elif c[1]/c[0] == c[3]/c[2]:
            f = int(c[1]/c[0]*c[3])
            c.append(f)
            print(*c)
        else:
            pass
else:
    pass
```
---

## 聖偉/a005/0307
```python=
a=int(input())
for i in range(a):
    s=input().split()
    d=int(s[1])-int(s[0])
    r=int(s[1])//int(s[0])
    if d==int(s[2])-int(s[1]):  #ari
        s.append(int(s[3])+d)
    elif r==int(s[2])//int(s[1]):    #geo
        s.append(int(s[3])*r)
    for i in range(5):
        print(s[i],end=" ")
    print("\n")
```

---
## 夏羽綾理 / a005 / 2022.03.07
```python=
def pdsl():
    a = input().split()
    cob = 0
    sl = ""
    for i in range(len(a)):
        a[i] = int(a[i])
    if a[-1]-a[-2] == a[-3]-a[-4]:
        cob = a[-1] - a[-2]
        for i in a:
            sl = sl + str("%d "%(i))
        sl = sl + str(int(a[-1])+cob)
    elif a[-1]/a[-2] == a[-3]/a[-4]:
        cob = a[-1] / a[-2]
        for i in a:
            sl = sl + str("%d "%(i))
        sl = sl + str(int(a[-1]*cob))
    return sl
c = int(input())
for i in range(c):
    print(pdsl())
```
---
## HungYuNung / a005 / 2022.03.07
```python=
t = int(input())
for i in range(0, t):
    test = [int(x) for x in input().split()]
    if test[1] - test[0] == test[2] - test[1]:
        count = test[1] - test[0]
        print(*test, test[len(test)-1] + count)
    elif test[1] // test[0] == test[2] // test[1]:
        count = test[1] // test[0]
        print(*test, test[len(test)-1] * count)
    else:
        pass

```
---

## 何咏謙 / a005 / 2022.03.07

```python=
while True:
    try:
        t = int(input())
        for i in range(t):
            a,b,c,d = map(int,input().split( ))
            
            if (b-a)==(c-b):
                print(a, b, c, d,d*2-c)
            else:
                print(a, b, c, d,d*d//c)
    except:
        break
```
---
## Jesse's code
```python=
length = int(input())

for i in range(length):  # 根據輸入的第一個數字，決定程式執行的次數
    cal_list = list(map(int, input().split()))  # 將輸入的數字列，用空格分隔，並依序轉換成數字，存在list裡
    a_1 = cal_list[0]  # 獲取list中的a1
    a_2 = cal_list[1]  # 獲取list中的a2
    d = a_2 - a_1  # 後項減前項，獲取公差
    if cal_list[-1] == cal_list[0] + (len(cal_list) - 1) * d:  # 判斷等差公式：an = a1 + (n - 1)*d
        cal_list.append(cal_list[-1] + d)  # 在list尾加上第n+1項(an+d)
    else:  # 否則(等比數列)
        d = (a_2 // a_1)  # 獲取前項除後項的商
        cal_list.append((cal_list[-1] * d))  # 在list尾加上第n+1項(an*d)

    for i in cal_list:  # 迭代list中的每個項目
        print(i, end=" ")  # print出來，並用一個空格相隔
    print()  # 結束後換行

```
---
## 蕭亦峰's code
```python=
#蕭亦峰/a005/2022.3.8
s = int(input())                  #輸入數列個數
for i in range(s):                #有幾個數列就執行幾次
    b = input().split()           #將數列分割
    a = list(map(int, b))         #用map將分割後的數列轉為整數的list
    if a[1]- a[0] == a[3] - a[2]: #如果公差相等為等差數列
        d = a[1] - a[0]           #求出公差
        a.append(a[3] + d)        #算出第五項後加入到list
        print(*a)                 #輸出
    else:                         #如果是等比數列
        d = a[1] // a[0]          #求出公比
        a.append(a[3] * d)        #求出第五項後加入到list
        print(*a)                 #輸出
```
---
## albert's code
```python=
t = int(input())
for i in range(t): 
    b = input().split()
    a = list(map(int, b))
    if a[1]- a[0] == a[3] - a[2]: 
        d = a[1] - a[0]
        a.append(a[3] + d)
        print(*a)
    elif  a[1] // a[0] == a[1] // a[0]:
        d = a[1] // a[0] 
        a.append(a[3] * d)
        print(*a)
```    
---



---
## Dino's code
```python=
x = int(input())
for i in range(x):
  A = input()
  a = [int(y) for y in A.split(' ')]
  if (a[1]-a[0]) == (a[2]-a[1]) == (a[3]-a[2]):
    print(A, end=' ')
    print(int(a[3]+a[3]-a[2]))
    continue
  if (a[1]/a[0]) == (a[2]/a[1]) == (a[3]/a[2]):
    print(A, end=' ')
    print(int(a[3]*(a[3]/a[2])))
    continue
```    
---
## jia qing's code
```python=
i = int(input())
if 0 <= i <=20:
    for a in range(i):
        c = list(map(int, input().split(" ")))
        if c[1]-c[0] == c[3]-c[2]:
            e = c[1]-c[0]+c[3]
            c.append(e)
            print(*c)
        elif c[1]/c[0] == c[3]/c[2]:
            f = int(c[1]/c[0]*c[3])
            c.append(f)
            print(*c)
        else:
            pass
else:
    pass
```
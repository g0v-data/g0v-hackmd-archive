# 2022.02.28 作業a053

#Please paste your code and follow the following rules:)
#Name / Question No. / Date
#code，code內容請反白後點選上列**</>**圖示
#之後在ˋˋˋ後加上python= 

For example:
```python=
#Aaron / a003 / 2022.02.28
#Example text
```
---
## 完成後請點選上列"**一**"圖示插入水平線
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_432d3f06db4ed9f89a889e54b5e95100.png)

## [a053題目連結](https://zerojudge.tw/ShowProblem?problemid=a053)
1. 本題解法和a004類似，用if，elif，else判斷即可
2. 回想一下input()的規則
---
## Andrew's Code
```python=
#宇承/a053/2022.03.07
num = int(input())
if num<=10:
    print(num*6)
elif num>10 and num<=20:
    print(60+2*(num-10))
elif num>20 and num<=40:
    print(80+num-20)
else:
    print(100)
```
---
## **丁博洋/ a053 / 2022.03.06**
```python=
對題數 = input("答對題數為:")
right= int(對題數)
得分 = 0
if 0<right <=10:
  得分=得分+right*6
elif 10<right<=20:
  得分=得分+right*2
elif 20<right<=40:
  得分=得分+right
elif right>40:
  得分=100
print(得分)
```
---
## **HungYuNung / a053 / 2022.03.02 :**
```python=
n = int(input())
if n <= 10:
    score = n * 6
elif 10 < n and n <= 20:
    score = 60 + (n - 10) * 2
elif 20 < n and n < 40:
    score = 60 + 20 + (n - 20)
else:
    score = 100
print(score)
```
---
## Jesse's code
```python=
def scoring(score):
    score = int(score)
    res = 0
    count = 0
    for times in range(score):
        count += 1
        if count <= 10:
            res += 6
        if 11 <= count <= 20:
            res += 2
        if 21 <= count < 40:
            res += 1
        if count >= 40:
            res = 100
            break
    print(res)

score = input()
scoring(score)
```
---
## albert's code
```python=
q=int(input("請輸入分數:"))
if q <= 10:
    s=q*6
    print(s)
elif q <= 20 and q >10:
    s=60+(q-10)*2
    print(s)
elif q <= 40 and q >20:
    s=80+(q-20)*1
    print(s)
elif q >40:
    s=100
    print(s)
```
---
## 夏羽綾理 / a053 / 2022.03.06
```python=
tishu = int(input())
score = 0
if tishu > 40:
    score = 100
elif tishu >= 21:
    score += 80 + (tishu-20)
elif tishu >= 11:
    score += 60 + (tishu-10)*2
elif tishu >= 0:
    score += tishu*6
print(score)
```
---
## 宇岑 / a053 / 2022.03.06
```python=
n = int(input())
point = 0

if n>=40:
    point = 100
elif n >20:
    point = 80 + (n-20)
elif n >10:
    point = 60 + (n-10)*2
else:
    point = n*6

print(point)
```
---
## 黃品誠 / a053 / 2022.03.06
```python=
q = int(input())
s = 0
if q > 40:
    s = 100
    type = "X"
elif q >= 11 and q < 21:
    s += 60
    q -= 10
    type = "add2"
elif q >= 21:
    s += 80
    q -= 20
    type = "add1"
if q > 0 and type == "X":
    s +=0
elif q > 0 and type == "add2":
    s += q*2
    q -= s
elif q > 0 and type == "add1":
    s += q
    q -= s
elif q > 0:
    s += q*6
    q -= s
print(s)
```
---
## 周旻儀's code
```python=
n = int(input())

if n <= 10:
    s = n * 6
elif n > 10 and n <= 20:
    s = 60 + (n-10)*2
elif n > 20 and n <=40:
    s = 60 + 20 + (n-20)
else:
    s = 100
print(s)
```
---
## HungYuNung / a053 / 2022.03.06
```python=
n = int(input())
point = 0

def sixpoint(x):
    return x * 6
def twopoint(y):
    return y * 2
def onepoint(z):
    return z * 1

if n <= 10:
    print(sixpoint(n))
elif 10 < n < 21:
    print(sixpoint(10) + twopoint(n-10))
elif 20 < n < 41:
    print(sixpoint(10) + twopoint(10) + onepoint(n-20))
else:
    print(100)
```
---
## 蕭亦峰's code
```python=
#蕭亦峰/a053/2022.03.06
question = int(input())
if int(question) <= 10:                  #如果小於10題 就將題數*6 輸出
    print(question * 6)
elif question >= 11 and question <= 20:  #如果介於11到20題之間 
    s = question - 10                    #先減去前面的10題
    print(60 + s * 2 )                   #題數*2 + 前面10的分數(60) 
elif question >= 21 and question <= 40:  #如果介於21到40題之間
    s = question - 20                    #先減去前面的20題
    print(80 + s)                        #題數 + 前面20題的分數(80)
else:                                    #40題以上100分
    print(100)
```
---
## Peggy's code
```python=
a = int(input())  #輸入答對的題數
if a >= 41:      #40題以上100分
    print(100)
else:
    if a >=21:   #21~40題每題1分
        b = (a-20)+80
        print(b)
    else:
        if a >= 11: #11~20題每題2分
            d = (a-10)*2+60
            print(d)
        else:       #10題或10題以下每題6分
            e = a*6
            print(e)

```
---
## 張家箐's code
```pthon=
a = int(input())
f = 0

if a < 10:
   f = a*6 

elif 11 < a < 20 :
     f =(a-20)*2 +60

elif 21 < a < 40:
     f =(a-40)*1 +80

else: 
     f = 100
print(f)
```
---




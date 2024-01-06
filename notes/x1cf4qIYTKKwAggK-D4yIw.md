# 2022.03.14 課堂a022

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

## [a022題目連結](https://zerojudge.tw/ShowProblem?problemid=a022)

---
## string slice
```python=
a = ["0", "1", "2", "3", "4"]
"""
index 0 ,  1 ,  2 ,  3 ,  4
index -5, -4 , -3 , -2 , -1
"""

print("origin", a)
print("1:", a[-2:-5: -1])
print("2:", a[-2:0:-1])
print("3:", a[3:0:-1])
print("4:", a[3:-5:-1])

#[output]
"""
origin ['0', '1', '2', '3', '4']
1: ['3', '2', '1']
2: ['3', '2', '1']
3: ['3', '2', '1']
4: ['3', '2', '1']
"""
```
---
## 丁博洋/a022
```python=
a = input("輸入資料共一行包含一個字串")
b= a[::-1]
if a==b:
  print("yes")
else:
  print("no")
  ```
## 周旻儀
```python=
#周旻儀/a022/2022.3.14
string = input()
s = string[::-1]
if s == string:
    print('yes')
else:
    print('no')
```
---

## 夏羽綾理/a022
```python=
s = input()
sr = s[-1:-len(s)-1:-1]
if s == sr:
    print("yes")
else:
    print("no")
`````


---




## 宇岑/a022
```python=

st = input()
x = [str(a)for a in str(st)]
a = []
string = ''
for i in range(len(x)-1, -1, -1):
    string += x[i]

if st == string:
    print('yes')
else:
    print('no')
```
---
## peggy's code/a022
```python=
a = input()         #輸入文字進去
b = a[::-1]         #讓他變成a的顛倒
if a[0] == b[0]:    #如果a的第0項和最後一項一樣
    print("yes")    #印出yes
else:               #不相同
    print("no")     #印出no
```
---
## albert's code/a022
```python=
a=input()
b=a[::-1]
if b == a :
    print("yes")
else:
    print("no")
```




---
## 何咏謙's code
```python=
s = input()
s3 = s[::-1]

if s==s3:
    print("yes")
else:
    print("no")
```


---
## Din0o0o0o
```python=
x=input()
if x==x[::-1]:
    print("yes")
else:
    print("no")

```
---
## 王聖偉/a022/0314
```python=
try:
    while True:
        l=input()
        rev=reversed(l)

        if l==''.join(rev):
            print("yes")
        else:
            print("no")
except EOFError:
    pass
```

---
## 蕭亦峰's code
```python=
#蕭亦峰/a022/2020.3.14
a = list(input())                #輸入
flip = list(reversed(a))         #用reversed()翻轉字串
if "".join(a) == "".join(flip):  #判斷是否一樣
    print("yes")                 
else:
    print("no")
```
---
## 黃品誠
```python=
enter = input()
e1 = enter[::-1]
if enter == e1:
    print("yes")
else:
    print("no")

```



---
## Jesse's code
```python=
string = input()

if string == string[::-1]:
    print("yes")
else:
    print("no")
```
---


## 家箐's code
```python=
n = input()
b = n[::-1]
if b == n:
    print("yes")
else:
    print("no")
```
---
## HungYuNung / a022 / 2022.03.14
```python=
a = [str(x) for x in input()]
output = 'yes'
for i in range(len(a)//2):
    if a[i] != a[len(a)-1-i]:
        output = 'no'
print(output)
```
---


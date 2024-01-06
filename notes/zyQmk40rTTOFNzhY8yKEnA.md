# 2022.03.14 作業a009

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

## [a009題目連結](https://zerojudge.tw/ShowProblem?problemid=a009)
### 解題步驟
1. 搜尋ASCII是什麼→本題會用到的語法chr() ord()
2. 先從範例輸入、範例輸出找到K=?
3. 用ord將字符返回ASCII數值和K進行運算
4. 用chr將運算結果返回字符後輸出

## 蕭亦峰/a009/2020.03.14
```python=
k = 7                       
ascii = []
a = list(input())
for i in range(len(a)):    #將char轉為ascii碼-7後轉回char加入到list中
    b = ord(a[i]) - k
    ascii.append(chr(b)) 
print(''.join(ascii))
```
---

## 王聖偉/a009/0314
```python=
l=input()
for i in range(len(l)):
    print(chr(ord(l[i])-7),end="")
```
---
## 宇岑/a009
```python=
string = input()
for i in range(len(string)):
    print(chr(ord(string[i])-7), end='')
```
---
## peggy'code
```python=
a = input()                                     #輸入字串

for i in range(len(a)):                         #依序放入

    print(chr(ord(a[i])-7),end = "")            #印出並讓ord(a[i])-7讓他的開頭1變成*
                                                #並讓他們在同一行不換行


```
---
## 周旻儀s code
```python=
#周旻儀/a009/2022.3.14
s = input()

for i in range(len(s)):
    print(chr(ord(s[i])-7), end='')
```
---
## Jesse's code
```python=
"""
# 找出k的方法
a = "1JKJ'pz'{ol'{yhklthyr'vm'{ol'Jvu{yvs'Kh{h'Jvywvyh{pvu5"

for i in range(100):
    if chr(ord(a[0]) - i) =="*":
        print(i)
        break
"""
import sys


for i in sys.stdin.readline().strip("\n"):
    print(chr(ord(i) - 7), end="")

```
---
## 夏羽綾理
```python=
s = input()
sr = ""
for i in s:
    sr += (chr(ord(i)-7))
print(sr)
'''
                   , eee ,
               ,*`         `*,
              *                *
            /      -`*EEEe       \
           A       ****EEE        ,
          .     aEEEEEEEEE EEe    .
          o    |EEEF***** ,EEE    o
          v    \EEE EEEEEEEEEE    v
           ,    `** EE*******     ,
            ,       EEEE**       ,
             +       *** `      +
              `-_            _-`
                 `*-,,,,,-*`




      p r i n t  '' H e l l o  W o r l d ''

'''
```


---
## 黃品誠
```python=
a = input()
a1 = ""
for i in a:
    a1 += (chr(ord(i)-7))
print(a1)

```


---
## HungYuNung / a009 / 2022.03.14
```python=
n = input()
for i in range(len(n)):
    print(chr(ord(n[i])-7), end='')
```


## 家箐'code
```python=
S = input()
for a in range(len(S)):
    print(chr(ord(S[a])-7), end='')
```
## 何咏謙's code
```python=
char = list(input())

ans = []

for i in range (len(char)):
    number = ord(char[i])-7
    words = chr(number)
    ans.append(words)

print(''.join(ans))
```

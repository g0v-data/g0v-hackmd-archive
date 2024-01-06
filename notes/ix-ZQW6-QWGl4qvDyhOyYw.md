# 2022.03.21 作業a065

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

## [a065題目連結](https://zerojudge.tw/ShowProblem?problemid=a065)
---
## HungYuNung / a065 / 2022.03.24
```python=
while True:
  try:
    en = list(input())
    password = ''
    for i in range(len(en)-1):
      password += str(abs(ord(en[i+1])-ord(en[i])))
    print(password)
  except EOFError:
    break
```
---
## Jesse's code
```python=
import sys

# convert password characters to integers
ordinal_passwords = []
for i in sys.stdin.readline()[:-1]:
    ordinal_passwords.append(ord(i))

# get distance between ordinal of passwords
ans = ""
for i in range(len(ordinal_passwords) - 1):
    ans = f"{ans}{abs(ordinal_passwords[i + 1] - ordinal_passwords[i])}"

print(ans)
```
---
## 夏羽綾理
```python=
d = input()
passwd = ""
for i in range(len(d)-1):
    passwd += str(abs(ord(d[i+1])-ord(d[i])))
print(passwd)
'''
     (       /             \+        |
     |       )              +        |
     /    ,_/               |        |
     q,,^v/                 |        +
      /   L_._______________+       /+
     +     |   ,           / ;;;;   /\
     |     |  |E|          +       / .\
    /|     |  |E|         /`      /   +
    |\     |   `          /      /|   |
    |+     \          +,,/      / /   |\
    |\     +,_          /      /+`|   ||
    |+     \  ` ````_``/      /   L___/|
    | \____,\;++`  L  +/     /         |
    |    /  \,\    /  /     /|         |
    `    `   ` `   ` ```````           `
      不    可    以    色    色  !  !

'''
```
---
## 何咏謙's code 
```python=
password = list(input()) 
passnub = []

for i in range (len(password)-1):
    passnumber = ord(password[i+1])-ord(password[i])
    passn = str(abs(passnumber))
    passnub.append(passn)

print(''.join(passnub))
```


---
## 黃品誠
```python=
m = input()
jm = ""
a = len(m)-1
i = 0
for i in range(a):
    jm +=str(abs((ord(m[i]) - ord(m[i+1]))))
print(jm)
```


---
## 蕭亦峰
```python=
#蕭亦峰/a065/3.21.2020
a = input()                                 #輸入
for i in range(len(a)-1):                   #因為算距離，所以執行的次數=字數-1
    print(abs(ord(a[i+1])-ord(a[i])),end="")#用ascii碼算距離，因為是距離所以用絕對值。
```
---

## Dino's code 
```python=
txt = list(input())    # 將輸入的文字轉換成串列
for i in range(len(txt)-1):# 取出串列中的字  計算時用 i+1，用 -1 
    x = ord(txt[i+1]) - ord(txt[i])  # 密碼
    print(f'{abs(x)}',end='')    #組合
print()
```
---
## 宇岑'S code
```python=
string = input()
for i in range(len(string)):
    if i < len(string)-1:
        print(abs(ord(string[i+1]) - ord(string[i])), end='')
```

---
## 聖偉/a065/0328
```python=
l=input()
for i in range(len(l)-1):
    print(abs(ord(l[i])-ord(l[i+1])),end='')
```

---
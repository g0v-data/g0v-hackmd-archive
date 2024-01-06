# 2022.03.07 作業a038

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

## [a038題目連結](https://zerojudge.tw/ShowProblem?problemid=a038)
1. 本題開始前可以先搜尋"python 反轉"尋找相關資料
2. 重點提示 ：* 前面有 0 的話應消除

---
## 夏羽綾理 / a038 / 2022.03.09
```python=
a = input("輸入一行包含一個整數的數")
m = ""#不知道為什麼
for i in range(1,len(a)+1):
    m = m + a[-i]
print(int(m))
```
---
## 夏羽綾理 / a038 / 2022.03.09
```python=
d = input()
m = ""
for i in range(1,len(d)+1):
    m = m + d[-i]
print(int(m))
'''
                               .----.,
                         / \.+         '+               /\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\
                        .   \             ‾\/\        <       ee         yE E E E      E      E     EEEEEEEEEE     EEE >
                      |\/   )   / / /         \.      <       ee        yeEeEeEeEee    E    eeEee            y     EEE >
                      /┘ └     /  | /   \ \|   <      < EEEEEEEEEEEEEE y  E E E E     yEk    =E=           y       EEE >
                      (┐  <  / |  \ |   | |) \  )     <       ee         eEeEeEeEe   y E k eeeEeee       y         EEE >
                     0/|  |  | | ＼ \   / // \  )     <      eeee         E E E E      E                 E         EEE >
                    0/ /  \  | \__\ _   | ／  | \     <     ee  ee      eeEeEeEeEee    E    EEEEE        E         EEE >
                    /    ||  \／/ \＼ ‾ ,-,   /  \_   <    ee    ee                    E    E===E        E             >
                   /. / /|\\  | , /     * |   - ‾\||  <   ee      ee     y E   E  E    E    E===E        E         EEE >
                 ／‾  ( ^\\ , \\ "      ''+^/ \ \  \  <  ee    6   ee   y  E   E   E   E   y   \E       \E         EEE >
               ／     \V ┌\\ \ \＼  (‾)  ┘/ /^\     |  vvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvv
             ／         /└_\   \＼"+-+"'‾/ //  \    /
          ／          ,／‾{ \   \    /  |< - ┐  (  )
       -          ／ |     \ \_ __' /,-‾ <   |  |‾‾|
      /         ／   \      (  \   ( )  )     \ |  |
    /         / /     \\    /     /  |  |/ /  \.|  |
'''
```

---
## HungYuNung / a038 / 2022.03.09
```python=
string = list(input())
def flip_arr():  #用作反轉 [array] 的 def function():
    newarr = []
    for i in range(len(string) - 1, -1, -1):
        newarr += string[i]
    return newarr
ans = ''.join(flip_arr())
print(int(ans))
```
---
## 黃品誠 / a038 / 2022.03.09
```python=
n = input("")
list = []
for i in range(len(n)):
    list.append(n[i])
list.reverse()
n2 = ""
for i2 in range(len(list)):
    n2 = n2+list[i2]
print(int(n2))
```
---
## Jesse's code
```python=
def reverse_str(string):  # 反轉字串的函式
    rev_str = string[::-1]  # 反轉字串
    res_str = int(rev_str)  # 轉成整數型態(去除前面多餘的零)
    print(res_str)  # 印出結果字串


reverse_str(input())  # 輸入數字進入函式

```
---
## albert's code
```python=
a=input()
b=''.join(reversed(a))
b = int(b)
print(b)
```
---




---
## Dino's code
```python=
In = list(input())
x = In[::-1]          # 反轉串列
out = ''.join(x)
print(int(out))       # 消除 0 
```
---
## 蕭亦峰s code
```python=
#蕭亦峰/a038/2022.3.14
#輸入
number = input()
list_num = list(number)
#翻轉
i = len(list_num) - 1 
overturn = []
while i >= 0:                    #將輸入的數字倒著放入另一個list
    overturn.append(number[i])
    i = i - 1
#輸出
print(int("".join(overturn)))    #先將list轉為int再轉為int
```
---
## 周旻儀s code
```python=
#周旻儀/a038/2022.3.14
string = input()
print(int(str(string[::-1])))
```
---

## 宇岑s code
```python=
#洪宇岑/a038/2022.3.14
num = input()
x = [str(a)for a in str(num)]
a = []
string = ''
for i in range(len(x)-1, -1, -1):
    string += x[i]



print(int(string))

```
---

## peggy's code
```python=
n = str(input())#輸入一串數字進去 轉成字串
b = int(n[::-1])#反轉之後再換成數字(可把0消除)
print(b)#印出
```
---

## 曉青
```python=
n = input()
s = ''
for i in range(len(n)-1, -1, -1):
    s += n[i]
print(int(s))
```
---
## jia qing's code
```python=
string = input()
print(int(str(string[::-1])))
```
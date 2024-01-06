# APCS課程共筆 2022/02/28
#Please paste your code and follow the following rules:)
#Name / Question No. / Date
#code，code內容請反白後點選上列**</>**圖示
#之後在ˋˋˋ後加上python= 

For example:


```python=
#Aaron / a003 / 2022.02.28
MonthDay = input() #輸入1 1
Date = MonthDay.split() #拆分1 空格 1 
solution = int(Date[0]*2) + int(Date[1]) #把str字串轉換為數值list [第一個值, 第二個值]
fortune = solution % 3 #得到餘數
#S=(M*2+D)%3 題目提供的公式

if fortune == 0:
    print('普通')

elif fortune == 1:
    print('吉')

else :
    print('大吉')
```

#完成後請點選上列"**一**"圖示插入水平線

---
## [a003 / 2022.02.21](https://zerojudge.tw/ShowProblem?problemid=a003)

### Aaron's code
```python=
#Aaron / a004 / 2022.02.28
MonthDay = input() #輸入1 1
Date = MonthDay.split() #拆分1 空格 1 
solution = int(Date[0]*2) + int(Date[1]) #把str字串轉換為數值list [第一個值, 第二個值]
fortune = solution % 3 #得到餘數
#S=(M*2+D)%3 題目提供的公式

if fortune == 0:
    print('普通')

elif fortune == 1:
    print('吉')

else :
    print('大吉')
```
---
### Jesse's code
```python=
def divination(month: int, day: int):
    value = (month*2+day)%3
    if value == 0:
        res = "普通"
    elif value == 1:
        res = "吉"
    elif value == 2:
        res = "大吉"
    print(res)

date=input().split()
divination(int(date[0]), int(date[1]))
```
---
### 蕭亦峰's code
```python=
#蕭亦峰/ a003 / 2022.2.21
brithday = input()            #輸入
date = brithday.split()       #切割輸入
M = int(date[0])              #M 存月份
D = int(date[1])              #D 存日期
S = ( M * 2 + D ) % 3         #S 存計算出來的結果
#用if and elif 判斷運勢並印出結果
if S == 0:                    
    print("普通")
elif S == 1:
    print("吉")
elif S == 2:
    print("大吉")
```
---
### Andrew's code
```python=
#Andrew/ a003 / 2022.3.7
str = input()
m = int(str.split(" ")[0])
d = int(str.split(" ")[1])
s = (m*2+d)%3
if s==0:
    print("普通")
elif s==1:
    print("吉")
else:
    print("大吉")
```
---
### 周旻儀's code
```python=
MD = input()
d = MD.split()
S = int(d[0]*2)+int(d[1])
s = S % 3

if s == 0:
    print('普通')
elif s == 1:
    print('吉')
else:
    print('大吉')
```
### HungYuNung / a003 / 2022.03.06
```python=
M, D = map(int, input().split())
S = ((M*2)+D) % 3
if S == 0:
    print('普通')
elif S == 1:
    print('吉')
else:
    print('大吉')

```
---
## Peggy's code
```python=
a = list(map(int, input().split(" ")))
# list(map讓他變成...的形式(int數字, input().split(" ")用空格分割))
M = a[0]
D = a[1]
#以上可寫成
# M , D = map(int, input().split())
S = (M*2+D)%3
if S == 0:
    print("普通")#如果S=0印出普通
elif S == 1:
    print("吉")#如果S=1印出吉
else:
    print("大吉")#如果S=2印出大吉
```
---
## 家箐's code
```python=
M = input()
d = M.split()
S = int(d[0]*2)+int(d[1])
s = S % 3

if s == 0:
    print('普通')
elif s == 1:
    print('吉')
else:
    print('大吉')
```
---
## [a004 / 2022.02.28](https://zerojudge.tw/ShowProblem?problemid=a004)
### Jesse's code
```python=
def calculate(year):
    year = int(year)
    res = "平年"
    if year % 4 == 0 and year % 100 != 0:
        res = "閏年"
    if year % 400 == 0:
        res = "閏年"
    print(res)


try:
    while True:
        year = input()
        calculate(year)
except EOFError:
    pass

```
---
### Diane's code
```python=
if __name__ == "__main__":
  while(1): 
    try:
      year = int(input())
    except:
      break
    if year % 4 == 0:
      if year % 100 == 0:
        if year % 400 == 0:
          print("閏年")
        else:
          print("平年")
      else:
        print("閏年")
    else:
      print("平年")

```
---
### albert's code
```python=
y=int(input("輸入年份:"))
if y%4 == 0 and y%100 != 0 or y%400 == 0:
    print("閏年")
else :
    print("平年")
```
---
### 蕭亦峰's code
```python=
#蕭亦峰/ a004 / 2022.2.21
while True:      #持續執行程式碼直到沒有輸入
    try:
        year = int(input())
        #如果西元年被4整除且不被100整除 輸出閏年
        if year % 4 == 0 and year % 100 != 0:
            print('閏年')
        #被400整除者即為閏年 輸出閏年
        elif year % 400 == 0:
            print('閏年')
        #其他輸出平年
        else:
            print('平年')
    except:
        break
```
---
### 宇岑 / a004
```python=
a = []

for i in range(0,2):
    year = input()
    a.append(year)
for o in range(0,len(a)):
    if (int(a[o]) % 400 == 0) :
        print('閏年')
    elif (int(a[o]) % 100) == 0: 
        print('平年')
```
---
### Dino's code
```python=
year = int(input())
if (year % 4) == 0:
   if (year % 100) == 0:
       if (year % 400) == 0:
           print("閏年".format(year))   # 4  100  400
       else:
           print("平年".format(year))    #4  100
   else:
       print("閏年".format(year))   #4
else:
   print("平年".format(year))
```
---
### HungYuNung / a004 / 2022.03.06
```python=
try:
    while True:
        n = int(input())
        if (n % 4 == 0 and n % 100 != 0) or n % 400 == 0:
            print('閏年')
        else:
            print('平年')
except EOFError:
    pass

```
---
### 何咏謙/a004/2022.3.7
```python=
count = 0
while count == 0:

    year = int(input())
    if (year % 4 == 0 and year % 100 != 0):
        print("閨年")
    elif year % 400 == 0:
        print("閨年")
    else:
        print("平年")
```

## 家箐'S code
```python=
i = []

for a in range(0,2):
    year = input()
    i.append(year)
for o in range(0,len(i)):
    if (int(i[o]) % 400 == 0) :
        print('閏年')
    elif (int(i[o]) % 100) == 0: 
        print('平年')
```
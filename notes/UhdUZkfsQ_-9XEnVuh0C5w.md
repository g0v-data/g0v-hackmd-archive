# 2022.04.18 課堂e283

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

## [e283題目連結](https://zerojudge.tw/ShowProblem?problemid=e283)
---

## jia qing's code
```python=
nu = int(input()) #輸入要回圈的次數
d = {"0 1 0 1" : "A", "0 1 1 1" : "B", "0 0 1 0" : "C", "1 1 0 1" : "D", "1 0 0 0" : "E", "1 1 0 0" : "F"}
q = input() #輸入字典中的數字
for i in range(nu): 
    n = d[q] 
    print(n)
```
---
## peggy'cold
```python=
import sys
while True:
    try:
        dictionary ={"0 1 0 1":"A"             #依題目所創的字典
                    ,"0 1 1 1":"B"
                    ,"0 0 1 0":"C"
                    ,"1 1 0 1":"D"
                    ,"1 0 0 0":"E"
                    ,"1 1 0 0":"F"}
        f = ""
        a = int(input())                       #輸入要幾行資料
        for i in range(a):                     #放進資料 並在字典找出所對應的英文字
            b = sys.stdin.readline().strip()
            f += dictionary[b]                 #將所有找到的英文字母加在一起
        print(f)                               #輸出
    except:
        break
```
---
## 宇岑's code
```python= 
import sys

mport sys

while True:
    try:
        n = int(input())
        ans = ""
        dic = {"0 1 0 1" : "A" , "0 1 1 1" : "B" , "0 0 1 0" : "C" , "1 1 0 1" : "D" , "1 0 0 0" : "E" , "1 1 0 0" : "F"}

        for i in range(n):
            a = sys.stdin.readline().strip()
            new = dic[a]
            ans += new

        print(ans)

    except EOFError:
        break
```
---
## Jesse's code
```python=
import sys


string_code = {"0 1 0 1": "A", "0 1 1 1": "B", "0 0 1 0": "C", "1 1 0 1": "D", "1 0 0 0": "E", "1 1 0 0": "F"}
while True:
    try:
        string_len = int(input())
        out_put = ""
        for i in range(string_len):
            string = sys.stdin.readline().strip()
            out_put += string_code[string]

        print(out_put)
    except EOFError:
        break
```
---
## 夏羽綾理
```python=
import sys
while True:
    try:
        dz = {"0101":"A","0111":"B","0010":"C","1101":"D","1000":"E","1100":"F"}
        ci = int(sys.stdin.readline().strip())
        res = ""
        for i in range(ci):
            d = sys.stdin.readline().strip()
            d = d.replace(" ","")
            res+=(dz[d])
        print(res)
    except:
        break
'''
                                                ii
                                               iFli
                                              ilolii
                                             iiOOOoii
 \                                     ,eEe EE `E``EEe,  ee,       ,
  `'-,__________  ,                   iEE`EEEi     `EEEEAVHH\\,eeiiiA
                `` ```'---,-'`---`)   i`EEEEC,,   eeEEEEEEA;H \RRRRRRA
                          |       /  sEEJOERZEEF,EEISEEEEEEF \ |RRRRRR|
                          |        \EEEEEEEEF^\ *EEEECATEEF   ||RRRRRR|
                          |        /EEEEEEF^ , \  `EEEEEFEEe  |L.RRRRRF
                          /        \*EEEE*E   `*`   `+*  jE*    )
                         |          (|EEE |         ___ /EF    |
                         |        ,/   `,|\         \   |EF`-,,/
                         |       /\,,,-'|  \,  ＼    \  )F
                         |      /   // ,|    \, ___/*`/;E,
                         |      )  //  |`    ,/`-,EEEEEEEA
                        ,|      <:` \  |   ,/    (EEEEEEEEF
                        |       \  `\\ | ,/    ,/// /EEEEEE
                        |       )    /\|/,    / /  /EEEEEEE
                        |     ,/    /   / `'-/_/  /,EEEEEEF
                       ,|      )_,/`L,,/      /     `EEEEEEA
                       |       |   ,/ /      /      /EEEEEEE
                       /      /   // |     ,/      /EEEEEEEEA
 +,                   /      (   //  |   ,/      R/EEEEEEEEEE
   `'-,,              |      ) ,/|   |\_//     O|/EEEEEEEEEEEA
        `'--.,_______/\,,   /\/e,|   |RR \,___,/`|EEEEEEEEEEEEA
                   mEEE  `-/eeRR|    |\: RRR/ /RR\EEEEEEEEEEEEEA
                  eeRRRR    RRRRL,   |  `\,/ /R*^`EEEEEEEEEEEEEEA
'''
```






---
## Din0o0o0o's code
```python=
import sys
list = {"0 1 0 1":"A","0 1 1 1":"B","0 0 1 0":"C","1 1 0 1":"D","1 0 0 0":"E","1 1 0 0":"F"}
 
for i in sys.stdin:
    n = int(i)
    ans = ""
    for i in range(n):
        s = sys.stdin.readline().strip()  #取出換行符號
        ans += list[s]
    print (ans)

```
---
## 黃品誠
```python=
import sys
while True:
    try:
        d = {"0 1 0 1":"A","0 1 1 1":"B","0 0 1 0":"C","1 1 0 1":"D","1 0 0 0":"E","1 1 0 0":"F"}
        ans = ""
        z = int(sys.stdin.readline().strip()) # 要幾個字母
        for i in range(z):
            a = sys.stdin.readline().strip()
            ans += str(d[a])
        print(ans)
    except:
        break
```


---
## 王聖偉//e283//0418
```python=
d={'0 1 0 1':'A','0 1 1 1':'B','0 0 1 0':'C','1 1 0 1':'D','1 0 0 0':'E','1 1 0 0':'F'}
try:
    while True:
        f=int(input())
        l=""
        for i in range(f):
            w=input()
            l+=d[w]
        print(l)
except EOFError:
    pass
```
---
## HungYuNung / e283 / 04.18
```python=
import sys
while True:
    try:
        dic = {'0 1 0 1':'A',
               '0 1 1 1':'B',
               '0 0 1 0':'C',
               '1 1 0 1':'D',
               '1 0 0 0':'E',
               '1 1 0 0':'F'}
        time = int(input())
        ans = ''
        for i in range(time):
            n = sys.stdin.readline().strip()
            ans += dic[n]
        print(ans)
    except EOFError:
        break
```
---
## albert's code
```python=
while True:
    try:
        x={"0101":"A","0111":"B","0010":"C","1101":"D","1000":"E","1100":"F"}  
        a=int(input())
        m=""
        for i in range  (a):
            b=input()
            m.append(x[b])
        print(m)
    except: 
        break

```
---
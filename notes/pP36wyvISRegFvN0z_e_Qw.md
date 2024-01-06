# 2022.04.4 作業a020

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

## [a020題目連結](https://zerojudge.tw/ShowProblem?problemid=a020)
---
## Jesse's code
```python=
import sys

id_dic = {}
number = 10
# (1)
for i in range(ord("A"), ord("Z") + 1):
    if chr(i) == "I":
        id_dic[chr(i)] = "34"
    elif chr(i) == "O":
        id_dic[chr(i)] = "35"
    elif chr(i) == "W":
        id_dic[chr(i)] = "32"
    elif chr(i) == "X":
        id_dic[chr(i)] = "30"
    elif chr(i) == "Y":
        id_dic[chr(i)] = "31"
    elif chr(i) == "Z":
        id_dic[chr(i)] = "33"
    else:
        id_dic[chr(i)] = str(number)
        number += 1
# end（1）

id = sys.stdin.readline()[:10]
c = 9
# （2）
output = int(id_dic[id[0]][0]) + int(id_dic[id[0]][1]) * c
# end（2）
# （3）（4）
for i in id[1:]:
    c -= 1
    if c >= 1:
        output += int(i) * c
    else:
        output += int(i)

# end（3）（4）
# （5）
if output % 10 == 0:
    print("real")
else:
    print("fake")
# end（5）
```
---
## 夏羽綾理
```python=
x = {"A":10,"J":18,"S":26,"B":11,"K":19,"T":27,"C":12,"L":20,"U":28,"D":13,"M":21,"V":29,"E":14,"N":22,"W":32,"F":15,"O":35,"X":30,"G":16,"P":23,"Y":31,"H":17,"Q":24,"Z":33,"I":34,"R":25}
d = input()
d = str(x[d[0]])+d[1::]
intd = []
c = 0
for i in range(len(d)):
    intd.append(int(d[i]))
for i in range(len(intd)):
    if i>0 and i<10:
        c += intd[i]*(10-i)
    else:
        c += intd[i]
if c%10 == 0:
    print("real")
else:
    print("fake")
#                              _____
#                         .,-'`      `'-.                              ______
#                     ,,/`,*    ,,--"---.,',                          /      |
#                  ,,/   *   ,/` ,-'''--,,``*,                       /  __   |
#                ,/       ,/` ,/`    /\  /\`- `-                    /  /  |  |
#              ,/       ,/  ,/ ,  /\/  ``  \/|, `,                 /  /___|  |
#            ,/        /  ,/  / \/           \ `, \               /          |
#          ,/ ,,/     /  / |\/       i        \/|\ \             /  ______   |
#        ,/ ,/       /  /  /         E          \ \ \           /  /      |  |
#        /,/        /  /\ /     , ,^EE   ||  \   `|\ \         /  /       |  |
#       /          /  /  V     // /||EV  ||  ||   \/| \       /__/        |__|
#     ,*          ,  ;      | / |/ |/|_,/|/|/|| ||  \ \\
#   ,/      ,     /  /     |/|/            *   \||   \\ \
#  /        |    /, ,`     |\="""=+,            v)   | ||
# /         |    |  ||     \\\(    )`       +"""=,   ; | \
# *---------*    |  ||    \ \`---.-         (   )|   | | |
#    |           |  \|     \,\              ``'-`|   | | |
#    \           |   //      \|_                / /  / |\|
#     *          \  //|     ||       -''''-    /`/   / /
#      \         ,\`` |     |\\       \   /    ||/| \\ |
#       \         \   \    V\ \\\,,    ``` ,.'` /|/  \\/
#        \.        \   \   VE\ \|  ``-,,.-`    /|,/ | \\
#          `\,      \   |\  VE\/\ /\ |,,  .  /\/|e  |  `
#          ,/ \,,    `\ \ \  VE\`'`-`---\/ \/  /eE  /
#        ,//| / ;\-,   `-,_\,_ \*     ,  \    /,F  /
#       // / /(`    ``'--,,__>\|\---...,,/,,,/`* ,/\
#       v / //+         *'\,  \,         /  // ,/   \,
#       ,/,//  `'-,         '-, \,      / ,'*'`    ,/ \
#      //  /       `'-,        `'-\    /,'       ,`    \
#          |            `'-.,      \   /    ,.-'`      \,
#         /                   `'-., \,/,.-'`            |,
#       ==================================================
```
---
## albert's code
```python=
縣市_char_dic= {'A':10,'B':11,'C':12,'D':13,'E':14,'F':15,'G':16,'H':17,'I':34,
        'J':18,'K':19,'L':20,'M':21,'N':22,'O':35,'P':23,'Q':24,'R':25,
        'S':26,'T':27,'U':28,'V':29,'W':32,'X':30,'Y':31,'Z':33}
z=input("請輸入身分證字號:")
m=縣市_char_dic [z[0]]
a=int(m/10)
b=int(m%10)
c=int(z[1])
d=int(z[2])
e=int(z[3])
f=int(z[4])
g=int(z[5])
h=int(z[6])
i=int(z[7])
j=int(z[8])
k=int(z[9])
L=a+b*9+c*8+d*7+e*6+f*5+g*4+h*3+i*2+j*1+k
if L%10 == 0:
    print("true")
elif L%10 != 0:
    print("false")
```
---
## 宇岑's code
```python=
import sys

dic = {"A":10, "B":11, "C":12, "D":13, "E":14, "F":15, "G":16,  "H":17, "I":34,  "J":18, "K":19, "L":20, "M":21, "N":22, "O":35, "P":23, "Q":24, "R":25, "S":26, "T":27, "U":28, "V":29, "W":32, "X":30, "Y":31, "Z":33}

b = sys.stdin.readline().strip()
if len(b) != 10:
    print('fake')
else:
    u =1
    kk = 0

    aa = str(dic[b[0]])
    aa[1]
    new = int(aa[0]) + int(aa[1])*9


    for i in range(8,0,-1):
        p = int(b[u])*i
        u+=1
        kk+=p
        
    kk +=int(b[9])
    kk +=new

    if kk%10 == 0:
        print('real')
    else:
        print('fake')
```
---
## 黃品誠
```python=
while True:
    try:
        d = { "A":10,"J":18,"S":26,"B":11,"K":19,"T":27,"C":12,"L":20,"U":28,"D":13,"M":21,"V":29,"E":14,"N":22,"W":32,"F":15,"O":35,"X":30,"G":16,"P":23,"Y":31,"H":17,"Q":24,"Z":33,"I":34,"R":25,}
        s = input()
        NumberAns = 0
        en = str(d[s[0]]) #前面的英文字母轉數字
        number = s[1::] #英文後面的數字
        for i in range(len(number)):
            NumberAns += int(number[(i*-1)-1])*int(i) # (i*-1)-1  ex:112663836倒著數 ==> 638366211 
        NumberAns += int(number[-1]) #第一次回圈為 int(i) = 0    (i*-1)-1])*int(i) ==> ex:6*0 = 0 這樣會忽略最後一個數字，所以要加回去
        enans = int(en[0]) + (int(en[1]))*9 # ex: T=27 ==> (2) + (7*9) = 65
        ans = NumberAns + enans 
        if ans%10 == 0:
            print("real")
        else :
            print("fake")
    except:
        break
```
---
## 王聖偉/a020/0418
```python=
d={'A':10,'J':18,'S':26,'B':11,'K':19,'T':27,'C':12,'L':20,'U':28,'D':13,'M':21,'V':29,'E':14,'N':22,'W':32,'F':15,'O':35,'X':30,'G':16,'P':23,'Y':31,'H':17,'Q':24,'Z':33,'I':34,'R':25}
f=input()
# print(d['F'])
sum=0
for i in range(1,len(f)-1):
    sum+=int(f[i])*(9-i)
if(((int(d[f[0]])//10) + ((int(d[f[0]])%10)*9) + sum + int(f[9]))%10==0):
    print('real')
else:
    print('fake')
```
---
## peggy'cold
```python=
import sys

id = {"A":10,"B":11,"C":12,"D":13,"E":14,"F":15,"G":16,"H":17,"I":34,"J":18,"K":19,"L":20,"M":21,"N":22,"O":35,"P":23,"Q":24,"R":25,"S":26,"T":27,"U":28,"V":29,"W":32,"X":30,"Y":31,"Z":33}

b = sys.stdin.readline().strip()
if len(b) != 10:                #如果它的長度不等於10輸出fake
    print("fake")
else:
    z = 1                       #第幾項
    x = 0                       

    a = str(id[b[0]])           #將英文轉成對應的數字
    c = int(a[1])*9+int(a[0])   #將個位數乘9加上十位數的數字

    for i in range(8,0,-1):     #數字從右到左乘上1~8再相加
        d = int(b[z])*i
        x += d
        z += 1
    x += int(b[9])              #因為最後一個沒乘到所以直接加上
    x += c                      #依題目(2)(3)相加求和
    if x % 10 == 0:             #如果有整除輸出real
        print("real")
    else:
        print("fake")           #沒有整除輸出fake

```
---
## HungYuNung / a020
```python=
place = {'A':10,'B':11,'C':12,'D':13,'E':14,'F':15,'G':16,'H':17,'I':34,
         'J':18,'K':19,'L':20,'M':21,'N':22,'O':35,'P':23,'Q':24,'R':25,
         'S':26,'T':27,'U':28,'V':29,'W':32,'X':30,'Y':31,'Z':33}
id = str(input())

if len(id) != 10:
    print('fake')
else:
    first_of_str = (place[id[0]]//10) + ((place[id[0]]%10)*9) # 把第一個字母出來的數字分開算出
    last_num = int(id[-1]) 
    mid_num = 0 
    arr_time = 8 
    for i in range(1, 9):
        mid_num += int(id[i]) * arr_time
        arr_time -= 1
    if (first_of_str + mid_num + last_num) % 10 == 0:
        print('real')
    else:
        print('fake')
```
---
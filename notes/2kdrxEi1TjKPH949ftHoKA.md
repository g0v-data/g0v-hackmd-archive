# 2022.05.16 作業c295

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

## [題目連結](https://zerojudge.tw/ShowProblem?problemid=c295)
## 夏羽綾理
```python=
import sys
hl = sys.stdin.readline().strip().split()
hl = int(hl[0])
l = [[]for i in range(hl)]
s = 0
zc = ""
for i in range(hl):
    l[i] = sys.stdin.readline().strip().split()
    l[i] = list(map(int,l[i]))
    s += max(l[i])
for i in range(hl):
    if s%max(l[i]) == 0:
        zc += str("%d "%(max(l[i])))
print(s)
if zc == "":
    print(-1)
else:
    print(zc[:len(zc)-1:])
'''
                   /               /                      \
                 /*      /*                       \        *\,,,
          ,eEEEF/       /    /                     \        (EEEee++,,
      ,eEEEEEEF/       /    /                       \       \VEEEEEEEEEe+,
   \VEEEEEEEEF/       /    /              /          \       \VEEEEEEEEEEEF/
    \VEEEEEEF/       /     |             |            \      \VEEEEEEEEEEF/
     \VEEEEF/       /  /   |             |             \      \VEEEEEEEEF/
      \VEEF/        / /    |             |              \      \VEEEEEEF/
       \VF/        /  |    |              \             \       \VEEEEF/
        \/*  /    /   |    /              |     \        |       \VEEF/
         /  /     /   /   | \ \           |\    |\  \    |      \ \VF/
        /   |    |   / \  |  \ \    \     | \   \ \  |   |      |  \*\
       */   |    | /*   \  \  *\\   \\,    \ \   \ *\+  / |     |  \  \
       /    |    |/      *-      *\_ *\\,,  \ *\,|   | /  |     |   \ \*
      /     \   /                   *--   *--    *   |/   |    ,|   \  \
     */     *\  |                                         |    /     \ \*
     /|      \  |          **+-,           ,-+**          |    /     \  \
    / /\     \  |  ,-*EEEEEE*+-.           ,-+EEEEEEE*+-, |   ,/     /|\\*
   *// *      \ | eeeeEEEEEEeeeee         eeeeEEEEEEEeeeee|   /     / | \|
   / | \      \* \                  ,                     |  /     /  |, \
  */ |  \      \ | / / / / / /               / / / / / / */ ,     ,/   | \
  */ |   \      \|                                       / /     /     |  \
  |  |    \      \                                      / /    ./      |  \
  |  |     \      \         \,               ,/        / /   ,/        |   \
  |  |      *\     \         *\VEEEEEEEEEEFEF/        ,/*  ,/         ,|   |
  |  \*       *\,   *\           ***EEEE***          //  ,/           | |  |
  \  *\E        * \__ \                             /  ,/            A/ |A  |
  \*  \EE,           * \--,,,___              ,,-+**  /            ,V/  |E  /
   \   \EEE,            *\EEEEEE+----------+** |,E//*            ,eEV/  |E /
    \  |\EEEA             \VEE/-|             ,+ \/            ,eEEE/   /E /
     \  \*\VEEA,           *\/   \         ,/*   /          ,eEEEEV/E  /VE/
      *\|  *\VEEEA,,         \    *\    /+*     /        ,eEEEEEV/EEF,/  V/
        *     *EEEEEEEA       \     *\/*        |      EEEEEEEV/EEEE/
'''
```
---
## Jesse's code
```python=
n, m = map(int, input().split())
num_list = [[]] * n
max_list = []

for i in range(n):
    num_list[i] = list(map(int, input().split()))
    max_num = max(num_list[i])
    max_list.append(max_num)


sum_num = sum(max_list)
print(sum_num)

out_put = ""
for i in max_list:
    if sum_num % i == 0:
        out_put += f"{i} "

if not out_put:
    print("-1")
else:
    print(out_put[:-1])
```
---
## 何咏謙's code
```python=
while True:
    try:
        #設輸入3,2
        N, M = map(int,input().split())

        nub = []
        factor = []
        
        count = 0
        for i in range(N): #執行3次
            #for j in(1,M):  #執行2次
            x = map(int,input().split()) #放入x
            nib = max(x)
            nub.append(nib)#nub裡面有三個數字

        total = sum(nub)

        for k in nub:   #nub是陣列 執行三次 k裡面會是由0到2的nub
            if total % k == 0:   #如果nub裡面其中有可以整除total的數字 就存進factor
                factor.append(k)
                count += 1

        print(total)
        if count == 0:
            print("-1")

        else:
            print(' '.join(map(str, factor))) 
        

    except EOFError:
        break
```
---
## ゆきねこ 
```python=
N, M = map(int, input().split())

choose_list = []
for _ in range(N):
	choose_list.append(max(map(int, input().split())))

sum_v = sum(choose_list)

answer_list = []
for v in choose_list:
	if not(sum_v % v):
		answer_list.append(str(v))

print(sum_v)
if len(answer_list):
	print(' '.join(answer_list))
else:
	print(-1)
```

---
## Din0o0o0o
```python=

N,M=map(int,input().split())

list1=[]
list2=[]
list3=[]

for i in range(N):
  arr=list(map(int,input().split()))
  list1.append(arr)
  list2.append(max(arr))

Max1=sum(list2)

for j in list2:
  if Max1%j==0:
    list3.append(j)

print(Max1)
print("-1") if list3==[] else print(*list3)
```
---
## 宇岑's code
完成了
```python=
N, M = map(int, input().split())
LL = []
DIVIDE = []

for i in range(N):
    num = list(map(int, input().split()))
    LL.append(max(num))#取一行輸入中的最大數

print(sum(LL))#最大數總和
for a in range(0, len(LL)):
    if sum(LL) % LL[a] == 0:   #一一檢查每個最大數是否為因數
        DIVIDE.append(LL[a])
    else:
        pass

if len(DIVIDE) == 0:   #最大數中完全沒有因數
    print(-1)
else:
    print(*DIVIDE)
```

---
## 聖偉/c295/0606
```python=
q=list(map(int,input().split()))
sum=0
first=False
maxv=[]
dvs=[]
for i in range(q[0]):
    k=list(map(int,input().split()))
    sum+=max(k)
    maxv.append(max(k))
print(sum)

# a=[i*i for i in range(5)]
for i in maxv:
    if sum%i==0:
        dvs.append(i)

if len(dvs) == 0:
    print(-1)
else:
    print(*dvs)
```

---
## 周旻儀/c295/0606
```python=
m,y = map(int, input().split())

arr = []
list = []
Nsum = 0
for i in range(m):
    a = map(int, input().split())
    aMax = max(a)
    arr.append(aMax)
    Nsum += aMax
print(Nsum)

for j in arr:
    if Nsum % j == 0:
        list.append(j)

if list == []:
    print(-1)
print(*list)        
```
---
## albert's code
```python=
N, M = map(int, input().split())
maxi = []
a=[]

for i in range(N):
    num = list(map(int, input().split()))
    maxi.append(max(num))

print(sum(maxi))
for b in range(len(maxi)):
    if sum(maxi) % maxi[b] == 0:   
        a.append(maxi[b])
    else:
        pass

if len(a) == 0:   
    print(-1)
else:
    print(*a)       
```
---
## peggy
```python=
a = list(map(int,input().split(" ")))
c = 0
e = [ ]
f = [ ]
for i in range(a[0]):
        b = list (map(int,input().split()))
        d = max(b)
        e.append(d)
        c = c + d   #最大值
print(c)
for j in e:
        if c%j == 0:
                f.append(j)
        else:
                pass
if len(f) == 0:
        print(-1)
else:
        print(*f)
```
---
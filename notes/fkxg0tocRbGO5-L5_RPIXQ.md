## 課堂c461

[題目連結](https://zerojudge.tw/ShowProblem?problemid=c461)

```python=
a,b,c = list(map(int, input().split()))

if a !=0:
    a = True
if b != 0:
    b = True
if c !=0 :
    c = True

flag = False

###  ↓ ↓ ↓以下部分為表格內容
if (a and b) == c: # 0 0 0
    flag = True
    print('AND')       
if (a or b) == c:  # 0 0 0
    flag = True
    print('OR')        
if (a != b) == c:
    flag = True
    print('XOR')
if not flag:
    print('IMPOSSIBLE')
```
---
### Kamisato Ayaka(Hung)
```python=
a, b, c = map(int, input().split())
if a > 0: a = 1
if b > 0: b = 1
value = False
if a & b == c:
    print("AND")
    value = True
if a | b == c:
    print("OR")
    value = True
if a ^ b == c:
    print("XOR")
    value = True
if value != True:
    print("IMPOSSIBLE")
```
---
### Jesse's code
```python=
a, b, c = map(int, input().split())
flag = False
la = (a != 0)
lb = (b != 0)
lc = (c != 0)
if (la and lb) == lc:
    print('AND')
    flag = True
if (la or lb) == lc:
    print('OR')
    flag = True
if ((la and (not lb)) or ((not la) and lb)) == lc:
    print('XOR')
    flag = True
if not flag:
    print('IMPOSSIBLE')
```
---
### 聖偉/c461/0516
```python=
q=input()
if(q[0]=='0'):               
    if(q[2]=='0'):              
        if(q[4]=='0'):      #0 0 0
            print('AND')
            print('OR')
            print('XOR')
        else:               #0 0 1
            print('IMPOSSIBLE')
    else:                       
        if(q[4]=='0'):      #0 1 0
            print('AND')
        else:               #0 1 1
            print('OR')
            print('XOR')
else:                        
    if(q[2]=='0'):          
        if(q[4]=='0'):      #1 0 0
            print('AND')
        else:               #1 0 1
            print('OR')
            print('XOR')
    else:                   
        if(q[4]=='0'):      #1 1 0
            print('XOR')
        else:               #1 1 1
            print('AND')
            print('OR')
```
---
### 何咏謙's code
```python=
a,b,c = map(int,input().split(' '))
no = 0

if a != 0:
    a == 1

if b != 0:
    b == 1
    
if (a and b) ==c:
    print('AND')
    no += 1

if (a or b) == c:
    print('OR')
    no += 1

if (a != b) and (c==1):
    print('XOR')
    no += 1

if (a == b) and (c == 0):
    print('XOR')
    no += 1

if no == 0:
    print('IMPOSSIBLE')
```
---
## 夏羽綾理
```python=
d = input().split()
im = 0
for i in range(len(d)):
    d[i] = int(d[i])
    if d[i] > 0:
        d[i] = 1
if (d[0]&d[1]) == d[2]:
    print("AND")
    im += 1
if (d[0]|d[1]) == d[2]:
    print("OR")
    im += 1
if (d[0]^d[1]) == d[2]:
    print("XOR")
    im += 1
if im == 0:
    print("IMPOSSIBLE")
```


---

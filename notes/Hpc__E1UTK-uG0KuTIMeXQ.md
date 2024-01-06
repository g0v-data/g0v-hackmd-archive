# 2022.05.02 課堂e286

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

## [題目連結](https://zerojudge.tw/ShowProblem?problemid=e286)
---
## Jesse's code
```python=
def ball_game(home_first, away_first, home_second, away_second):
    home_first_score = [int(x) for x in home_first.split()]
    away_first_score = [int(x) for x in away_first.split()]
    home_second_score = [int(x) for x in home_second.split()]
    away_second_score = [int(x) for x in away_second.split()]
    home = {"home": sum(home_first_score), "away": sum(away_first_score)}
    away = {"home": sum(home_second_score), "away": sum(away_second_score)}

    if home["home"] > home["away"] and away["home"] > away["away"]:
        res = "Win"
    elif home["home"] < home["away"] and away["home"] < away["away"]:
        res = "Lose"
    else:
        res = "Tie"

    print(f'{home["home"]}:{home["away"]}')
    print(f'{away["home"]}:{away["away"]}')
    print(res)


ball_game(input(), input(), input(), input())
```
---
### 宇岑's code
```python=
g1_t1 = sum( list(map(int, input().split())))
g1_t2 = sum(list(map(int, input().split())))
g2_t1 = sum(list(map(int, input().split())))
g2_t2 = sum(list(map(int, input().split())))
G1 = 0
G2 = 0
Sg1_t1 = 0
Sg1_t2 = 0
Sg2_t1 = 0
Sg2_t2 = 0

if g1_t1>g1_t2:
    G1+=1
elif g1_t1<g1_t2:
    G2+=1
if g2_t1>g2_t2:
    G1+=1
elif g2_t1<g2_t2:
    G2+=1

print('{}:{}'.format(g1_t1, g1_t2))
print('{}:{}'.format(g2_t1,g2_t2))




if G1 > G2:
    print('Win')
elif G1 < G2 :
    print('Lose')
else:
    print('Tie')
```
---
### Albert's code
```python=
g1_t1 = sum( list(map(int, input().split())))
g1_t2 = sum(list(map(int, input().split())))
g2_t1 = sum(list(map(int, input().split())))
g2_t2 = sum(list(map(int, input().split())))
t1=g1_t1+g2_t1
t2=g1_t2+g2_t2
print(g1_t1,g1_t2 ,sep = ':')
print(g2_t1,g2_t2 ,sep = ':')
if t1>t2 :
    print("Win")
elif t1<t2 :
    print("Lose")
elif t1==t2:
    print("Tie")
```
---
## 夏羽綾理
```python=
import sys
f = [[],[],[],[]]
for i in range(4):
    f[i] = sys.stdin.readline().strip().split()
for i in range(4):
    for j in range(4):
        f[i][j] = int(f[i][j])
for i in range(4):
    f[i] = sum(f[i])
print("%d:%d\n%d:%d"%(f[0],f[1],f[2],f[3]))
if f[0]>f[1] and f[2]>f[3]:
    print("Win")
elif f[0]<f[1] and f[2]<f[3]:
    print("Lose")
else:
    print("Tie")
'''
 _    _    _    _    _   _    _______        ___     _    _____    _   _    ______ 
\ \  / /  | |  | |  | | / /  |__   __|      |   \   | |  |  ___|  | | / /  /  __  \
 \ \/ /   | |  | |  | |/ /      | |         | |\ \  | |  | |__    | |/ /   | |  | |
  \  /    | |  | |  |   |       | |         | | \ \ | |  |  __|   |   |    | |  | |
  / /     | |__| |  | |\ \    __| |__       | |  \ \| |  | |___   | |\ \   | |__| |
 /_/       \____/   |_| \_\  |_______|      |_|   \___|  |_____|  |_| \_\  \______/
'''
```
---
## 黃品誠
```python=
import sys
z = 0
k = 0
zc1 = sys.stdin.readline().strip().split(" ") #主隊第一場的分數
kc1 = sys.stdin.readline().strip().split(" ") #客隊第一場的分數
zc2 = sys.stdin.readline().strip().split(" ") #主隊第二場的分數
kc2 = sys.stdin.readline().strip().split(" ") #客隊第二場的分數
zc1z = int(zc1[0])+int(zc1[1])+int(zc1[2])+int(zc1[3])
kc1z = int(kc1[0])+int(kc1[1])+int(kc1[2])+int(kc1[3])
zc2z = int(zc2[0])+int(zc2[1])+int(zc2[2])+int(zc2[3])
kc2z = int(kc2[0])+int(kc2[1])+int(kc2[2])+int(kc2[3])

print(str(zc1z)+":"+str(kc1z))
print(str(zc2z)+":"+str(kc2z))

if zc1z - kc1z > 0:
    z += 1
else:
    k += 1

if zc2z - kc2z > 0:
    z += 1
else:
    k += 1

if z > k :
    print("Win")
elif z == k :
    print("Tie")
elif z < k :
    print("Lose")
```
---
## ゆきねこ
```python=
getScore = lambda: sum(map(int, input().split()))
status = {
	0: 'Lose',
	1: 'Tie',
	2: 'Win'
}

M1, G1, M2, G2 = (getScore(), getScore(), getScore(), getScore())

print(M1, ':', G1, sep='')
print(M2, ':', G2, sep='')

print(status[(M1 > G1) + (M2 > G2)])
```
---
### Hung Yu Nung
```python=
r1t1, r1t2, r2t1, r2t2 = [int(x) for x in input().split()], [int(x) for x in input().split()], [int(x) for x in input().split()], [int(x) for x in input().split()]

print('{}:{}'.format(sum(r1t1), sum(r1t2)))
print('{}:{}'.format(sum(r2t1), sum(r2t2)))

if sum(r1t1) > sum(r1t2) and sum(r2t1) > sum(r2t2):
    print('Win')
elif sum(r1t1) < sum(r1t2) and sum(r2t1) < sum(r2t2):
    print('Lose')
else:
    print('Tie')

```
---

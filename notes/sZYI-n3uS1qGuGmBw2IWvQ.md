## 夏羽綾理 / a053 / 2022.02.28
```python=
tishu = int(input())
score = 0
step = 0
if tishu > 40:
    score = 100
elif tishu >= 21:
    score += 80 + (tishu-20)
elif tishu >= 11:
    score += 60 + (tishu-10)*2
elif tishu >= 0:
    score += tishu*6
print(score)
```

---

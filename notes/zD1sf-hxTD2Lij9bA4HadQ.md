# 聖偉/a005/0307
```python=
a=int(input())
for i in range(a):
    s=input().split()
    d=int(s[1])-int(s[0])
    r=int(s[1])//int(s[0])
    if d==int(s[2])-int(s[1]):  #ari
        s.append(int(s[3])+d)
    elif r==int(s[2])//int(s[1]):    #geo
        s.append(int(s[3])*r)
    for i in range(5):
        print(s[i],end=" ")
    print("\n")
```

---

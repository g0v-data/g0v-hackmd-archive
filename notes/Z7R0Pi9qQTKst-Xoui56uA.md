# python coding technique
# input
read multiple variable
```
a, b = map(eval, input().split())
print(a+b)
```
read to EOF
```
while True:
    try:
        var=input()
    except:
        break
```

# transformation
join()
```
sep = '-'
ls = ['a','b','c']
sep.join(ls)
```
OUTPUT: a-b-c
#王聖偉/a022/0314
```python=
try:
    while True:
        l=input()
        rev=reversed(l)

        if l==''.join(rev):
            print("yes")
        else:
            print("no")
except EOFError:
    pass
```

---

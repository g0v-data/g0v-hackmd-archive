# 群暉面試題目一

給兩個字串s1,s2，反轉s2中的某個區間，使得兩個字串對應位置匹配字母個數最大，如果有多個區間滿足，選擇區間差值最小的那個，最後輸出
舉例： 
s1 : happycoding
s2 : onedocument
4, 4, 8

```python
def match(s1, s2):
    ret = 0
    for c_s1, c_s2 in zip(s1, s2):
        if c_s1 == c_s2:
            ret += 1
    return ret

max_match, left, right = -1, -1, -1
min_cut = 1e9
for i in range(len(s2))
    for j in range(2, len(s2)-i):
        o_s2 = s2[:i]
        r_s2 = s2[i:]
        r2_s2 = r_s2[:j]
        r2_s2 = r2_s2[::-1]
        r_s2 = r_s2[j:]
        res = match(s1, o_s2 + r2_s2 + r_s2)
        
        if res > max_match 
            and (i + j) - (i + 1) < min_cut:
            max_match, left, right = res, i + 1, i + j
            min_cut = (i + j) - (i + 1)
```
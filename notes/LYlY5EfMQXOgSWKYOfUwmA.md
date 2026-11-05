# 考題一： 字串「 . 」比對
函數給定 2 個字串 ，一個由英文字母a-z組成的 S 和另一個為英文字母外加 1 個「 . 」組成的 P，
請實作一個函式去判斷 S 是否匹配 P，其中，「 . 」字元代表任意 a-z 字元。
Example:
s = abc, p = a.c, return True
s = abc, p
= ac. ,return False


Implement here：
s=ab , p=a.c



```python=
def compare(s: str, p: str):
    if s.len()==0 and p.len()==0:
        return true
    elif s.len()!=0 and p.len()==0:
        return false
    elif s.len()==0 and p.len()!=0:
        return false
    elif s.len() != p.len():
        return false
    
    for(i in range(s.len())):
        if p[i]==s[i] or p[i] == '.'
            continue
        else:
            return false
    return true

```

s[1] a p[1] a
s2 b p2 c



考題二： 字串「 * 」比對
函數給定 2 個字串 ，一個由英文字母組成的 S 和另一個為英文字母外加 1 個「 *」組成的 P，
請實作一個函式去判斷 S 是否匹配 P，其中，「  *  」字元代表重複前字元0次到任意N次。


Example:
s = ac, p = a*c, return True
s = aaac, p = a*ac, return True
s = aaaaaaac, p = a*c, return True
s = abc, p = a*c ,return False

Implement here:

```python=

s = aaac, p = a*ac
def compare(s: str, p: str):
    if s.len()==0 and p.len()==0:
        return true
    elif s.len()!=0 and p.len()==0:
        return false
    elif s.len()==0 and p.len()!=0:
        return false

    idxs = 0 // 3
    idxp = 0 // 2
    while(true):
        if(idxs == s.len() and idxp == p.len())
            break
        elif(idxs != s.len() and idxp == p.len())
            return false
        elif(idxs == s.len() and idxp == p.len())
            return false
        
        if(s[idxs] == p[idxp]):  
            idxs+=1
            idxp+=1
        if(s[idxs] != p[idxp] and p[idxp] != '*'):
            return false 
        if(s[idxs] != p[idxp] and p[idxp] == '*'): 
            temp_c = p[idxp-1]  
            while(s[idxs] == temp_c):
                idxs+=1
            idxp+=1 
        

    return true

```
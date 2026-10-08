# 面試題目： 字串「 . 」比對
函數給定 2 個字串 ，一個由英文字母組成的 S 和另一個為英文字母外加 1 個「 . 」組成的 P，
請實作一個函式去判斷 S 是否匹配 P，其中，「 . 」字元代表任意 a-z 字元。
Example:
s = abc, p = a.c, return True
s = abc, p = ac. ,return False
Implement here:

# S-len != P-len

. in p position  > 1
compare left of . and right of . is same as s

--
dot_index = p.index('.')
p_left, p_right = p[:dot_index], p[dot_index+1:]
if dot_index > len(s):
   return False
   
s_left, s_right = s[:dot_index], s[dot_index+1:]
return s_left == p_left and p_right == s_right

time: O(N)
space: O(N)

--
dot_index > 0, dot_index > right
s = abcc, p = a.c, return True
s = abc, p = ac. ,return False

if s_len != p_len:
    return False
    
dot_index = p.index('.') # 1
for i, c in enumerate(p): # 0, a, # 1, b, # 2, c
    if i >= s_len:
        return False
        
    if i == dot_index:
        continue
        
    if c != s[i]:
        return False
        
return True
        
---

        

 字串「 * 」比對
函數給定 2 個字串 ，一個由英文字母組成的 S 和另一個為英文字母外加 1 個「 *」組成的 P，
請實作一個函式去判斷 S 是否匹配 P，其中，「  *  」字元代表重複前字元0次到任意N次。


Example:
s = aac, p = a*c, return True
s = abc, p = a*c ,return False

    
a*c == aaac == ac == aaaaac
a* 前後都要保持相同

1. 找出 * 的位置
2. 看前一個位置的 char 是什麼 >> a; 
    3. *c > 第一個字元是 * 就 return False
4. 從 s 的右側往左跟 p 比對，如果遇到 * 前就不一致，直接回 False
    6. 到了 p 的米字後，才去檢查如果都是 a 都是合法的，直到不同的 char 出現
6. 如果遍歷完成，代表 * 左邊都是正確的


star = p.index('*')
if star == 0:
    return False
    
s_len = len(s)
find_star, star_prev_char = False, ''
p_index = None

for i in range(s_len-1, 0, -1):
    if not find_star and s[i] == p[i]:
        continue
    if p[i] == '*':
        find_star = True
        star_prev_char = p[i-1]
        p_index = i-1
        
    if not find_star: # s!=p
        return False
        
    # find_star
    if s[i] == star_prev_char:
        continue
    
    p_index -= 1
    if s[i] != p[i]:
    
        
    
        
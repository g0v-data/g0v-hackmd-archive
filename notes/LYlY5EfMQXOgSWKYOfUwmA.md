# 考題一： 字串「 . 」比對
函數給定 2 個字串 ，一個由英文字母a-z組成的 S 和另一個為英文字母外加 1 個「 . 」組成的 P，
請實作一個函式去判斷 S 是否匹配 P，其中，「 . 」字元代表任意 a-z 字元。
Example:
s = abc, p = a.c, return True
s = abc, p = ac. ,return False


Implement here：
bool isPair(string s, string p) {
    if(s.size() != p.size())
        return false;
        
    for(int i=0;i<s.size();i++) {
       if(s[i] != p[i] && p[i] != '.')
           return false;
    }
    
    return true;
}


考題二： 字串「 * 」比對
函數給定 2 個字串 ，一個由英文字母組成的 S 和另一個為英文字母外加 1 個「 *」組成的 P，
請實作一個函式去判斷 S 是否匹配 P，其中，「  *  」字元代表重複前字元0次到任意N次。


Example:
s = aaaaac, p = a*c, return True
s = ac, p = a*c, return True
s = abc, p = a*c ,return False

Implement here:
bool match(string s, string p, int i, int j) {

    
    if(p[j+1] == '*') {
        if(match(s, p, i, j+2))
            return true;
        if(s[i] == p[j] && match(s, p, i+1, j))
            return true;
            
        return false;
    }
    
    if(s[i] == p[j])
        return match(s, p, i+1, j+1);
        
    return false;
    
}
bool isPair(string s, string p) {

    for(int i=0;i<s.size();i++) {
        if(s[i] != p[i] && p[i] != '*')
            return false;
            
        
    }
}
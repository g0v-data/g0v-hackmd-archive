# 考題一： 字串「 . 」比對
函數給定 2 個字串 ，一個由英文字母組成的 S 和另一個為英文字母外加 1 個「 . 」組成的 P，
請實作一個函式去判斷 S 是否匹配 P，其中，「 . 」字元代表任意 a-z 字元。
Example:
s = abc, p = a.c, return True
s = abc, p = ac. ,return False

abcd a.c -> False


Hi
clarify:
    1. 2 inputs: string S, string P
    2. only one '.' 
    3. same lenth -> if lenth is not the same -> false
    
thoughts:
 2 pointer -> one for S, one for P
 Time complexityO(N)
 Space complexity:O(1)
 
 Implementation:
     bool IsMatched(string S, string P){
        if(static_cast<int>(S.size()) != static_cast<int>(P.size()) return false;
        for(int i = 0; i < static_cast<int>(S.size()); i++){
             if(P[i] == '.') continue;
             if(S[i] != P[i]) return false
        }
        return true;
     }
    
    
    
dry run:
    s = abc, p = a.c, return True
    same lenth:
    s = abc, p = a.c
    i:     ^        ^
    
    

    
考題二： 字串「 * 」比對
函數給定 2 個字串 ，一個由英文字母組成的 S 和另一個為英文字母外加 1 個「 *」組成的 P，
請實作一個函式去判斷 S 是否匹配 P，其中，「  *  」字元代表重複前字元0次到任意N次。


Example:
s = aac, ac, aaaaac, p = a*c, return True
s = abc, p = a*c ,return False

Implement here:
aaaaaacd, a*cd
 ^        ^

    3 ways:
    if(p[ptr] == *):
    1. s move, p move -> * == 'prev * 1'
    2. s stop, p move -> * == ''
    3. s move, p stop-> * == 'prev' -> *n
    else{
        
        cd, cde
        
        return false or true
    }
    
    
    bool backtracking(const string& S, const string& P, s_ptr, p_ptr){
        if(P[p_ptr] == '*'){
            char prev_p = P[p_ptr-1];
            if(S[s_ptr] == prev_p){
                if(backtracking(S, P, s_ptr+1, p_ptr+1)) return true;
                if(backtracking(S, P, s_ptr+1, p_ptr)) return true;
            }
            else{
                if(backtracking(S, P, s_ptr, p_ptr+1)) return true;
            }
        }
        else{
            
        }
    }
    
    
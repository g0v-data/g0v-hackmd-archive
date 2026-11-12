# 字串「 * 」比對
函數給定 2 個字串 ，一個由英文字母組成的 S 和另一個為英文字母外加 1 個「 *」組成的 P，
請實作一個函式去判斷 S 是否匹配 P，其中，「  *  」字元代表重複前字元0次到任意N次。


Example:
s = ac, p = a*c, return True
s = aac, p = a*c, return True
s = aaaaaaac, p = a*c, return True
s = abc, p = a*c ,return False


     ^
s = acb
      ^ 
p = a*cb

s.size() = 2
p.size() = 3
cur_s = 2
cur_p = 2

bool compare(std::string s, std::string p) {
    int cur_s = 0;
    int cur_p = 0;
    
    while (cur_s < s.size() && cur_p < p.size()) {
        if (s[cur_s] != p[cur_p]) {
            if (p[cur_p] != '*') {
                return false;
                
            }
            if (s[cur_s] == p[cur_p-1]) {
                cur_s++;
                cur_p++;
                continue;
            }
            if (cur_p == p.size()-1) {
                return false;
            }
            cur_p++;
            if (s[cur_s] != p[cur_p]) {
                return false;
            }
        }
        cur_s++;
        cur_p++;
    }
    return cur_s == s.size() && cur_p == p.size();
}
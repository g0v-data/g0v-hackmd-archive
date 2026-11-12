# 字串「 * 」比對
函數給定 2 個字串 ，一個由英文字母組成的 S 和另一個為英文字母外加 1 個「 *」組成的 P，
請實作一個函式去判斷 S 是否匹配 P，其中，「  *  」字元代表重複前字元0次到任意N次。


Example:
s = ac, p = a*c, return True
s = aac, p = a*c, return True
s = aaaaaaac, p = a*c, return True
s = abc, p = a*c ,return False


s = aabaaaac -> a*ba*c =? p

O(n)

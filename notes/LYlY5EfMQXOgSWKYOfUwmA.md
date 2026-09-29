# CTF 題目
以下是密碼檢查執行檔的原始碼，請找出方法只靠執行就能找出真實的密碼。

#include <iostream>
#include <fstream>
#include <string>

int main(int argc, char *argv[]) {
    if (argc != 2) {
        std::cerr << "Usage: " << argv[0] << " <password>" << std::endl;
        return 1;
    }

    std::ifstream file("/tmp/mypassword");

    if (!file.is_open()) {
        std::cerr << "Unable to open mypassword file." << std::endl;
        return 1;
    }

    std::string storedPassword;
    if (std::getline(file, storedPassword)) {
        size_t i = 0;
        while (i < storedPassword.length() && i < strlen(argv[1])) {
            if (storedPassword[i] != argv[1][i]) {
                std::cout << "Password mismatched!" << std::endl;
                file.close();
                return 0;
            }
            ++i;
        }
        std::cout << "Password matched!" << std::endl;
        
    } else {
        std::cerr << "Unable to read password from the file." << std::endl;
    }

    file.close();

    return 0;
}

考題一： 字串「 . 」比對
函數給定 2 個字串 ，一個由英文字母組成的 S 和另一個為英文字母外加 1 個「 . 」組成的 P，
請實作一個函式去判斷 S 是否匹配 P，其中，「 . 」字元代表任意 a-z 字元。
Example:
s = abc, p = a.c, return True
s = abc, p = ac. ,return False
Implement here:
s=aczz  p=ac.
    if len(s) != len(p):
        return False
    
    int i = 0
    
    while i < len(s) && i < len(p):
        if p[i] == ".":
            i += 1 
            continue
        
        if s[i] != p[i]:
            return False
    
        i += 1 
    
    return True


考題二： 字串「 * 」比對
函數給定 2 個字串 ，一個由英文字母組成的 S 和另一個為英文字母外加 1 個「 *」組成的 P，
請實作一個函式去判斷 S 是否匹配 P，其中，「  *  」字元代表重複前字元0次到任意N次。


Example:
s = aac, p = a*c, return True
s = abc, p = a*c ,return False
aac aaaac ac
Implement here:
    
    
# CTF 題目
以下是密碼檢查執行檔的原始碼，請找出方法只靠執行找出真實的密碼。

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


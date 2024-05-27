VScode 配置 c_cpp_properties.json
---

如果你的 C++ 編譯器路徑不在系統 PATH 環境變量中，請配置 c_cpp_properties.json。

先打開剛剛的sfml.cpp
```
```code sfml.cpp


打開 VS Code 中的命令面板（快捷鍵 Ctrl + Shift + P），輸入 C/C++: Edit Configurations。




在打開的 c_cpp_properties.json 文件中，添加或修改編譯器路徑配置項 compilerPath 和 includePath，指向你 C++ 編譯器和 SFML 頭文件的路徑。


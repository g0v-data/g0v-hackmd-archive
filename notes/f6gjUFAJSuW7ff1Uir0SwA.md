VScode 配置 c_cpp_properties.json
---

如果你的 C++ 編譯器路徑不在系統 PATH 環境變量中，請配置 c_cpp_properties.json。在打開的 c_cpp_properties.json 文件中，添加或修改編譯器路徑配置項 compilerPath 和 includePath，指向你 C++ 編譯器和 SFML 頭文件的路徑。

##### 在VScode中打開資料夾
```
code <目標資料夾>
```
##### 打開 VS Code 中的命令面板，輸入 C/C++: Edit Configurations。

###### 快捷鍵: `Ctrl + Shift + P` 或 `Cmd + Shift + P`

###### 點擊  C/C++: Edit Configurations(JSON)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_afece8b27495cc722e51918ab0ed1443.png)

##### 在c_cpp_properties.json 輸入include 路徑
###### 記得在"/opt/homebrew/.../"之前加上逗號
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_20f209e96b9c51a9646af3637263dc38.png)

##### 重新加載窗口：

###### 有時 VS Code 需要重新加載才能讀取配置變更。你可以打開命令面板（Cmd+Shift+P），然後輸入 "Reload Window" 命令來重新加載 VS Code 窗口。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_120dc7216488d323642f80fb2867c5c6.png)


##### 存檔離開
###### 若路徑沒有紅色底線，成功配置，存檔離開
###### 存檔快捷鍵： `Cmd + S`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b892e00d20be138798229f7f5a092a0b.png)












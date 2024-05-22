＃Coding規範


1. 變數命名由型別縮寫當開頭  
   - Ex: Stirng sName, int iIndex, List<String> accountList
  enum於末端加上type     Ex: enum LoginType{}, enum GameType{}

2. DataClass/Model命名分三種
      - requestData _Ex: LoginRequestData      
      - responseData _Ex: LoginResponseData 
      - 自定義Data _Ex: 可能是依情況整理過的Data 

3. 各Function()定義出private public 

4. 自認為較複雜流程時，盡量加上註解
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_110f5350c706c5f2998d9d0ebc3d4652.png)


5. 宣告變數的後面都加上註解，API的responseData欄位也加上註解(同文件上的欄位說明)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_27664fbc1f2633f2c769b4a04f061acd.png)


6. code自動格式化的字數設為105 
   - 設定路徑為 Settings > Editor > Code Style > Dart

7. Coding Style：
   - 括號以巢狀對稱分層 (開頭在同一行結尾也在同一行)
   - 該空一格的地方要空格 Ex: if () {} 或 onPressed: () {}
   - 使用Auto Format前，要將
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7c8acdbd5aa49c2a3301b10931d346cd.png)

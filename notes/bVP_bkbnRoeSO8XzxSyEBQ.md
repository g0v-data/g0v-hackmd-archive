# Complier Design

## 02/26
1. **Lexical analysis** : 辨別單一character轉換成string or token

    對token的分析會先知道是variable、function、type哪一個，在下一階段知道variable是哪個型態(eg:int)
    
3. **Semantic analysis** : (狹義)型態檢查

e.g.
```clike=
int n = 60;
double n1 = 30;
printf(n*n1);
```
以上在做乘法的時候compiler會直接將n轉換成double，在計算出結果。

3. **Syntax analysis** : 

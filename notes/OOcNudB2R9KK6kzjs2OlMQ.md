**正則表達式處理字符串**

```
public class RegExp { 
   public static void main( String[] args ) {
      String firstString = "123Af4567890";
      // 請利用regular expression的方法，將firstString中
      // 兩個英文字母接著三個digits的部分以"XXXXX"替代 
      // 例如 : 應該列印 "123XXXXX7890"
       
      firstString = firstString.replaceAll("[a-zA-Z]{2}\\d{3}", "XXXXX");
      System.out.println(firstString); // 應該輸出 "123XXXXX7890"
       
      firstString = "12 34567   890";
      // 請利用regular expression的方法，將firstString中
      // 所有連續的一個或多個的 white-space characters 以"X"替代 
      // 例如 : 應該列印 "12X34567X890"
       
      firstString = firstString.replaceAll("\\s+", "X");
      System.out.println(firstString); // 應該輸出 "12X34567X890"
       
      firstString = "123 one 456 two three";
      // 請利用regular expression的方法，將firstString中
      // 所有的英文 word 都以 “XXX"替代 
      // 例如 : 應該列印 "123 XXX 456 XXX XXX”
       
      firstString = firstString.replaceAll("[a-zA-Z]+", "XXX");
      System.out.println(firstString); // 應該輸出 "123 XXX 456 XXX XXX"
   } 
}
```
**Answer**
```
package quiz3_b;

public class RegExp {

    public static void main(String[] args) {

        // Replace two letters followed by three digits with "XXXXX"
        //匹配兩個英文字母 接著三個數字的模式
        String firstString = "123Af4567890";
        String result = firstString.replaceAll("[a-zA-Z]{2}\\d{3}", "XXXXX");
        System.out.println(result);

        // Replace consecutive whitespace characters with "X"
        // \\s+ 匹配連續的一個或多個空格字符
        firstString = "12 34567   890";
        result = firstString.replaceAll("\\s+", "X");
        System.out.println(result);

        // Replace all English words with "XXX"
        // [a-zA-Z]+ 
        firstString = "123 one 456 two three";
        result = firstString.replaceAll("[a-zA-Z]+", "XXX");
        System.out.println(result);
    }
}
```

正則表達式筆記
1.反斜線 \\
反斜線是用來轉義特殊字符的，例如：\\\d 表示數字，\\\s 表示空白字符。

2.字符類 [ ]
方括號內的任意字符都會匹配，例如：[a-zA-Z] 匹配任何英文字母。

3.量詞 { }
指定匹配的次數，例如：{2} 表示匹配兩次，{3} 表示匹配三次。

4.量詞 +
+ 表示匹配1次或多次，等價於 {1,}。

5.邊界符號 \\\b
\\\b 匹配單詞邊界（單詞的開始或結束）。

6.replaceAll("", "") 方法
replaceAll 方法用來替換符合正則表達式的部分。



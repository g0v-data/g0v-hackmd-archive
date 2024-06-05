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


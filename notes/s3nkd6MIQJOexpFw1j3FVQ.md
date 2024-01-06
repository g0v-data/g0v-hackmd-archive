# Java基礎練習-日期、數值、讀寫檔

介紹一些基礎計算用的
有些雖然有底層可以用先學JAVA原生的，再看底層的

項目
- [日期](#日期)
  - [1-1] 範例 - Date
  - [1-2] 範例 - Calendar
  - [1-3] 範例 - 日期格式 SimpleDateFormat
  - [1-4] 範例 - 底層套件DATE (Date大小寫有差)
  - [1-5] 練習題 - 讓使用者輸入三個數字，組成日期判斷日期格式
  - [1-6] 練習題 - 同上只解析日期格式，轉字串後用底層判斷

- [數值運算](#數值運算)
  - [2-1] 範例- Math 絕對值和平方根
  - [2-2] 範例- Random 隨機整數和浮點數
  - [2-3] 練習題 - 產生0~100分，把60分不到的踢出去
  - [2-4] 範例 - bigdecimal 加減乘除
  - [2-5] 範例 - bigdecimal 四捨五入和精確位數
  - [2-6] 練習題 - bigdecimal 賣商品
  - [2-7] 練習題 - bigdecimal 匯率統一成台幣比大小

- [檔案處理](#檔案處理)
  - [3-1] 範例 - 讀檔 FileReader
  - [3-2] 範例 - 讀檔 FileReader  切割=的內容 line.split("=");
  - [3-3] 範例 - 寫檔 FileWriter 
  - [3-4] 練習題 - 將3-1 算出平均值後放到最後一行
  - [3-5] 練習題 - 賣出結果寫檔，將2-6的賣出明細寫成檔案



# 日期

## 1-1 範例 - DATE
```java 
    public static void main(String[] args) {
        Date currentDate = new ___ ();//完成他
        System.out.println("當前日期和時間：" + currentDate);
    }

```

## 1-2 範例 - Calendar

```java 
    public static void main(String[] args) {
        Calendar calendar = Calendar.getInstance();
        int year = calendar.get(Calendar.);
        int month = calendar.get(Calendar.) + 1; // 月份從 0 開始，所以需要加 1
        int day = calendar.get(Calendar.);
        int hour = calendar.get(Calendar.);
        int minute = calendar.get(Calendar.);
        int second = calendar.get(Calendar.);//完成各.後面

        System.out.println("年：" + year);
        System.out.println("月：" + month);
        System.out.println("日：" + day);
        System.out.println("時：" + hour);
        System.out.println("分：" + minute);
        System.out.println("秒：" + second);
    }

```
## 1-3 範例 - 日期格式 SimpleDateFormat
```java 

 		 String inputDate = "2023/07/22";
		   // 將 "2023/07/22" 轉換成 "2023-07-22" 的格式
		 SimpleDateFormat inputFormat = new SimpleDateFormat("yyyy/MM/dd");
        SimpleDateFormat outputFormatObj = new SimpleDateFormat("yyyy-MM-dd");
        
        
        //解析日期： 使用 parse 方法將字串解析成輸入日期物件
        //因又可能解析錯誤 (來源輸入不是日期 要拋出錯誤)
        Date date = inputFormat.
        inputDate = outputFormatObj.format( ) ;//把解析後的放入想要格式
        System.out.println("Formatted Date (yyyy-MM-dd): " + inputDate);
        
        //給日期格式 日 時分秒
            SimpleDateFormat outputFormatOb2j = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        inputDate = outputFormatOb2j.format();
        System.out.println("Formatted2 Date (yyyy-MM-dd): " + inputDate);
    }
```

## 1-4 範例 - 底層套件DATE (Date大小寫有差)
有很多 簡單練習即可，很容易忘記每次要用.看一下就可以了
```java 
		 DATE.getDBDate();
		 DATE.toY2KDate( ) //民國年轉西元年
		 DATE.diffDay(, ) //相差幾天

```

## 1-5 練習題 - 讓使用者輸入三個數字，組成日期判斷日期格式
```java 
//使用者輸入
Scanner scanner = new Scanner(System.in);

//組成STRING
	String str_date =year +"-" + month + "-" + date;
    
    //使用SimpleDateFormat 的parse解析來判斷是否為日期格式

```


## 1-6 練習題 - 同上只解析日期格式，轉字串後用底層判斷
承接上提放在後面
```java 
         Date a = 使用SimpleDateFormat parse
		 String result_date = inputFormat.format();//完成他 轉字串
		 DATE.isDate //底層isDate需要字串

```

# 數值運算
原生常用的是Math跟Random
另外還有處理數值的bigdecimal

## 2-1 範例- Math 絕對值和平方根

```java 
    public static void main(String[] args) {

        int num = -10;
        int absValue = Math.abs();//完成他
        System.out.println("絕對值：" + absValue);
        
        int number = 16;
         squareRoot = Math.sqrt();//完成他
        System.out.println("平方根：" + squareRoot);
    }
```


## 2-2 範例- Random 隨機整數和浮點數


```java 
    public static void main(String[] args) {
       Random random = new Random();

        // 定義範圍
        int min = 0;
        int max = 100;

        // 產生隨機整數，範圍從 min 到 max（包含 min 和 max）
        int randomNumber = random.nextInt(max);
        System.out.println("隨機整數：" + randomNumber);
        
        
        // 產生隨機小數，範圍從 0.0 到 1.0（不包含 10.0）
        double randomDecimal = Math.random();
        System.out.println("隨機小數：" + randomDecimal);

        // 定義範圍
        double min = 1.0;
        double max = 10.0;

        // 產生隨機小數，範圍從 min 到 max（不包含 max）
        double randomNumber = min + randomDecimal * (max - min);
        System.out.println("範圍隨機小數：" + randomNumber);
    }
```


## 2-3 習題 - 產生0~100分，把60分不到的踢出去

```java 
    //可以先印出全部 不管偶數 偶數要想想某個條件
    public static void main(String[] args) {
            //使用2-2產出三個數字
            
            //依序放入MAP "OO" : 分數1 "IVY" : 分數2 "DORIS" : 分數3
            
            // MapUtils 取值
            // 假設DORIS一定不及格，分數3如果>= 60使用WHILE迴圈 產出一個< 60的數字 重新放入MAP
            
            // 判斷整個MAP被踢出去的人有誰
        }
    }

```

## 2-4 範例 - bigdecimal 加減乘除

```java 
    //同上 但要想一下FOR迴圈
    public static void main(String[] args) {
        BigDecimal num1 = new BigDecimal("10.25");
        BigDecimal num2 = new BigDecimal("5.75");

        BigDecimal sum = num1.add(num2);
        System.out.println("加法結果：" + sum);

        BigDecimal difference = num1.subtract(num2);
        System.out.println("減法結果：" + difference);
        
        BigDecimal product = num1.multiply(num2);
        System.out.println("乘法結果：" + product);
        
        BigDecimal quotient = num1.divide(num2);
        System.out.println("除法結果：" + quotient);
        
        // divide可以多給一個參數 決定四捨五入的方法
        
        RoundingMode 0  1 2 3分別代表不同模式
        
        搞不清楚的話就自己寫
        // 設定精確位數為2位，並使用四捨五入舍入模式
        result = result.setScale(2, RoundingMode.HALF_UP);
    }

```


## 2-5 範例 - bigdecimal 四捨五入和精確位數

```java 
    public static void main(String[] args) {
    //RoundingMode BigDecimal .按下去常用的有四捨五入 無條件捨去/進入
        BigDecimal num1 = new BigDecimal("10.25678");
        BigDecimal num2 = new BigDecimal("5.75");

        // 設定精確位數為2位，並使用四捨五入舍入模式
        BigDecimal result1 = num1.setScale(2, RoundingMode.);
        BigDecimal result2 = num2.setScale(2, RoundingMode.);

        System.out.println("num1 精確位數：" + result1);
        System.out.println("num2 精確位數：" + result2);
        
         // 使用除法時，需要指定除法的精確位數和舍入模式
        BigDecimal quotient = num1.divide(num2, 2, BigDecimal.);

    }

```


## 2-6 練習題 - bigdecimal 賣商品

```java 
    public static void main(String[] args) {
      List<BigDecimal> prices = new ArrayList<>();
        prices.add(new BigDecimal("9.99"));
        prices.add(new BigDecimal("19.25"));
        prices.add(new BigDecimal("14.50"));
        
        //讓使用者輸入購買數量a b c
        
        //先直接呈現加總  a*第一個商品 + b*第二個商品 +c*第三個商品
        
        //客戶優待 小數去掉 分別將 a*第一個商品 b*第二個商品 c*第三個商品 去掉
        //EX a=4 b=3 去掉小數 c=2 因為是00不動
        
        
    }

```

## 2-7 練習題 - bigdecimal 匯率統一成台幣比大小

```java 
    public static void main(String[] args) {
        Map<String, BigDecimal>
        //裡面有USD 31.34  RMB4.36 日圓JPY 0.22
        
        //讓兩個USER輸入幣別+金額 
        //印出 USER A 擁有 __幣 __ 元
        
        // BigDecimal轉換成台幣 取小數第三位
         //印出 USER A 擁有 __幣 __ 元，等同台幣amt1元
         //印出 USER B 擁有 __幣 __ 元，等同台幣amt2元
         
         
         //比大小
         //amt1.compareTo(amt2)
         //較大的人印出 如果B大
         //印出 USER B 擁有 __幣 __ 元，等同台幣__元 比較大
           
        
    }

```

# 檔案處理
檔案處理 通常會拋 IOException 

## 3-1  範例 - 讀檔 FileReader
將以下的檔案存成txt
```java 
10.5
20.7
15.2
8.9
```
以下練習路徑要自己放對 請注意用 \\
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_108bc407bb972a32c7d7a20573ed8bc9.png)

```java 
    public static void main(String[] args) {
       String filePath = ""; //完成他
        FileReader fileReader = new FileReader(filePath);
        BufferedReader bufferedReader = new BufferedReader(fileReader); //readLine處理一行一行字串

            String line;
            while ((line = bufferedReader.readLine()) != null) {
                BigDecimal number = new BigDecimal(line);
                System.out.println(number);
            }
            try {
                if (bufferedReader != null) { //一定要關掉 很重要 
                    bufferedReader.close();
                }
            } catch (IOException e) {
                e.printStackTrace();
            } 
    }
    
    先會讀後在while前面先NEW一個bigdecimal SUM 等等把四個數字加起來
    }

```



## 3-2 範例 - 讀檔 FileReader  切割=的內容 line.split("=");

將以下的檔案存成txt
```java 
name=OO
age=30
salary=50000.00
```


```java 
    public static void main(String[] args) {
    
        放造前面3-1 先能讀出來
        
         //在while迴圈 使用等號 "=" 將每一行拆分為 key 和 value
         //String[] keyValue = line.split("=");
         //將keyValue 存成一個MAP印出
    }

```

## 3-3 範例 - 寫檔 FileWriter 

```java 
    public static void main(String[] args) {
    //檔案路徑使用3-2 最後多寫一行
    //檔案路徑可以給另一個路徑(會寫新的檔案)
        FileWriter fileWriter = new FileWriter(filePath, true); // 使用 true 表示附加到檔案末尾
        BufferedWriter bufferedWriter = new BufferedWriter(fileWriter) ;
       
        bufferedWriter.newLine();//換行
                bufferedWriter.write("身高為: " + 168);
        
        
         bufferedWriter.close();//一樣要記得
    }

```


## 3-4 練習題 - 將3-1 算出平均值後放到最後一行

```java 
    //
    public static void main(String[] args) {
      //SUM會友總和 //WHILE中間要有一個計數器 才知道有幾個數字
      //最後只是把SUM/計數器後呼叫 new FileWriter(filePath, true);
       
        
    }

```

## 3-5 練習題 - 賣出結果寫檔，將2-6的賣出明細寫成檔案

```java 
    public static void main(String[] args) {
       //先能印出來
       //SYSTEM OUT 可以顯示 商品a 單價:XXX 賣出 O個 
       //SYSTEM OUT 可以顯示 商品b 單價:XXX 賣出 O個 
       //SYSTEM OUT 可以顯示 商品c 單價:XXX 賣出 O個 
       //SYSTEM OUT 可以顯示 賣出總和是
       
       //如果能做到以上
       //只是在印出的時候 呼叫   bufferedWriter.write 
       
        
    }

```

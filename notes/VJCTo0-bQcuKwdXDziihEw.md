# Java基礎練習-數值和

其實想先介紹CLASS(類別)和OBJECT(物件)
但怕大家不熟悉 先介紹字串

項目
- [長度](#長度)
  - [1-1] 範例 - 字串長度
  - [1-2] 練習題 - 使用Scanner 後取得長度

- [子字串](#子字串)
  - [2-1] 範例-取得第n個
  - [2-2] 範例-取得第3~6個
  - [2-3] 練習題 - 練習題取得偶數字串
  - [2-4] 練習題 - 將hello world 轉成 dlrow olleh

- [切割字串](#切割字串)
  - [3-1] 範例 - 切割字串
  - [3-2] 練習題 - 人名切割

- [檢索字串](#檢索字串)
  - [4-1] 範例-開頭和結尾
  - [4-2] 範例-是否包含某字串
  - [4-3] 範例-字串的index
  - [4-4] 練習題 - 判斷姓名是否有AEIOU
  - [4-5] 練習題 - 包含練習 判斷a~z是否包含在火山矽肺
  - [4-6] 練習題 - for迴圈 找到火山矽肺包含幾個s
  - [4-7] 練習題 - 火山矽肺的s坐落在哪些index

- [字串取代](#字串取代)
  - [5-1] 範例 - 字串取代 
  - [5-2] 練習題 - 活用2-3 4-3 將hello world取代

- [字串CLASS和物件](#字串CLASS和物件)


# 長度
取得字串長度length

## 1-1 範例 - 字串長度
```java 
    public static void main(String[] args) {
        String name = "OO";
        int length = name._____; // 填空處
        System.out.println("字串長度為：" + length);
    }

```

## 1-2 練習題 - 使用Scanner 後取得長度
練習題 使用Scanner


```java 
    public static void main(String[] args) {
        //使用使用Scanner
        System.out.print("請輸入一個字串：");
        String input = scanner.nextLine();
        
        int length = input._____; // 填空處
        System.out.println("字串長度為：" + length);
    }

```


# 子字串
charAt 取得字元
和 substr 取得子字串
## 2-1 範例-取得第n個

```java 
    public static void main(String[] args) {

        String str = "abcdefghij";
        char charAtIndex3 = str.charAt(2);
        System.out.println("第3個字元為：" + charAtIndex3);
    }
```


## 2-2 範例-取得第3~6個


```java 
    public static void main(String[] args) {
        String str = "abcdefghij";
        String substring = str._____; // 填空處
        System.out.println("第3到第6個字元為：" + substring);
    }
```



## 2-3 練習題 - 練習題取得偶數字串

```java 
    //可以先印出全部 不管偶數 偶數要想想某個條件
    public static void main(String[] args) {
        String str = "abcdefghij";
        for (int ____ ; ___ < _____ ; i++) { //用1-1
            char c = ___ //用2-1
            System.out.print(c);
        }
    }

```

## 2-4 練習題 - 將hello world 轉成 dlrow olleh

```java 
    //同上 但要想一下FOR迴圈
    public static void main(String[] args) {
        String str = "hello world";
        for (int ____ ; ___ < _____ ; ___) { //用1-1
            char c = ___ //用2-1
            System.out.print(c);
        }
    }

```

# 切割字串
split 可用來切割字串 並用 String [] 來接
記住 String []無法直接印出來 要用for迴圈
兩個方法都可以印

## 3-1 範例-切割字串

```java 
    public static void main(String[] args) {
        String sentence = "Hello, World! This is a sentence.";
        String[] words = sentence._____; // 填空處
        
        for (String word : words) {
            System.out.println(word);
        }
        for (int i = 0; i < words.length; i++) {
            System.out.println(words[i]);
        }
    }

```

## 3-2 練習題 -人名切割

```java 
    //同上 但要想一下FOR迴圈
    public static void main(String[] args) {
        String namesString = "OO,IVY,DORIS,AUTHER,MACHI";
         // 切割字串

        // 逐行印出每個人名
        
    }

```

# 檢索字串
str.startsWith
str.endsWith
str.contains
三個都回傳True False
str.indexOf
回傳整數 沒找到是-1
## 4-1 範例-開頭和結尾 (是否h開頭，是否o結尾)

```java 
    public static void main(String[] args) {

        String str = "hello";
        str.startsWith // 完成他
        str.endsWith// 完成他

    }
```


## 4-2 範例-是否包含某字串 (包含xyz和包含ll)


```java 
    public static void main(String[] args) {
        String str = "hello";
        str.contains  // 完成他
        str.contains  // 完成他
    }
```

## 4-3 範例-字串的index 找到o在第幾個


```java 
    public static void main(String[] args) {
	    String str2 = "yes yes yes  ok ok ok ok";

		int index2 = str2. // 完成他
		System.out.println(index2);
        //找到第15個字串以後有O的
        int index3 = str2. // 完成他
		System.out.println(index3);
    }
```


## 4-4 練習題 - 判斷姓名是否有AEIOU

```java 
    //使用練習3-2
    public static void main(String[] args) {
        String namesString = "OO,IVY,DORIS,AUTHER,MACHI";
        String[] english = {"A","E","I","O","U"};
         // 切割字串namesString

        // FOR逐行印出每個人名 印出
        
        //再用FOR迴圈滾english 將牠放入contains
    }

```

## 4-5 練習題 - 火山矽肺包含幾個a~z有哪些

```java 
    //同上 但要想一下FOR迴圈
    public static void main(String[] args) {
        String str = "pneumonoultramicroscopicsilicovolcanoconiosis";
        
        //這樣可以印出 a~z
        for (char tmp = 'a'; tmp <= 'z'; tmp++) {
            System.out.print(tmp + " ");
            
            印出 
            a: true
            b: false
            ...
            z: false
        }

        
    }

```
## 4-6 練習題 - for迴圈 找到火山矽肺包含幾個s
```java 
    //同上 但要想一下FOR迴圈
    public static void main(String[] args) {
        String str = "pneumonoultramicroscopicsilicovolcanoconiosis";
        
        int count = 0;
	    for (int i = 0 ; i < str2.___ ; i++) { // 完成他活用前面教的某個
            //substring 可以依序拿出 p n e ...
	        String tmp = str2.substring(i, i+1);
	        System.out.println(tmp);
            if  (tmp.包含S ){//完成他
                count = count _____  //完成他
            }
               
	    }
         System.out.println(count);
        
    }

```
## 4-7 練習題 - 火山矽肺的s坐落在哪些index
```java 
//如果是用前面的4-6 可以印出來index
    public static void main(String[] args) {
        String str = "pneumonoultramicroscopicsilicovolcanoconiosis";
   
	    for (int i = 0 ; i < str2.___ ; i++) { // 完成他活用前面教的某個
            System.out.println(某個東西);//完成他
               
	    }

        
    }
    //如果不要用FOR迴圈 (因為有點呆 改用indexof 
    
    public static void main(String[] args) {
     	String str2 = "pneumonoultramicroscopicsilicovolcanoconiosis";
		char ch = 's';

		int index = str2.indexOf(___);
		while (index != ___) { 
			System.out.println(index);//完成他
			index = str2.indexOf(ch, index + 1); 
		}
    }

```




# 字串取代
replace 可用來取代字串 

## 5-1 範例-字串取代 

```java 
        //將hello world 變hellx wxrld 
        //將hello world 變成 hEllo world
    public static void main(String[] args) {
        String input = "Hello, World!";
        char oldChar = 'o';
        char newChar = 'x';
        String replaced = input._____; // 填空處
        System.out.println("替換後的字串為：" + replaced);
        
        String input = "Hello, World!";
          // 填空處
        String replaced = input._____; // 填空處
        System.out.println("替換後的字串為：" + replaced);
    }

```

## 5-2 練習題 - 活用2-3 4-3 將HELLO, WORLD取代

```java 
    //Hello World! 取出偶數個
    //如果包含AEIOU取代成X 答案應該變成HXLLO WORLD!
    public static void main(String[] args) {
        String input = "HELLO, WORLD!";
        String[] english = {"A","E","I","O","U"};
         //for迴圈取得input偶數字元
         
         // for迴圈 english 是否== 取得的字元

        // 如果包含使用replace
        
    }
```

# 字串CLASS和物件

回到CLASS 和物件
String 是 CLASS
str str2 是物件

```java 
    //要知道NEW模組的概念 其實跟NEW STRING一樣
    public static void main(String[] args) {
        String str = new String();  // 使用預設的空字串建構子
		str ="WEI";
        
        //常用方法
        String str2 = "WEI";
        
        //因為Java"編譯器"對字串進行了特殊處理
        
    }
```
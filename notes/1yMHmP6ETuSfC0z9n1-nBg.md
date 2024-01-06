# Java基礎練習-HashMap

介紹最常用的Map的
會先從最基本的Map操作講起
然後公司規定一定要使用MapUtils對Map作取值得動作

項目
- [添加鍵值對 和取值](#添加和取值)
  - [1-1] 範例 - 添加鍵(KEY)值(VALUE)
  - [1-2] 練習題 - 使用迴圈取值把不及格的人挑出來

- [長度和為空](#長度和為空)
  - [2-1] 範例-長度
  - [2-2] 範例-為空
  - [2-3] 練習題 - 輸入姓名跟年紀後判斷是否為老人

- [Map的型別](#Map的型別)
  - [3-1] 範例 - 有無形別的NEW MAP方式
  - [3-2] 範例 - 有無形別取值的問題
  - [3-3] 練習題 - 讓取值繼續進行 期末+10判斷不及格

- [取出MAP所有的KEY然後取得VALUE](#取出MAP所有的KEY然後取得VALUE)
  - [4-1] 範例-KeySet取出KEY 然後取出VALUE
  - [4-2] 範例-題外話 字串== 和 equals的差別 總之記住用equals
  - [4-3] 練習題 - KEY值是否等於某值 使用.equals 不要用==(順便知道remove)


- [MapUtils](#MapUtils)
  - [5-1] 範例 - MapUtils取得物件
  - [5-2] 範例 - MapUtils取得物件 但KEY不是用STRING
  - [5-3] 練習題 - 不同資料型別 將我的常用聯絡人 整理
  - [5-4] 練習題 - 不同資料型別 使用者輸入

- [ VO類似固定EKY的MAP]( #VO類似固定KEY的MAP)


# 添加和取值
Map添加使用put
Map取值使用get (先用get等等練習MapUtils)

## 1-1 範例 - 添加鍵(KEY)值(VALUE)

```java 
    public static void main(String[] args) {
        // 創建HashMap並添加鍵值對
        HashMap<String, Integer> hashMap = new HashMap<>();
        hashMap.put("OO", ___);// 完成他
        hashMap.put("DORIS", ___);
        hashMap.put(___, 59);
        
        // 取值印出
        System.out.println(Map.___("DORIS"))// 完成他
        System.out.println(Map.___("WEI"))
    }

```

## 1-2 練習題 - 使用迴圈取值把不及格的人挑出來
迴圈取得分數 把不及格的印出來

```java 
    public static void main(String[] args) {
        String[] name = {"OO","DORIS","IVY"}; //value 90 / 80 // 59
        //先組出MAP
        
        //使用String練習題4-4的FOR迴圈 先用小於判斷
        for (String s : _____ ){ //不要用傳統的FOR迴圈 i++
            ___  score = Map.___()
            if (score < 60){
                 System.out.println("被排擠出去的人是: " + s );
            }
        
        }
    }

```


# 長度和為空
size 取得長度
和 isEmpty 判斷使否為空
## 2-1 範例-取得長度

```java 
    public static void main(String[] args) {

        HashMap<String, Integer> hashMap = new HashMap<>();
        hashMap.put("OO", ___);
        hashMap.put("DORIS", ___);
        hashMap.put(___, 59);
        System.out.println("hashMap長度為：" + hashMap.);// 完成他
    }
```


## 2-2 範例-判斷使否為空


```java 
    public static void main(String[] args) {
        HashMap<String, Integer> hashMap = new HashMap<>();
        hashMap.put("OO", ___);
        System.out.println("hashMap 是否為空：" + hashMap.);// 完成他
        
        HashMap<String, Integer> hashMap2 = new HashMap<>();
        System.out.println("hashMap2 是否為空：" + hashMap2.);// 完成他
    }
```



## 2-3 練習題 - 輸入姓名跟年紀後判斷是否為老人

```java 
    //可以先印出全部 不管偶數 偶數要想想某個條件
    public static void main(String[] args) {
        //使用scanner
		Scanner scanner = new Scanner(System.in);

		// 創建老人的 Map 和非老人的 Map
		Map elderlyMap 
		Map nonElderlyMap 

		System.out.print("請輸入人名：");
		String name = scanner.next();
		System.out.print("請輸入年紀：");
		int age = scanner.nextInt();

		// 根據年紀將資料放入老人的 Map 或非老人的 Map
		if (  > 65) {
			elderlyMap.put(name, age);
		} else {
			nonElderlyMap.put(name, age);
		}

		// 用size ==0 判斷 誰為空

		// 用isEmpty 判斷誰為空
    }

```

# Map的型別
沒有型別如果前端送的東西確定為某種類型
譬如String Int Boolean 等等 
通常不會錯 編譯只提示你黃燈 
但如果可以還是確定型別 後續比較不會有問題


## 3-1 範例 - 有無形別的NEW MAP方式
看一下hashMap2 題是你的黃色警告

```java 
    public static void main(String[] args) {
        HashMap<String, Integer> hashMap = new HashMap<>();
        HashMap hashMap2 = new HashMap(); //默認為Object
        //也就是 HashMap<Object, Object> hashMap2 = new HashMap<>();
    }

```

## 3-2 練習題 -有無形別取值的問題

```java 
    //跑看看 拿到錯誤的狀況
    public static void main(String[] args) {
        HashMap<String, Integer> hashMap = new HashMap<>();
        hashMap.put("AA", 111);
        hashMap.put("BB", 111);
        hashMap.put("CC", 111);
        
        HashMap hashMap2 = new HashMap(); //默認為Object
        hashMap2.put("DD", 30);
        hashMap2.put("EE", ___); //放Boolean
        hashMap2.put("FF", __); // 放字串
        
        int a = hashMap.get("AA");
        int b = hashMap.get("BB");
        int c = hashMap.get("CC");
        int d = hashMap2.get("DD"); //先強轉讓他可以跑
        int e = hashMap2.get("EE"); //先強轉讓他可以跑
        int f = hashMap2.get("FF");  //先強轉讓他可以跑
        
    }

```

## 3-3 練習題 - 讓取值繼續進行 分數+10後判斷不及格

```java 
    //數學老師 最會期末每個人加十分
    public static void main(String[] args) {
        String[] name = {"OO","DORIS","IVY","AUTHER"};
        int [] score = {90,80,59,10};
        HashMap  hashMap = new HashMap();
        //先用FOR迴圈放進去 大家的分數
        for (int i = 0; i < name.___; i++) {
        
        
          
        }
        // 強迫放一個 不是數字的
        hashMap.put("WEI", true);
        
        for (int i = 0; i < name.___ ; i++) { 
            int score = 0;
             hashMap.get 
            
      
        
        }
        //額外處理 第五筆 WEI
              //先判斷是否為整數
            if (obj1 instanceof Number) {
                System.out.println("obj1 是數值");
                score = 
                score =  //加十分
            } else {
                System.out.println("obj1 不是數值 設定為0");
                score = 0;
            }
        
            if (score < 60){
                 System.out.println("被排擠出去的人是: " + s );
            }

        
    }

```




# 取出MAP所有的KEY然後取得VALUE
keySet這方法很不值觀 但應用場景仍不少
因為無法知道 前端或上游給你什麼資料 
你不會知道有什麼"KEY" 無法像前面案例在那邊取得人名之後GET VALUE
往往會用keySet這種方式滾資料
基本上String key : hashMap.keySet()都是固定形式
## 4-1 範例-KeySet取出KEY 然後取出VALUE

```java 
    public static void main(String[] args) {
    //先建立練習題1-1MAP
    
    // 滾HashMap並印出所有鍵值對 使用 hashMap.keySet()
        for (Object key : hashMap.keySet()) {
            //可以先印出 KEY (假裝不知道有那些人名)
            
            
            // int value = hashMap.get(key); 取值印出
            //System.out.println(key + " -> " + value);
        }

    }
```


## 4-2 範例-題外話 字串== 和 equals的差別 總之記住用equals
大致的意思是
equals() 方法比較兩個字串的內容是否相等，而 == 運算符比較兩個字串的引用是否相等
簡單來說equals 就是單純比較
== 因為str1 跟str2 指向不同樣的物件 所以給FALSE
但是str1 跟str3 指向同樣的東西 "hello"

而且如果兩個字串要比較
其中一個是已經確定的字串 EX: "hello"要放在前面比較 否則有null pointer可能

```java 
    public static void main(String[] args) {
        String str1 = "hello";
        String str2 = new String("hello");  // 用 new String的方式new出str2
        String str3 = "hello";

        // 使用 equals() 方法比較內容是否相等
        boolean isEqual1 = str1.equals(str2);
        boolean isEqual2 = str1.equals(str3);

        System.out.println("str1.equals(str2) 結果：" + isEqual1);
        System.out.println("str1.equals(str3) 結果：" + isEqual2);

        // 使用 == 運算符比較引用是否相等
        boolean isReferenceEqual1 = (str1 == str2);
        boolean isReferenceEqual2 = (str1 == str3);

        System.out.println("str1 == str2 結果：" + isReferenceEqual1);
        System.out.println("str1 == str3 結果：" + isReferenceEqual2);
        
        
         Map<String, String> map = new HashMap<>();
        map.put("apple", "hello");
        String tmp = map.get("apple");
        tmp.equals("hello") ; //(X)
        "hello".equals(tmp) ; //(O) 因為tmp有可能是null 放前面會錯
    }
```


## 4-3 練習題 - KEY值是否等於某值 使用.equals 不要用== (順便知道remove)


```java 
    public static void main(String[] args) {
        //NEW MAP 裡面放五個人 OO IVY WEI DORIS AUTHER
        //VALUE 分數 隨便
        
        //用KEY SET滾 MAP 
        for (String key : hashMap.keySet()) {
            //如果 == AUTHER 移除他 使用equals
            map.remove("AUTHER"); 
            
            
            //如果 < 60 分 移除他
        }
        
        //印出移除AUTHER和< 60分的人
        
            
        
    }
```

補充
```java 
      Map<String, Integer> map = new HashMap<>();
        map.put("Alice", 25);
        map.put("Bob", 30);
        map.put("Charlie", 28);

        System.out.println("刪除前的 Map：");
        System.out.println(map);

        Iterator<Map.Entry<String, Integer>> iterator = map.entrySet().iterator();
        while (iterator.hasNext()) {
            Map.Entry<String, Integer> entry = iterator.next();
            String key = entry.getKey();
            int value = entry.getValue();

            // 在遍歷時，使用 Iterator 的 remove() 方法移除符合條件的元素
            if (value > 28) {
                iterator.remove();
            }
        }
```


# MapUtils
MapUtils 要引用正確是Apache的套件
org.apache.commons

## 5-1 範例 - MapUtils取得物件

```java 
    public static void main(String[] args) {
        Map<String, Integer> map = new HashMap<>();
        map.put("apple", 10);
	    map.put("banana", 20);
	    map.put("orange", 15);


	   int Value = MapUtils.getIntValue(map, "apple");
	   int defaultValue = MapUtils.getIntValue(map, "apple", -1);
       int Value2 = MapUtils.getIntValue(map, "apple2");
	   int defaultValue2 = MapUtils.getIntValue(map, "apple2",__); ///預設值888
       
       //印出來比較四個值看看
       
       
       //預設值只要符合型別都可以 也就是String 預設值就是STRING 
          Map<String, String> map2 = new HashMap<>();
          //自創一些東西進入MAP
          
          ___ getValue = MapUtils.get___ (map2, "apple", "YA");//完成他
       
       
       

    }

```

## 5-2 範例 - MapUtils取得物件 但KEY不是用STRING

```java 
    public static void main(String[] args) {
       //並非KEY一定要STRING  
        Map<Integer, Boolean> map = new HashMap<>();
	    map.put(33, true);
	    map.put(44, false);
        map.put(55, false);

        Boolean boo = MapUtils.getB_____ //完成他
        
    }
```


## 5-3 練習題 - 不同資料型別 將我的聯絡人 整理常用清單

通訊錄有很多人 整理常用的人加入
```java 
    public static void main(String[] args) {
    
        Map<String, Boolean> DorisFavoList = new HashMap<>();
        
        Map<String, ___ > dataMap = new HashMap<>();// 多種物件 要用哪個
        dataMap.put("name", "OO");
        dataMap.put("age", 25);
        dataMap.put("isFavo", false);
        
        Map<String, ___ > dataMap2 = new HashMap<>();
        dataMap2.put("name", "IVY");
        dataMap2.put("age", 26);
        dataMap2.put("isFavo", false);
        
        
        Map<String, ___ > dataMap3 = new HashMap<>();
        dataMap3.put("name", "WEI");
        dataMap3.put("age", 34);
        dataMap3.put("isFavo", false);
        
        Map<String, ___ > dataMap4 = new HashMap<>();
        dataMap4.put("name", "AUTHER");
        dataMap4.put("age", 50);
        dataMap4.put("isFavo", true);

        //依序GET DATAMAP1~4的所有值 如果判斷isFavo 為TRUE 放入DorisFavoList
        //最後 印出Doris的FavoList 和對應dataMap資訊
        // 常用聯絡人是: 年齡是: 
        
    }
```

## 5-4 練習題 - 不同資料型別 使用者輸入
```java 
  //使用scanner
		Scanner scanner = new Scanner(System.in);
        //輸入 姓名 (STRING) 年齡(INT) 是否結婚(Boolean)
        // 體重(Double) 地址(String) 放入dataMap
        


     Map<String, Object> dataMap = new HashMap<>();
        dataMap.put("name",);
        dataMap.put("age",);
        dataMap.put("isMarried", );
        dataMap.put("weight", );
        dataMap.put("address", );
        
        //如果NAME輸入為空 程式直接跳錯 姓名不可為空
        //其餘照舊
        //地址為空時 補上預設值 陽光街888號
        //印出dataMap
```
        

# VO類似固定KEY的MAP
Map幾乎是最常用的物件了
因為KEY VALUE的方式太方便
基本上熟悉的話 各位不熟的VO BO 就可以想像成
"固定KEY"的MAP了

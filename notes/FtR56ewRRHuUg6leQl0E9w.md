# Java基礎練習-陣列和List(列表)



項目
- [陣列](#陣列)
  - [1-1] 範例 - 陣列宣告
  - [1-2] 範例 - 陣列取值
  - [1-3] 範例 - 二維陣列
  - [1-4] 練習題 - 買東西算總和
  - [1-5] 練習題 - 撲克牌取值

- [列表](#列表)
  - [2-1] 範例-列表宣告
  - [2-2] 範例-列表取值
  - [2-3] 範例-列表大小、新增和刪除和塞值
  - [2-4] 練習題- 賣商品和庫存

- [列表迭代](#列表迭代)
  - [3-1] 範例 - for loop 迴圈迭代List
  - [3-2] 範例 - Enhanced(增強型) for loop 迭代List
  - [3-3] 範例 - Iterator 迭代List
  - [3-4] 練習題 - FOR迴圈處理List 判斷既有資料的年齡
  - [3-5] 練習題 - Iterator 移除偶數
  - [3-6] 練習題 - Iterator 移除母音

- [列表排序](#列表排序)
  - [4-1] 範例-Collections.sort排序 
  - [4-2] 範例-自定義Collections.sort排序
  - [4-3] 練習題-自定義Map順序


# 陣列
取得字串長度length

## 1-1 範例 - 陣列宣告
```java 
    public static void main(String[] args) {
	int[] integers = {1, 2, 3, ___, ___};
	boolean[] flags = {true, ___, true, ___};
	Double[] doubles = {___ , ___, 3.3, 4.4};
	String[] names = {"APPLE", "BANANA", ___ };
	
	int[] integers = new int[5]; // 宣告長度為 5 的整數陣列，初始值為 0
	boolean[] flags = new boolean[4]; // 宣告長度為 4 的布林陣列，初始值為 false
	Double[] doubles = new Double[4]; // 宣告長度為 4 的包裝類型浮點數陣列，初始值為 null
	String[] names = new String[3]; // 宣告長度為 3 的字串陣列，初始值為 null
    
    //new出一個 String[] machi_group 裡面有OO DORIS IVY AUTHER
    
    }

```

## 1-2 範例 - 陣列取值
陣列的索引是從 0 開始的
如果取超過會噴ArrayIndexOutOfBoundsException

```java 
    public static void main(String[] args) {
    
        讓使用者輸入區代號0~11 如果輸入1 顯示401 東區
        
            // 台中市12個區的區代號
        String[] taichungDistrictCodes = {"400", "401", "402", "403", "404", "406", "407", "408", "411", "412", "413", "414"};
        
        // 台中市12個區的中文區名
        String[] taichungDistrictNames = {"中區", "東區", "南區", "西區", "北區", "北屯區", "西屯區", "南屯區", "太平區", "大里區", "霧峰區", "烏日區"};
     
        //如果使用者輸入3 顯示 西區 輸入10 顯示 霧峰區
        //讓使用者輸入13 拿到 IndexOutOfBoundsException
         
        //為了避免以上錯誤加上判斷 如果輸入超過taichungDistrictCodes的長度 提示USER輸入太多
        taichungDistrictNames.length ...
        //加上判斷 根據國泰房地產報告 如果取得 西屯區 南屯區 西區 顯示 好地方
        //反之顯示 __地方 可用三個IF 搭配ELSE
    }

```


## 1-3 範例 - 二維陣列


```java 
    public static void main(String[] args) {

        String[] color = {"Spade", "Heart", "Diamond", "Club"};
        String[] number = {"2", "3", "4", "5", "6", "7", "8", "9", "10", "J", "Q", "K", "A"};
	        // 創建一個二維陣列來表示撲克牌
	    String[][] pokerCards = new String[color.length][number.length];
        
        使用FOR迴圈塞入pokerCards
    }

```


## 1-4 練習題 - 買東西算總和


```java 
    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);
        // 輸入要買幾個東西
        System.out.print("請輸入要買幾樣東西：");
        int numItems = scanner.nextInt();

        //  Double[] 陣列
        Double[] prices = new Double[]; //完成他 

        // 輸入 N 個價格，並存入 Double[] 陣列
        System.out.println("請依序輸入 " + numItems + " 個價格：");
        for (int i = 0; i < numItems; i++) {
           ___  = scanner.nextDouble();  //將___ 放入prices
        }

        // 計算總和
        double sum = 0.0;
        for (double price : prices) {
            //逐筆拿出來加起來
        }
        // 輸出總和
    }

```



## 1-5 練習題 - 撲克牌取值
使用練習1-3 做出 String[][] pokerCards

```java 
    public static void main(String[] args) {
        //使用1-3
         String[][] pokerCards
         
        // 產出2個隨機數 0~3 和0~12
        Random random = new Random();
        int randomSuitIndex = random.nextInt(suits.);
        int randomRankIndex = random.nextInt(ranks.);
        String selectedCard = pokerCards[][];
        
        
       //產出"1個" 隨機整數 1~52 是1印出黑桃2 15印出紅心3 ... 50印出梅花Q
       // int需使用mod 取得商數和餘數
        int randomSuitIndex = random.nextInt(52) + ___;
    }

```


# 列表
List 通常宣告 ArrayList
## 2-1 範例-列表宣告
同上針對 Integer Boolean BigDecimal String Map 宣告
需使用List搭配ArrayList 請需要給型別，型別不一樣會噴錯
```java 
    public static void main(String[] args) {

        List<Integer> integerList = new ArrayList<>();
        integerList.add(10);
        integerList.add(20);
        integerList.add(30);
        //integerList.add(40.5); //會錯
        
        List<Boolean> booleanList = new ArrayList<>();
        booleanList.add(true);
        booleanList.add(); 
        booleanList.add();//完成他
        
        List<BigDecimal> bigDecimalList = new ArrayList<>();
        bigDecimalList.add(new BigDecimal("10.50"));
        bigDecimalList.add();
        bigDecimalList.add();//完成他
        //bigDecimalList.add(0);//會錯
        
        
        List<String> stringList = new ArrayList<>();

        // 將元素加入 List 中
        stringList.add("yesyesyes");
        stringList.add("okok");
        stringList.add("昏倒");


        List<Map> mapList = new ArrayList<>();
        Map<String, String> map1 = new HashMap<>();
        map1.put("name", "OO");
        map1.put("age", "18");
        mapList.add(map1);

        Map<String, String> map2 = new HashMap<>();
        map2.put("name", "IVY");
        map2.put("age", "87");
        mapList.add(map2);
        
        Map<String, ___ > map3 = new HashMap<>();//完成他 可以不塞String
        map3.put("name", "DORIS");
        map3.put("age", 18);
        mapList.add(map3);//可ADD成功 只要是MAP都行 不一定要跟其他MAP一樣
        //但後續取值要小心處理
    }
    
```


## 2-2 範例-列表取值
List 的索引是從 0 開始的，所以要取得第一個元素，可以使用 get(0)...
同樣取超過長度會噴IndexOutOfBoundsException

```java 
    public static void main(String[] args) {
        List<Integer> integerList = new ArrayList<>();
        integerList.add(10);
        integerList.add(20);
        integerList.add(30);

        int firstElement = integerList.get(0); // 取得第一個元素 10
        int secondElement = integerList.get(1); // 取得第二個元素 20
        int thirdElement = integerList.get(2); // 取得第三個元素 30
        
        
        List<Map> mapList = new ArrayList<>();
        Map<String, String> map1 = new HashMap<>();
        map1.put("name", "OO");
        map1.put("age", "18");
        mapList.add(map1);

        Map<String, String> map2 = new HashMap<>();
        map2.put("name", "IVY");
        map2.put("age", "87");
        mapList.add(map2);
        
        Map<String, Object> map3 = new HashMap<>();
        map3.put("name", "DORIS");
        map3.put("age", 18);
        mapList.add(map3);
        
        Map<String, String> firstElement = mapList.get(0); // 取得第一個元素，即 Map1
        String name1 = firstElement.get("name"); // 取得 Map1 中的 name，值為 "Alice"
        String age1 = firstElement.get("age"); // 取得 Map1 中的 age，值為 "25"

        Map<String, String> secondElement = mapList.get(1); // 取得第二個元素，即 Map2
        String name2 = secondElement.get("name"); // 取得 Map2 中的 name，值為 "Bob"
        String age2 = secondElement.get("age"); // 取得 Map2 中的 age，值為 "30"
        
        Map<String, String> thridElement = mapList.get(2); // 取得第三個元素，即 Map3
        String name3 = thridElement.get("name"); // 取得 Map2 中的 name，值為 "Bob"
        String age3 = thridElement.get("age"); // 取得 Map2 中的 age，值為 "30"
        
        //改用這個才可以 
        //Map<String, Object> thridElement = mapList.get(2); // 取得第三個元素，即 Map3
        //String name3 = (String) thridElement.get("name"); // 取得 Map2 中的 name，值為 "Bob"
        //int age3 = (int) thridElement.get("age"); // 取得 Map2 中的 age，值為 "30"
        //以上範例先偷懶用map.get 後續練習請愈MapUtils
    }
```



## 2-3 範例-列表大小、新增和刪除和塞值
size() 方法是一個方法，因此需要使用括號 () 來調用。

陣列其大小在宣告時確定並不能改變。
length 是陣列的一個屬性，而不是方法，所以不需要使用括號。

add 和 remove可以新增和刪除 如果remove不到不影響
使用remove 方法時，如果要移除的元素不存在於LIST中，remove方法會回 false

```java 
    public static void main(String[] args) {
        List<String> stringList = new ArrayList<>();
        stringList.add("A");
        stringList.add("B");
        stringList.add("C");

        int size = stringList.(); //注意有括號 陣列的length沒有
        System.out.println("List 的大小為：" + size);
        
             
        List<String> machi = new ArrayList<>();
        machi.add("OO");
        machi.add("DORIS");
        machi.add("AUTHER");

        //新增IVY
        machi.a
        
        //剔除AUTHER 顯示移除成功
        if ( machi.re ___) 
        
        //移除WEI 顯示移除失敗
        if ( machi.re ___) 
        
        //直接將第三個改成AUTHER
        machi.set(2, "AUTHER")
    }
    

```

## 2-4 練習題 - 賣商品和庫存
1. 先NEW出商品物件 蘋果5個香蕉6個貓1隻狗3條
2. 先用SIZE印出品項跟個數
3. 讓使用者輸入品像跟各數
4. 如果沒品項無此商品
5. 如果該品項庫存不足跳庫存不足
6. 將賣出後的數量存入

```java 
    //同上 但要想一下FOR迴圈
    public static void main(String[] args) {
        //第1部分
        List<String> inventoryItems = new ArrayList<>();
        List<Integer> inventoryQuantities = new ArrayList<>();
        inventoryItems.add("");
        inventoryItems.add("");
        inventoryItems.add("");
        inventoryItems.add("");

        inventoryQuantities.add();
        inventoryQuantities.add();
        inventoryQuantities.add();
        inventoryQuantities.add();

        //第2部分 使用SIZE印出
        System.out.println("目前庫存：");
        for (int i = 0; i < inventoryItems.; i++) {
            System.out.println(inventoryItems.) + ": " +     inventoryQuantities.);
        }
        
        //第3部分 接一個STRING 和INT
        Scanner scanner = new Scanner(System.in);
        
        //第4部分 判斷品項是否包含
        IF inventoryItems.contains(___){
        
            return ;//程式直接結束
        }
        
        //第5部分 判斷庫存數量足夠與否
        inventoryItems.indexOf(__); //取得BANANA在第幾個INDEX
        inventoryQuantities.get(itemIndex);//取得庫存數量 比較大小 如果小於0 跳庫存不足直接return 
        
        //第6部分 set 可以直接改值
        inventoryQuantities.set(___, ___);
        
        //可呼叫第二部份看庫存
        
        
    }

```

# 列表迭代
取的List的物件常用的有FOR迴圈跟Enhanced loop還有Iterator
通常前兩個最常用，如果是需要remove的情況則需要用Iterator
否則會噴ConcurrentModificationException，大概想像如果List的size為5
迴圈要跑5次，中間突然移除物件會造成各數不符


## 3-1 範例- for loop 迴圈迭代List

```java 
    public static void main(String[] args) {
        List<String> names = new ArrayList<>();
        names.add("OO");
        names.add("DORIS");
        names.add("IVY");

        System.out.println("使用 for ：");
        for (int i = 0; i < names.___ i++) {
            String name = names.g_____ ;
          
        }
    }

```

## 3-2 範例 - Enhanced for loop 迭代List

```java 
    public static void main(String[] args) {
        List<String> fruits = new ArrayList<>();
        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Orange");

        System.out.println("使用增強型 for ：");
        for (String fruit : fruits) {
           
        }
        
    }

```

## 3-2 範例 - Enhanced(曾強型) for loop 迭代List

```java 
    public static void main(String[] args) {
        List<String> fruits = new ArrayList<>();
        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Orange");

        System.out.println("使用增強型 for ：");
        for (String fruit : fruits) {
           
        }
        
    }

```

## 3-3 範例 - Iterator 迭代List

```java 
    public static void main(String[] args) {
        List<String> names = new ArrayList<>();
        names.add("OO");
        names.add("DORIS");
        names.add("IVY");
        names.add("AUTHER");

        System.out.println("使用 Iterator不刪除東西：");
        Iterator<String> iterator = names.iterator();
        while (iterator.hasNext()) {
            String name = iterator.next();
            System.out.println(name);
        }
        
        
        
        List<String> names = new ArrayList<>();
        names.add("OO");
        names.add("DORIS");
        names.add("IVY");
        names.add("AUTHER");

        System.out.println("原始 List: " + names);

        // 使用 Iterator 刪除 "OO" 和 "DORIS"
        // 比較字串時使用 "字串常數".equals(name) 的方式不要用==
        Iterator<String> iterator = names.iterator();
        while (iterator.hasNext()) {
            String name = iterator.next();
            if ("OO".equals(name) || "DORIS".equals(name)) {
                iterator.remove();
            }
        }

        System.out.println("刪除後的 List: " + names);
        
    }

```



## 3-4 練習題- FOR迴圈處理List 判斷既有資料的年齡
有四筆資料
判斷哪些人是老人 年輕人 和輸入錯誤的
輸入錯誤使用instanceof Integer 有給部分範例

```java 

		  List<Map<String, Object>> peopleList = new ArrayList<>();

	        // 添加人的名字和年齡到 List<Map> 中
	        Map<String, Object> person1 = new HashMap<>();
	        person1.put("name", "OO");
	        person1.put("age", 18); //數值
	        peopleList.add(person1);

	        Map<String, Object> person2 = new HashMap<>();
	        person2.put("name", "IVY");
	        person2.put("age", 87); // 數值
	        peopleList.add(person2);

	        Map<String, Object> person3 = new HashMap<>();
	        person3.put("name", "DORIS");
	        person3.put("age", 19); // 數值
	        peopleList.add(person3);

	        Map<String, Object> person4 = new HashMap<>();
	        person4.put("name", "WEI");
	        person4.put("age", "YA~"); // 故意錯
	        peopleList.add(person4);

	        // 使用增強型 for 迴圈處理資料
             for (){
             
             
              Object ageObj = person.get("age");
             if (ageObj instanceof Integer) {
	                int age = (int) ageObj;
	                if (age <= 65) {
	                    adults.add(name);//前面創個年輕人的LIST
	                } else {
	                	 System.out.println("老人是：" + name);
	                }
	            } else {
	                System.out.println("使用者" + name  +"輸入錯誤：年齡必須為數字");
	            }
             
             
             }        
```

## 3-5 練習題 - Iterator 移除偶數
有時間練習可以把numbersList用隨機數列產出

```java 
    List<Integer> numbersList = new ArrayList<>();
    numbersList.add(10);
    numbersList.add(25);
    numbersList.add(8);
    numbersList.add(17);
    numbersList.add(12);
    
     // 使用 Iterator 並刪除所有偶數
        Iterator<Integer> iterator = numbersList.iterator();
        while (iterator.hasNext()) {
            判斷 % 2 ==0 移除
        }

```

## 3-6 練習題 - Iterator 移除母音
```java 
        List<String> namesList = new ArrayList<>();
        namesList.add("AUTHER");
        namesList.add("TOM");
        namesList.add("RYAN");
        namesList.add("DORIS");
        namesList.add("EVE");
        namesList.add("NEAR");
        namesList.add("WEI");
        namesList.add("OO");
        namesList.add("IVY");
        namesList.add("JASON");

        
       Iterator<String> iterator = namesList.iterator();
        while (iterator.hasNext()) {
            拿出name
            判斷name.charAt的第一個字
        }

        
```
        
# 列表排序
 Integer、Double、String、 Character、 BigDecimal、 Boolean
只有這些可使用Collections.sort排序

## 4-1 範例-Collections.sort排序 

```java 
    public static void main(String[] args) {
  // List<Integer>：整數型別的列表
        List<Integer> integerList = new ArrayList<>();
        integerList.add(10);
        integerList.add(5);
        integerList.add(20);

        // 使用 Collections.sort(list) 方法進行遞增排序
        Collections.sort(integerList);

        // 輸出排序後的結果
        System.out.println("整數的列表排序結果：");
        for (Integer value : integerList) {
            System.out.println(value);
        }

        // List<String>：字符串型別的列表
        List<String> stringList = new ArrayList<>();
        stringList.add("OO");
        stringList.add("DORIS");
        stringList.add("IVY");

        // 使用 Collections.sort(list) 方法進行字母順序排序
        Collections.sort(stringList);

        // 輸出排序後的結果
        System.out.println("字串列表排序結果：");
        for (String value : stringList) {
            System.out.println(value);
        }

        // List<BigDecimal>：大數字型別的列表
        List<BigDecimal> bigDecimalList = new ArrayList<>();
        bigDecimalList.add(new BigDecimal("10.5"));
        bigDecimalList.add(new BigDecimal("5.2"));
        bigDecimalList.add(new BigDecimal("20.1"));

        // 使用 Collections.sort(list) 方法進行遞增排序
        Collections.sort(bigDecimalList);

        // 輸出排序後的結果
        System.out.println("BigDecimal的列表排序結果：");
        for (BigDecimal value : bigDecimalList) {
            System.out.println(value);
        }
        //可自行add remove 一些int string BigDecimal 試試看結果
    }
```
## 4-2 範例-自定義Collections.sort排序 
以上型別可以是因為有順序性才可以排
如果不為以上類型，譬如常見的MAP就無法排序 需要自記定義一個方法讓程式知道你的排序規則

```java 

 
   List<Integer> integerList = new ArrayList<>();
        integerList.add(60);
        integerList.add(20);
        integerList.add(30);

        // 使用自定義的比較器對 List<Object> 進行排序
        Collections.sort(integerList, new CompareMethod()); //給一個CompareMethod ,CompareMethod只是一個名詞 隨你怎麼取 要在外面new一個class
        名稱為CompareMethod

        // 輸出排序後的結果
        System.out.println("排序後的結果：");
        for (Object obj : integerList) {
            System.out.println(obj);
        }
        
   
```
```java 
private static class CompareMethod implements Comparator<Object>{
		 
}
```
游標移過去 會教你複寫比較方法
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_aac4995d294e79c19f610eb9d5a0231c.png)

```java 
		@Override
		public int compare(Object o1, Object o2) {
			// TODO Auto-generated method stub
			return 0;
		}
        
        以這題 簡單來說 就是要你告訴他 60跟20 和30怎麼比 需自定義
        compareTo
        如果小於，則返回負整數。
        如果等於則返回 0。
        如果大於，則返回正整數。
   int result = Integer.valueOf(10).compareTo(Integer.valueOf(5)); // 返回正整數，因為 10 大於 5
        int result2 = Integer.valueOf(5).compareTo(Integer.valueOf(10)); // 返回負整數，因為 5 小於 10
        int result3 = Integer.valueOf(5).compareTo(Integer.valueOf(5)); // 返回 0，因為 5 等於 5
        
        
         //    @Override
        //public int compare(Integer o1, Integer o2) {
//            return o2.compareTo(o1); // 將 o2.compareTo(o1) 改為 //o1.compareTo(o2) 即為升序排序
  //      }
```

## 4-3 練習題-自定義Map順序
```java 
        List<Map<String, Object>> personList = new ArrayList<>();

        Map<String, Object> person1 = new HashMap<>();
        person1.put("姓名", "OO");
        person1.put("年齡", 18);
        personList.add(person1);

        Map<String, Object> person2 = new HashMap<>();
        person2.put("姓名", "IVY");
        person2.put("年齡", 87);
        personList.add(person2);

        Map<String, Object> person3 = new HashMap<>();
        person3.put("姓名", "DORIS");
        person3.put("年齡", 99);
        personList.add(person3);

        // 使用自定義的比較器對列表進行姓名排序
        personList.sort(new ());//給一個CompareMethod這次取名NameComparator

        // 輸出排序後的結果
        System.out.println("姓名排序後的結果：");
        for (Map<String, Object> person : personList) {
            System.out.println("姓名：" + person.get("姓名") + "，年齡：" + person.get("年齡"));
        }
    }

    // 自定義比較器來指定姓名排序規則
    private static class NameComparator implements Comparator<Map<String, Object>> {
        @Override
        public int compare(Map<String, Object> o1, Map<String, Object> o2) {
            String name1 = 
            String name2 = 
            return .compareTo(); //完成他
        }
    }
    
    如果搞不懂 可以印一下
    int result = "IVY".compareTo("OO"); 
    int result = "IVY".compareTo("DORIS"); 
    看一下回傳的result


```
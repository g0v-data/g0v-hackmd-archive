# C#的一些知識 & 常用筆記


---


# 強型別 v.s. 弱型別

* 強型別 (Stronly Type)

定義：相對弱型別而言，較不允許隱性型別轉換，程式在檢查上較為**嚴格**。因此，在開發過程中也會相對較難撰寫，但是同時也能夠**降低**遇到 Bug 的風險性。

例如：Java、C#、Python

* 弱型別 (Weakly Type)

定義：相對強型別而言，較允許隱性型別轉換，程式在檢查上較為**寬鬆**。因此，在開發過程中也會相對較容易撰寫，但是同時也會**增加**遇到 Bug 的風險性。

例如：C、C++、PHP、JavaScript

【Q】靜態語言一定是強型別？動態語言一定是弱型別？
【A】不一定。靜態語言和動態語言最大的差別在於 Data Type 的處理方式。因此，與強型別或弱型別並無一定關係。

| 語言型態 | 強弱型別 |       程式語言        |
|:--------:|:--------:|:---------------------:|
|   靜態   |    強    |       Java, C#        |
|   靜態   |    弱    |         C/C++         |
|   靜態   |    強    |     Python, Ruby      |
|   靜態   |    弱    | Perl, PHP, JavaScript |

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e7e6a84d26a0f7d97993884dbc95dd8d.png)


---

# 泛型容器 (Dictionary & List)

* 泛型(Generics)：泛型允許我們根據自身需求在定義類別、方法或資料結構時暫時不指定具體的資料類型，而是在使用時根據需求指定類型。也就是它可以讓我們在定義 Class、Method、 Interface 時先不用決定型別，到了要實體化的時候再決定其型別，可以用更有彈性的方式來設計 Class、Method，操作資料等。

【註】都需要先引用命名空間：`System.Collections.Generic`

* Dictionary

定義：是鍵值的集合 ，主要透過 Key 取得 Value (e.g. `myDictionary["key"]`) 進行快速查找，長度任意。

適用場景：用來根據標籤(Key)快速找到資料(Value)，像是大型資料庫。

語法：`Dictionary<TKey, TValue> myDictionary = new Dictionary<TKey, TValue>();`
【新增】`myDictionary.Add(Key, Value)`
【刪除】`myDictionary.Remove(Key)`

範例：
```
Dictionary<string, int> myDictionary = new Dictionary<string, int>();
myDictionary.Add("Alice", 30);
myDictionary.Add("Bob", 25);
int aliceAge = myDictionary["Alice"]; // 30
```


* List

定義：是相同型別的集合，主要透過 Index 取得元素 (e.g. `myList[index]`)，長度任意。於 C# 2.0 後開始被廣泛使用，甚至取代 C# 1.0 的 ArrayList。

適用場景：用來存放有順序的東西，像是清單或列表。

語法：`List<T> myList = new List<T>();`
【新增】`myList.Add(T)`
【刪除】`myList.Remove(T)` 或 `myList.RemoveAt(index)`

範例：
```
List<int> myList = new List<int>();
myList.Add(1);
myList.Add(2);
myList.Add(3);
int firstNumber = myList[0]; // 1
```


---

# Legacy Objects (Array, ArrayList, DataTable)




---

# Oracle 的 Lock Type 運作模式




---

# 變數(variable)與屬性(property)本質上的差異




---

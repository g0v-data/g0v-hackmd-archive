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

# 泛型容器 (Dictionary & List & HashSet & LinkedList)

* 泛型(Generics)：泛型允許我們根據自身需求在定義類別、方法或資料結構時暫時不指定具體的資料類型，而是在使用時根據需求指定類型。也就是它可以讓我們在定義 Class、Method、 Interface 時先不用決定型別，到了要實體化的時候再決定其型別，可以用更有彈性的方式來設計 Class、Method，操作資料等。

【註】都需要先引用命名空間：`System.Collections.Generic`

* Dictionary

定義：是鍵值的集合 ，可以透過 Key 取得 Value (e.g. `myDictionary["key"]`) 進行快速查找，長度任意。

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

定義：是相同型別的集合，可以透過 Index 取得元素 (e.g. `myList[index]`)，長度任意。於 C# 2.0 後開始被廣泛使用，甚至取代 C# 1.0 的 ArrayList。

適用場景：用來存放有順序的東西，像是清單或列表。

語法：`List<T> myList = new List<T>();`
【新增】`myList.Add(T)`
【刪除】`myList.Remove(T)` 或 `myList.RemoveAt(index)`

範例：
```
    List<int> numbers = new List<int>();
    numbers.Add(1);
    numbers.Add(2);
    numbers.Add(3);
    int firstNumber = numbers[0]; // 1
```

* HashSet

定義：是相同型別，但不允許重複的集合(即允許存取唯一值)，長度任意。但 HashSet 集合內的順序並非固定，又不支持使用 Index 取得元素。因此，僅能透過 Contains 查找是否存在於集合中。

語法：`HashSet<T> myHashSet = new HashSet<T>();`
【新增】`myHashSet.Add(T)`
【刪除】`myHashSet.Remove(T)`

範例：
```
    HashSet<int> numbers = new HashSet<int>();
    numbers.Add(1);
    numbers.Add(2);
    numbers.Add(2); // 不會添加重複的 2
    bool exists = numbers.Contains(1); // true
```

* LinkedList

定義：是相同型別的集合，長度任意，允許在任意位置快速插入和刪除元素。LinkedList 集合內的順序為有序的(根據添加順序排列)，但同樣不支持使用 Index 取得元素。因此，需要使用 foreach 查找特定的元素是否存在於集合內。

語法：`LinkedList<T> myLinkedList = new List<T>();`
【新增】`myLinkedList.AddFirst(T)` 或 `myLinkedList.AddLast(T)`
【刪除】`myLinkedList.Remove(T)`

範例：
```
    LinkedList<int> numbers = new LinkedList<int>();
    numbers.AddLast(1);
    numbers.AddLast(2);
    numbers.AddFirst(0); // 在開頭添加 0
    bool exists = false;
    foreach (var number in numbers)
    {
        if (number == 2)
        {
            exists = true; // 查找元素
            break;
        }
    }
```

---

# Legacy Objects (Array, ArrayList, DataTable)

* Array

定義：Array是一個不特定型別、長度固定的資料結構，因此一開始就要先宣告其長度大小，才能夠將資料放進指定位置，長度大小一旦宣告即無法修改。可以透過 Index 取得元素，位置從 0 開始計算。

範例：
```
    static void Main()
    {
        int[] numbers = {1, 2, 3, 4, 5}; // def. an array
        numbers[1] = 10; // update numbers[1]
        Console.WriteLine(numbers[1]);  // output = 10
    }
```

* ArrayList

定義：ArrayList 是一個不特定型別，不固定長度的陣列。相較於 Array 來說，ArrayList 更加彈性，其可動態增加或減少 ArrayList 中的項目。在 C#2.0 之後建議用 List<T> 替代 ArrayList，因
ArrayList 可以儲存任何類型的 object，可能在程式運作時會導致轉換錯誤。

【註】需先引用命名空間：`System.Collections`

範例：
```
    static void Main()
    {
        ArrayList fruits = new ArrayList();

        fruits.Add("Apple");
        fruits.Add("Banana");
        fruits.Add("Cherry");

        Console.WriteLine(fruits[1]);  // output: Banana
    }
```

* DataTable

定義：DataTable 就像是一張全新的表格，允許使用者自行新增 Column 和 Row ，每一列都能夠自行定義資料類型(使用 typeof())，且可以在運行的時候增加或刪除行、列。通常適用於儲存和操作結構化資料，特別是和資料庫交互的情況下，因此，也可以將許多 DataTable 進行串聯，建立一個 DataSet。

範例：
```
    static void Main()
    {
        DataTable table = new DataTable("Products");

        table.Columns.Add("ID", typeof(int));
        table.Columns.Add("Name", typeof(string));
        table.Columns.Add("Price", typeof(decimal));

        table.Rows.Add(1, "Laptop", 999.99m);
        table.Rows.Add(2, "Smartphone", 499.99m);
        table.Rows.Add(3, "Tablet", 299.99m);

        foreach (DataRow row in table.Rows)
        {
            Console.WriteLine($"{row["ID"]}, {row["Name"]}, {row["Price"]}");
        }
    }
```

---

# Oracle 的 Lock Type 運作模式

* ACCESS SHARE：

* ROW SHARE：

* ROW EXCLUSIVE：

* SHARE UPDATE EXCLUSIVE：

* SHARE：

* SHARE ROW EXCLUSIVE：

* EXCLUSIVE：


---

# 變數與屬性本質上的差異
* 變數 (Variable)：

* 屬性 (Property)：


---



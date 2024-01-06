C# 修練30天 常見的資料型態 & 變數 Day-1
===

字串 string 使用
---
> **string 字串型別，它代表 C# 中的一段文字。**
>> **用法:**
>> <font color="blue">string</font> name = "Bill";
Console.WriteLine(aFriend);
<font color="#D94DFF">//Bill</font>

字元 char 使用
---
> **char字元型別，它代表 C# 中的一個字，如果超過一個字就不能使用。**
>> **用法:**
>> <font color="blue">char</font> aFriend = "A";
Console.WriteLine(aFriend);
<font color="#D94DFF">//A</font>

整數 int 使用
---
> **int數字整數型別，它代表 C# 中的整數。**
>> **用法:**
>> <font color="blue">int</font> aFriend = "60";
Console.WriteLine(aFriend);
<font color="#D94DFF">//60</font>

浮點數 double 使用
---
> **double數字浮點數型別，它代表 C# 中的有小數點的數字。**
>> **用法:**
>> <font color="blue">double</font> aFriend = "160.5";
Console.WriteLine(aFriend);
<font color="#D94DFF">//160.5</font>

布林值 bool 使用
---
> **bool判斷型別，它代表 C# 中的true跟false。**
>> **用法:**
>> <font color="blue">bool</font> aFriend = "true";
Console.WriteLine(aFriend);
<font color="#D94DFF">//true</font>

Console.Write()
---
> **Console.Write() 表示向控制台直接寫入字串，不進行換行，可繼續接著前面的字寫入。**
>> **用法:**
>> Console.Write("Hello World!");
>> <font color="#D94DFF">//Hello World!</font>

Console.WriteLine()
---
> **Console.WriteLine() 表示向控制台寫入字串後可換行。**
>> **用法:**
>> <font color="blue">string</font> <font color="#00BFFF">aFriend</font> = <font color="red">"Bill"</font>;
>> Console.WriteLine(<font color="red">"Hello World!"</font>);
>> Console.WriteLine(<font color="red">"Hello "</font> + <font color="#00BFFF">aFriend</font>);
>> Console.WriteLine(<font color="red">$"Hello {<font color="#00BFFF">aFriend</font>}"</font>);
>> <font color="#D94DFF">//大括號裡面是變數</font>

Length
---
> **.Length 是字串的屬性，會傳回該字串的字元數**
>> **用法:**
>> <font color="blue">string</font> <font color="#00BFFF">secondFriend</font> = <font color="red">"Sage"</font>
Console.WriteLine(<font color="red">$"The name {<font color="#00BFFF">secondFriend</font>} has {<font color="#00BFFF">secondFriend.Length</font>} letters."</font>);
<font color="#D94DFF">//The name Sage has 4 letters.</font>

綜合運用
---
> **以下為上方所有介紹示範**
> 注意:每個變數都可以隨意更改內容，但是只能更改同樣型別的東西，否則無法使用。
>> **用法**
>> <font color="blue">string</font> <font color="#00BFFF">name</font> = <font color="red">"小澄"</font>;
>> <font color="blue">char</font> <font color="#00BFFF">sex</font> = <font color="red">'男'</font>;
>> <font color="blue">int</font> <font color="#00BFFF">age</font> = <font color="red">35</font>;
>> <font color="blue">double</font> <font color="#00BFFF">height</font> = <font color="red">180.3</font>;
>> <font color="blue">bool</font> <font color="#00BFFF">is_male</font> = <font color="red">true</font>;
>> Console.WriteLine(<font color="red">$ "我的名子叫 + {<font color="#00BFFF">name</font>}"</font>);
>> <font color="#D94DFF">//我的名子叫小澄</font>
>> <font color="#00BFFF">name</font> = <font color="red">"小黃"</font>;
>> Console.WriteLine(<font color="red">$ "{<font color="#00BFFF">name</font>} + 今年{<font color="#00BFFF">age</font>}歲"</font>);
>> <font color="#D94DFF">//小黃今年35歲</font>
>> <font color="#00BFFF">name</font> = <font color="red">"小灰"</font>;
>> Console.WriteLine(<font color="red">$ "{<font color="#00BFFF">name</font>} + 身高{<font color="#00BFFF">height</font>}"</font>);
>> <font color="#D94DFF">//小灰身高180.3</font>
>> <font color="#00BFFF">name</font> = <font color="red">"小綠"</font>;
>> Console.WriteLine(<font color="red">$ "{<font color="#00BFFF">name</font>} + 是個{<font color="#00BFFF">sex</font>}的"</font>);
>> <font color="#D94DFF">//小綠是個男的</font>
>> Console.WriteLine(<font color="red">$ "{<font color="#00BFFF">name</font>} + 是個{<font color="#00BFFF">sex</font>}的嗎? 答案:{<font color="#00BFFF">is_male</font>}"</font>);
>> <font color="#D94DFF">//小綠是個男的嗎? 答案:ture</font>


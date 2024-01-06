<font size="9">C# 修練30天 Day-2 常見用法</font>
===

<font size="6">1.字串常見用法</font>
---
### \n
> \n 換下一行。
>> **用法:**
>> Console.WriteLine(<font color="red">"Hello \nMr.White"</font>);
>> <font color="#D94DFF">//Hello</font>
>> <font color="#D94DFF">&nbsp;&nbsp;&nbsp;Mr.White</font>;

### \ \"
> \ \" 在要顯示的字串中顯示雙引號。
>> **用法:**
>> Console.WriteLine(<font color="red">"Hello \ \"Mr.White\ \"</font>);
>> <font color="#D94DFF">//Hello"Mr.White"</font>;

### \ \'
> \ \' 在要顯示的字串中顯示單引號。
>> **用法:**
>> Console.WriteLine(<font color="red">"Hello \ \'Mr.White\ \'</font>);
>> <font color="#D94DFF">//Hello'Mr.White'</font>; 

### .ToUpper()
> .ToUpper() 把所有字串的文字變成大寫。
>> **用法:**
>> <font color="blue">string</font> <font color="#00BFFF">phrase</font> = <font color="red">"Hello Mr.White"</font>;
>> Console.WriteLine(<font color="#00BFFF">phrase</font>.ToUpper());
>> <font color="#D94DFF">//HELLO MR.WHITE'</font>; 

### .ToLower()
> .ToLower() 把所有字串的文字變成小寫。
>> **用法:**
>> <font color="blue">string</font> <font color="#00BFFF">phrase</font> = <font color="red">"Hello Mr.White"</font>;
>> Console.WriteLine(<font color="#00BFFF">phrase</font>.ToLower());
>> <font color="#D94DFF">//hello mr.white'</font>; 

### .Contains()
> .Contains() 可搜尋字串中是否有包含我們想選的字，顯示true或false。
> 注意:要留意大小寫是否正確，否則也會判定false。
>> **用法:**
>> <font color="blue">string</font> <font color="#00BFFF">phrase</font> = <font color="red">"Hello Mr.White"</font>;
>> Console.WriteLine(<font color="#00BFFF">phrase</font>.Contains(<font color="red">"Hello"</font>);
>> <font color="#D94DFF">//true</font>; 

### []
> 在字串後面加入中括號[]填數字可找出該位子的字元。
> 注意:所有的開頭都是從0開始算起，空格也算一個位數，位置算法是01234567....
>> **用法:**
>> <font color="blue">string</font> <font color="#00BFFF">phrase</font> = <font color="red">"Hello Mr.White"</font>;
>> Console.WriteLine(<font color="#00BFFF">phrase</font>.[<font color="#B8860B">1</font>]);
>> <font color="#D94DFF">//e</font>; 

### .IndexOf()
> .IndexOf() 可搜尋我們想選的字在第幾個位置。
> 注意:空格也算一個位數，要留意大小寫是否正確，否則沒有也會判定-1。
>> **用法:**
>> <font color="blue">string</font> <font color="#00BFFF">phrase</font> = <font color="red">"Hello Mr.White"</font>;
>> Console.WriteLine(<font color="#00BFFF">phrase</font>.IndexOf(<font color="red">"M"</font>));
>> <font color="#D94DFF">//6</font>; 
>> Console.WriteLine(<font color="#00BFFF">phrase</font>.IndexOf(<font color="red">"z"</font>));
>> <font color="#D94DFF">//-1</font>;

### .Substring()
> .Substring() 可顯示選定位置之後的字，含選定位置，如果有第二個數字的話就會顯示，第一個數字選定的位置之後開始數到指定數字為止
>> **用法:**
>> <font color="blue">string</font> <font color="#00BFFF">phrase</font> = <font color="red">"Hello Mr.White"</font>;
>> Console.WriteLine(<font color="#00BFFF">phrase</font>.Substring(2));
>> <font color="#D94DFF">//llo Mr.White</font>; 
>> Console.WriteLine(<font color="#00BFFF">phrase</font>..Substring(2, 8));
>> <font color="#D94DFF">//llo Mr.</font>;

<font size="6">2.數字常見用法 (整數 浮點數)</font>
---
### + - * /(加減乘除)
> 基礎運算
> 注意:一樣先乘除後加減的算法，如果用的都是整數，就會只顯示整數無條件捨去 EX(5 / 2 = 2)，只要其中一方有小數點就會顯示小數點。
>> **用法:**
>> Console.WriteLine(<font color="#B8860B">10 + 2</font>;);
>> <font color="#D94DFF">//12</font>;
>> Console.WriteLine(<font color="#B8860B">10 - 2</font>;);
>> <font color="#D94DFF">//8</font>;
>> Console.WriteLine(<font color="#B8860B">10 * 2</font>;);
>> <font color="#D94DFF">//20</font>;
>> Console.WriteLine(<font color="#B8860B">10 / 2</font>;);
>> <font color="#D94DFF">//5</font>;
>> Console.WriteLine(<font color="#B8860B">(10 + 2) * 3</font>;);
>> <font color="#D94DFF">//36</font>;
>> Console.WriteLine(<font color="#B8860B">10 + 2 * 3</font>;);
>> <font color="#D94DFF">//16</font>;

### .Math.Abs()
> .Math.Abs() 代表數字的絕對值
>> **用法:**
>> Console.WriteLine(Math.Abs(<font color="#B8860B">-10</font>));
>> <font color="#D94DFF">//10</font>; 

### .Math.Pow()
> .Math.Pow() 代表數字的次方
>> **用法:**
>> Console.WriteLine(Math.Pow(<font color="#B8860B">2, 3</font>));
>> <font color="#D94DFF">//8</font>; 

### .Math.Sqrt()
> .Math.Sqrt() 代表數字的開根號
>> **用法:**
>> Console.WriteLine(Math.Sqrt(<font color="#B8860B">36</font>));
>> <font color="#D94DFF">//6</font>; 

### .Math.Max()
> .Math.Max() 比較數字最大
>> **用法:**
>> Console.WriteLine(Math.Max(<font color="#B8860B">2, 100</font>));
>> <font color="#D94DFF">//100</font>;

### .Math.Min()
> .Math.Min() 比較數字最小
>> **用法:**
>> Console.WriteLine(Math.Min(<font color="#B8860B">2, 100</font>));
>> <font color="#D94DFF">//2</font>;

### .Math.Round()
> .Math.Round() 代表數字的四捨五入
>> **用法:**
>> Console.WriteLine(Math.Round(<font color="#B8860B">5.5</font>));
>> <font color="#D94DFF">//6</font>;

### .Math.Ceiling()
> .Math.Ceiling() 代表數字的無條件進位
>> **用法:**
>> Console.WriteLine(Math.Ceiling(<font color="#B8860B">5.5</font>));
>> <font color="#D94DFF">//6</font>;

### .Math.Floor()
> .Math.Floor() 代表數字的無條件捨去
>> **用法:**
>> Console.WriteLine(Math.Floor(<font color="#B8860B">5.5</font>));
>> <font color="#D94DFF">//5</font>;

<font size="6">3.取得用戶輸入</font>
---
### .ReadLine()
> .ReadLine() 儲存用戶輸入的值，可多次儲存。
> 注意:儲存的值都是字串型別。
>> **用法:**
>> Console.WriteLine(<font color="red">"請輸入你的名子 :"</font>);
>> <font color="blue">string</font> <font color="#00BFFF">FullName</font> =  Console.ReadLine();
>> Console.WriteLine(<font color="red">$"你好啊! {<font color="#00BFFF">FullName</font>}!!"</font>);
>> <font color="#D94DFF">順序1</font>
>> <font color="#D94DFF">//請輸入你的名子 :</font>
>> <font color="#D94DFF">EX:輸入了"小白"</font>
>> 
>> <font color="#D94DFF">順序2</font>
>> <font color="#D94DFF">//你好啊! 小白!!</font>
>> 
>> Console.WriteLine(<font color="red">"請輸入你的名子 :"</font>);
>> <font color="blue">string</font> <font color="#00BFFF">FullName</font> =  Console.ReadLine();
>> Console.WriteLine(<font color="red">"請輸入你的年紀 :"</font>);
>><font color="blue">string</font> <font color="#00BFFF">age</font> =  Console.ReadLine();
>> Console.WriteLine(<font color="red">$"你好啊! {<font color="#00BFFF">FullName</font>}!!你今年{<font color="#00BFFF">age</font>}歲了"</font>);
>> <font color="#D94DFF">順序1</font>
>> <font color="#D94DFF">//請輸入你的名子 :</font>
>> <font color="#D94DFF">EX:輸入了"小白"</font>
>> 
>> <font color="#D94DFF">順序2</font>
>> <font color="#D94DFF">//請輸入你的年紀 :</font>
>> <font color="#D94DFF">EX:輸入了"23"</font>
>> 
>> <font color="#D94DFF">順序3</font>
>> <font color="#D94DFF">//你好啊! 小白!!你今年23歲了</font>
>> 

<font size="6">4.轉換 .Convert</font>
---
> Convert 將資料類型轉換為其他資料類型，包括 ToInt32 、 ToBoolean 和 ToString。
### .Convert.ToInt32()
> .Convert.ToInt32() 將其他資料類型轉換為數字資料類型，限整數，有小數點的數會無法計算。
>> **用法:**
>> Console.WriteLine(<font color="red">"請輸入第一個數 : "</font>);
>> <font color="blue">int</font> <font color="#00BFFF">num1</font> = Convert.ToInt32(Console.ReadLine());
>> Console.WriteLine(<font color="red">"請輸入第二個數 : "</font>);
>> <font color="blue">int</font> <font color="#00BFFF">num2</font> = Convert.ToInt32(Console.ReadLine());
>> Console.WriteLine(<font color="#00BFFF">num1</font> +<font color="#00BFFF">num2</font>);
>> <font color="#D94DFF">順序1</font>
>> <font color="#D94DFF">//請輸入第一個數 : </font>
>> <font color="#D94DFF">EX:輸入了"1"</font>
>> 
>> <font color="#D94DFF">順序2</font>
>> <font color="#D94DFF">//請輸入第二個數 : </font>
>> <font color="#D94DFF">EX:輸入了"2"</font>
>> 
>> <font color="#D94DFF">順序3</font>
>> <font color="#D94DFF">//3</font>
>> 

### .Convert.ToDouble()
> .Convert.ToDouble() 將其他資料類型轉換為數字資料類型，整數和小數點都可以計算。
>> **用法:**
>> Console.WriteLine(<font color="red">"請輸入第一個數 : "</font>);
>> <font color="blue">double</font> <font color="#00BFFF">num1</font> = Convert.ToDouble(Console.ReadLine());
>> Console.WriteLine(<font color="red">"請輸入第二個數 : "</font>);
>> <font color="blue">double</font> <font color="#00BFFF">num2</font> = Convert.ToDouble(Console.ReadLine());
>> Console.WriteLine(<font color="#00BFFF">num1</font> +<font color="#00BFFF">num2</font>);
>> <font color="#D94DFF">順序1</font>
>> <font color="#D94DFF">//請輸入第一個數 : </font>
>> <font color="#D94DFF">EX:輸入了"1.5"</font>
>> 
>> <font color="#D94DFF">順序2</font>
>> <font color="#D94DFF">//請輸入第二個數 : </font>
>> <font color="#D94DFF">EX:輸入了"2"</font>
>> 
>> <font color="#D94DFF">順序3</font>
>> <font color="#D94DFF">//3.5</font>
>> 

<font size="6">5.陣列 Array</font>
---
> Array 提供建立、管理、搜尋和排序陣列的方法，可在 Common Language Runtime 時做為所有陣列的基底類。
> 
> Array為程式設計中最基本元素之一. 陣列就是用一個[]記下多個同類的值(記憶體中的位置), 以供日後所調用。
>> **用法:**
>> <font color="blue">int</font> <font color="#00BFFF">score1</font> = <font color="#B8860B">50</font>;
>> <font color="blue">int</font> <font color="#00BFFF">score2</font> = <font color="#B8860B">60</font>;
>> <font color="blue">int</font> <font color="#00BFFF">score3</font> = <font color="#B8860B">70</font>;
>> <font color="blue">int</font> <font color="#00BFFF">score4</font> = <font color="#B8860B">80</font>;
>> <font color="blue">int</font> <font color="#00BFFF">score5</font> = <font color="#B8860B">90</font>;
>> 可以整理成
>> <font color="blue">int</font> <font color="#00BFFF">scores</font> = { <font color="#B8860B">50</font>, <font color="#B8860B">60</font>, <font color="#B8860B">70</font>, <font color="#B8860B">80</font>, <font color="#B8860B">90</font>, <font color="#B8860B">20</font> };
>> Console.WriteLine(<font color="#00BFFF">scores</font>[0]);
>> Console.WriteLine(<font color="#00BFFF">scores</font>[1]);
>>
>> 或是先建立一個空陣列。
>> <font color="blue">string[]</font> <font color="#00BFFF">phones</font> = new string[10];
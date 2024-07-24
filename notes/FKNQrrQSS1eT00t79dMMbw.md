# **CS50 course**
**Binary**
個位數/十位數/百位數 -> 2^2^ / 2^1^/2^0^ -> 4/2/1

<pre> ex: 4 2 1
1 1 1 = 1*4+1*2+1*1= 7 </pre>
> 1 byte =8 bit   ex: 00101100
 alphabits are represented in ASCII    
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7f8a9d59868aba0ce6b20893d50553cb.png)

unicode: a text encoding standard(ex: 👍= U+1F44D)
* functions,conditionals,boolean expression,loops...
* the $ (dollar sign in terminal) is where you type the prompt
*std=standard

# **c code**
___
help:https://manual.cs50.io/#stdio.h
* f=formated
* semicolon(;)=the end of every sentence
* backslashn(\n)=換行
* string=字符
  ex:string ...= get string("..."); 
 int=數字(interger整數)
 * %s(placeholder)讓 input 或 textarea 顯示預設的文字，並且當使用者輸入文字時，它將會自動消失，當使用者移除文字時，它會再次顯示。

<pre>
code hello.c  ->create the file
make hello ->compile the file from source code(letters) to machine code(binary)
.hello ->show
</pre>

some basic mods:
printf("hello, %$\n", answer);
, answer = second input

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_683c935d7c8b15c06e6619cc97a460d5.png)
### **why use "else if" instead of just "if"?**
it's more efficient, because the computer only has to check conditions until it finds a condition that returns the value TRUE
**<use if>**
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bfa6325427dec4c453a0cf414b836e5a.png)
**<use else if>**
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c1e38490442f8ed89c04755da80e6bd3.png)

___
> ## **include <cs50.h>**
get_char - short for character,(letter, number, etc.)
get_double - 雙精度浮點數（即帶有小數點且精度較高的數字）
get_float - 浮點數
get_int - 整數
get_long - int但記憶體更大(4byte)
get_short -int但記憶體更小(2byte)
get_string - 一串字符的序列



| 格式符号 | 描述                                   |
|----------|----------------------------------------|
| %c       | 用于读取或打印单个字符（char）          |
| %f       | 用于读取或打印浮点数（float或double）   |
| %i       | 用于读取或打印整数（int）              |
| %li      | 用于读取或打印长整数（long int）       |
| %s       | 用于读取或打印字符串（char数组或指针） |

这些格式符号在编程中常用来指示输入输出函数如何处理不同类型的数据。例如，在使用 `scanf` 函数读取输入时，你可以使用这些格式符号来告诉编程语言如何解析输入的内容。

how to use them?
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_07e3cf4f190e7d0c9f8f85f082fbc832.png)
use:  **("example:%f\n", details from example)**

---

> ### *checking lower or upper case*
>* 很多字符"" , 一個字符''
>* &&為共同存在 , || 為or(或)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_de7d65fa9196be272cb7a186e9b0fc20.png)


>## loop
>![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8a368c1801d2b91af8ce25a78fc4d8f3.png)

>i = integer(these abbreiviation are typically used in simpler codes)
>* ++i;   i = i + 1;
>*  --i;   i = i - 1;
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_80fe1a627b84ca28fed7b41ccd0ddd4d.png)

>## "for" loop
>general:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0386a9e7a5087dd850e5209e3895df7f.png)
forever loop:
while(true)-程式碼的運作邏輯是重複的柏努力試驗，一直為true,會無限運行下去

return value: function returns to the calling script or function when it completes its task

>create variabe (define the function before u use it)
## 新變數需在上, void 變數(void)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3e1410eefc806ddffa6a4931aa56b959.png)
more abstracted:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_30a8319d4f94152cbb055731a8ed0823.png)
special case where it's at the bottom
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_84cb147341c2762ef88425dc7dda6297.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cd8340ba887975ef81e8ae2334fec4b1.png)

> ## using placeholder(%i)
>u can not typre x + y in the "" beacause it would literally print x + y, use placeholder i to represent the sum
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fb16b64189d8939be60ea3ad50889b9c.png)

>## representation, 
a and b can be anything(ex:first and second),it stands as the position for variable to fit in.
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_537a178da7bb1e1d569a2f809bb8dafe.png)
___
>## linux 快捷
| 命令   | 描述                           |
|--------|--------------------------------|
| cd     | Change Directory（更改目录）    |
| cp     | Copy（复制文件或目录）         |
| ls     | List（列出当前目录下的文件和目录） |
| mkdir  | Make Directory（创建新目录）   |
| mv     | Move（移动文件或目录，也可用于重命名） |
| rm     | Remove（删除文件）            |
| rmdir  | Remove Directory（删除空目录） |
use $clear to clear the terminal
在終端使用 上箭頭 快捷提示前一步
___

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a24730bbe78a04bffa4a5f0c95f733fd.png)

* \n在外-->完成所有動作後才換行
* const int n = 5; 固定n,使其不易被改變
(const= constant)
* 要求使用者回答:get
ex: n = get_int("sized: ");
* truncation: to describe limitation to decimals


# Arrays
____

* clang:compile specific file(link source file into libary)
ex: clang example.c -o example
* **start counting at 0**

> * debugging: 
debug50 ./example
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_338365c9fe51cb38f064969be88fbb0f.png)
set a breakpoint(click on the red dot besides the lines)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_66d7d6c00c140a5e1440a72e2694db4e.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2704db1ceb05fa1272a8318d687f229d.png)
* when setting variables, give size
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8f337578a2b89e4f13902bf0b473b07d.png)
> **global variables:** Accessible from any part of the program, at the top.
**local variables:** Accessible only within the block or function, inside a function .

## Mathematic symbols:


| Symbol | Operator | Description                    | Example Code                       | Equivalent Code                 |
|--------|----------|--------------------------------|------------------------------------|---------------------------------|
| +      | `+`      | Addition                       | `int sum = a + b;`                 |                                 |
| -      | `-`      | Subtraction                    | `int difference = a - b;`          |                                 |
| *      | `*`      | Multiplication                 | `int product = a * b;`             |                                 |
| /      | `/`      | Division                       | `int quotient = a / b;`            |                                 |
| %      | `%`      | Modulus (remainder)            | `int remainder = a % b;`           |                                 |
| +=     | `+=`     | Addition Assignment            | `a += b;`                          | `a = a + b;`                    |
| -=     | `-=`     | Subtraction Assignment         | `a -= b;`                          | `a = a - b;`                    |
| *=     | `*=`     | Multiplication Assignment      | `a *= b;`                          | `a = a * b;`                    |
| /=     | `/=`     | Division Assignment            | `a /= b;`                          | `a = a / b;`                    |
| %=     | `%=`     | Modulus Assignment             | `a %= b;`                          | `a = a % b;`                    |
| ++     | `++`     | Increment                      | `a++;`                             | `a = a + 1;`                    |
| --     | `--`     | Decrement                      | `a--;`                             | `a = a - 1;`                    |
____
# prototype
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9472af72a25ee33eb49f3e9aa4cef886.png)
* ### 函數原型 (prototype 部分)
<pre>float average(int length, int array[]);</pre>
名為average的函數，float類型。兩個參數：int類型的長度和一個**整數數組(array)**。
* ### main部分
<pre>printf("Average:%f\n", average(N, scores));</pre>

打印平均值。將N和scores數組作為參數傳遞給它

* ### average部分
<pre>    {
        sum += array[i];
    }
    return sum / (float) length;</pre>
將前一項與這一項加起來，
>return 跟 printf 的差別是，return將值返回給 main 函數。這樣，main 函數可以做進一步處理，例如打印輸出或進行其他計算。

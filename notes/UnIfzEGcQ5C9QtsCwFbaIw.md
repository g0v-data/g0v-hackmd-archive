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

> ## **include <cs50.h>**
get_char - short for character,(letter, number, etc.) **(use '  ')**
get_double - 雙精度浮點數（即帶有小數點且精度較高的數字）
get_float - 浮點數
get_int - 整數
get_long - int但記憶體更大(4byte)
get_short -int但記憶體更小(2byte)
get_string - 一串字符的序列  **(use "")**



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
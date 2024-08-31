# C Language Notes
# ***1. c***
# **開發過程**
**規劃程式**
**編輯程式**
**編譯程式**
有引用標頭檔則此過程中會將它讀進來
**產生目的檔**
副檔名.obj或.o 是編譯過程中將原始檔轉譯成電腦指定的CPU機器語言所產生的中間產物
**連結程式**
將目的檔和函數庫連結在一起以產生一可執行檔
**產生可執行檔**
副檔名.exe 是一可獨立於作業系統下執行的程式
**程式執行**
# **基本結構**
**1.**
#include<stdio.h>    <font color="#1936C9">//引用stdio.h標頭檔</font>
int main<font color="#f00">()    </font> <font color="#1936C9">//主函式</font>
<font color="#f00">{</font>
   ...
   return <font color="#AC19C9">0</font>;     <font color="#1936C9">//無回傳值 ;則代表每一敘述的結束</font>
<font color="#f00">}</font>
**2.**
#include<stdio.h>    <font color="#1936C9">//引用stdio.h標頭檔</font>
#include<stdlib.h>
int main<font color="#f00">()    </font> <font color="#1936C9">//主函式</font>
<font color="#f00">{</font>
   ...
   system("pause");     <font color="#1936C9"> //system()函數包含在stdlib.h函式庫內，用來凍結視窗使螢幕顯示「請按任意鍵繼續...」</font>
   return <font color="#AC19C9">0</font>;     <font color="#1936C9">//無回傳值 ;則代表每一敘述的結束</font>
<font color="#f00">}</font>

# **資料處理概念**
* # **變數名稱的使用**
**變數定義**
將記憶體內某區塊保留，供未來程式放入資料使用。
**命名限制**
1. 第一個字元可為大寫字母、小寫字母或底線
2. 整體名稱可由大寫字母、小寫字母、底線或數字組成<font color="#f00">*阿拉伯數字不可作變數名稱開頭</font>
3. 不可以系統保留自作變數名稱(ex:auto,break,char.case,for...)
* # **基本資料型態**
<font color="#1936C9">**1. int: 整數**</font>

|    整數宣告型態    | 長度(位元) |        值的範圍        |
|:------------------:|:----------:|:----------------------:|
|        int         |     32     | -2147483648~2147483647 |
|     signed int     |     32     | -2147483648~2147483647 |
|    unsigned int    |     32     |      0~4294967295      |
| short int / short  |     16     |      -32768~32767      |
|  signed short int  |     16     |      -32768~32767      |
| unsigned short int |     16     |        0~65535         |
|  long int / long   |     32     | -2147483648~2147483647 |
|  signed long int   |     32     | -2147483648~2147483647 |
| unsigned long int  |     32     |      0~4294967295      |

**溢位(overflow)**
當整數變數值超過範圍時發生的現象，例如:設 short a=32767，a++原本該是32768，卻因超出short值的範圍而結果變為-327682的現象。
<font color="#1936C9">**2. float: 單精度浮點數**</font>
小數點以下更精確值時使用
| 浮點數宣告型態 | 長度(位元) |                                                                                                               值的範圍                                                                                                                |
|:--------------:|:----------:|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|     float      |     32     | ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_dd3420588557aa18da1705114c6347a8.png)~![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_392b579e33b20f5e3c5e12e34e1d2af8.png) |
|     double     |     64     | ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1f49033f95e6f2d015334fa6d7435cad.png)~![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3bad42dd16d39d39dfd596c7877367a9.png) |
<font color="#1936C9">**3. char: 字元**</font>


<font color="#1936C9">**4. double: 雙倍精度浮點數**</font>
* # **變數的宣告**
# ***2. c++***



# ***3. c#***

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

#include<stdio.h>    <font color="#1936C9">//引用stdio.h標頭檔</font>
int main<font color="#f00">()    </font> <font color="#1936C9">//主函式</font>
<font color="#f00">{</font>
   ...
   return <font color="#AC19C9">0</font>;     <font color="#1936C9">//無回傳值 ;則代表每一敘述的結束</font>
<font color="#f00">}</font>

---

#include<stdio.h>    <font color="#1936C9">//引用stdio.h標頭檔</font>
#include<stdlib.h>
int main<font color="#f00">()    </font> <font color="#1936C9">//主函式</font>
<font color="#f00">{</font>
   ...
   system("pause");     <font color="#1936C9"> //system()函數包含在stdlib.h函式庫內，用來凍結式窗使螢幕顯示「請按任意鍵繼續...」</font>
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
1. int: 整數

| Column 1 | Column 2 | Column 3 |
| -------- | -------- | -------- |
| Text     | Text     | Text     |

2. float: 單精度浮點數
3. char: 字元
4. double: 雙倍精度浮點數
* # **變數的宣告**
# ***2. c++***



# ***3. c#***

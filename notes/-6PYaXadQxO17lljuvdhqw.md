# shell script

## 背景
> 甚麼是shell
#### Kernel(核心)
## 實作
> 注意事項
- 指令的執行是從上而下、從左而右的分析與執行；
- 指令的下達就如同第四章內提到的： 指令、選項與參數間的多個空白都會被忽略掉；
- 空白行也將被忽略掉，並且 [tab] 按鍵所推開的空白同樣視為空白鍵；
- 如果讀取到一個 Enter 符號 (CR) ，就嘗試開始執行該行 (或該串) 命令；
- 至於如果一行的內容太多，則可以使用『 \[Enter] 』來延伸至下一行；
- 『 # 』可做為註解！任何加在 # 後面的資料將全部被視為註解文字而被忽略！

```
3.	[dmtsai@study ~]$ mkdir bin; cd bin  
4.	[dmtsai@study bin]$ vim hello.sh
5.	#!/bin/bash     
6.	# Program:
7.	#       This program shows "Hello World!" in your screen.
8.	# History:  
9.	# 2015/07/16	VBird	First release
10.	PATH=/bin:/sbin:/usr/bin:/usr/sbin:/usr/local/bin:/usr/local/sbin:~/bin
11.	export PATH
12.	echo -e "Hello World! \a \n"
13.	exit 0

```
# bat檔的使用小筆記
## 註解方式
標準是使用 rem，大小寫沒差別，另外可使用 2 個冒號來當註解符號。
* rem
* ::

## <font color="#e37c54">顯示訊息</font>
用來顯示訊息的指令是 echo，其後可加上字串或變數(可混搭)，在正常的情況下，批次檔中的每道指令執行前都會先出現螢幕上，使用 echo off 指令，就可以關閉顯示指令，通常在不需要互動的批次檔中都一定會出現。
```
@echo off
set /P myname=Please input your name:
echo Hello %myname%
echo.
echo Today is %date% %time%
pause
```


# SQL Agent啟動又停止
# 啟動時錯誤代碼7023 指定的会话名称已处于使用中

情境:SERVER中存在兩個或以上的SQL環境時，SQL Agent啟動時發生啟動又停止的情況。

要啟動SQL Agent之前要先到SQL 的組態管理員內將要啟動的SQL Agent打開，找到「服務」的頁籤，在「啟動模式」內選擇「自動」，接著「套用」設定。

通常套用完畢就能回到「登入」頁籤去啟動該服務，

因為有N個SQL Agent存在，所以會產生錯誤。

此時進入Windows內的「登錄編輯程式」內，然後照著順序進入：HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL11.SQL\SQLServerAgent

注意：「MSSQL11.SQL」這個名稱會依據不同電腦的設定而有所改變。

在Server Host 內打入np:servername

servername的部分可以在SQL SSMS內下@@servername的指令看到，譬如：DESKTOP-M4V123F\SQLSERVER

依據MSDN內解釋，具名執行個體會是'servername\instancename'這個格式，所以我們取用的時候只需要取前段的DESKTOP-M4V123F部分就可以了，所以我下在Server Host的指令會是np:DESKTOP-M4V123F，最後按下確定，再回到SQL組態管理員內去啟動SQL Agent即可。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_000249e960da4b9853da8ea21c78f5cb.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a5dee714a439bf41bd1bad5a94ba9042.png)


方法2:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_abca529173f8fba33e438cf59a8db0f2.png)
右鍵內容 選擇這個帳戶
帳戶名稱仿照上面其他的登入身分 不用輸入密碼直接確定就行了

如下圖登入身分為相同
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_53b9f8fc0aff1c4422170921990f13bf.png)




https://docs.microsoft.com/zh-tw/sql/t-sql/functions/servername-transact-sql?view=sql-server-ver15
https://dotblogs.com.tw/lanlith/2020/06/21/135248
https://i-freelancer.net/WebHelp/Qboss/SBP30R2_WebHelp/dzWO_TH.html
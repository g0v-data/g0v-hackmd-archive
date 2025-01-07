:::danger
Chainlon2 資訊管理用暫存區，公開頁面、嚴禁機密資料
:::
:::warning
目錄
[TOC]
:::

#### 常用連結
04-D4-C4-57-62-AD

Get-AppxPackage Microsoft.SecHealthUI -AllUsers | Reset-AppxPackage
O:\25資訊組\FPG\ERP\FPG.xlsx
7-Zip https://www.7-zip.org/a/7z2301-x64.exe
Chainlon 01Backup https://www.chainlon.net/1/01Backup.zip
https://tw.bitwar.net/course/tips/3528.html
#### Windows標準安裝
    前置作業： (最好先備份一次當前系統)關閉防毒
    自動安裝開始(要檢查，有缺的改用手動)：7-Zip、 OpenShell、Notepad++、01Backup(M1.bat+Dism全選清理硬碟)並刪除下載檔案
    curl https://www.chainlon.net/1/7z.msi -o C:\users\\%username%\Downloads\7z.msi
    curl https://www.chainlon.net/1/OpenShell.exe -o C:\users\\%username%\Downloads\OpenShell.exe
    curl https://www.chainlon.net/1/npp.exe -o C:\users\\%username%\Downloads\npp.exe
    timeout 5
    C:\users\\%username%\Downloads\7z.msi /quiet
    timeout 5
    C:\users\\%username%\Downloads\OpenShell.exe /qb START_MENU_FOLDER=0
    timeout 5
    C:\users\\%username%\Downloads\npp.exe /S
    timeout 5
    del C:\users\\%username%\Downloads\7z.msi /q
    del C:\users\\%username%\Downloads\npp.exe /q
    timeout 5
    del C:\users\\%username%\Downloads\OpenShell.exe /q
    Curl https://www.chainlon.net/1/01Backup.zip -o C:\users\\%username%\Downloads\01Backup.zip
    "C:\Program Files\7-Zip\7z.exe" x C:\users\\%username%\Downloads\01Backup.zip -oc:\ -y
    del C:\users\\%username%\Downloads\01Backup.zip /q
    cd\01Backup\tools
    m1.bat
    自動安裝結束
    手動補充安裝
    telnet client
    .Net Frame Work 3.5-，注意磁碟機代號
    dism /online /enable-feature /featurename:netfx3 /All /LimitAccess /Source:D:\sources\sxs
    磁碟清理(全選)
    cd Dism
    Dism++x64.exe 完成後重新開機一次，檢查系統是否正常

#### 設定共用設定檔並封裝
    1.	啟用預設帳戶：administrator 
        net user administrator /active:yes
        logoff
    2.	登入Administrator，刪除admin使用者設定檔
    3.	登入admin，進行標準環境設定作為範本如下方
        Edge-入門-設定完成-繼續但不登入
        系統內容-進階-設定-效能-高級-最佳效能、啟動和修復—小記憶體256KB、允許遠端桌面
        控制台—電源—高效能(限桌機)
        設定→隱私權，逐一手動關閉
        磁碟機設定：關閉磁碟碎片整理計劃、C:關閉索引
        檔案總管設定：關閉快速存取、顯示副檔名、及其他相關
        刪除無用捷徑：桌面Edge、工作列新聞、搜尋只要圖示
    4. 關閉並移除OneDrive、移除市集，登出
    5. 登入Administrator，取得Defprof並安裝，執行：C:\01Backup\Tools\Defprof.exe admin /NoAppx
    6.	顯示為成功，再進行Windows封裝
	Cd\windows\system32\sysprep
	Sysprep /generalize /shutdown /oobe
	進行備份以供異機還原：Ghost、HBS皆可

#### 允許資產管理LanSweeper(Dos)
curl https://www.chainlon.net/1/ls.zip -o C:\users\\%username%\Downloads\ls.zip
"C:\Program Files\7-Zip\7z.exe" x C:\users\\%username%\Downloads\ls.zip -oC:\01Backup\Tools\ -y
curl https://www.chainlon.net/1/ls.zip -o C:\03users\\%username%\Downloads\ls.zip
"C:\Program Files\7-Zip\7z.exe" x C:\03users\\%username%\Downloads\ls.zip -oC:\01Backup\Tools\ -y
c:
cd \01Backup\tools
M1.bat
del C:\users\\%username%\Downloads\ls.zip /q
del C:\03users\\%username%\Downloads\ls.zip /q

#### 以下尚未清理
Windows sysprep(重新封裝Windows以製作用戶端)
Cd\windows\system32\sysprep
Sysprep /generalize /shutdown /oobe

#### 常用指令：
顯示外部IP：curl ifconfig.me
顯示內部IP：ipconfig | find /i "IPv4" | find /i "192.168."
移除TFG
cd\Program Files (x86)\TFG\Agent
TFGInstallTool.exe -ForceUninstallMachineID
安裝Rdm RS.msi /quiet
設定Rdm C:\Windows\SysWOW64\rserver30\rserver3.exe /setup

系統管理專用共同目錄(後面要加上密碼)：(視環境擇一使用)
net use T: http://192.168.5.50/cy /u:admin
net use T: \\192.168.5.50\cy /u:admin
Xcopy "P:\21.MIS\01Backup\" "C:\01Backup\" /s /e /y /i /h /d
執行CMD管理員：
powershell Start-Process cmd -verb runas
#### 812用戶端環境
echo 刪除JAVA版本升級檢查：
reg delete "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Run" /v "SunJavaUpdateSched" /f
schtasks /delete /tn "Adobe Acrobat Update Task" /f
schtasks /delete /tn "OneDrive Per-Machine Standalone Update Task" /f
reg delete "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\AdobeARMservice" /f

chainlon Startup
C:\Users\chainlon\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup

All Users Desktop
C:\Users\Public\Desktop

All Users Desktop/Windows AD

@net use N: \\d6.chainlon.net\02Public\21.MIS\29ChainlonSoftware\misrun
區網速度測試
https://totusoft.com/files/LAN_SpeedTest.exe
區網速度測試目標
竹山
\\192.168.3.46\04Test
斗三
\\192.168.9.46\04Test
\\192.168.9.152\erp


cd\
"C:\Program Files\7-Zip\7z.exe" x C:\CY.zip -oc:\ -y
del C:\CY.zip /q
cd\01Backup\tools
m1.bat

Services for NFS
mount -o anon \\NFS_IP\NFS_share

### 暫存

MAS 啟動授權，powershell run:
irm https://massgrave.dev/get | iex

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_21760c94aa006b7dcd594944edab5210.png)

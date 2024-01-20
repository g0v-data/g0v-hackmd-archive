:::danger
Chainlon2 資訊管理用暫存區，公開頁面、嚴禁機密資料
:::
:::warning
目錄
[TOC]
:::
https://www.chainlon.net/vcf/101.vcf
https://p180907:4343/SMB/console/html/cgi/cgiChkMasterPwd.exe

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_45455a164fcda14a227a0df129d0db3e.png)

@reg add ”HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced” /v ”NoNetCrawling” /d ”1” /t REG_DWORD /f


del f:\2040DB_Backup\pubs.bak /q
"C:\Proqram Files\Microsoft SQL Server\80\Tools\Binn\sqlcmd.exe" -U sa -P password -Q "BACKUP DATABASE pubs TO DISK='f:\2040DB_Backup\pubs.bak'"
sqlcmd -U sa -P password -Q "BACKUP DATABASE DB_Name TO DISK = '\Folder\dbBackupname.bak' WITH INIT, SKIP" -o C:\01Backup\Log\dbBackuplog.txt
#### 常用連結
7-Zip https://www.7-zip.org/a/7z2301-x64.exe
Chainlon 01Backup https://www.chainlon.net/1/01Backup.zip
展頌小工具(包含AnyDesk,VPN)壓縮檔：http://www.chainlon.net/1/CYTools.zip
展頌小工具(包含AnyDesk,VPN)安裝檔：http://www.chainlon.net/1/CYTools.exe
VNC遠端遙控：http://www.chainlon.net/1/ChainlonVNC.exe
rdm參數檔1：http://web1.emax.net.tw/ken542014/Temp/newtstop.dat
rdm參數檔2：http://web1.emax.net.tw/ken542014/Temp/newtstop.dll
https://drive.google.com/uc?id=1e0quXt20XF8QZkpFgR4Wj-z1LYKLGrkM&export=download
curl hhttp://192.168.5.49:8080/Temp/ShowKeyPlus.zip -o C:\02Temp\ShowKeyPlus.zip

#### 程式安裝指令
powershell Start-Process cmd -verb runas
安裝7-Zip+ OpenShell+Notepad++
curl https://www.chainlon.net/1/7z.msi -o C:\users\\%username%\Downloads\7z.msi
curl https://www.chainlon.net/1/OpenShell.exe -o C:\users\\%username%\Downloads\OpenShell.exe
curl https://www.chainlon.net/1/npp.exe -o C:\users\\%username%\Downloads\npp.exe
C:\users\\%username%\Downloads\7z.msi /quiet
C:\users\\%username%\Downloads\OpenShell.exe /qb START_MENU_FOLDER=0
C:\users\\%username%\Downloads\npp.exe /S
del C:\users\\%username%\Downloads\7z.msi /q
del C:\users\\%username%\Downloads\npp.exe /q
timeout 5
del C:\users\\%username%\Downloads\OpenShell.exe /q
Curl https://www.chainlon.net/1/01Backup.zip -o C:\users\\%username%\Downloads\01Backup.zip
"C:\Program Files\7-Zip\7z.exe" x C:\users\\%username%\Downloads\01Backup.zip -oc:\ -y
del C:\users\\%username%\Downloads\01Backup.zip /q
cd\01Backup\tools
m1.bat
cd Dism
Dism++x64.exe
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
AcroRdrDC1900820071_zh_TW.exe /sAll
FontPack1900820071_XtdAlf_Lang_DC.msi /quiet /norestart
npp.exe /S

Windows sysprep(重新封裝Windows以製作用戶端)
Cd\windows\system32\sysprep
Sysprep /generalize /shutdown /oobe

#### 複製常用軟體或程式
cd\01Backup\Tools
copy P:\21.MIS\29ChainlonSoftware\TFG\TFG-Open.exe
copy P:\21.MIS\01Backup\Bat\Reboot.exe
#### 常用指令：
顯示外部IP：curl ifconfig.me
顯示內部IP：ipconfig | find /i "IPv4" | find /i "192.168."
移除TFG
cd\Program Files (x86)\TFG\Agent
TFGInstallTool.exe -ForceUninstallMachineID
安裝Rdm RS.msi /quiet
設定Rdm C:\Windows\SysWOW64\rserver30\rserver3.exe /setup
主機板可支援的最大記憶體上限：wmic memphysical get maxcapacity
系統管理專用共同目錄(後面要加上密碼)：(視環境擇一使用)
net use T: http://192.168.5.50/cy /u:admin
net use T: \\192.168.5.50\cy /u:admin
Xcopy "P:\21.MIS\01Backup\" "C:\01Backup\" /s /e /y /i /h /d
#### 812用戶端環境
echo 刪除JAVA版本升級檢查：
reg delete "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Run" /v "SunJavaUpdateSched" /f
schtasks /delete /tn "Adobe Acrobat Update Task" /f
schtasks /delete /tn "OneDrive Per-Machine Standalone Update Task" /f
reg delete "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\AdobeARMservice" /f


https://docs.google.com/spreadsheets/d/1LJ62xUzrUl3aX1xFNhoYd4pEslgml_j-LrRmXSZV45E/edit?usp=sharing

chainlon Startup
C:\Users\chainlon\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup

All Users Desktop
C:\Users\Public\Desktop

All Users Desktop/Windows AD


https://drive.google.com/file/d/1q5ZBUEutPBNNhGReOXYy5gFzlG4mpKNF/view
https://ithelp.ithome.com.tw/questions/10151926
https://dotblogs.com.tw/ghoseliang/2013/03/04/95113

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
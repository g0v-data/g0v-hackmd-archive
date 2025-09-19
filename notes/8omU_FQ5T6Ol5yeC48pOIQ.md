:::danger
Chainlon2 資訊管理用暫存區，公開頁面、嚴禁機密資料
:::
:::warning
目錄
[TOC]
:::
https://chainlon-my.sharepoint.com/:o:/g/personal/meeting_chainlon_net/EoV2aw0_b7VKvx231JwTa1sBxjVRSTShjEWiH-SVlsZJFg?e=wb9yeY

Remove-AppxPackage -Package NotepadPlusPlus_1.0.0.0_neutral__7njy0v32s6xk6

ipconfig | find /i "IPv4" | find /i "192.168." >> O:\25資訊組\Temp\Wanip.txt && curl ifconfig.me >> O:\25資訊組\Temp\Wanip.txt

reg add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System" /v InactivityTimeoutSecs /t REG_DWORD /d 1800 /f

9點關機：
schtasks /Create /TN "Shutdown" /TR "shutdown /s /t 0" /SC DAILY /ST 21:00 /RU SYSTEM /RL HIGHEST /F

Windows 閒置 30 分鐘自動鎖定
reg add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System" /v InactivityTimeoutSecs /t REG_DWORD /d 1800 /f

https://app.powerbi.com/groups/ea74a80c-0759-4de3-9a85-0c6d4c165b59/reports/9510db41-7352-4d9e-8444-795b93f36382/c5baaebd74dec3548c54?experience=power-bi
#### 常用連結
Get-AppxPackage Microsoft.SecHealthUI -AllUsers | Reset-AppxPackage
O:\25資訊組\FPG\ERP\FPG.xlsx
7-Zip https://www.7-zip.org/a/7z2301-x64.exe
Chainlon 01Backup https://www.chainlon.net/1/01Backup.zip
https://tw.bitwar.net/course/tips/3528.html
下載Brave
curl https://www.chainlon.net/1/Brave-portable.zip -o C:\App\Brave-portable.zip 
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
移除"所有內建APP"，使用前請三思。
power shell：Get-AppXProvisionedPackage -online | Remove-AppxProvisionedPackage –online

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
chainlon Startup
C:\Users\chainlon\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup

@net use N: \\d6.chainlon.net\02Public\21.MIS\29ChainlonSoftware\misrun
區網速度測試
https://totusoft.com/files/LAN_SpeedTest.exe

### 暫存

MAS 啟動授權，powershell run:
irm https://massgrave.dev/get | iex
irm https://get.activated.win | iex

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_21760c94aa006b7dcd594944edab5210.png)

![Uploading file..._2qsfooucv]()
1.開啟以上Log，看到Error，例如
Error SYSPRP Package Microsoft.LanguageExperiencePackzh-TW_19041.12.27.0_neutral__8wekyb3d8bbwe was installed for a user, but not provisioned for all users. This package will not function properly in the sysprep image.
2.Powershell中使用指令查詢系統當前的程式，匯出以方便文字搜尋
get-appxpackage -allusers | select name, packagefullname
3.在Powershell中使用指令移除這個有問題的程式
remove-appxpackage -allusers -package "Microsoft.LanguageExperiencePackzh-TW_19041.12.27.0_neutral__8wekyb3d8bbwe"
4.重新封裝sysprep
5.保持Windows Update到最新


remove-appxpackage -allusers -package "Microsoft.BingSearch_1.0.92.0_x64__8wekyb3d8bbwe"

滑鼠右鍵選單改為傳統，省得每次都要按Shift
reg add HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32 /ve /f
reg add "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /f /ve
https://codeload.github.com/Raphire/Win11Debloat/zip/refs/heads/master

機聯網效益和階段：設備感測-->系統整合-->智慧決策

一、連網、數據收集
連網、感測器、取得數據，監控中心

二、智慧分析與維護，可視化、跨系統整合
取得設備狀況與生產關聯性，優化生產、降低庫存
整合不同系統，即時戰情，從訂單到生產、出貨的一貫資訊

三、智慧工廠先不談，至少作到一眼決策
能耗、生產進度、供應鍊協同

隱藏和禁用Win10系統自帶的｢立即開會
https://allinfa.com/zh-tw/hide-close-win10-meet-now.html

https://www.autohotkey.com/

五、安裝到新電腦，使用異機還原
開始安裝：登入為chainlon，無密碼，僅須以下小修改
	1. m2.bat、AppMgmt移除市集(屬於個人用戶的設定，可忽略，這帳號不重要)
	2. 確認並修改電腦名稱、IP(特殊使用者) 須完成電腦盤點登記、電腦名稱修改、IP指派
		O:\25資訊組\網路硬體設備\ComputerList.xlsx
3. 設定本機帳號：C:\01Backup\Bat\Y1.bat
@echo off
set /p pwd1=Type password:
net user administrator /active:no
net user admin %pwd1%
net user chainlon %pwd1%
set /p pwd2=Type password:
@net user "assets" %pwd2% /add
@net user "assets" %pwd2%
@net user "assets" /expires:never
@net localgroup administrators "assets" /add
@wmic useraccount where name="assets" set PasswordExpires=False
重新開機再次確認



六、加入網域
1. 加入網域C:\01Backup\Bat\Y2.bat
@chcp 65001
@SET /P ans1=請輸入網域管理員帳號(格式：僅需輸入ID)：
@powershell add-computer -Credential chainlon\%ans1% -DomainName chainlon.net
@net localgroup "administrators" /add "chainlon\41"
@net localgroup "administrators" /add "chainlon\domain users"
@echo 注意：一般網域用戶已成為本機管理員，請登出重新登入開始使用者設定
2. 重新開機，以使用者身份登入開始作業，有管理員權限，可自由個人化電腦

七、額外補充安裝
1.	安裝附加軟體(TFG,Office…)
2.	安裝驅動程式、印表機
3.	將一般網域用戶離開本機管理員
@net localgroup "administrators" /delete "chainlon\domain users"
4.	其他項目交由使用者自行安裝，重新登出後即無管理權限

八、管理注意
1.是否需要固定IP：DHCP Server保留區，新增該電腦名稱、MAC、IP
2.資產管理掃描是否正常
3.該電腦網域使用者不可以有管理員權限
4.該電腦遠端桌面僅允許特定IP連入、特定用戶

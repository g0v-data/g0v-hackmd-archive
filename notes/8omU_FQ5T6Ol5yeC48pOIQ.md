:::danger
Chainlon2 資訊管理用暫存區，公開頁面、嚴禁機密資料
:::
:::warning
目錄
[TOC]
:::

#### 常用連結
Get-AppxPackage Microsoft.SecHealthUI -AllUsers | Reset-AppxPackage
O:\25資訊組\FPG\ERP\FPG.xlsx
7-Zip https://www.7-zip.org/a/7z2301-x64.exe
Chainlon 01Backup https://www.chainlon.net/1/01Backup.zip
https://tw.bitwar.net/course/tips/3528.html
下載Brave
curl https://www.chainlon.net/1/Brave-portable.zip -o C:\App\Brave-portable.zip 

#### 常用指令：
```
顯示外部IP：curl ifconfig.me
顯示內部IP：ipconfig | find /i "IPv4" | find /i "192.168."

移除TFG
cd\Program Files (x86)\TFG\Agent
TFGInstallTool.exe -ForceUninstallMachineID
安裝Rdm RS.msi /quiet
設定Rdm C:\Windows\SysWOW64\rserver30\rserver3.exe /setup
Xcopy "P:\21.MIS\01Backup\" "C:\01Backup\" /s /e /y /i /h /d

CY01+CY02檔案備份，注意路徑
robocopy O: G:\CY01 /mir /XD DfsrPrivate Z9-準備刪除
robocopy P: G:\CY02 /mir /XD __DFSR_DIAGNOSTICS_TEST_FOLDER__ DfsrPrivate

Windows 閒置 30 分鐘自動鎖定
reg add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System" /v InactivityTimeoutSecs /t REG_DWORD /d 1800 /f

個人化/鎖定畫面(要有檔案+Windows啟用)
@REG ADD "HKLM\SOFTWARE\Policies\Microsoft\Windows\Personalization" /v LockScreenImage /t REG_SZ /d "C:\01Backup\Tools\lockscreen.jpg" /f

Windows sysprep(重新封裝Windows以製作用戶端)
Cd\windows\system32\sysprep
Sysprep /generalize /shutdown /oobe
執行CMD管理員：
powershell Start-Process cmd -verb runas
滑鼠右鍵選單改為傳統，省得每次都要按Shift
reg add "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /f /ve

@降低選單延遲時間(400-->50)
reg add "HKEY_CURRENT_USER\Control Panel\Desktop" /v MenuShowDelay /t REG_SZ /d 50 /f

9點關機：
schtasks /Create /TN "Shutdown" /TR "shutdown /s /t 0" /SC DAILY /ST 21:00 /RU SYSTEM /RL HIGHEST /F
```

#### Windows標準安裝
```
curl https://www.chainlon.net/1/7z.msi -o C:\users\\%username%\Downloads\7z.msi
curl https://www.chainlon.net/1/OpenShell.exe -o C:\users\\%username%\Downloads\OpenShell.exe
curl https://www.chainlon.net/1/npp.exe -o C:\users\\%username%\Downloads\npp.exe
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
```


#### 812用戶端環境
chainlon Startup
C:\Users\chainlon\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup

@net use N: \\d6.chainlon.net\02Public\21.MIS\29ChainlonSoftware\misrun
區網速度測試
https://totusoft.com/files/LAN_SpeedTest.exe



#### Windows 部署安裝

五、安裝到新電腦，使用異機還原
開始安裝：登入為chainlon，無密碼，僅須以下小修改
	1. m2.bat、AppMgmt移除市集(屬於個人用戶的設定，可忽略，這帳號不重要)
	2. 確認並修改電腦名稱、IP(特殊使用者) 須完成電腦盤點登記、電腦名稱修改、IP指派
		O:\25資訊組\網路硬體設備\ComputerList.xlsx
3. 設定本機帳號：C:\01Backup\Bat\Y1.bat

```
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
```
重新開機再次確認



六、加入網域
1. 加入網域C:\01Backup\Bat\Y2.bat
```
@chcp 65001
@SET /P ans1=請輸入網域管理員帳號(格式：僅需輸入ID)：
@powershell add-computer -Credential chainlon\%ans1% -DomainName chainlon.net
@net localgroup "administrators" /add "chainlon\41"
@net localgroup "administrators" /add "chainlon\domain users"
@echo 注意：一般網域用戶已成為本機管理員，請登出重新登入開始使用者設定
```
2. 重新開機，以使用者身份登入開始作業，有管理員權限，可自由個人化電腦

七、額外補充安裝
1.	安裝附加軟體(TFG,Office…)
2.	安裝驅動程式、印表機
3.	將一般網域用戶離開本機管理員
`@net localgroup "administrators" /delete "chainlon\domain users"`
4.	其他項目交由使用者自行安裝，重新登出後即無管理權限

八、管理注意
1.是否需要固定IP：DHCP Server保留區，新增該電腦名稱、MAC、IP
2.資產管理掃描是否正常
3.該電腦網域使用者不可以有管理員權限
4.該電腦遠端桌面僅允許特定IP連入、特定用戶

### 暫存

MAS 啟動授權，powershell run:
```
irm https://massgrave.dev/get | iex
irm https://get.activated.win | iex
```

https://codeload.github.com/Raphire/Win11Debloat/zip/refs/heads/master

隱藏和禁用Win10系統自帶的｢立即開會
https://allinfa.com/zh-tw/hide-close-win10-meet-now.html

https://www.autohotkey.com/




```


# 檔案名稱建議：Remove-SysprepBlockers.ps1
# 請以系統管理員身分執行

Write-Host "開始檢查並移除可能阻擋 Sysprep 的 Appx 套件..." -ForegroundColor Cyan

# 取得所有使用者的 Appx 套件
$packages = Get-AppxPackage -AllUsers

foreach ($pkg in $packages) {
    # 常見阻擋 Sysprep 的套件：語言體驗包、Microsoft Store App、Xbox、Zune、Skype 等
    if ($pkg.Name -match "LanguageExperiencePack" -or
        $pkg.Name -match "Xbox" -or
        $pkg.Name -match "Zune" -or
        $pkg.Name -match "Skype" -or
        $pkg.Name -match "Microsoft.People" -or
        $pkg.Name -match "Microsoft.Microsoft3DViewer" -or
        $pkg.Name -match "Microsoft.MSPaint") {

        Write-Host "移除套件: $($pkg.Name)" -ForegroundColor Yellow
        try {
            Remove-AppxPackage -AllUsers -Package $pkg.PackageFullName -ErrorAction SilentlyContinue
            dism /online /Remove-ProvisionedAppxPackage /PackageName:$pkg.PackageFullName | Out-Null
        } catch {
            Write-Host "移除失敗: $($pkg.Name) - $($_.Exception.Message)" -ForegroundColor Red
        }
    }
}

Write-Host "檢查完成。請重新執行 Sysprep。" -ForegroundColor Green
```
Set-ExecutionPolicy Bypass -Scope Process -Force
.\Remove-SysprepBlockers.ps1
sysprep /generalize /oobe /shutdown


https://www.ute.com/tw/ezsetup

```
[HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\FeatureManagement\Overrides\14\2792562829]
"EnabledState"=dword:00000001
"EnabledStateOptions"=dword:00000000

[HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\FeatureManagement\Overrides\14\3036241548]
"EnabledState"=dword:00000001
"EnabledStateOptions"=dword:00000000

[HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\FeatureManagement\Overrides\14\734731404]
"EnabledState"=dword:00000001
"EnabledStateOptions"=dword:00000000
```
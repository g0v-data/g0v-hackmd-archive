note1





!#取得BIOS SN & OEM KEY
wmic bios get serialnumber
wmic path softwarelicensingservice get OA3xOriginalProductKey

wmic baseboard get product,Manufacturer,version,serialnumber


---


備份序號 & OS
安裝OS & 測試序號
	若序號啟用失敗，則還原OS然後直接升級，啟用序號，
	沒問題後再重灌OS

安裝OS
移除APP及開始畫面釘選項目
更新Windows & Store

安裝驅動程式

安裝office 2013
更新
修改寄送大小限制為20MB

安裝日文輸入法

安裝軟體
7-ZIP > 設定關聯性
Chrome
Adobe Reader > 更新
OpenVPN > 複製設定檔 > 測試
印表機
AutoCAD LT

調整預設應用程式 [ 網頁瀏覽器 ] 和 [ Adobe ]
停用意見反應

開啟防火牆
	icmp
	netsh advfirewall firewall add rule name="ICMP Allow incoming V4 echo request" protocol=icmpv4:8,any dir=in action=allow
	遠端桌面
	遠端管理
	防火牆遠端管理

複製 AnyDesk & TeamViewerQS 到 [ 文件\遠端桌面協助軟體 ]

刪除桌面捷徑 & 複製 [桌面捷徑] 到桌面

關閉還原
開啟遠端桌面

設定mail
LDAP
內部共用通訊錄

	
增加pop設定
	
垃圾郵件
	Reg add "HKCU\software\policies\microsoft\office\15.0\outlook\options\mail" /v junkmailprotection /t REG_DWORD /d 0x6 /f
	Reg add "HKCU\software\policies\microsoft\office\15.0\outlook\options\mail" /v outlookenablespoofyemails /t REG_DWORD /d 0x0 /f
	Reg add "HKCU\software\policies\microsoft\office\15.0\outlook\options\mail" /v junkmailenablelinks /t REG_DWORD /d 0x0 /f
	
關閉讀取窗格
Reg add "HKCU\Software\Policies\Microsoft\office\15.0\outlook\options" /v disablereadingpane /t REG_DWORD /d 0x1 /f
	
不要傳送回條
Reg add "HKCU\Software\Policies\Microsoft\Office\15.0\Outlook\Options\Mail" /v "Receipt Response" /t REG_DWORD /d 0x1 /f
	
Reg add "HKCU\SOFTWARE\Policies\Microsoft\Office\15.0\Outlook\Options\General" /v "AutoProcRcpts" /t REG_DWORD /d 0x0 /f
Reg add "HKCU\SOFTWARE\Policies\Microsoft\Office\15.0\Outlook\Options\General" /v "AutoProcReq" /t REG_DWORD /d 0x0 /f
	
Reg Query "HKEY_CURRENT_USER\software\policies\microsoft\office\15.0\outlook\options"
	

新增admin
net user admin /add
net localgroup Administrators admin /add
Set-LocalUser -Name "admin" -PasswordNeverExpires 1

net user user 


清除紀錄

重開機測試

備份


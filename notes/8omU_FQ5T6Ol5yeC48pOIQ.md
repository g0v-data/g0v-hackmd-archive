:::danger
Chainlon2 資訊管理用暫存區，公開頁面、嚴禁機密資料
:::
:::warning
目錄
[TOC]
:::
https://www.youtube.com/watch?v=vZXD3-SAnkE&t=107s
https://join.skype.com/p2NkbssUvTC1
docker run -d --network=host -v open-webui:/app/backend/data -e OLLAMA_BASE_URL=http://127.0.0.1:11434 --name open-webui --restart always ghcr.io/open-webui/open-webui:main
#### 常用連結
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

https://drive.google.com/file/d/1KZOfo9z0gUJQjO1QO10m5eh1gyoIVuja/view?usp=sharing
https://docs.google.com/spreadsheets/d/1Ndt5H3dUxXh_n0zgCKrz2EVQQWcEaFl4oHHyYhHvAOk/edit?usp=sharing

機聯網效益和階段：設備感測-->系統整合-->智慧決策

一、連網、數據收集
連網、感測器、取得數據，監控中心

二、智慧分析與維護，可視化、跨系統整合
取得設備狀況與生產關聯性，優化生產、降低庫存
整合不同系統，即時戰情，從訂單到生產、出貨的一貫資訊

三、智慧工廠先不談，至少作到一眼決策
能耗、生產進度、供應鍊協同

我的建議：
1.網路架設屬於現場連網設備，應獨立報價
2.重新提報最小可行性方案，在連網完成情況下，采威願意提供的最小方案是什麼？後續增加的點數怎麼計算？
例如：竹山廠3F紡紗機*10點，含監視中控台及告警
後續增加點數：費用000*數量+到場安裝調適*數量

采威規劃的問題/Ken
1.P15，第一階段不包含ERP串接，是刻意誤導或資料膨脹？
2.P13，P17，設備告警是超簡單功能，機台既已連網，為何要第二期才能實現？
3.不要客制，把你們既有的機聯網方案拿出來用，如果『每一個專案都是客制』，那是話術
..簡單舉例：ERP全客制？這是自架團隊做的事，不是SI公司，先把『標準功能』拿出來試用，再搭配『客戶需求的客制或修改』，這樣才對，如果100%客制，請簽約，包含程式碼提交、權利分配、允許雙方商用等等
4.P15，不要管外廠設備，除非確認外廠可以分享機器設備細節，這類的設備要獨立報價
5.P17-P23，生產流程可視化立意良善，但單是資料清理、整併、跨系統整合，要多久？卻寫在第一階段
6.P26-27，能源管理平台已在洽談中，暫時不要加入評估，只要有設備能耗資料
7.P23-24，請說明電腦架構和使用情境、規格
8.P33，第一階段沒有跨系統整合，不可能看到生產排程、完工進度

一、能源監控系統
1. 電力（電壓、電流、功率、用電量）
2. 水（用水量、流量、壓力）
3. 空壓系統（壓力、流量、用電量、漏氣偵測）
4. 冰水系統（冷媒壓力、冷媒溫度、冷卻水出入口溫度、COP值、kw/RT）
5. 針對建築內各種能源設備進行整合管理（照明、空調、電梯）
二、空壓機及水水機系統智能監控
1. 各設備用電情況
2. 智能監控自動調節最佳用電
3. 尖峰預測，並協助調整或削減負載
4. 成本分析
三、製程效能監控，可進行生產能效分析（各機台耗電量）
1. 乾燥系統
2. 押出機
3. 冷卻
4. 牽伸
5. 捲取
四、戰情室生產管理
1. 稼動率、生產中未掛紡機台（清洗機台、故障機台、改紡機台、斷絲機台）
2. 可統計：滿管率、斷絲次、交換成功率、掛絲停機時間
五、條件卡與客訴管理
1. 條件卡連動生產統計效率，作為效率改善起點
2. 系統判讀條件卡生產效率建議最佳化改善方式
3. 系統提醒批號規格以往客訴反映問題
4. 系統與條件卡作為互聯紀錄，改善生產效率及客戶反映問題
六、碳排監控與 ESG 報告
1. 將能源數據自動換算為碳排量
2. 支援碳盤查報表對應格式
3. 能源節約與減碳成效追蹤

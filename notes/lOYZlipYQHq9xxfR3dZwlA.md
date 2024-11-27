EFK
一、正式上版主機
1.修改appsettings
1.1新增Serilog設定
1.2修改path路徑(寫log位置)
2.下載最新fluent-bit的zip檔
3.在正式機D:槽新增ProgramFiles\fluent-bit的資料夾
4.將Fluent-bit.zip在此解壓所
5.先copy 商火的設定檔進行修改
  5.1.fluent-bit.conf
    5.1.1.修改log_level -> error
    5.1.2.新增log_file(可絕對路進)
    5.1.3.修改parsers_file(可絕對路進)
    5.1.4.修改plugins_file(可絕對路進)
    5.1.5.修改[INPUT]
    5.1.6.修改[FILTER]
    5.1.7.修改[OUTPUT]
  5.2.fluent-bit.lua
  5.3.fluent-bit-parser.conf
  5.4.parsers.conf
  5.5.plugins.conf
6.新增建立Windows服務
sc.exe create fluent-bit binPath= "D:\ProgramFiles\fluent-bit\bin\fluent-bit.exe -c D:\ProgramFiles\fluent-bit\conf\fluent-bit.conf"
7.啟動服務並設定成自動啟動
8.在EFK建立Space
9.設定DataView
10.後續動作
 10.1.申請定期清fluent-bit Log
 10.2申請定期清Web及Api Log

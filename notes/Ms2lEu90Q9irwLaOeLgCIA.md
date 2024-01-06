# 筆記

---
advosol文件-OpcDaNet.Net4.dll
https://advosol.com/manuals/opcdanet/webframe.html
https://advosol.com/manuals/opcdanet/topic23.html
advosol錯誤代碼
https://advosol.com/Manuals/DanSrv/topic39.html

---


用c#製做和安裝service心得整理
https://sites.google.com/site/willsnote/Home/services
Windows 服务 同时启动多个服务
http://dlgcy.com/windows-service-multi/
C#写一个Windows服务程序，启动多个service的问题
https://bbs.csdn.net/topics/70466914


---

c#連接mongodb-連接資料庫與資料新增
https://salu099.github.io/blog/2018/04/blog-csharp-mongodb-insert/
c#連接mongodb-資料查詢
https://salu099.github.io/blog/2018/04/blog-csharp-mongodb-query/
MongoDB——BsonDocument
https://blog.csdn.net/Shiyaru1314/article/details/52442957


---

Linq loop in C#
https://kodify.net/csharp/loop/range/
DataSet 欄位及資料行的屬性使用方式
https://jeterh.blogspot.com/2013/01/cdataset.html

---

使用批次檔使系統啟動時自動啟動服務
https://christmasq.wordpress.com/2016/10/13/win7-%E5%A6%82%E4%BD%95%E5%9C%A8%E7%B3%BB%E7%B5%B1%E5%95%9F%E5%8B%95%E6%99%82%E8%87%AA%E5%8B%95%E5%95%9F%E5%8B%95%E6%9C%8D%E5%8B%99/

---
使用者權限指派 MS技術文件
https://docs.microsoft.com/zh-tw/windows/security/threat-protection/security-policy-settings/user-rights-assignment
建立通用物件	     SeCreateGlobalPrivilege
建立永久共用物件    SeCreatePermanentPrivilege

Object picker UI
https://docs.microsoft.com/en-us/previous-versions/orphan-topics/ws.11/dn789205(v=ws.11)?redirectedfrom=MSDN

---
使用Global\前 建立使用者權限指派
1.系統管理工具>本機安全性原則(secpol.msc,本地安全策略)
2.本機原則展開>使用者權限指派
3.右窗格>建立全域物件SeCreateGlobalPrivilege
4.於本機安全性原則設定>新增
5.選取使用者or群組↑Object picker UI>加入Guest、Everyone、SYSTEM
# DBeaver

## 使用Oracle驅動出現 locale not recognized
DBeaver 啟動時會判斷電腦的語系並自動切換為中文，透過界面上調整語系後卻出現存取錯誤的訊息：
Can't save startup configuration - access denied. You could try to change national locale manually in '/usr/share/dbeaver/dbeaver.ini'. Refer to readme.txt file for details. /usr/share/dbeaver/dbeaver.ini /usr/share/dbeaver/dbeaver.ini

在讀了 readme.txt 後依照說明在 **dbeaver.ini** 新增 -nl en 但重啟軟體還是無效，最後在網路上找到在 --add-modules 下方，新增 -Duser.language=en 就解決了，如下
--add-modules=ALL-SYSTEM
-Duser.language=en <= 增加這行
-Xms64m
-Xmx1600m

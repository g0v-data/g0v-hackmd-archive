# Debian 打包筆記

分享將source code打包成deb file的流程與指令
* 打包deb package必備套件
apt-get install debhelper devscripts automake dh-make

* 打包流程圖
![image](https://hackmd.io/_uploads/r1L345CIR.png)


* 產生一個source code package
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b9367d8230ceecfcef81439d0036ebce.png)


* 將source code package打包成.tar.gz
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c16fc9494f5a767fc3ae40c66be5b8b3.png)
DEBMAIL:作者的信箱
DEBFULLNAME:作者姓名
檔名格式:<Package>-<versoin>
* dh_make指令：
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ff21d7d39b5036f45916a5a39677f161.png)
成功後會產生 debian
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2aca26cdf43a4716787bb04a5d56f547.png)

介紹debian內容:

* control:
![image](https://hackmd.io/_uploads/r1-5lPRIA.png)

    Section: package進入發行版本的分類。
    分為main(自由軟體)、non-free(非自由軟體)、contrib(依賴於非自由軟件的自由軟件)、admin(供系統管理員使用)、devel(開發工具)、doc(文檔)、libs（庫）、x11(不屬於其他分類的x11).....。

    Priority:安裝優先級。

    Architecture:標示package適用於何種cpu架構。all:不需要根據cpu做區分，編譯成一個package即可。any:表示四種cpu架構須分別編譯會產生四個package。
四種cpu架構:amd64、i386、armhf、arm64。

    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a85bc14a9f48e2dc1573b259c8dd3469.png)

* copyright:包含上游軟體的版權及LICENSE認證等資訊。
執行dh_make後，自行產生的內容。
![image](https://hackmd.io/_uploads/ryrqXPR8C.png)
debian官方教學中的copyright。
![image](https://hackmd.io/_uploads/r1j0jwCL0.png)

    
* changelog:包含軟體名稱、版本、發行版本和修改內容等資訊。
![image](https://hackmd.io/_uploads/SkiAEDALA.png)

* rules:rules就像Makefile一樣，包含許多rules，以target名稱作為參數調用dh_*指令。

![image](https://hackmd.io/_uploads/S1tjRSC80.png)
% -> "任何targets"。
dh$@ -> 執行dh_*指令。
    
覆寫rules的dh_*指令
![image](https://hackmd.io/_uploads/r1hGvDA80.png)

* 其他檔案
preinst(preinstallation):安裝.deb前的腳本。
postinst(postinstallation):執行安裝後的configg
prerm(preremove):刪除.deb前的腳本，一般用於停止service之類的操作。
postrm(postremove):刪除.deb後的腳本，可執行刪除捷徑等工作。



* 打包deb檔
![image](https://hackmd.io/_uploads/S1a7ASC8A.png)
![image](https://hackmd.io/_uploads/SJxSRB08R.png)

* 安裝.deb
![image](https://hackmd.io/_uploads/Sk5vk8A8C.png)

* 顯示control內容
![image](https://hackmd.io/_uploads/SJHeZL08A.png)

* 確認安裝後檔案位置
![image](https://hackmd.io/_uploads/H1LMG80LA.png)

待解問題：
如何將檔案安裝到指定路徑
1.在Makefile指定安裝路徑
2.在debian 新增xxxx.install
https://www.debian.org/doc/manuals/maint-guide/dother.zh-cn.html
https://www.debian.org/doc/manuals/debmake-doc/ch05.zh-tw.html#simplerules
 > **參考來源**
https://www.debian.org/doc/manuals/maint-guide/dreq.zh-cn.html.
https://github.com/Rickylss/Notes/blob/write/Debain%E7%BB%B4%E6%8A%A4%E8%80%85%E6%8C%87%E5%8D%97/deb%E6%89%93%E5%8C%85%E5%B7%A5%E4%BD%9C%E6%B5%81.md
---


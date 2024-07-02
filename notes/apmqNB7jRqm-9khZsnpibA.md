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
檔名格式必須是<PackageName>-<versoin>
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2b93b02f50352d9ef8cd26ae9199a5ce.png)
* dh_make指令：
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ff21d7d39b5036f45916a5a39677f161.png)
成功後會產生 debian
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2aca26cdf43a4716787bb04a5d56f547.png)

介紹debian內容:

* control:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9e98bf325181a1bb17c2db01dbaafa55.png)


    Section: package進入發行版本的分類。
    分為main(自由軟體)、non-free(非自由軟體)、contrib(依賴於非自由軟件的自由軟件)、admin(供系統管理員使用)、devel(開發工具)、doc(文檔)、libs（庫）、x11(不屬於其他分類的x11).....。

    Priority:安裝優先級。

    Architecture:標示package適用於何種cpu架構。all:不需要根據cpu做區分，編譯成一個package即可。any:表示四種cpu架構須分別編譯會產生四個package。
四種cpu架構:amd64、i386、armhf、arm64。

    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a85bc14a9f48e2dc1573b259c8dd3469.png)

* copyright:包含上游軟體的版權及LICENSE認證等資訊。
執行dh_make後，自行產生的內容。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c00803d3ac5c9a09b718eaac24dc80d5.png)

debian官方教學中的copyright。
![image](https://hackmd.io/_uploads/r1j0jwCL0.png)

    
* changelog:包含軟體名稱、版本、發行版本和修改內容等資訊。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_afaa80162178c92ffe7da79fd39b7b38.png)


* rules:rules就像Makefile一樣，包含許多rules，以target名稱作為參數調用dh_*指令。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5287358efd18cd2e194a3ea99ef72feb.png)

% -> "任何targets"。
dh$@ -> 執行dh_*指令。
    
覆寫rules的dh_*指令
https://github.com/oerdnj/cmake/blob/master/debian/rules

* 其他檔案
preinst(preinstallation):安裝.deb前的腳本。
postinst(postinstallation):執行安裝後的configg
prerm(preremove):刪除.deb前的腳本，一般用於停止service之類的操作。
postrm(postremove):刪除.deb後的腳本，可執行刪除捷徑等工作。



* 打包deb檔
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f0d91427fcc741530e4c7ce9112a0a34.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_852fb489a830ac37c3fd62c403a88d15.png)


* 安裝.deb
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4d9f3810735d095ee59c842049bf4270.png)


* 顯示control內容
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cab64c6da73e2f4330d5a4330c827f9a.png)

* 確認安裝後檔案位置
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b7ed13b3555d38bef083f6f59b340623.png)


待解問題：
如何將檔案安裝到指定路徑
https://github.com/exoscale/pkg-qemu/blob/precise/debian/control
https://github.com/oerdnj/cmake/blob/master/debian/control
1.在Makefile指定安裝路徑
https://docs.deepin.org/info/%E5%BC%80%E5%8F%91%E8%BF%9B%E9%98%B6/%E9%80%82%E9%85%8D%E8%AE%A4%E8%AF%81/%E8%AE%A4%E8%AF%81%E6%8A%80%E6%9C%AF%E9%97%AE%E9%A2%98/%E8%AE%A4%E8%AF%81%E6%8A%80%E6%9C%AF%E9%97%AE%E9%A2%98/%E6%BA%90%E7%A0%81%E6%89%93%E5%8C%85%E4%B8%BAdeb
2.在debian 新增xxxx.install
https://www.debian.org/doc/manuals/maint-guide/dother.zh-cn.html
https://www.debian.org/doc/manuals/debmake-doc/ch05.zh-tw.html#simplerules
 > **參考來源**
https://www.debian.org/doc/manuals/maint-guide/dreq.zh-cn.html.
https://github.com/Rickylss/Notes/blob/write/Debain%E7%BB%B4%E6%8A%A4%E8%80%85%E6%8C%87%E5%8D%97/deb%E6%89%93%E5%8C%85%E5%B7%A5%E4%BD%9C%E6%B5%81.md
---


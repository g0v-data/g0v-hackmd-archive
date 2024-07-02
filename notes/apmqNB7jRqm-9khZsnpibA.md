# Debian 打包筆記

分享將source code打包成deb的流程與指令
* 打包deb package必備套件
apt-get install debhelper devscripts automake dh-make

* 打包流程圖

     ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a26f787e2f9787482585df1b9e63c95d.png)

* 產生一個source code package



* 將source code package打包成.tar.gz

    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c16fc9494f5a767fc3ae40c66be5b8b3.png)
    DEBMAIL:作者的信箱
    DEBFULLNAME:作者姓名
    
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_76555ba830a86bdbe78ef4f415dc0dd7.png)
    檔名格式必須是<PackageName>-<versoin>
* dh_make指令：

    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4768150a96252c1151500a60aaa52c66.png)

    成功後會產生 debian
    
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2aca26cdf43a4716787bb04a5d56f547.png)

> 介紹debian內容

* control:

    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9e98bf325181a1bb17c2db01dbaafa55.png)


    Section: package進入發行版本的分類。
    分為main(自由軟體)、non-free(非自由軟體)、contrib(依賴於非自由軟件的自由軟件)、admin(供系統管理員使用)、devel(開發工具)、doc(文檔)、libs（庫）、x11(不屬於其他分類的x11).....。

    Priority: 安裝優先級。
    optional: 新的套件不和上面優先權套件衝突時通常使用該權限。
    extra: 新的套件和上面優先權套件衝突時使用該權限。
    
    Build-Depends: 編譯此軟體包需要的軟體包。
    Build-Depends-Indep:作為Build-Depends的附加。
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a85bc14a9f48e2dc1573b259c8dd3469.png)
    Depends： 寫明Package所必須的套件。
    Recommends： 當用戶安裝軟體包時，所有前端工具都會詢問是否要安裝這些推薦的軟體包。
    Conflicts： 當所有衝突的套件都已經刪除後此套件才可以安裝。
    
    Architecture: 標示package適用於何種cpu架構。
    all: 套件和平台無關，可能是文件、圖片會是直譯式的語言套件。
    any： 任何平台皆可，通常是需要編譯的套件。
    
    Q: debhelper是如何在x86平台編譯出適合所有cpu的deb檔?
    A: 編譯package的過程中，自動編譯系統會根據Build-Depends的設定下載相關套件並對 Architecture: any 的軟件包，重構和建立適合所有架構的deb檔。
    
* copyright: 包含上游軟體的版權及LICENSE認證等資訊。

    執行dh_make後，自行產生的內容。
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c00803d3ac5c9a09b718eaac24dc80d5.png)
    
    pkg-qemu的copyright
    https://github.com/exoscale/pkg-qemu/blob/precise/debian/copyright
    cmake的copyright
    https://github.com/oerdnj/cmake/blob/master/debian/copyright
    
* changelog: 包含軟體名稱、版本、發行版本和修改內容等資訊。

    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_afaa80162178c92ffe7da79fd39b7b38.png)


* rules: rules就像Makefile一樣，包含許多rules，以target名稱作為參數調用dh_*指令。

    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5287358efd18cd2e194a3ea99ef72feb.png)

    % -> 所有target。
    dh$@ -> 執行dh_*指令。
    詳細內容可參考官網文件：
https://www.debian.org/doc/manuals/maint-guide/dreq.zh-tw.html#control
    覆寫rules的dh_*指令
    https://github.com/oerdnj/cmake/blob/master/debian/rules

* 其他檔案
    preinst(preinstallation): 安裝.deb前的腳本。
    postinst(postinstallation): 執行安裝後的configg
    prerm(preremove): 刪除.deb前的腳本，一般用於停止service之類的操作。
    postrm(postremove): 刪除.deb後的腳本，可執行刪除捷徑等工作。
    package.cron.*： 在希望的時間下運行package。
    
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3c2a0f88f9f7e0d505886ae053d2f4c0.png)


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
https://pi3g.com/zh/creating-configuration-files-in-etc-in-debian-packages/
https://www.debian.org/doc/manuals/maint-guide/dother.zh-cn.html
https://www.debian.org/doc/manuals/debmake-doc/ch05.zh-tw.html#simplerules
 > **參考來源**
https://www.debian.org/doc/manuals/maint-guide/dreq.zh-cn.html.
https://github.com/Rickylss/Notes/blob/write/Debain%E7%BB%B4%E6%8A%A4%E8%80%85%E6%8C%87%E5%8D%97/deb%E6%89%93%E5%8C%85%E5%B7%A5%E4%BD%9C%E6%B5%81.md
https://wen00072.github.io/blog/2014/06/10/package-debian-packages-study-on-the-debian-directory/
---


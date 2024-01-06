---
title: "Instant Setup hack.g0v.tw for Windows Users"
tags: 開發環境,hackpad
---

# Instant Setup hack.g0v.tw for Windows Users

> [點此觀看原始內容](https://g0v.hackpad.tw/L0mEqjsanOA)

快速上手：架好 hack.g0v.tw 專案的開發環境 (Windows)

**NOTE**: 這邊的資訊已經過舊，新版 hack.g0v.tw 可以在 windows 上直接裝好 nodejs 後用 gulp （按照 readme 的步驟跑起來）

注意：**以下步驟最好事先在自己家裡完成**，不要到會場才做，不然網路可能會爆炸慢，尤其是 Part 2 的「下載虛擬電腦」要抓的 .box 檔案很大，我用 50M 光纖抓了 25 分鐘才抓完 = =b


## Part 1：建立專案資料夾


### 安裝 github for Windows

1.  下載：[http://windows.github.com/](http://windows.github.com/) 右上角「download」
2.  安裝：執行 GitHubSetup.exe
3.  登入：打開 github for Windows，登入或註冊你的 github 帳號
> 什麼是 github
> [name=ET B]

> 為什麼要裝 github for Windows
> [name=ET B]


### 複製 hack.g0v.tw 專案資料夾到自己的電腦

1.  打開專案頁面： [https://github.com/g0v/hack.g0v.tw](https://github.com/g0v/hack.g0v.tw)
2.  複製：按下「Clone in Windows」按鈕，按鈕在頁面左邊中上的位置。按下後，github for Windows 會自動下載專案資料夾。
3.  看檔案：下載的專案資料夾預設的位置會在 C:\\Users\\ETBlue(替換成你的使用者名稱)\\My Documents\\github\


## Part 2：架設開發環境


### 安裝 vagrant

1.  下載：[http://downloads.vagrantup.com/tags/v1.2.2](http://downloads.vagrantup.com/tags/v1.2.2)
2.  安裝：執行 Vagrant_1.2.2.msi
> 安裝完以後程式集沒有多出東西來，不代表沒裝好，他只是沒有 gui 、要從 command line 才看的到而已。
> [name=ET B]

> 什麼是 vagrant
> [name=ET B]

> vagrant 是一個電腦程式，人類可以把好幾件想做的事情寫在一張筆記（vagrant file）上，vagrant 程式會按照人類寫的筆記，自動把所有事情都做好。
> [name=ET B]

> 為什麼架設環境的時候要用到 vagrant
> [name=ET B]

> 因為 clkao 在寫程式的時候喜歡用很多有的沒的外掛，如果想跟他一起寫程式，儘管我們只是寫個 html 或 css，也得跟著他一起安裝一堆有的沒的外掛，才能在自己的電腦預覽修改的結果，否則就只能矇眼射箭，看不到頁面改完以後長什麼樣子。
> [name=ET B]

> 裝外掛的過程眉眉角角很多，等裝完黑客松都結束了，所以我們決定叫 clkao 事先把所有要裝的東西寫好在一張筆記（vagrant file）上， 讓 vagrant 按照 clkao 的指示幫我們裝，這樣我們一到黑客松現場就可以馬上架好環境、捲袖子做事了。
> [name=ET B]


> 現在已經不用橋了，hack.g0v.tw裡面就會附上
> [name=ET B]

### ~橋好 vagrant 設定檔~

1.  ~下載：~[~https://dl.dropboxusercontent.com/u/4339854/g0v/Vagrantfile~](https://dl.dropboxusercontent.com/u/4339854/g0v/Vagrantfile)
2.  ~橋好：放到 hack.g0v.tw 的 repo 資料夾中~
> ~什麼是 hack.g0v.tw~
> [name=ET B]

> ~專案的名稱，clkao 取的。指的是開發 g0v hackfoldr 的這個專案。~
> [name=ET B]

> ~什麼是 repo~
> [name=ET B]

> ~repo 資料夾在哪裡~
> [name=ET B]


### 使用討人厭的 terminal 下載虛擬電腦

1.  打開：
    1.  按下鍵盤上的「Windows」鍵
> 出現開始功能表，游標自動跑到下方搜尋列
> [name=ET B]

    2.  按下「c」然後「o」然後「m」鍵
> 第一個搜尋結果通常就會是 command prompt
> [name=ET B]

> 更精準是按下「c」然後「m」然後「d」，搜尋結果 cmd.exe 那個就是了
> [name=廖三凱]

    3.  按下「enter」鍵
> 執行被選起來的搜尋結果，預設是清單上的第一個，也就是 command prompt
> [name=ET B]

    4.  恭喜！你已經打開討人厭的 terminal 了！ =3=
2.  移動目前位置：
    1.  一開始畫面上有 C:\Users\ETBlue>_
> 「ETBlue」是在我的電腦裡的使用者名稱，在你的電腦裡會顯示成你的名稱
> [name=ET B]

    2.  輸入「cd "my documents"\github\hack.g0v.tw/」然後按「enter」鍵
> 會移動到 my documents 資料夾裡的 github 資料夾裡的 hack.g0v.tw 資料夾
> [name=ET B]

3.  下載虛擬電腦：
    1.  輸入「vagrant box  add g0v [https://dl.dropboxusercontent.com/u/4339854/g0v/g0v-ubuntu-precise64.box](https://dl.dropboxusercontent.com/u/4339854/g0v/g0v-ubuntu-precise64.box)」然後按「enter」鍵
> 會下載 g0v-ubuntu-precise64.box 這個檔案，我用 50M 光纖大概花 25 分鐘抓完
> [name=ET B]

> 目前這個路徑來源已失效，正在研究如何自己打造
> [name=Yu-Lung S]

> 先用這個看看？
> [name=NewCliCker]

> [http://cloud-images.ubuntu.com/vagrant/precise/current/precise-server-cloudimg-amd64-vagrant-disk1.box](http://cloud-images.ubuntu.com/vagrant/precise/current/precise-server-cloudimg-amd64-vagrant-disk1.box)
> [name=NewCliCker]


 安裝VirtualBox
 設定環境變數Path 加入 "C:\\Program Files\\Oracle\\VirtualBox\\VBoxManage.exe"

### 以下步驟還要再跟 hychen 、audrey 確認，步驟有改過，現在有點搞不清楚到底要不要先裝 mingw 才打 vagrant up？ orz


    1.  輸入「vagrant up」然後按「enter」鍵
> 據說這樣就可以讓虛擬電腦開機 = =b
> [name=ET B]

> 什麼是 terminal
> [name=ET B]


    vagrant bug [https://github.com/mitchellh/vagrant/wiki/%60vagrant-up%60-hangs-at-%22Waiting-for-VM-to-boot.-This-can-take-a-few-minutes%22](https://github.com/mitchellh/vagrant/wiki/%60vagrant-up%60-hangs-at-%22Waiting-for-VM-to-boot.-This-can-take-a-few-minutes%22)

### 幫 vagrant 安裝 ssh 連線軟體

> 什麼是 ssh
> [name=ET B]

> 據說是讓我們可以連到虛擬機器裡面的東西... = =
> [name=ET B]

1.  下載：[http://sourceforge.net/projects/mingw/files/Installer/mingw-get-inst/mingw-get-inst-20120426/mingw-get-inst-20120426.exe/download](http://sourceforge.net/projects/mingw/files/Installer/mingw-get-inst/mingw-get-inst-20120426/mingw-get-inst-20120426.exe/download)
> 據說是個可以讓 vagrant 程式的 ssh 連線功能發揮作用的東西 = =?
> [name=ET B]

2.  安裝：執行 mingw-get-inst-20120426.exe
    - [Audrey](https://g0v.hackpad.tw/ep/profile/JkW68dALfOIsbbu2ir5eU)[Audrey Tang](https://g0v.hackpad.tw/ep/profile/JkW68dALfOIsbbu2ir5eU) [Tang](https://g0v.hackpad.tw/ep/profile/JkW68dALfOIsbbu2ir5eU) 說安裝過程中會讓你選要裝哪些套件（Select Components），那頁要捲到下方勾選 MSYS Basic System 和 MinGW Developer Toolkit
> 怕死的我當然是不分青紅皂白之全部都打勾 = ="
> [name=ET B]

3.  使用：
    1.  開始 -> 所有程式 -\> MinGW -> MinGW Shell
    2.  輸入「vagrant ssh」然後按「enter」鍵
    3.  進入虛擬電腦
        1.  cd /vagrant


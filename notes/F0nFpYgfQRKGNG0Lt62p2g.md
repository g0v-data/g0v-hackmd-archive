# 安裝odoo流程:
## 環境：Linux 64bit ubuntu 18.04.4
- 課本上說**不能**在root用戶上安裝`odoo`，so==創建一個新使用者==：
```linux=****
    sudo adduser odoo
```
- 編輯文件/etc/sudoers：
```linux=
    sudo vi /etc/sudoers
```
        進去之後按i啟用編輯
        找到#User privilege specification後
        在下面       root    ALL=(ALL:ALL) ALL
        新增一行     odoo    ALL=(ALL:ALL) ALL
        然後按Esc退出編輯
        使用:wq!保存退出
        然後切換到odoo用戶
```linux=
    su odoo
    cd ~
```
- 這樣就有root權限，接下來更新安裝軟體並安裝git：
```linux=
    sudo apt update
    sudo apt upgrade
    sudo apt install git
```
    更新完重啟
```linux=
    sudo reboot
```
- 安裝Node.js：
```linux=
    sudo apt-get install -y npm
    sudo ln -s /usr/bin/nodejs /usr/bin/node
    sudo npm install -g less
```

- 從git上clone odoo：
```linux=
    sudo git clone https://github.com/odoo/odoo.git -b 13.0 
```
- 安裝python3需要的pip3
```linux=
    sudo apt-get install -y python3-pip
```
- 安裝PostgreSQL
```linux=
    sudo apt-get install -y postgresql
```
    然後進到postgres命令窗庫創建用戶odoo
```linux=
    sudo su - postgres
    createuser --createdb --username postgres --no-createrole --no-superuser --pwprompt odoo
```
    然後會出現
    Enter password for new role:
    Enter it again:
    這邊自己設定就可以
    然後輸入
    exit
    退出postgres命令視窗
- 啟動odoo
    到你的odoo資料夾底下
```linux=
    cd odoo
```
    啟動odoo
```linux=
    ./odoo-bin
```
    這時候還沒辦法啟動，他會告訴你啟動還需要下載什麼套件，在根據提示下載相關套件
- 安裝相關套件
    當出現no module named XXX
    使用
```linux=
    sudo pip3 install XXX
```
    然後再啟動一次，還是會發現缺少套件，然後繼續安裝套件
    重複這個步驟直到所有套件安裝完
- 當出現no module named psycopg2 無法使用上述方法，需使用：
```linux=
    sudo apt-get install python3-psycopg2
```
- 當出現no module named werkzeug 因為新版無法使用，網路上說使用0.16.0版：
```linux=
    sudo pip3 install werkzeug==0.16.0
```
- 當出現no module named PIL 因為已被pillow取代：
```linux=
    sudo pip3 install pillow
```
- 當安裝完pypdf2,passlib,babel,werkzeug==0.16.0,lxml,decorator,polib,psutil,jinja2,psycopg2時，可以正常啟動，但是還是會出現criticl和error的紅字警告，最下面會有ModuleNotFoundError:no module named XXX，先按control+c關閉，繼續照上面安裝：
```linux=
    sudo pip3 install XXX
```
- 之後會出現一個warning說The num2words python library in not install .....
  我們就安裝：
```linux=
    sudo pip3 install num2words
```
- 這時如果內建firefox不能用，建議安裝chrome
```linux=
    wget -c https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
    sudo dpkg -i google-chrome-stable_current_amd64.deb
```
    只要打上述兩行指令就可以輕鬆下載並安裝 Chrome 了，如果過程遇到錯誤打sudo apt-get install -f  補齊相依套件就能解決。
- 進去瀏覽器輸入http://0.0.0.0:8069進入localhost就可以使用了

- 安裝文字和打印需要的wkhtmltopdf,這邊無法使用pip3,檔案會找不到
```linux=
    sudo apt-get install ttf-wqy-zenhei -y
    sudo apt-get install ttf-wqy-microhei -y
    wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.2.1/wkhtmltox-0.12.2.1_linux-trusty-amd64.deb
    sudo dpkg -i wkhtmltox-0.12.2.1_linux-trusty-amd64.deb
```
    這時會缺少libpng-12.0 且無法使用apt-get安裝,因為ubuntu14.0以上已經不支援libpng12,請使用以下方法：
```linux=
    sudo vim /etc/apt/sources.list
```
    根據官網提示,我們加上 deb http://cz.archive.ubuntu.com/ubuntu xenial main
    然後更新
    安裝
```linux=
    sudo apt-get update
    sudo apt-get install libpng12-0
```

* style error
:::danger
WARNING test odoo.addons.base.models.assetsbundle: Could not execute command 'sassc'This error occured while compiling the bundle 'web.assets_common' containing:
:::
solution : 
[how to install sassc ?](http://odoocustomize.com/blog/odoo-tips-tricks-1/post/how-to-install-sassc-1)
```linux=
sudo pip3 install libsass==0.12.3
```
:::info
- 可能還會需要安裝報表打印用的wkhtmltopdf
前兩步是安裝中文字體
```linux=
    sudo apt-get install ttf-wqy-zenhei -y
    sudo apt-get install ttf-wqy-microhei -y
```
後面是下載及安裝wkhtmltopdf
```linux=
    sudo wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.2.1/wkhtmltox-0.12.2.1_linux-trusty-amd64.deb
    sudo dpkg -i wkhtmltox-0.12.2.1_linux-trusty-amd64.deb
```
最後一步可能會有問題，需要再安裝相關套件，使用sudo apt-get -f install XXX就行



但Ubuntu 14以上就已经不再支持libpng12，然而有些软件又依赖于libpng12（如我要使用的Cisco Packet Tracer）。我们可以采用特定的方法安装低版本的libpng。

sudo vim /etc/apt/source.list(可能是souces)
根据Ubuntu官網的提示，我们在其中加上deb http://cz.archive.ubuntu.com/ubuntu xenial main

然后保存，并更新package list后即可安装

sudo apt-get update
sudo apt-get install libpng12-0
————————————————
版权声明：本文为CSDN博主「l_ricardo」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/l_ricardo/java/article/details/82718241
:::


:::info
- 若虛擬機空間不足
  需先電腦關機進行更改硬碟空間 
  參考：
  https://www.itread01.com/content/1550182874.html
  https://www.itread01.com/content/1545148823.html
:::

## 使用"xlrd"讀取Excel數據
```
sudo pip3 install xlrd
```
## 進入odoo
```linux=
./odoo-bin
```
## 進入開發者模式
* 安裝初始化設定模組
* 啟用開發者模式

# 建立模組：
## 參考 https://alanhou.org/odoo-13-building-module/
## 一、加入addons路徑
### 先在odoo/debian/odoo.conf加入自己要建立模組的資料夾路徑
### 例如：建立my-module資料夾在odoo/my-module，直接複製預設路徑到addons前面，然後加上my-module，如下圖
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_326991acc2e7d0fa57b3d904b10308e8.png)
## 二、使用scaffold建立預設模組
### sudo ./odoo-bin scaffold <modul_name> <document>
### 例如要在my-module下建立一個my_library
### 就輸入 sudo ./odoo-bin scaffold my_library /my-
### 這樣就會建立一個空的模組，重啟後就可以安裝

## 三、

## ***若要在ubuntu裡面下載網路上圖片
### wget -O /你的/目标/文件夹/图片名.png  "图片链接"
### ex:在目前目錄下下載並命名為book.png,後面網址為圖片連結,指令如下
wget -O book.png  "https://play-lh.googleusercontent.com/a7jUyjTxWrl_Kl1FkUSv2FHsSu3Swucpem2UIFDRbA1fmt5ywKBf-gcwe6_zalOqIR7V"




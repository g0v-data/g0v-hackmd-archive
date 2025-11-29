# Ubuntu 架設步驟
1. **將系統更新至最新**
```
sudo apt update && sudo apt upgrade && sudo apt dist-upgrade && sudo apt-get update
```
2. **安裝 LAMP**
```
sudo apt-get install lamp-server^
```
3. **安裝 PhpMyAdmin**
```
sudo apt install phpmyadmin 
```
    1.伺服器：Apache
    2.dbconfig-common：yes
    3.設定密碼
4. **設定 root 帳號**
```
sudo mysql -u root mysql
```
5. **輸入sql指令**
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '123456';
FLUSH PRIVILEGES;
exit;
```
6. **設定root密碼**
```
sudo mysql_secure_installation
```
7. **設定Ipv4直接進入PhpMyAdmin**
```
sudo vim /etc/apache2/apache2.conf
```
    Include /etc/phpmyadmin/apache.conf //最後一行輸入
    sudo /etc/init.d/apache2 restart //重啟
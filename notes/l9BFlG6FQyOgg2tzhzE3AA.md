# picoctf
[toc]
## Scavenger Hunt
There is some interesting information hidden around this site http://mercury.picoctf.net:5080/. Can you find it?
- 點進網址後，檢查網頁程式碼
- 在html的頁面能發現第一部份的flag
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5e61fe4380228363880365bc4f3ad545.png)
- 猜測第二部分在css裡，嘻嘻猜中了
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_01478b99f09bf28b725994dcf534a62d.png)
- 按照題目尿型，第三部分應該在javascript
- 但發現了這句(How can I keep Google from indexing my website?)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9abb75d1be3ad72f0fe470411242f75d.png)
- 是要藏什麼讓google不能查?
- 利用robots.txt，找到了第三部分
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_11e21913f5a36382132c5daa7a19ae22.png)
- 另一個提示透過大寫的“Access”，我們可以猜測他們可能正在談論.htaccess檔案。
- `.htaccess`（HyperText Access）是一個在 Apache Web 伺服器上用來配置網站設置的配置文件。這個文件允許使用者自定義伺服器的行為，包括 URL 重寫、訪問控制、重新導向等等。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_341b52093332bde9b9896874025df9cb.png)
- 給的另一個提示跟mac和store有關，應該是指.DS_Store
- .DS_Store 是 macOS 操作系統中用於存儲目錄自定義屬性的隱藏文件。這個文件包含有關目錄的顯示設置、圖標位置、自定義視圖選項等信息。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_deb4040da9c3167a47e21cf2ea76b716.png)
- ans:picoCTF{th4ts_4_l0t_0f_pl4c3s_2_lO0k_35844447}






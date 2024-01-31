# picoCTF(page 1)
[TOC]
## Obedient Cat
This file has a flag in plain sight (aka "in-the-clear")
```
wget https://mercury.picoctf.net/static/704f877da185904ec3992e7255a15c6c/flag
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a46ade358bf81469999c915c79925181.png)
ans:picoCTF{s4n1ty_v3r1f13d_1a94e0f9}

## Mod 26
Cryptography can be easy, do you know what ROT13 is?
將這串英文進行ROT13
cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_jdJBFOXJ}
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3571c86879cdf9f9e3f9dd3187670b16.png)
ANS:picoctf{next_time_i'll_try_2_rounds_of_rot13_wqwosbkw}

## Python Wrangling
Python scripts are invoked kind of like programs in the Terminal... Can you run this Python script using this password to get the flag?
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e6945d66f170d88e4c80483bc1a5b5f9.png)
ans:picoCTF{4p0110_1n_7h3_h0us3_192ee2db}

## Wave a flag
Can you invoke help flags for a tool or binary? This program has extraordinarily helpful information...
```
 wget https://mercury.picoctf.net/static/beec4f433e5ee5bfcd71bba8d5863faf/warm
```
chmod +x :使腳本可執行
./檔案名:執行該檔案
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1efc7719c58e86993a71b3fc8d8c73d7.png)
ans:picoCTF{b1scu1ts_4nd_gr4vy_616f7182}

## information
Files can always be changed in a secret way. Can you find the flag? cat.jpg
將cat.jpg利用exiftool打開，發現license值怪怪的
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_93bac961d73ad4713e89993eb7e8c6a0.png)
進行base64解碼
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_faac353725fec91af3bf996963602700.png)
ans:picoCTF{the_m3tadata_1s_modified}

## Nice netcat...
There is a nice program that you can talk to by using this command in a shell: $ nc mercury.picoctf.net 7449, but it doesn't speak English...
執行後有一串數字
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_540b4c0d23191eb510d94a6be910a13b.png)
進行[ASCII解碼](https://zh-tw.rakko.tools/tools/76/)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_aa1dcc520ffd169743cf47f1adf56e1f.png)
ANS:picoCTF{g00d_k1tty!_n1c3_k1tty!_f2d7cafa}

## Transformation
I wonder what this really is... enc ''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e6181830badac6613a926c36a2029839.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fde4d6a510873a10f840f31c0d8e3801.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7612643297f56c0cdbd83c64c5449ac0.png)
ans:picoCTF{16_bits_inst34d_of_8_75d4898b}

## GET aHEAD
Find the flag being held on this server to get ahead of the competition http://mercury.picoctf.net:45028/
利用BURP SUITE攔截，send to repeater
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_39e87a10d7b27674360734f1dd64ab4e.png)
修改post 改成head(獲取僅標頭信息而不獲取實際內容的資源信息)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4adbb778af0cd437f8bdf7657071bcf0.png)
ans:picoCTF{r3j3ct_th3_du4l1ty_775f2530}

## Mind your Ps and Qs
In RSA, a small e value can be problematic, but what about N? Can you decrypt this? values
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_742ce04102025f0ad880f24b8edfbdb0.png)
[rsa cipher](https://www.dcode.fr/rsa-cipher)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_585509d544cdbe4a0bcaf9f62105af72.png)
ans:picoCTF{sma11_N_n0_g0od_73918962}

## Static ain't always noise
Can you look at the data in this binary: static? This BASH script might help!
```
wget https://mercury.picoctf.net/static/66932732825076cad4ba43e463dae82f/static
```

```
wget https://mercury.picoctf.net/static/66932732825076cad4ba43e463dae82f/ltdis.sh
```
1.chmod +x static
2.`./static`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bfa6abed647487e4a6057659921ffd23.png)
3.chmod +x ltdis.sh
4.`./ltdis.sh`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_613c5da87faf15f5a08c79212de60a1b.png)
5.`./ltdis.sh ./static`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3136d7b85208038ddfeb63b84468515e.png)
可以看到產生了兩個檔案：
./static.ltdis.x86_64.txt 與 ./static.ltdis.strings.txt ，
根據程式輸出訊息，任何找到的字串都在 ./static.ltdis.strings.txt 中，
我們用 grep 命令來找出 flag ：
```
grep 'picoCTF' ./static.ltdis.strings.txt
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_94d1928c8c590e9480c44865c295d8ac.png)
ans:picoCTF{d15a5m_t34s3r_f5aeda17}


## Tab, Tab, Attack
Using tabcomplete in the Terminal will add years to your life, esp. when dealing with long rambling directory structures and filenames: Addadshashanammu.zip

```
wget https://mercury.picoctf.net/static/72712e82413e78cc8aa8d553ffea42b0/Addadshashanammu.zip
```
```
unzip Addadshashanammu.zip
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b7ddd041e27275c116bb148c61801990.png)
只要先打 ./ 再一路按 tab 鍵，shell 自動幫你補上所有路徑
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_83bcbc47bb0eab2c97904678b3c4734f.png)
ans:picoCTF{l3v3l_up!_t4k3_4_r35t!_6f332f10}






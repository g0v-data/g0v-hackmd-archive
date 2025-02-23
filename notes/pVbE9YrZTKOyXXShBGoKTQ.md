# General Skills
[toc]
## easy
### Binary Search
從1~1000選十次數字，如果guess>target，則lower，guess<target，則higher，一開始先猜500，然後逐步縮小範圍
![](https://g0v.hackmd.io/_uploads/HyepF84_qJg.png)

![](https://g0v.hackmd.io/_uploads/Bylhw8NdcJe.png)
ans:picoCTF{g00d_gu355_ee8225d0}
### Wave a flag
Can you invoke help flags for a tool or binary? This program has extraordinarily helpful information...
```
 wget https://mercury.picoctf.net/static/beec4f433e5ee5bfcd71bba8d5863faf/warm
```
chmod +x :使腳本可執行
./檔案名:執行該檔案
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1efc7719c58e86993a71b3fc8d8c73d7.png)
ans:picoCTF{b1scu1ts_4nd_gr4vy_616f7182}
### Python Wrangling
Python scripts are invoked kind of like programs in the Terminal... Can you run this Python script using this password to get the flag?
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e6945d66f170d88e4c80483bc1a5b5f9.png)
ans:picoCTF{4p0110_1n_7h3_h0us3_192ee2db}
### Nice netcat...
There is a nice program that you can talk to by using this command in a shell: $ nc mercury.picoctf.net 7449, but it doesn't speak English...
執行後有一串數字
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_540b4c0d23191eb510d94a6be910a13b.png)
進行[ASCII解碼](https://zh-tw.rakko.tools/tools/76/)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_aa1dcc520ffd169743cf47f1adf56e1f.png)
ANS:picoCTF{g00d_k1tty!_n1c3_k1tty!_f2d7cafa}

### Tab, Tab, Attack
Using tabcomplete in the Terminal will add years to your life, esp. when dealing with long rambling directory structures and filenames: Addadshashanammu.zip
```
wget https://mercury.picoctf.net/static/72712e82413e78cc8aa8d553ffea42b0/Addadshashanammu.zip
```
```
unzip Addadshashanammu.zip
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a442e517573718f0534d846ffbf8ca98.png)
- 輸入`./`+Addadshashanammu後，一值按tab鍵就能到最後一個檔案了
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_74e5b88588f1229c87fb23c1c9cef2eb.png)
- ans:picoCTF{l3v3l_up!_t4k3_4_r35t!_6f332f10}

### Magikarp Ground Mission
Do you know how to move between directories and read files in the shell? Start the container, `ssh` to it, and then `ls` once connected to begin. Login via `ssh` as `ctf-player` with the password, `ee388b88`
Additional details will be available after launching your challenge instance.
```
ssh ctf-player@venus.picoctf.net -p 50273
```
- 輸入密碼:ee388b88
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ce8087143b5ffb31f2e040cc140faec0.png)
- `ls`+`cat 1of3.flag.txt` 得出第一部份的flag
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e851c22bb6c38093d3a8b8f834cd0676.png)
- `cd /`到根目錄
- `ls`+`cat 2of3.flag.txt` 得出第二部份的flag
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c677c95f897a47108aa1c53369e3e0c8.png)
- `cd ~`返回到你的用戶家目錄
- `ls`+`cat 3of3.flag.txt` 得出第三部份的flag
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ff81e62919033f2f63f6d0c1aa22b057.png)
- ans:picoCTF{xxsh_0ut_0f_\/\/4t3r_3ca613a1}

###
## medium
## hard
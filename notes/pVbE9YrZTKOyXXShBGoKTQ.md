# General Skills
[toc]
## easy
### Binary Search
從1~1000選十次數字，如果guess>target，則lower，guess<target，則higher，一開始先猜500，然後逐步縮小範圍
![](https://g0v.hackmd.io/_uploads/HyepF84_qJg.png)

![](https://g0v.hackmd.io/_uploads/Bylhw8NdcJe.png)
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
## medium
## hard
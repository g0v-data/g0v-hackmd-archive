# General Skills
[toc]
## easy
### Collaborative Development
My team has been working very hard on new features for our flag printing program! I wonder how they'll work together?
You can download the challenge files here:
[challenge.zip](https://artifacts.picoctf.net/c_titan/176/challenge.zip)
- Hint
- git branch -a會讓你看到可用的分支
- 如何將文件‘差異’帶到主分支？別忘了git config！
- 合併衝突可能會很棘手！嘗試使用 nano、emacs 或 vim 等文字編輯器。
```
git branch -a //該命令將顯示四個可用分支，現在我們位於主分支
```
- 假設其他提交或更改是flag.py在另一個分支中，因為我們從第一個提示中得到了一些線索。
![](https://g0v.hackmd.io/_uploads/HJoPdyMoye.png)

![](https://g0v.hackmd.io/_uploads/BkxdcdkGsJx.png)

- 要切換到不同的分支，使用git checkout，`git checkout feature/part-1`，下面以此類推
![](https://g0v.hackmd.io/_uploads/HJgq3D1fo1l.png)

![](https://g0v.hackmd.io/_uploads/SJWLPkMjyl.png)

![](https://g0v.hackmd.io/_uploads/Sya5wkfikx.png)

![](https://g0v.hackmd.io/_uploads/BJxowkGjJx.png)

- ans:picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_2c91ca76}
### Commitment Issues
I accidentally wrote the flag down. Good thing I deleted it!
You download the challenge files here:
[challenge.zip](https://artifacts.picoctf.net/c_titan/76/challenge.zip)
- 解壓縮後，可以發現檔案都在drop-in資料夾裡
![](https://g0v.hackmd.io/_uploads/BJkSGDxoye.png)
- 有個message.txt，打開後寫TOP SECRET，很可疑
![](https://g0v.hackmd.io/_uploads/H1C9zwejJl.png)
- `git log`後，發現在e720dc26a1a55405fbdf4d338d465335c439fb3e這個ID有create flag
![](https://g0v.hackmd.io/_uploads/BkCzNPljyx.png)

- `git show e720dc26a1a55405fbdf4d338d465335c439fb3e `，找到flag了
![](https://g0v.hackmd.io/_uploads/S1lT-vgiyx.png)
ans:picoCTF{s@n1t1z3_7246792d}

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
### dont-you-love-banners

Can you abuse the banner?
The server has been leaking some crucial information on tethys.picoctf.net 63856. Use the leaked information to get to the server.
To connect to the running application use nc tethys.picoctf.net 54462. From the above information abuse the machine and find the flag in the /root directory.

![](https://g0v.hackmd.io/_uploads/ryGp2pYs1x.png)

![](https://g0v.hackmd.io/_uploads/rkUXa6Fiyl.png)
![](https://g0v.hackmd.io/_uploads/rkO7aTts1x.png)

![](https://g0v.hackmd.io/_uploads/SJfL66Foyl.png)

![](https://g0v.hackmd.io/_uploads/SkgULT6Yokx.png)

![](https://g0v.hackmd.io/_uploads/rJO8paYs1x.png)

![](https://g0v.hackmd.io/_uploads/ByHd6TYj1e.png)

![](https://g0v.hackmd.io/_uploads/rJ59p6YoJx.png)

```
 with open("/home/player/banner", "r") as f:
        print(f.read())
```

![](https://g0v.hackmd.io/_uploads/HyogAptjJx.png)

![](https://g0v.hackmd.io/_uploads/SyCx0aFoye.png)

![](https://g0v.hackmd.io/_uploads/By4bCpYiJx.png)
 
 ans:picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_68ca8b23}
### Permissions
Can you read files in the root file?
Additional details will be available after launching your challenge instance.
- 題目一開始將說能在根目錄找到檔案嗎? 所以先cd到根目錄
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_19098b36c983c1f4d8f05196b4cecee2.png)
- 查看根目錄有哪些檔案和權限，發現challenge這個路徑有問題，權限不夠無法cd
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_662f7a48fccbc3db395a3277505348b7.png)
- 查看sudo 發現使用者可以用sudo權限使用vi
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3bb9e3625f6e4438d60bc896f7fc11f6.png)
- 輸入sudo vi
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ef84f11576ff54fbf880b73ce2e92742.png)
- 啟動一個新的 shell 並暫時離開 vi
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c7cbdba033fdda13c9ae29379a873f75.png)
- 查看目前身分
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_123ecb02f31bac5a0101ac54083cdae4.png)
- cd challenge+ls，發現有個json檔
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a09484a6026ce0b57c92713a30d13b0c.png)
- `cat metadata.json`
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b79da13823a5c77c7c04230d43c3adcc.png)

- ans:picoCTF{uS1ng_v1m_3dit0r_1cee9dcb}
## hard
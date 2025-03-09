# Cryptography
[toc]
## easy
### Mod 26
Cryptography can be easy, do you know what ROT13 is?
將這串英文進行ROT13
cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_jdJBFOXJ}
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3571c86879cdf9f9e3f9dd3187670b16.png)
ANS:picoctf{next_time_i'll_try_2_rounds_of_rot13_wqwosbkw}

### The Numbers
The numbers... what do they mean?
- 把numbers下載後打開，發現一串數字
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b92105aba29b9dfd4bd9f0f7efed5359.png)
- 依照以往flag前面會是picoCTF的數字
- 英文排序位置剛好對應到圖片上的數字
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_86894d798f9dd82454c2fdb6ef956ab8.png)
- ans:picoCTF{thenumbersmason}
## medium
### Mind your Ps and Qs
In RSA, a small e value can be problematic, but what about N? Can you decrypt this? values
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_742ce04102025f0ad880f24b8edfbdb0.png)
[rsa cipher](https://www.dcode.fr/rsa-cipher)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_585509d544cdbe4a0bcaf9f62105af72.png)
ans:picoCTF{sma11_N_n0_g0od_73918962
### credstuff
We found a leak of a blackmarket website's login credentials. Can you find the password of the user cultiris and successfully decrypt it?
Download the leak here.
The first user in usernames.txt corresponds to the first password in passwords.txt. The second user corresponds to the second password, and so on.
- 在username.txt找cultiris在第378行
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c5de8fee19877d935733b05f2f30e720.png)
- password.txt
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_de5d9f3416ac97a4d22593c0b8789050.png)
- 丟到[rot轉換器](https://zh.planetcalc.com/1434/)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6364f9288979aa30c5e092fc5e8215bf.png)
- ans:picoCTF{C7r1F_54V35_71M3}

### HideToSee
How about some hide and seek heh?
Look at this image here.
[steghide](https://seamiloak.github.io/2020/08/24/Steghide%E4%BD%BF%E7%94%A8%E6%95%99%E7%A8%8B%E5%8F%8A%E5%85%B6%E5%AF%86%E7%A0%81%E7%88%86%E7%A0%B4/)
hint:Download the image and try to extract it.
- 下載圖檔
```
wget https://artifacts.picoctf.net/c/239/atbash.jpg
```
- 從atbash.jpg中解出
```
steghide extract -sf atbash.jpg
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_be7387e318f59d952244a7620215a7ea.png)

- 解出了一個encrypted.txt，cat出來後是一段加密後的文字
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a300dba2b02b18c399e5b3b37e2a0b48.png)
- 推測是透過atbash
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2d8eb996e11fc13f924fe647fe054422.png)
- ans:picoCTF{atbash_crack_1f84d779}

### Flags
What do the flags mean?
- 打開圖片，發現一堆像是國旗的東東
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_028583d1e35a30c6d88d40c2c3da2888.png)
- 推測前面7個代表picoctf，但這樣並無法推出全部
- 後來發現這是國際信號旗
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d744ca30d59c279dbadc12dfe380e71b.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c3fe6383daacf4a54270773a4dd4de10.png)
- ans:PICOCTF{F1AG5AND5TUFF}

### substitution1
A second message has come in the mail, and it seems almost identical to the first one. Maybe the same thing will work again.
Download the message [here](https://artifacts.picoctf.net/c/181/message.txt).

- 這題要解替換式密碼
![](https://g0v.hackmd.io/_uploads/HJ_iKzosyg.png)
- 使用[quipqiup](https://quipqiup.com/)

![](https://g0v.hackmd.io/_uploads/BJmgoGji1x.png)
![](https://g0v.hackmd.io/_uploads/HygSejfojJg.png)



## hard
# picoctf(page 2)
[toc]
## Insp3ct0r
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

## Magikarp Ground Mission
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

## Glory of the Garden
This garden contains more than it seems.
```
wget https://jupiter.challenges.picoctf.org/static/43c4743b3946f427e883f6b286f47467/garden.jpg
```
- hint:What is a hex editor?
1.用hex editor滑到最後
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_566bdf75cf6bdd96d55d220e88047e1a.png)
2.
```
strings garden.jpg | grep CTF
```
- 在 garden.jpg 文件中使用 strings 提取所有可讀的字符串，然後使用 grep 過濾包含 "CTF" 字符串的行
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_10f042265eff6516b146b5c687ca7461.png)

- ANS:picoCTF{more_than_m33ts_the_3y3657BaB2C}

## Matryoshka doll
Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one? Image: this
```
binwalk -Me dolls.jpg
```
- 找到存放flag.txt的路徑
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c7a31bc7eddf7843bd96653e9d862e62.png)
```
cat _dolls.jpg-0.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images/_4_c.jpg.extracted/flag.txt
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f1594ead64702721af3b9a9f1c605ec9.png)
- ans:picoCTF{4cf7ac000c3fb0fa96fb92722ffb2a32}

## crackme-py
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_20cd754015df300ffee7ee2156052d49.png)
- 將A:4@r%uL`M-^M0c0AbcM-MFE0d_a3hgc3N進行ROT47
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bab94d213a96af95f44889b516c013e3.png)
- ans:picoCTF{1|\/|_4_p34|\|ut_502b984b}

## cookies
- 將cookie name設為18
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cad512bfd736e327bea4cf6add089ced.png)
- ans:picoCTF{3v3ry1_l0v3s_c00k135_96cdadfd}




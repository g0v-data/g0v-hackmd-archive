# picoCTF(page 7)
[toc]
## credstuff
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
# picoCTF(page 15)
[toc]
## Flags
What do the flags mean?
- 打開圖片，發現一堆像是國旗的東東
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_028583d1e35a30c6d88d40c2c3da2888.png)
- 推測前面7個代表picoctf，但這樣並無法推出全部
- 後來發現這是國際信號旗
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d744ca30d59c279dbadc12dfe380e71b.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c3fe6383daacf4a54270773a4dd4de10.png)
- ans:PICOCTF{F1AG5AND5TUFF}

## picobrowser
This website can be rendered only by picobrowser, go and catch the flag! https://jupiter.challenges.picoctf.org/problem/26704/ 
- 點進連結後，點下flag顯示我不是picobrowser，後面那串是在顯示user-agent
- 利用burp suite進行攔截，將user-agent改成picobrowser
- 重整後可在response的程式碼看到flag
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6752a208c38a36adabc784fcf2f47bb8.png)
- ans:picoCTF{p1c0_s3cr3t_ag3nt_e9b160d0}

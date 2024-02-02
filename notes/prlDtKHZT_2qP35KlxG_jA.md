# picoCTF(page 5)
[toc]
## logon
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

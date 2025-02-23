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
## hard
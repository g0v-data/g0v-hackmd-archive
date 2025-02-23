# Forensics
[toc]
## easy
### information
Files can always be changed in a secret way. Can you find the flag? cat.jpg
將cat.jpg利用exiftool打開，發現license值怪怪的
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_93bac961d73ad4713e89993eb7e8c6a0.png)
進行base64解碼
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_faac353725fec91af3bf996963602700.png)
ans:picoCTF{the_m3tadata_1s_modified}
## medium
## hard
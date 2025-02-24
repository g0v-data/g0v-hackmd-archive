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

### Glory of the Garden
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
### Scan Surprise
- 掃描qrcode答案就出來了
![](https://g0v.hackmd.io/_uploads/BycnO_Oqyx.png)
- ans:picoCTF{p33k_@_b00_3f7cf1ae}

### Secret of the Polyglot
- This problem can be solved by just opening the file in different ways(題目提示用其他方式開)
- 看到pn9下意識想到png
![](https://g0v.hackmd.io/_uploads/r1eoX5Od5Jl.png)
- 將副檔名改成png
![](https://g0v.hackmd.io/_uploads/BJK59d_cJe.png)

- ans:picoCTF{f1u3n7_1n_pn9_&_pdf_53b741d6}
## medium
### Matryoshka doll
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

### Packets Primer
Download the packet capture file and use packet analysis software to find the flag.
```
wget https://artifacts.picoctf.net/c/194/network-dump.flag.pcap
```
```
cat network-dump.flag.pcap
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_dd16a9a3749b5813c6f35edd0fc3fb34.png)
- 開啟wireshark，在tcp處按follow
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_888bc560c0a755fc8570b4dc4285a1dd.png)
## hard
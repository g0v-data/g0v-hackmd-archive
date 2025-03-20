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

### Verify
- 先查看有什麼檔案
![](https://g0v.hackmd.io/_uploads/Skgr4KZJjJg.png)
- 看一下checksum.txt，發現是一串像是經過sha256後的密文
![](https://g0v.hackmd.io/_uploads/Sy0IFb1iyx.png)
```
5848768e56185707f76c1d74f34f4e03fb0573ecc1ca7b11238007226654bcda
```
- 依照提示`./decrypt.sh files/<file>`，告知我們要去files資料夾裡使用ls -R，發現很多檔案

![](https://g0v.hackmd.io/_uploads/HkgnCYb1i1g.png)

![](https://g0v.hackmd.io/_uploads/BJ1ZqZkjJl.png)

- 應該是有某個檔案名稱sha256後，會是上面的密文
- 透過指令找出該檔案
![](https://g0v.hackmd.io/_uploads/B1eLIcbJjyl.png)
```
sha256sum files/* |grep 5848768e56185707f76c1d74f34f4e03fb0573ecc1ca7b11238007226654bcda
```
- 利用decrypt.sh進行解密
```
./decrypt.sh files/8eee7195
```
ans: picoCTF{trust_but_verify_8eee7195}

### CanYouSee
How about some hide and seek?
Download this file [here](https://artifacts.picoctf.net/c_titan/4/unknown.zip).
- 使用exiftool對圖片進行分析，發現有一串亂文像是base 64
```
exiftool ukn_reality.jpg
```
![](https://g0v.hackmd.io/_uploads/H1cYOUliyg.png)
- 丟去cyberchef進行解密
![](https://g0v.hackmd.io/_uploads/B16ktUeoyl.png)
- ans:picoCTF{ME74D47A_HIDD3N_deca06fb}

### Ph4nt0m 1ntrud3r
- 提示
    - 過濾您的資料包以縮小搜尋範圍。
    - 攻擊及時進行。
    - 時間至關重要
- 打開封包後，看不出有什麼特別
![](https://g0v.hackmd.io/_uploads/S1lKNKnKhJx.png)
- 依照提示讓封包按照時間順序排好
![](https://g0v.hackmd.io/_uploads/SylwPFhKhkl.png)
- payload 包含類似 base64 的數據，從 5 號資料包開始它變成了 picoCTF base64
![](https://g0v.hackmd.io/_uploads/r1GQ5hYnJe.png)

```
cGljb0NURg==
ezF0X3c0cw==
bnRfdGg0dA==
XzM0c3lfdA==
YmhfNHJfZQ==
NWU4Yzc4ZA==
fQ==
```
- Base64 解碼後，我們得到了flag
- ans:picoCTF{1t_w4snt_th4t_34sy_tbh_4r_e5e8c78d}

## medium

### endianness-v2

### MSB
This image passes LSB statistical analysis, but we can't help but think there must be something to the visual artifacts present in this image...
Download the image [here](https://artifacts.picoctf.net/c/301/Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png)
- 使用stegsolve對圖片進行處理
![](https://g0v.hackmd.io/_uploads/ByzkP25jJx.png)
- 將資料下載下來，然後搜尋pico，就能找到答案
![](https://g0v.hackmd.io/_uploads/BJCWvn9jkx.png)


- ans:picoCTF{15_y0ur_que57_qu1x071c_0r_h3r0 1c_3a219174}
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
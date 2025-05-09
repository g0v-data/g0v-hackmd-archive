# 女婕思小抄
[toc]
## 解圖片工具
- [LSB ONLINE TOOL](https://georgeom.net/StegOnline/upload)
- exiftool
    - 用途：讀取圖片的 metadata（如 EXIF 資訊），常有 flag 藏在這裡。
    - `exiftool image.jpg`
- zsteg
    - 用途：分析 PNG、BMP 等圖片的 LSB 隱寫技術。
    - `zsteg image.png`
    - `zsteg -a image.png #自動掃描所有常見通道與隱寫方式`
    - `zsteg -E image.png #自訂掃描通道和位元層（如 b1,r）`
    - `zsteg --lsb image.png #列出所有可能存在的隱寫資訊`
    - `zsteg --bits N image.png #指定幾個最低有效位元來分析`
    - `zsteg -v image.png #顯示詳細輸出`
`
`
- strings
    - 用途：直接抓出圖片中的可見 ASCII 字串，有時 flag 會直接藏在圖片 metadata 或尾部。
    - `strings image.jpg | grep -i flag`
- binwalk
    - 用途：分析圖片中是否嵌入了其他檔案（例如 zip、PNG、MP3 等）。
    - `binwalk image.jpg`
    - `binwalk -Me image.jpg  # 多層遞迴解壓`
    - `binwalk -D='gzip:gz' image.jpg #解壓包含壓縮資料（如 gzip）`
- stegsolve
    - 打開圖片後，可以切換各種視角查看藏匿資訊。
- [steghide](https://seamiloak.github.io/2020/08/24/Steghide%E4%BD%BF%E7%94%A8%E6%95%99%E7%A8%8B%E5%8F%8A%E5%85%B6%E5%AF%86%E7%A0%81%E7%88%86%E7%A0%B4/)
    - 用途：藏有資料的圖片（如 JPEG）中提取藏匿內容。
    - `steghide info image.jpg #查看藏了什麼資訊`
    - `steghide extract -sf image.jpg #提取藏在圖片中的資料`
    - 執行後會詢問你是否有密碼（若有設密碼就要輸入），若成功，會提取出藏的資料，例如 flag.txt 或其他檔案。
    - `steghide extract -sf image.jpg -p yourpassword # 若已知密碼，直接加上`

## 滲透測試工具
### sqlmap
抓出資料庫名稱
```
sqlmap -u "http://example.com/item.php?id=1" --dbs
```
顯示資料表
```
sqlmap -u "http://example.com/item.php?id=1" -D <資料庫名稱> --tables
```
顯示欄位名稱
```
sqlmap -u "http://example.com/item.php?id=1" -D <資料庫名稱> -T <資料表名稱> --columns
```
抓取表內資料
```
sqlmap -u "http://example.com/item.php?id=1" -D <資料庫名稱> -T <資料表名稱> -C <欄位名稱> --dump
```
--dump-all 的意思：
自動執行以下步驟：

掃出所有資料庫（--dbs）

每個資料庫中的表（--tables）

每個表的欄位（--columns）

把每個表格的資料全部拉下來（--dump）
```
sqlmap -u "http://target.com/page.php?id=1" --dump-all --batch --threads=10 --random-agent
#--batch	非互動模式（自動選預設值）
#--threads=10	多執行緒，加速處理
#--random-agent	假裝成正常瀏覽器，避免封鎖
```

若目標需要登入才注入，搭配 cookie：
```
sqlmap -u "http://target.com/profile.php?id=1" --cookie="PHPSESSID=abcd1234" --dump-all
```
### nmap
基礎掃描
```
nmap 192.168.1.1
```
掃描指定的埠（port）
```
nmap -p 80,443,3306 192.168.1.1 #指定特定 port
nmap -p- 192.168.1.1 #掃描所有 65535 個 TCP 埠
```
服務與版本偵測
```
nmap -sV 192.168.1.1 #嘗試偵測開放 port 的服務類型與版本（如 Apache 2.4.46）
```
作業系統偵測
```
nmap -O 192.168.1.1 #偵測目標主機的作業系統（例如 Linux、Windows）
```
快速掃描常見埠
```
nmap -F 192.168.1.1 #掃描 nmap 預設清單中的最常見 100 埠。
```
偵測主機是否存活
```
nmap -sn 192.168.1.0/24 #僅 ping 掃描，不進行 port 掃描。
```
跳過 ping，直接掃描
```
nmap -Pn 192.168.1.1 
```
進階偵測模式
```
nmap -A 192.168.1.1 #結合 OS 掃描、版本、指令碼、traceroute
```
開放的 port

該 port 所屬服務名稱與版本（如 Apache 2.4）

作業系統類型（如 Windows 10）

執行預設指令碼（如抓 HTTP title、檢查 TLS 設定）

網路 hop 資訊（像 traceroute）
### John the Ripper
基本破解（字典模式）
```
john --wordlist=rockyou.txt hash.txt
```

查看破解結果
```
john --show hash.txt #顯示已破解的帳密結果（格式為 使用者:密碼）
```
識別 hash 類型(john --list=formats)
```
john --wordlist=rockyou.txt --formats=raw-md5 hash.txt
john --wordlist=rockyou.txt --formats=crypt hash.txt
```

![](https://g0v.hackmd.io/_uploads/SJlOHIP9exx.png)

### hash-identifier
`sudo apt install hash-identifier`
開啟工具
```
hash-identifier
```
貼上你的 hash
```
5f4dcc3b5aa765d61d8327deb882cf99
```
觀看分析結果
```
Possible Hashs:
[+] MD5
[+] Domain Cached Credentials
```
### sslscan
```
sudo apt update
sudo apt install sslscan
```
掃描指定主機與預設 SSL 埠（443）
```
sslscan example.com
```
指定 IP 和 Port
```
sslscan 192.168.1.10:8443
```
沒有使用 SSL/TLS 時你可以做的事
![](https://g0v.hackmd.io/_uploads/rJ3gHxoxgx.png)

### [curl](https://feifei.tw/deep-dive-into-curl/)
用來與各種網路協定（最常見的是 HTTP/HTTPS）互動
![](https://g0v.hackmd.io/_uploads/rJlOFHeilxg.png)

### Hydra
### Netcat 


## 密碼學decode網站
### [CYBER CHEF](https://gchq.github.io/CyberChef/)
### [檢查是哪種hash](https://hashes.com/en/tools/hash_identifier)
### [md5 decode](https://10015.io/tools/md5-encrypt-decrypt#google_vignette)
### [sha1 decode](https://10015.io/tools/sha1-encrypt-decrypt)
### [sha256 decode](https://10015.io/tools/sha256-encrypt-decrypt)
### [rsa cipher](https://www.dcode.fr/rsa-cipher)
### [rot轉換器](https://zh.planetcalc.com/1434/)
### [解替換式密碼](https://quipqiup.com/)
### [RSA簽章解碼](https://redkestrel.co.uk/tools/decoder)


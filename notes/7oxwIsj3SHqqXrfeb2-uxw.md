# OpenVex 使用心得

## 安裝vexctl前置作業，GOlang環境安裝
``` 
apt-get update
apt install -y build-essential
wget https://go.dev/dl/go1.22.0.linux-amd64.tar.gz
tar -C /usr/local -xzf go1.22.0.linux-amd64.tar.gz
echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.profile
source ~/.profile
go version

``` 
## 安裝vexctl
```
git clone https://github.com/openvex/vexctl.git
cd vexctl
make
./vexctl version
```


## 建立一個測試資料夾
```
mkdir demo
./vexctl create "pkg:generic/product@1.0.0" CVE-1234-5678 under_investigation | tee demo/demo1.vex.json

#進入到資料夾中查看
vi demo/demo1.vex.json
```

Vex 可以記錄過去的歷程
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5ae44d038a5ad44d849fa8f290f45e82.png)

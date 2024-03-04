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


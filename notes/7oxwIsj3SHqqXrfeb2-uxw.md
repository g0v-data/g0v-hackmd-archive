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


## 進行驗證
```
./vexctl filter ./examples/sarif/nginx-trivy.sarif.json ./examples/sarif/sample-1statement.openvex.json > johnson0307.json

#nginx-trivy.sarif.json >> trivy的報告
#sample-1statement.openvex.json  >> 使用者的白名單
#johnson0307.json >> filter後的json文字 
```

必對過後的成果截圖

小結論
VEX 是一個JSON-LD 文件，滿足VEX最低需求
其目的是「關閉」已知不影響產品的漏洞警報。
VEX 可以被視為「漏洞白名單」。使用 VEX，可以向使用者傳達易受攻擊的元件對其產品沒有安全影響的訊息。


VEX 可以記錄過去的歷程
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5ae44d038a5ad44d849fa8f290f45e82.png)


可透過vexctl 進行VEX文件的建立與過濾


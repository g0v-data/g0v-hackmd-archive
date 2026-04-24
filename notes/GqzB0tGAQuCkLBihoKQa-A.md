# Using Isaac Sim WebRTC Streaming Client to solve the problem of no NVIDIA GPU on the local machine.
[toc]
:::info
使用情境為client端為mac電腦，server端為學校實驗室電腦(具備NVIDIA GPU)
:::
## 成大VPN安裝
[成大VPN安裝入口](https://cc.ncku.edu.tw/p/412-1213-7637.php?Lang=zh-tw)
- 選擇適合自己系統的
![](https://g0v.hackmd.io/_uploads/H1oYKBdTbe.png)
![](https://g0v.hackmd.io/_uploads/rJZ5FBu6Zg.png)

- 使用成功入口帳號登入取得權限:https://ncku.twaren.net/dana-na/auth/url_default/welcome.cgi
- 設定完後，開啟Ivanti Secure Access Client Installer進行VPN連線
![](https://g0v.hackmd.io/_uploads/rJlKcKrOp-g.png)


## client端安裝
- 在client端安裝Isaac Sim WebRTC Streaming Client
[安裝連結](https://docs.isaacsim.omniverse.nvidia.com/6.0.0/installation/download.html#isaac-sim-latest-release)
![](https://g0v.hackmd.io/_uploads/rklL_W6GPZl.png)
:::success
* Apple M1 / M2 / M3 → 下載 arm64
* Intel Core i5/i7 → 下載 x86_64
:::

## Server端環境
1.  Isaac Sim Server 需檢查：Streaming 功能是否已啟用`window-->extension-->輸入livestream`![](https://g0v.hackmd.io/_uploads/S16pvq4IZx.png)
2. 要先在server的cmd輸入
- Windows版本
```
cd C:\isaacsim
isaac-sim.streaming.bat
```
- Linux版本
```
cd ~/isaacsim
./isaac-sim.streaming.sh
```
- Docker (x86_64)版本
```
cd /isaac-sim
./runheadless.sh
```
## Client端開啟Isaac Sim WebRTC Streaming Client

1.  使用者啟動 Streaming Client，輸入Server端IP
![](https://g0v.hackmd.io/_uploads/Bk55ocE8Zl.png)

2.  連線畫面![](https://g0v.hackmd.io/_uploads/SyGyQztUWe.png)
## 整體流程圖
![](https://g0v.hackmd.io/_uploads/HJTSTTZwWx.png)

## 參考資料
[Isaac Sim WebRTC Streaming Client](https://docs.isaacsim.omniverse.nvidia.com/5.1.0/installation/manual_livestream_clients.html)
[成大VPN](https://cc.ncku.edu.tw/p/412-1213-7637.php?Lang=zh-tw)
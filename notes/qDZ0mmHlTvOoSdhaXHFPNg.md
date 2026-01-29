# 遠端連線(解決本地端沒有nvidia gpu問題，使用server gpu)
[toc]


| 項目 | Isaac Sim WebRTC Streaming Client | Parsec |
| -------- | -------- | -------- |
| 本質     | Isaac Sim 專用串流 Client     | 通用型遠端桌面  |
| 官方定位     | NVIDIA 官方支援| 第三方（業界常用）|
| 串流來源  | Isaac Sim Viewport     | 整個 Windows 桌面  |
| macOS 支援 | ✅     | ✅  |
| 連線方式     | 使用ip連線 (外網連內網麻煩)    | 登入同一mail帳號設定host  |
| NAT / 防火牆敏感度| 高     | 低  |
| 設定難度     | 中～高     | 低  |

## [Isaac Sim WebRTC Streaming Client](https://docs.isaacsim.omniverse.nvidia.com/6.0.0/installation/download.html#isaac-sim-latest-release)
1.  使用者啟動 Streaming Client![](https://g0v.hackmd.io/_uploads/Bk55ocE8Zl.png)

2.  Streaming Client 連線至 Isaac Sim Server(實際執行 Isaac Sim 的那台電腦)
3.  Isaac Sim Server 需檢查：Streaming 功能是否已啟用`window-->extension-->輸入livestream`![](https://g0v.hackmd.io/_uploads/S16pvq4IZx.png)
4.  連線畫面
## [parsec](https://parsec.app/downloads)
1. 在client和server端都下載parsec
2. 可都登入同一支帳號
![](https://g0v.hackmd.io/_uploads/SJgLGK-YL-x.png)
3. server畫面
![](https://g0v.hackmd.io/_uploads/HJ6YabF8-g.png)
4. client畫面，點選connect即可連接到server主機![](https://g0v.hackmd.io/_uploads/BJfibfFLbl.png)



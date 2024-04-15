## 一、重點整理
預計星期二下午 15:00 以前難以順利整合網頁應用至 AWS 平臺，說明如下。

## 二、Web 現況

目前 [GPTs 網頁版](https://github.com/SamurAIGPT/Open-Custom-GPT) 的進度如下：

1. 將 Logo 暫時換成國眾電腦
2. 統一成藍色色調
3. 將英文翻成中文
4. 放在 [GitHub](https://github.com/YippineLeosys/AI-Customer-Service/tree/v0.1.0) 以私人專案進行版控

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a317dee020cafd76d205dfc5643db280.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_10c80c991b7d81cfe2be00d90041261c.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_64d6f43c349f3246c5de4e8b8332fd73.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1e4ce09e73f5bac86d53dfd5b2f09b5a.png)

## 三、AWS 現況

- <b>第一步：</b>將網頁應用部署在 EC2
- <b>第二步：</b>開放外部網址，不太確定具體步驟，但會依照下列順序逐一嘗試：
    - 在 VPN 建立端點連接 EC2
    - 檢查 AWS Certificate Manager (ACM) 建立 HTTPS 憑證

不過 4/15(一) 花太多時間卡在第一步，截圖如下：

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b7fb617efc0f0fbfe48b5fec840a85b1.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8f4c32d7d1dcd0c778bb2be235cc0d4e.png)

所有的設置都是對的，但是伺服器拒絕連線，已多次詢問 Chatbot、網路爬文及詢問班上同學，目前仍然無解<span style="color:red">可能需要援助</span>。

1. IPv4 地址正確

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ff528f5318de2d80da8ebe45926d0d06.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e8e28e0c1b2ee6e378c81cf59cf1eabd.png)

2. 使用者名稱正確

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_916304ac5c49181c36ece83e5c582bd6.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_700a112ed977c001b1cf43f5c9858d00.png)

3. 連接埠號正確

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_dcbbea11c32b883e079dccab61d85db6.png)

4. 公私鑰正確

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_128c1f9dba397eb566c8d897063b397a.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_539d44a2f3d4af74e4daf787477c3059.png)

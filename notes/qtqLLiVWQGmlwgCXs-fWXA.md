# 資料連結層
## 簡介:
主機和路由稱為節點，中間網路稱為鏈結。提供服務給網路層，接受實體層服務。為何要封裝和解封裝?因為鏈結使用不同的協定。
### 1. 服務:
訊框包裝、流量控制、錯誤控制、壅塞控制
### 2.兩種鏈結:
點對點、廣播
### 3. 兩個子層:
資料鏈結控制(date link control, DLC)、媒體存取控制(media access control, MAC)
## 鏈結層定址
3種位址:單播、群播、廣播
### 1.位址解析協定(address resolution protocol, ARP):
屬於網路層協定，將IP協定的IP位址對應到鏈結層位址。送出ARP請求封包，封包有來源的IP位址、鏈結層位址、目的地IP位址，透過鏈結層廣播，符合目的地IP位址的主機會單播回覆自己的鏈結層位址
#### 封包格式
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_014dcef28127a4df47da734b0c9d86f5.jpg)


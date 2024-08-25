# Ch9資料連結層簡介
:::spoiler
## <font color="#AC19C9">簡介</font>
主機和路由稱為節點，中間網路稱為鏈結。提供服務給網路層，接受實體層服務。為何要封裝和解封裝?因為鏈結使用不同的協定。
### 1. 服務:
訊框包裝、流量控制、錯誤控制、壅塞控制
### 2.兩種鏈結:
點對點、廣播
### 3. 兩個子層:
資料鏈結控制(date link control, DLC)、媒體存取控制(media access control, MAC)
## <font color="#AC19C9">鏈結層定址</font>
3種位址:單播、群播、廣播
### 1.位址解析協定(address resolution protocol, ARP):
屬於網路層協定，將IP協定的IP位址對應到鏈結層位址。送出ARP請求封包，封包有來源的IP位址、鏈結層位址、目的地IP位址，透過鏈結層廣播，符合目的地IP位址的主機會單播回覆自己的鏈結層位址
#### 封包格式
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_014dcef28127a4df47da734b0c9d86f5.jpg)
## <font color="#AC19C9">一個範例</font>
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_697815d92d658cef4b82a7f013a90878.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d583712ae82df17187b0caee5d069aa3.jpg)
:::
# Ch10錯誤偵測和修正
## <font color="#AC19C9">簡介</font>
### 1.錯誤的類型:
干擾(非預期改變)、單位元錯誤(single-bit error)、連串錯誤(burst error)
### 2.冗餘:
修正和偵測錯誤的核心概念為冗餘(redundancy)
### 3.偵測VS修正:
修正比偵測錯誤難多了
### 4.編碼:
冗餘位元和真正資料間的關聯，區塊編碼(block coding)、迴旋編碼(convolution coding)
## <font color="#AC19C9">區塊編碼</font>
將訊息切割成區塊，每區塊有k位元，稱為資料字串(dataword)，每區塊加入r位元的冗餘，區塊長度變為n=k+r，n位元區塊稱為代碼字串(codeword)，如果代碼字串無效的話代表有錯誤，有效以原本資料取代回來
漢明距:
代表傳輸時毀損的位元數，d(00000,01101)=3，兩字串做XOR然後計算1的個數






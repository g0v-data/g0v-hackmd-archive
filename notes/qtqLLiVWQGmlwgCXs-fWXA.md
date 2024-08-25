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
:::spoiler
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
### 1.漢明距:
代表傳輸時毀損的位元數，d(00000,01101)=3，兩字串做XOR然後計算1的個數
### 2.最小漢明距:
如果要能偵測到s個錯誤，最小漢明距Dmin=s+1
### 3.線性區塊碼:
現今區塊邊碼幾乎都是線性區塊碼，是一種能以XOR運算，使兩個字串產生另一個有效代碼字串。
#### 同位檢查碼:
在資料字串後加入一位同位元(parity bit)，同位元=資料字串1的個數%2(1的個數為偶數，同位元=0，反之)。無法偵測偶數個錯誤。
## <font color="#AC19C9">循環碼</font>
### 1.循環檢查碼(cyclic redundancy check, CRC)：
使用於LAN、WAN網路。在資料字串k後加入n個0，然後除以已知除數，所的餘數n位元加到資料字串後，所的代碼字串為k+n位元，如果接收端代碼字串可以用已知除數整除，則沒有錯誤。可能偵測不到錯誤。
#### 單位元錯誤：
以多項式表示單位元錯誤為x^i^，當除數的x^0^=1時且除數為兩項以上，所有單位元錯誤都可被偵測
#### 兩個獨立單位元錯誤：
x^j^-x^i^=x^i^(x^j-i^-1)
#### 一個好的除數多項式有以下特徵：
    1.至少有兩項
    2.x^0^的係數為1
    3.不可整除x^t^-1，t介於2和k+n-1之間
    4.應該含x+1的因式
:::
## <font color="#AC19C9">檢查加總(chechsum)</font>







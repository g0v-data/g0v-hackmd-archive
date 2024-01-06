## BAG
* HIP(Head In Pillow)枕頭效應
BGA焊點的不良現象，就類似一個人把頭靠在枕頭上的形狀而得名
* 電路板的BGA零件在回焊(Reflow)的高溫過程中，BGA載板或是電路板因受不了高溫而發生板彎、板翹(warpage)或是其他原因變形，使得BGA的錫球(ball)與印刷在電路板上的錫膏分離，當電路板經過高溫「回焊區(reflow zone)」後溫度漸漸下降冷卻，BGA head in pillow defect (HIP,枕頭效應)這時IC載板與電路板的變形量也慢慢回復到變形前的狀況（有些情況下變形會回不去），但這時的溫度早已低於錫球與錫膏的熔錫溫度了，也就是說錫球與錫膏早就已經從熔融狀態再度凝結回固態。當BGA的載板與電路板的翹曲慢慢恢復回到變形前的形狀時，已經變回固態的錫球與錫膏才又再次互相接觸，於是便形成類似一顆頭靠在枕頭上的虛焊或假焊的焊接形狀。

### 如何檢測HIP(Head-In-Pillow)焊接不良
枕頭效應(HIP)大部分應該都會發生在BGA零件的邊緣，尤其是四個角落的位置，因為那裏的翹曲最為嚴重，如果是這樣，就可以試著使用顯微鏡或是光纖內視鏡來觀察，但通常這樣只能看到最外面的兩排錫球，再往內就很難辨認了，而且這樣觀察BGA的錫球還得確保其旁邊沒有高零件擋住視線，以現在電路板的高密度設計，執行起來限制頗多。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d2f7655488b40af287ea286baed5dcd3.png)


## 發生原因
BGA封裝(Package)大小不一的焊球(solder ball)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e6b518ac5543f53d00716180ef28dc9b.png)
錫膏印刷(Solder paste printing)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f24a3c0a89a6070e4278981bc10ae86c.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_32a74bfce5a964f7409ac3b5c9f19f26.png)

1. A) 導通孔完全沒有處理。
2. B)、D)是最好的導通孔設計
3. C) 盲孔(Blind hole)。
4. E) 電鍍填孔。可以使用，但價格較貴。

---
title: "利用電力通信線(PLC)裝置達成遠距網路通訊"
tags: hackpad
---

# 利用電力通信線(PLC)裝置達成遠距網路通訊

> [點此觀看原始內容](https://g0v.hackpad.tw/RiKBaC4XT4Q)


在"第零次向日葵數位體驗營"中 ( [http://ccc.logdown.com/posts/2014/04/13/osdc2014-audrey](http://ccc.logdown.com/posts/2014/04/13/osdc2014-audrey) )，R2到R1之間的實體網路通訊是利用改裝過的HomePlug PLC (Power-line communication)裝置達成的。示意圖如下：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_544c3f7d67f3a99da50dee66fc99c421)

會需要使用這種通訊方式，主要是為了解決一般Ethernet網路100M距離的限制。

HomePlug的設計想法是，將PHY訊號送入110V市電網路中，利用市電網路傳送訊號。而在這邊改裝的想法，基本上是將PHY的訊號獨立出來，不要送往110V市電網路。

## ASUS PL-X31

以下以ASUS PL-X31 ( [http://www.asus.com/tw/Networking/PLX31/](http://www.asus.com/tw/Networking/PLX31/) ) 的電路圖為例，不過原理應該也適用其他廠牌/型號的PLC裝置。

### 電路板正面

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_637c0ec1679f329b522677448f5d26d7)

### 電路板背面

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_24347776f19df4e6bc17416e2724c5fb)

### 電路圖

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_04322c78670c9f9b81d85e344131162d)
1.  電壓器
2.  感應線圈
3.  突波吸收器
4.  保險絲
5.  EMI Suppression Capacitor
6.  光耦合器Photo coupler

### 第一種可行的改裝方式

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_38cd1352700f7585dbc48d05c658b919)

綠色的部分表示利用美工刀將電路板上的連接線斷開。拉出RJ11的接頭。實際使用的時候，可以使用任意2P的線路連接兩台改裝過後的PLC裝置。

實務上，可以使用RJ11桌上盒方便轉接至不同的線材。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2b44d7f9f85dabd9b3a3a515e7e34f29)

在"第零次向日葵數位體驗營"中，因為考慮到踩踏以及距離的問題，選擇使用500米長5C2V的同軸電纜。之前也有使用電話線成功的經驗。

### 另外一種可行的改裝方式

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7c406af6cba2da41c4a769ef828a97b8)

### 參考資料


ASUS PL-X31 使用 Intellon 6300 可用 [faifa](https://github.com/ffainelli/faifa)  進行網管功能。[晶片規格手冊](http://bit.ly/1kREDMa) 。

## Dlink DHP-200 PLC

在台灣零時政府第捌次解除戒嚴黑客松( [http://g0v-tw.kktix.cc/events/g0v-hackath8n](http://g0v-tw.kktix.cc/events/g0v-hackath8n)  ) 中，我們將Dlink DHP-200 PLC以上面這種方式修改，經測試是可行的。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_72b6e6d4d08ed538b775b840fa13b519)

## PLC裝置的選擇


在選擇PLC裝置時，建議選擇像ASUS PL-X31電源線為獨立拉出的裝置。像是Dlink DHP-200這種電源接頭直接固定在機殼上的設計，拆解電路板會比較困難，需要解焊電源接腳。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_25a6bdcb0cef49914a4ba17d55915733)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3c8cc5a06061b32bba40c47c531aa900)

## 補充資料


[http://zh.wikipedia.org/wiki/HomePlug](http://zh.wikipedia.org/wiki/HomePlug)






---
tags: GIS
---

# 臺灣碎形：蒐集臺灣輪廓外形的地景景點

:::info
Fractal Taiwan - https://g0v.hackmd.io/@chewei/fractal-taiwan
:::

蒐集 庭院造景、策展場域運用臺灣本島輪廓，或是外形近似臺灣的島嶼，標記在地圖上
https://goo.gl/maps/igmsKHUWLpRnA52t7

<iframe src="https://www.google.com/maps/d/u/0/embed?mid=1AxLffaXG0wZllCTazyJuQ56zwG24W68&ehbc=2E312F" width=100% height="480"></iframe>

<br>地點清單(依實際範圍大小排序)
- [法律邊界] 臺灣島-近岸海域
    - 形成一個與臺灣本島海岸線外推 5~20 公里的形狀
    - 以平均高潮線往海洋延伸至三十公尺等深線
    - https://eland.cpami.gov.tw/CAMN/Web_GIS
- [自然島嶼] 臺灣島-海岸線
- [法律邊界] 海岸法陸域範圍-內陸邊界
    - 形成一個與臺灣本島海岸線退縮 1~10 公里的形狀
    - https://eland.cpami.gov.tw/CAMN/Web_GIS
- [道路路線] 台2線+台3線+台26線+台9線路網 
    - 形成一個與臺灣本島海岸線退縮 5~50 公里的形狀
    - [台3線](https://zh.wikipedia.org/zh-tw/%E5%8F%B03%E7%B7%9A)、[台3線](https://www.google.com/maps/d/u/0/viewer?mid=1URnZ_lfPiB1B5hZnMLR-6eQ5OiRiY1tY&hl=en_US&ll=23.85848987201846%2C120.98753&z=8)
    - [台9線](https://zh.wikipedia.org/zh-tw/%E5%8F%B09%E7%B7%9A)
- [自然島嶼] Madeira 
- [人造圖樣] 雲林新興太陽能發電廠光電板排列圖像
- [自然島嶼] Province Island
- [人造圖樣] 2022 高雄港活動臺灣島嶼形狀外框 [已撤除，僅有衛星影像]
- 待登載，武漢寶島公園 湖中島嶼 https://maps.app.goo.gl/GnM5qkXXNGBGviPQ9
- [自然島嶼] 臺南市六甲區六甲烏山頭水庫夢之湖湖中小島
- [人造圖樣] 桃園市新屋區農博園區內 [已撤除，僅有衛星影像]
- [水域形狀] 高雄市世運主場館生態池
- [人工土丘] 嘉義縣六腳鄉-蒜頭糖廠蔗埕文化園區
- [人工土丘] 桃園市中壢區私人庭院
- [人工土丘] 北投行天宮之台灣島景觀池
    - https://www.facebook.com/share/p/q8sP3cSncY6dEv8e/
- [水域形狀] 臺中市南區中興大學台灣湖
- 待登載 板橋放送所，水池內的島嶼
- [人造圖樣] 臺北市新生國小屋頂臺灣圖樣
- [人造圖樣] 臺北市劍潭山老地方觀機平台石碑圖樣
- [人造石板] 待確認-熊本城臺灣形狀石板鋪面
    - 待確認近年修繕後石板是否還在、經緯度
    - https://www.facebook.com/qdymag/posts/pfbid0gDSS12qdgjgXcBCTN9WL2Hs4TQwFMdLJ3yi4R5G3oQmA727PTRWECkgcWxrx6Hx1l
- [人造] 蓋板
    - https://www.facebook.com/share/c4rzgpGfdZgbLp2z/

評估地點
- 請見線上地圖中的「評估中的地點與容易生成台灣輪廓的地景地區」圖層
    - 重要 待登載 丹麥世界地圖造景 https://maps.app.goo.gl/bKxVMELX8BpmtyZF8
    - 待登載 玉里 水稻田 https://www.facebook.com/share/p/JzwiuMN2uCU6M5N2/
    - 待登載 35.9986650, 10.4955462
    - 東京舉辦一場市區的步行活動，路線形成臺灣本島輪廓形狀 https://japhub.com/?c=17767
    - 待查找 臺中草悟道座椅椅面形狀 https://www.facebook.com/share/p/sQXQddGeDKnekQau/
- 有一些自然地理作用，蠻容易大量生成台灣輪廓，所以此圖層也蒐集這類的地區，例如：
    - 北歐海島
    - 北美阿拉斯加州北坡自治市鎮的北部地區，凍土與冰蝕湖?
    - 澳洲內陸的阿馬迪厄斯湖，湖中小島
    - 巴西西北部沙漠 https://www.facebook.com/story.php?story_fbid=pfbid0M8HHvP5tRLqxd7gkAEGDPNMytgqaptFxNA1dZ9LHz3nnt4Bm2aEhHuewv6bbtmAil&id=100064035190296&mibextid=qC1gEa

已評估過的內容
- 海域：形狀與台灣本島不太一樣
    - [領海] 海岸基線向外12浬 (海域單位：1浬＝1.852公里)
        - https://www.oac.gov.tw/ch/home.jsp?id=243&parentpath=0,4,242
    - [經濟海域] 中華民國之專屬經濟海域為鄰接領海外側至距離領海基線二百浬間之海域
        - https://eland.cpami.gov.tw/CAMN/Web_GIS

資料分析構想
- 工具：LAND LINES - Start with a line, let the planet complete the picture. https://lines.chromeexperiments.com/
    - 使用 Draw 功能，在一定長度內，劃出臺灣形狀
        - 注意：繪製方向會影響系統取樣
        - 例如繪製南北方向的臺灣形狀，則系統會採用南北方向來比對，例如下面的圖片
        - 例如 Madeira、Tunø 聰島，外型接近臺灣形狀，但屬於東西向

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_de05b2e55b98b4f32d40bf50ed76833e.png)

## 活動

https://www.facebook.com/CitizenoftheEarth/photos/a.152858528108735/6093708947356967/

https://www.facebook.com/11.11LAPeaceGo/photos/a.291644340944594/307234052718956/

## 其他

食物外型近似臺灣，例如雞排、牛肉片、芒果斷面、韭菜盒子
https://www.facebook.com/story.php?story_fbid=pfbid02d4Xwq3JQaCbJin9m57z8Kaxsj8mX15NXQ9vbaAnzQc1PWii1Ez7CD47f2Nt7Pedvl&id=100070186572262&mibextid=qC1gEa
https://www.facebook.com/share/9mQvLC9ty996R6gr/

logo
https://photos.app.goo.gl/tN3Az3zyKYJex43a9

碎形理論應用於台灣地區建地空間型態之研究
https://hdl.handle.net/11296/2qw6r6

雙北行政區輪廓線
https://maps.app.goo.gl/sXYMBs7z7LtVpAzo8
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_80a43a328684d130120a5508a35b3705.png)

日本關西 高雄台北公園、高雄台南公園
https://www.facebook.com/healingkyoto/posts/pfbid0BPVdMcTTHZV6mYYEWSEA4JtHzHxDQB9xpVFNu8rdpEfZnVzg41cubr7brurG8DkRl

## 其他地貌輪廓

日本列島
https://www.facebook.com/share/m4QcPqw7ToNxxRJX/
---
title: "如何讓群眾願意Crowdsourcing生物資訊"
tags: Issue-Mapping,hackpad
---

# 如何讓群眾願意Crowdsourcing生物資訊

> [點此觀看原始內容](https://g0v.hackpad.tw/EZP1GRsWtBk)

前情提要：因為討論到[路殺社](http://roadkill.tw/)的現況，以及生物資訊很有機會讓人一起協作，因此整理了這段討論。
### 有趣的形式：

from AU:
有趣的一些形式，讓一般人也會拍照上傳測試，如果有Park or bird 1/10好玩，也可能讓人更願意投入，把東西放到網路中，再進行機器辨識。
- PARK or BIRD：辨識鳥或是國家公園的簡易演算法
    - [http://parkorbird.flickr.com/](http://parkorbird.flickr.com/)
- Deep Visual-Semantic Alignments for Generating Image Descriptions
    - 史丹佛大學的自動為圖片下標
    - [http://cs.stanford.edu/people/karpathy/deepimagesent/](http://cs.stanford.edu/people/karpathy/deepimagesent/)
- 相關報導：
    - [http://www.nytimes.com/2014/11/18/science/researchers-announce-breakthrough-in-content-recognition-software.html?_r=1](http://www.nytimes.com/2014/11/18/science/researchers-announce-breakthrough-in-content-recognition-software.html?_r=1)

### 簡易的門檻：

from Jimmy：
如果手機不用另外安裝App，門檻能夠降低，照片又能保留geocoding，即可方便擷取資訊
- Facebook照片會有問題，會去掉Meta Data，而且無法取得打卡的座標
    - 詳看「你們的meta都是我家的」[https://www.youtube.com/watch?v=ITehdhhkhCE](https://www.youtube.com/watch?v=ITehdhhkhCE)
- Twitter、 Instagram，都有保持照片的geo coding


### 相關案例：

- 人工解析照片的案例： [http://nettuesday.tw/events/2014/10/477](http://nettuesday.tw/events/2014/10/477)
- 目前的台灣生命大百科物種資料，由各學者集合而成，部分來自民眾自願上傳，但民眾提供的部分無專家積極控管資料品質（非 Crowdsourcing） [http://eol.taibif.tw](http://eol.taibif.tw)
- 補充說明路殺社案例，透過Facebook社團經營與收集資料，但獨立架設一資料儲存點保存資料(此案例採用Drupal)，該資料儲存點會定期去Facebook爬回資料做清理以獲得堪用的科學資料 (這邊有配合一些工具與人工清理Facebook的雜亂資訊)，也處理授權課題 [http://roadkill.tw/](http://roadkill.tw/)
- [http://feederwatch.org](http://feederwatch.org) \- Project FeederWatch is a winter-long survey of birds that visit feeders at backyards, nature centers, community areas, and other locales in North America. FeederWatchers periodically count the birds they see at their feeders from November through early April and send their counts to Project FeederWatch.
- [http://content.yardmap.org](http://content.yardmap.org) \- YardMap is a citizen science project designed to cultivate a richer understanding of bird habitat, for both professional scientists and people concerned with their local environments.
- 用 Drupal 產生地圖服務、偵測手機 Geocode 相關案例
    - [http://yosku-aulu.geo.ntnu.edu.tw/](http://yosku-aulu.geo.ntnu.edu.tw/)


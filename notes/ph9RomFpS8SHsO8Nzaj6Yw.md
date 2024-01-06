---
title: "零時政府與阿龜的邂垢 G0V x Agrithon@Taiwan"
tags: hackpad
---

# 零時政府與阿龜的邂垢 G0V x Agrithon@Taiwan

> [點此觀看原始內容](https://g0v.hackpad.tw/lWjdiQNqhuP)


### 為什麼要做這個

G0V 這邊光整理農業相關的就一百多個坑了，常常可以看到大家整理了一些列表以及分類，但說真的... 坑坑相連到天邊，究竟怎麼個連法其實隔坑如隔山(!?)，光列表分類似乎不是什麼有 sense 的事情... (被毆飛)

所以在想的是，是不是再來挖一個坑，打算引用文字分析的技術，然後分析後轉為網路關聯圖，用視覺的方式串聯目前 G0V 與各種農業相關議題，以及農業黑客松的關係。順利的話，這份網路圖除了有視覺的效果外，應該也能夠在這基礎之上順手進行分群 (graph-based clustering) ，應該就可以把概念相近的坑送做堆了 (遠目)。

### 想要達成的目標

希望能讓所有想要挖坑填坑跳坑的人，都能很輕鬆地了解相關聯的坑有哪些，促進社群相關坑的串聯及活絡。
具體上呢，就是一個線上工具，可以分析任一個指定的 G0V 專案與其他專案的關聯性 (像是新加入的熱騰騰的專案)，這樣子可以用最有效率的方式得知究竟這個議題有沒有人做過，以及有什麼相關鄰近的坑可以參考。


### 預計作法

爬完所有 G0V Hackpad 中有關農業的資料 => 斷詞及詞性標註 => 關鍵詞萃取 => 議題相似度計算 => 社會網路分析 => 視覺化

- [x] 寫網路爬蟲爬進每個農業相關坑把資料 dump 下來
- [x] 斷詞及詞性標註 (CKIP)
- [x] 關鍵詞萃取 (Length filtering + POS pattern filtering+ TF-IDF)
- [x] 議題相似度計算 (Cosine Similarity)
- [x] 社會網路分析 (Weighted-degree Centrality, Modularity clustering)
- [x] 坑坑相連到天邊的共現網路視覺化分析 (Gephi : 1-mode, homogeneous network analysis)
- [ ] Web 端連結 (JSON/GEXF to D3/Vis/Sigma)
> 目前輸出資料直接用 Vis 的 ForceAtlas2 排好像有點難收斂跑不完, 接下來改從 Gephi 輸出排好的 JSON/GEXF 直接用 Sigma 畫畫看
> [name=keith@beehivedt.com]

- [ ] 自動化上面的流程

### 需要的資料

- [G0V 農業相關坑的清單](https://github.com/keithning/g0vxagrithontw) ([G0V@Hackpad](https://g0v.hackpad.com/))

### 目前整理好的資料庫結構及資料

- [撈到並整理好的坑的資料](https://drive.google.com/open?id=0B5Y4G6hItLzfZ1MyLXFXR3NmbDA) (`坑名`, \`hackpad\`, `內容`, `斷詞及POS標註結果`, `更新日期時間`, \`weighted_degree\`, \`modularity\`)
- [關鍵詞及坑向量候選資料](https://drive.google.com/open?id=0B5Y4G6hItLzfSVpxV3dmQWViQVU) (`關鍵詞`, `詞性`, `字串長度`, `在坑中出現次數`, \`TF-IDF\`)
- [網路連結](https://drive.google.com/open?id=0B5Y4G6hItLzfVXdqM2t3TjBqbnc) (`坑1`, `坑2`, `坑坑相似度`)

### 需要的人力或資源

- [ ] 網路爬蟲
- [ ] 中文斷詞系統 (CKIP)
- [ ] 資料視覺化 (Vis.js or D3.js)
- [ ] 前端框架 (Boostrap)

### N+1 視覺化結果

- 節點：G0V 中與農業議題相關的 118 個坑
- 連結：坑與坑彼此之間的議題相似度，越粗代表相似度越高
- 顏色：坑與坑之間相似度結構所凝聚而成的議題群集，不同顏色代表不同的議題
- 大小：越熱門的坑節點看起來會越大 (連結量+議題相似度)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c7a366159679e06043a53d1c3847a851)
> 都市農耕議題因為頁面數多的關係所以有點太過明顯了XD 實際上我覺得看 [https://github.com/g0v/awesome-g0v](https://github.com/g0v/awesome-g0v) 會比較接近社群投入的情境
> [name=che l]


### 其他想法

> 其實其他議題也是可以比照辦理啦.. 或許應該把所有 G0V 坑的第一層爬下來建立 index snapshot, 然後依據不同的 category online query 產生對應的坑坑相連到天邊圖
> [name=keith@beehivedt.com]




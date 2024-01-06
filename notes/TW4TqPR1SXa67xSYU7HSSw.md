---
title: "自己的照片自己存"
tags: hackpad
---

# 自己的照片自己存

> [點此觀看原始內容](https://g0v.hackpad.tw/JcpwPHXeiAR)


### 緣起

picasaweb 倒閉, flickr 又是前途未卜的 Yahoo 在維護... 有沒有什麼更好的解決方案呢？

### 相簿服務自己來

我希望有個相簿服務可以滿足這些條件：
- 開源，並統一下列規格的基本介面
- 跨服務 \- 不管你背後用什麼系統，都可以運作
    - 在自己電腦也好，用 AWS 也好，用Google Cloud Storage 也好
    - 甚至既有的服務也好，像 flickr 、 google photo
- 分散式的照片流，讓任何自己架的服務仍可以串流在一起
    - 沒有中央主機，但架好自己的服務，馬上可以跟其它人共享標籤、集合等。
    - 從此 hackathon 的照片，自己拍的就自己host，但仍然所有人都可以看
> YES!
> [name=chihao y]

> 共同篩選照片：可以用標籤解決
> [name=chihao y]

> 共同調整、編輯照片：shared parameters
> [name=chihao y]

- 同布 / 備份 / 搬家機制
    - 可以很容易將自己所有照片從 A 服務轉移到 B 服務
        - 例如： flickr 到 smugmug, 500px 到 local disk
    - 可以很容易備份特定標籤
        - 這樣子我們仍可架設中央主機，定時備份網路上所有重要事件的照片
    - 可以讓多個服務同步照片，讓他們同時維護同一份照片集
        - 主要用途：異地備援 or 自動上傳

Summary: 開源、分散、同步、跨服務
其它有也很好的功能:
- flickr 的所有功能：版權標示、權限管理、集合、相簿、社交功能、標籤、搜尋、社團
- 500px 的評分機制
- stockphoto 的交易機制
- 匿名上傳
- 感覺有 buffer 的 [pablo](https://buffer.com/pablo) 可以幫坑主或講者做Quote

### 服務調查

- GIT 似乎滿足這樣的條件，但照片不需要版本管理
    - 有些東西還是要管理版本，像是：
        - Lightroom export 的 edit meta
        - photoshop 過的照片也要管理版本

### 專案庫

若找不到滿足上述需求的開源套件而要自己開發的話，將會放在 [http://github.com/g0v/photos](http://github.com/g0v/photos)

### 人力需求

設計師  / 前端工程師 / 後端工程師 / 攝影師


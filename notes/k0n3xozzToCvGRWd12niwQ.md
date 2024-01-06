---
tags: hackfoldr 2.0
---

# MeshFoldr: The Next Generation of Hackfoldr 共筆飛龍～


## 一句話簡介

Hackfoldr 之 IPFS 版

> Hackfoldr 是 g0v 社群重要基礎建設，開發於 2012 年。大松、太陽花運動、氣爆等都使用 hackfoldr 作為快速整合資訊的入口站。

## 長一點的介紹：

MeshFoldr: the next generation *real*  decentralized collaboration tool, boldly unites communities and teams across vast distances, fostering the courage to face the unknown. 

MeshFoldr creates a resilient power of collective wisdom, its crowd-audited architecture standing vigilant against crisis.

Join us on this voyage with Meshub as our guiding star, exploring strange new worlds and boldly going where no one has gone before. Engage.

新一代 ㊣ 去中心化協作文件夾，連結分散社群和團隊，培養勇氣面對未知的挑戰。

MeshFoldr 創造了一種集體智慧的強大力量，其經過眾包審核的架構在危機中保持警惕。

加入我們的旅程，以 MeshFoldr 為指南星，探索陌生的新世界，勇敢地去往沒有人去過的地方。出發！


## 重點功能：

* 整合各種文件的 portal（原 Hackfoldr 功能）
* Hackfoldr 之 IPFS 版
* 推不倒的多中心編輯檯
* 配備編輯權限設置
* 適用於危機時刻整合資訊
* RWD！手機用，不會爛

## 延伸相關：

* 編輯群可連結 Meshnetwork 實體訓練


## 提案人：
ipa, clkao 

@2023/4/30 桐花松


## 桐花松工作區

### hacking 重點

* 想想與農業的連結～
* 設定使用情境
* 確認重點功能與開發架構
* 設計 LOGO!


### 參與者簽到區

### 討論筆記區

* 使用情境：危機時刻
    * 多中心編輯儲存，不會倒
    * 大型社運、災難、戰時民防
    * 需要整合多方資訊
        * 即時資訊：直播、資訊判讀、共筆
        * 資源分享：物資、急救、血庫、口罩
        * 教學文件：mesh network、
    
* 編輯流程
    * Persona:
        * 開啟文件者 owner
        * 有權限修改者 editor
        * 編輯貢獻者 contributor
    * 初步流程圖： https://www.figma.com/file/NWIjckziBSi5S42KVSIMAa/Meshub-sketch?t=WnoObhJ7LZuvSc2Y-1

* Hackfoldr painpoints:
    - centralized store, single point of failure (ethercal or gdoc)
    - no authorization
        - prone to vandelize (intentional or accidental)
        - but has the benefit of low entry barrier for editing
    - not auditable
        - who did what? how to build a trust system?

* MeshFoldr feature
    - decentralized store
    - 編輯權限：
        - owner: grant editor
        - editor: approve contribution
        - contributor: propose editing   
    - contribution can be anonymous 
    - intuitive contribution flow, pull-request flow (PR)
        - version control



## References


https://github.com/automerge/automerge
https://github.com/holepunchto/corestore
https://github.com/liveblocks/liveblocks

https://driftingin.space/posts/you-might-not-need-a-crdt

## 相關專案

* [Hackfoldr 快取計畫](https://g0v.hackmd.io/A175kRMVSxGqBRCerawXIA
)   / Ronny
---
title: "g0v 零時空汙觀測專案-感測器開發共筆"
tags: hackpad
---

# g0v 零時空汙觀測專案-感測器開發共筆

此區為[g0v 零時空汙觀測專案](https://g0v.hackmd.io/QeNRXR7XQQK7JU0vRrnEYA)的子分區，提供感測器方面開發共筆

簡述:
由於g0v空汙觀測專案是從ProbeCube專案分支出來，目前PC開發團隊也以支援g0v為主要任務，故此g0v空汙專案下的感測器架構目前採用ProbeCube方案去推廣。

## 感測器開發方向大綱


### 開發方向

- 零件需容易取得
- 低組裝與操作門檻

### 基本規格

- Arduino liked 控制板 (Particle Photon)
- 溫度濕度 (DHT22)
- 懸浮微粒PM2.5 (G3)

### 附加規格

- 全腳位預留輸出排母
- I2C預留接座x2
- groove 預留接座x1
- VoC總揮發物汙染感測器 (TGS2602)

### 外殼

- 3D 列印外殼
- 自行加工收納盒 ( ex. 大創$39x2)

## To-Do List (已有工程師規劃填坑區)

- [ ] 設計雷切外殼以便在需要大量部屬時比3D列印更能快速生產
- [ ] 3G 通訊 \- Particle electron

## 許願區或其他疑問待討論 (等待工程師跳坑區)

    - [ ] 解決無wifi區域，靠電信通訊
        - [ ] 3G \- Particle electron
        - [ ] LoRa
        - [ ] 用離線方式運作，資料暫存於機器
    - [ ] 嘗試開發機器自動登入wifi驗證頁面的可行性, 抑或是使用網路線的版本
        - 或許得為每個志願放置的單位做客製化!
    - [ ] 手機APP工程師
    - [ ]
## 感測器目前開發狀態

專案詳細資料 github repo: [https://github.com/Lafudoci/ProbeCube](https://github.com/Lafudoci/ProbeCube)

2016/3/10 - v1.0 PCB版已送洗
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9e7fe7ac7f46379c5982115a32e932aa)
2016/03/10 - v0.99 3D列印外殼完成
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_03426d2f0e12d70c1720e58c81c17b36)

2016/02/25 - v0.99 測試成功+大創收納盒做外殼
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_edb595775cc13e47a7433f76d3e3a941)
2016/02/25 - 收到v0.99 PCB
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_91f8a5c3f32450e88696b8cb35536ae4)


20170329 - 最後一批感測器即將發送
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f8ca2c73afdca0d70d58bfae9329b996)


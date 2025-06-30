# vTaiwan視訊自動逐字稿生成與校對說明

## 工程圖(old)

![](https://g0v.hackmd.io/_uploads/rkgLaAh4Nee.jpg)

### 目前狀態和上圖的主要異動：

1. 取消JaaS的字幕服務
2. 改為自架轉錄分軌音訊和後端轉錄服務
3. [後端轉錄模型whisper-large-v3-turbo與計費說明](https://developers.cloudflare.com/workers-ai/models/whisper-large-v3-turbo/)


## 應用備忘(new)

1. 視訊前需先用Google Login登入
2. 要即時轉錄並記錄的發言，在發言前請按右下的"麥克風"鈕
3. 一次轉錄上限為30秒鐘
3. 所有登入的用戶都可以協力校對
4. 測試步署點(目前只能說中文)：https://vtaiwan.pages.dev/jitsi


## 施工狀態 

1. 前端程式(視訊與逐字稿校對)：
- [x] 介面完工
- [x] 自架轉錄分軌音訊，完工
- [ ] 待多人連線實測bug

2. 後端程式(中文音訊轉錄)
- [x] 完工

3. 後端程式(分類歸檔)：
- [x] 完工

4. 後端程式(查閱)：
- [x] 完工


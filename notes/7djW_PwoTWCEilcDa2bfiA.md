---
title: "公民連署平台"
tags: g0v.us,hackpad
---

# 公民連署平台

> [點此觀看原始內容](https://g0v.hackpad.tw/s3bij8M6Ypx)


### 簽到

> 負責網頁相關
> [name=verysure]




## 需求種類：

1.  發起公投用
2.  罷免用
3.  一般連署書/個人陳情書


### 一、民間版公投連署

_範例：核四公投發起連署_
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4324ef4a427dd931af4f1df3cea2f8aa)
#### 需要個資：

（1～4必須線上填）
1.  姓名
2.  詳細戶籍地址（含鄰里）
3.  出生年月日
4.  身份證
5.  **親筆簽名或蓋章**

#### 系統欄位：

- 編號：自動產生，前五碼為3+2郵遞區號，後面才接序號，方便公民團體整理（法規規定一定得照縣/市+鄉/鎮/市/區裝訂成冊，very labor intense!）
- 發起團體
- 連署單位是啥？


### 二、罷免用

_範例：割闌尾--吳育昇 By 憲法133實踐聯盟_
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_52123f15c20c92c7b30415d07b2f3e95)
↗這東西真的不能再更醜了…

#### 需要個資：

（除了1 2 4 6 哪幾個還需要驗證？）
1.  姓名
2.  身份證
3.  性別
4.  出生年月日
5.  職業
6.  戶籍地址
7.  **親筆簽名或蓋章**
8.  備註是幹嘛用的？

### 三、陳情書產生器

_範例：318學運期間PTT鄉民寫好的陳情書範本_
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3cac8dbfdaa9c398e19356da1db946d9)
#### 需要個資：

（因為是個人用，不一定要線上填，但可以填了地址自動產生民代名字跟聯絡方式！）
1.  選區立委/議員
2.  姓名
3.  身份證
4.  詳細戶籍地址（含鄰里）
5.  簽署日期
6.  **親筆簽名或蓋章**

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_db55b56bfaa913080487f587d9c7b900)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_cb73e0fe9de18dab46acdebc612a63ea)

## TODO:

### User Facing Site:

    - 議題列表
> 這個我來試試 包括輸入下面個人資料的 之後再來perfect
> [name=verysure]

    - 輸入個人資料
> 地址有台灣郵局Api可以用的樣子 提高地址正確率
> [name=Chia-Yin T]

    - 送出連署書

### Admin Facing Site:

> 這個我目前不知不知道能作到怎樣地步
> [name=verysure]

    - Create Issue:
        - 選擇下載意見書模式，連署書模式，或直接用傳真API，或email到市長信箱
        - 輸入訴求內容/陳情書內容
    - Download/Print/Fax/Send 連署書

### 網頁部份

- 目前我打算用Meteor


## references

[全民公投 app 構想 / 罷免 / 連署網站](https://g0v.hackpad.tw/-app--cbeSqmtPCjX)



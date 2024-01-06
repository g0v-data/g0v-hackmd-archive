---
title: 「我有參加🙋」徽章計劃 attendence-badge
tags: 徽章, attendence-badge, NFT
---
# 「我有參加🙋」徽章計劃 attendence-badge

## 專案簡介

為參加本次 Hackth44n 黑客松(2021/6/23) 的人發數位徽章, 以證明確實有參加過

會議開始時可以到 Gather Town G0V LOGO 旁邊的販賣機, 按 x 領取

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f07f0bc95287deabcfce51f4d6c6ef08.png)

前往 (當活動開始時附上 Spreadsheet 網址)

在頁面上面選擇一組兌換碼，然後請將其標示為已領取

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3f685943da74af5fd5cc84099adcf7dc.png)


請自行保存標示為已領取的兌換碼。活動過程中或結束後, 可以隨時開啟領取頁面領取

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8a30db4dbdca52e2430acf0c967d47d3.png)


加密錢包地址可照以下方式產生
(
不需要儲值, 只要有地址就可以領取徽章
不需要儲值, 只要有地址就可以領取徽章
不需要儲值, 只要有地址就可以領取徽章
)
https://medium.com/taipei-ethereum-meetup/%E9%80%8F%E9%81%8E-metamask-%E4%BD%BF%E7%94%A8-ethertw-tickets-%E5%A0%B1%E5%90%8D%E6%B4%BB%E5%8B%95-c313e33f87a5
或 https://www.youtube.com/watch?v=wS5WjvANwXA

徽章網址 https://poap.gallery/event/3272


----

# 籌備紀錄

## 可能的做法:

1. 透過 POAP 收集參與者地址後, 一次發放徽章 <- 要求使用者人人有 wallet...😅
2. 自己來寫一個類似的. NFT factory + IPFS (放圖檔或 svg 檔)
3. 這是 [POAP 的管理畫面](https://app.poap.xyz/admin/events/pennydao-ethglobal-scaling-hackathon-2021), 他只用 PNG 圖檔.(但我們只有一個 event, 不需要這麼複雜) 
4. 查詢的前台 [POAP 前台](https://app.poap.xyz/scan/0x9E4C996EFD1Adf643467d1a1EA51333C72a25453), 這樣的作法, 基本上要大家裝一個 Metamask, 已經要有一個帳號. (或我們可以用 ether 帳號跟 DID 結合. 就自動有 DID 帳號了)

## 需求:

- 不要求使用者先有 wallet
- 發放 redeem code 或 redeem url, 收到的人可隨時自行兌換徽章
- 限量 150 枚 (粗估, 120 人報名 + 工作人員, 若有確切數字歡迎提供)


## 證明

1. 我們怎麼證明, 他有參加? <- 僅在黑客松期間發放 redeem code
2. 最簡單的方法是, 大會給我們清單.(POAP 是這麼做, 檢查你是否在清單裡) <-- 但是萬人註冊 != 到場
3. 難ㄧ點的方法是, 我們自己收集 user list, 能證明他的確有參加.(先發 DID, 讓其他單位掃描 QR code, 證明有來過 (有點像現在的聯名制))
4. 活動現場 （ex: gather town 上發放）?? 這次不是虛擬的嗎? <-- gather town 是虛擬的空間

## 收集

- 參與過程中自助填寫 address <- 難
- 透過 bot 填寫 address

- 透過 bot 在大會期間取得 redeem code
- 沒以太坊地址的人, 可以用 redeem code 換徽章
- 透過坑主發送 redeem code

## 取得圖面

可能的選擇：

[x] 商請 Designer (Tofu) 提供圖像

或經授權 擷取本次黑客松的廣告圖像部分當作徽章圖面

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8215db3856b192b70bf59df52fd1c0ce.png)

徽章示意圖:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b68c94d06d86fe91e9f6e6ea4489810e.png)

https://badge.design/?_ga=2.243801541.1198559638.1610964152-583521409.1605026358 


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cf742ed6c5a9bdc0d00543a493a5445a.png)


https://www.facebook.com/g0v.tw/photos/a.456791061028852/5694787190562520/?type=3

或大會提供我們也行 (類似下圖)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7860fdc76aaddf36862ad9fe16369272.png)


POAP Badge specs:
Mandatory: PNG format
Recommended: measures 500x500px, round shape, size less than 200KB

## 建立徽章


徽章內容

name: g0v Hackath44n 世界最危險黑客松
desc: 參與 6/26 g0v Hackath44n 世界最危險黑客松 線上活動
country: taiwan
Start Date: 6/26
Website: https://jothon.g0v.tw/events/

可能的選擇：

1. [x] 透過管理介面自建
https://app.poap.xyz/admin/events

2. 連繫 POAP
https://docs.google.com/forms/d/e/1FAIpQLSccs0z4fk07q1Eqc9SCzXkb9T50IY9v0vRkDvJu3GGKPIFG5w/viewform

3. 自幹系統, 將徽章存到IPFS

做個前端把資料收集到Google form/SPREADSHEET,  會後一次一起發送最便宜

- NFT factory https://paper.dropbox.com/doc/g0v-badgets-NFTs-GmnF9EKeThx4Mgw9kSCBA
- NFT 的 smartcontract https://gist.github.com/mingderwang/0e1ea9f9a31f1d2857f8a6229c8fc1c5

### POAP 建立徽章教學
- [How to set up a POAP website](https://tomso11.medium.com/how-to-set-up-a-poap-website-511ef979ea19)


## 散佈

記得以前 POAP 有發一些貼紙, 上面有代碼可以 redeem badge
https://medium.com/poap/what-is-poap-d7e8fdfc207d

[ ] 提供兌換指引


## 後續想法

- 技能貼紙 badge 化
https://drive.google.com/drive/folders/19EskaGwNsPba-qrzVpRtKsRsYYrkai9B

可能的選擇：

將技能貼紙的 redeem code 發給坑主, 坑主可以發給參與者

- 根據反饋, 整合進 ARAY 大松活動報名https://g0v.hackmd.io/vJ7_irbLRQGMYF29C9mZGA#%E5%A4%A7%E6%9D%BE%E7%AD%89%E6%B4%BB%E5%8B%95%E5%A0%B1%E5%90%8D

- 跟報名綁在一起 做個網站或App, 活動期間輸入報名者的id或序號可以換一組 redeem code

## 參考資料
- 討論 (telegram) https://t.me/solidity_taiwan_1
- Graph team 發 NFT 給有貢獻過的人
https://thegraph.com/blog/poap-graph-nfts
- 神州載人飛行badge
https://app.poap.xyz/claim/czdnn9

- 類似: https://gitcoin.co/kudos/27230/taipei_ethereum_meetup 或 https://app.poap.xyz/scan/0x9E4C996EFD1Adf643467d1a1EA51333C72a25453 的數位徽章 (且用 NFT 來做)

----


### 緣由
https://beta.hackfoldr.org/g0v-hackath44n/https%253A%252F%252Fg0v.hackpad.tw%252FProject-Readme-aCZGg48I5pX

### 要解決的問題
### 預定使用者
### 預定功能
### 現有類似專案
### 相關專案
### 授權方式
### 使用資料
### 專案目前狀態

[X] 構想
[x] 規劃
[x] 雛形
[x] 實作

### 徵求協作者
發起人/拋磚人：gasolin

找出合理的兌換方式
撰寫如何領取徽章的教學文章: https://g0v.hackmd.io/jL2TkkcFQi-m_v6fA7U8Rg by johnson
撰寫如何建立新徽章的教學文章 https://blog.gasolin.idv.tw/2021/06/26/create-poap-badge-for-event/
如何複用到後續活動

### 實作細節

進度與 to-do

- [x] 從 tofu 取得 badge 圖面
- [x] 透過管理介面自建 badge
https://app.poap.xyz/admin/events
- [x] 回信要求 badge 數量
- [x] 收到 google spreadsheet 
- [x] 測試可兌換 badge
- [x] 找出合理的兌換方式: gather town 販賣機開啟網頁 https://g0v.hackmd.io/jL2TkkcFQi-m_v6fA7U8Rg , 會議期間提供 spreadsheet 連結

撰寫如何領取/查看徽章的教學文章
- 準備錢包 (不用有$), 產生地址 https://www.youtube.com/watch?v=wS5WjvANwXA
- 在 redeem url 中填入地址, 取得徽章
- 在 https://app.poap.xyz/ 查看徽章

- POAP是一個公開的發放NFT徽章工具
- 透過提供兌換 URL 的方式, 讓參加者可以隨時去兌換徽章
- 參加者需要提供一個加密錢包地址來收取徽章 (有非常多種加密錢包可選擇, 建立錢包地址也是免費的)
- 只要提供錢包地址就可收取徽章, 不需要額外費用
- 可在 https://app.poap.xyz/ 查看所有收到的徽章 (或在其他的NFT瀏覽工具中查看)
- 收到NFT徽章後, 也可以轉移到別的錢包地址

- [ ] 撰寫如何建立新徽章的教學文章
如何複用到後續活動

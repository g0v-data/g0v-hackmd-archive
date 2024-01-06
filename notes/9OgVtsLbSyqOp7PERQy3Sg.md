---
title: 英文版臺灣防疫日誌 - 提案
tags: COVID-19
---

# 英文版臺灣防疫日誌 - 提案

坑主：@timhsiaotw

坑主說明：坑主目前是臺大醫學系的學生會會長，與一些朋友主要是台大的學生，開始與官方交流疫情近況後，希望能夠有台灣的防疫經驗英文版，可以提高台灣在國際的能見度，透過網站分享給國際上防疫人士的資料，4/2 才開始籌備

網站
- [初始架構討論頁面，包含內容類型與標籤](https://docs.google.com/document/d/1SkhxgyDbQSYv5Rl-C9qfHvJuLLvP8KhHmo5aRzcYQ0o/edit?usp=sharing)
- 一開始想像是 wiki 資料庫的模式
- 目前有得到林宗男老師的幫忙，後端可以幫忙架設
- 預計跟台大的計中借學術網路，用主機架 domain
- 徵求網站工程師(前端)
- 理想上，希望兩週內有網站上線
- 有正在跟疾管署接洽相關文件
- 想要有一個「大事記」，類似 Jason Wang 整理的 https://bit.ly/3dYlecE
    > [name=chihao] 如果是大事記的話，面海松（FtO）社群有整理一份台港日韓的大事記，雖然還沒有很完整 XD https://g0v.hackmd.io/@chihao/facing-the-coronavirus

資料
- 團隊目前正在翻譯 CDC 臨床指引
- 會有比較醫學專業的東西，並且也會從疾管局那邊得到一些資料
- 也徵求協助英文翻譯的朋友

目標群眾
- 其他國家駐台辦事處人員
- 國際媒體 (方便發新聞稿)
- 各國的防疫人士 (第一線防疫人員、制定政策的人)


# 討論

## 工具與方案分享
> mrorz: 過去雨蒼開的，使用 **HackMD Book mode** - https://hackmd.io/@billy3321/2019-nCoV
>
> Tim: Hackmd 有審查機制嗎？
> mrorz: 關於防疫日誌，我覺得用 hackmd book mode 或 hackfoldr 或甚至是 Google site 做骨幹，會比招募網站前後端容易呢，也能比較專注在內容整理與生成上面。
> Tim: 回應mrorz，行政院資安處長簡宏偉Howard，很擔心被中國網友出征的事情
> mrorz: Google site 可以設定協作者唷。hackmd 其實也可以
> mrorz: 畢竟協作專案最重要的應該是內容生成，方便分享、大家共編。
> mrorz: 網站的部分應該是盡可能把東西丟出去的 publish 端，像是一個可以共編的 CMS （wordpress 之類）就好，所以有現成、免費、又能控制編輯權限的產品，就直接用吧
> Stimim: 我也覺得 mrorz 的提案不錯，還不確定後端需要什麼東西
> chihao: 提案標題裡面寫 Wiki，我還以為是真的要架個 Wiki？:D
> Stimim: Q:有需要做資料視覺化嗎？
> mrorz: 如果是疫情指引之類的，原本 CDC 呈現是這樣：
https://www.cdc.gov.tw/Category/MPage/V6Xe4EItDW3NdGTgC5PtKA
> mrorz: 我想就是大量的文字，所以適合 Google site 呈現，或者是用 hackmd book mode
> chewei: 標籤化呈現網頁案例參考 http://bit.ly/tree-taiwan ；後台是 google sheet
> chewei: 參考網站，蒐集與呈現 Best Practices 
http://www.cec-design.com/?s=covid-19


## 協作工具的編輯權限設定

### Hackmd

個別文件右上角可以設定「受邀者才能編輯」
但大家都可以看得到
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b331f4daa5ad164e218f5e20d1d6abb1 =300x)

書本模式教學：
https://hackmd.io/s/how-to-create-book-tw

### Google doc

- 可以開放所有人能 suggest：https://support.google.com/docs/answer/6033474?hl=zh-Hant
    - 也可以分享給特定人士或是群組 (googlegroups)
- 「發佈」功能可以把文件變成靜態網頁，流量再大也不怕：https://support.google.com/docs/answer/183965?hl=zh-Hant


### Google site

- <https://support.google.com/sites/answer/97934?hl=zh-Hant>


### Sheet2site
- 用 googlespreadsheet 當作後端的資料庫，並用 Sheet2site 來呈現
- 案例：http://bit.ly/tree-taiwan 
- 案例-結合google表單：https://bit.ly/3aOt0UE

### License
- 可以參考 https://en.wikipedia.org/wiki/Creative_Commons_license
- CC 授權小幫手 https://g0v.github.io/cchelper/
> [name=chihao] 還是要從眾多 CC 之中選一個？
> [name=stimim] 對 XD
> [name=chihao] https://choosealicense.com/
> 感覺可以區分
> (1) 原始資料來源的授權
> (2) 協助翻譯的貢獻者的授權
> (3) 團隊產製的成果的授權

## 採訪範例
- [g0v COVID-19 採訪共筆](https://g0v.hackmd.io/@kiang/covid19-interviews/)

## g0v的建議：HackFoldr
- https://beta.hackfoldr.org/g0v-hackath37n/http%3A%2F%2Fg0v-jothon.kktix.cc%2Fevents%2Fg0v-hackath37n

## 缺乏前端/公衛背景的話...
- g0v的 @caasi、@Bear 說叡揚資訊公司內部有前端工程師/公衛背景的人願意幫忙

## nCoV_API...
- https://documenter.getpostman.com/view/1223095/SzS4S7kd?version=latest

## 各國的Best practice
- http://www.cec-design.com/?s=covid-19

## CDC Official English Guideline
- https://www.cdc.gov.tw/En/Category/ListContent/bg0g_VU_Ysrgkes_KRUDgQ?uaid=0nAzwpXdBNIAPOvJhwrGoQ

## 和Bear、Caasi討論我們目前的網頁前端需求：
### 網頁現況
- 目前網頁的網址：fightcovid.edu.tw
- 目前網頁搭配的臉書粉絲專頁面：https://www.facebook.com/FightCovidTaiwan/
- 下週一行政院想要用媒體宣傳我們的網頁，並且推廣我們下一波社群活動#AskTaiwanAnything
### 提案需求
- 想要在下週一之前，設計一個簡潔，以文字為主的網頁首頁
- 參考：https://www.healthforall.tw/
1. 想法：About us；Main Topics(with links to specific pages)；#AskTaiwanAnything
- #AskTaiwanAnything希望可以模仿：https://petitions.whitehouse.gov/
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a7a3d723610a49191395828e059b42ef.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d65b9f3293b69f3ccd1a363fb88b7ce4.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a6de5bdec54571ed4b2fd4610f564d68.png)
1. 教學三步驟提問方法、顯示目前熱門的提案問題、Log In來做連署
### 後續溝通的平台
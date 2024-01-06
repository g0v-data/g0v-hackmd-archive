---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20221019 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：MrOrz, nono, bil, charles, 助理
- 線上出席：4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API

> https://github.com/cofacts/rumors-api/releases/tag/release%2F20221013

- env var cleanup

#### :globe_with_meridians: Site

> https://github.com/cofacts/rumors-site/releases/tag/release%2F20221013

- Audio & video support
- filter by media type
- comment list in profile page

#### :robot_face: rumors-line-bot

> https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20221013

- Fix "No such message" bug
- LIFF support image
- audio & video support

## 影片上線後

### 宣傳
- 還沒做 QAQ
- 第一次 announce 會是在大松 [name=mrorz]

### 數量與檔案大小

- 查詢數 (UserInput / MessageType event)
- 送進資料庫數
- Proxy 經手數量
  - 若為新的檔案，會有查詢一次、送出一次
- Proxy 檔案大小

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5a1caaa65689f7c87f3596fa5812993e.png)

https://datastudio.google.com/u/0/reporting/499d372a-07d1-49ce-a96e-88a52f71b865/page/o6W5C/edit?hl=en-US

- Preview 有時候會壞掉 [name=4000]
  - As expected, implementation of thumbnails are not finished yet [name=mrorz]
- 發現影片比較多 [name=bil]

### Cost

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bb6eb389a5790b813ef4013569386758.png)
- 包含資料儲存、進出 bucket 流量等等

Breakdown by SKU:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f8e5c448984cb14b51a2b3d1fea11758.png)
- Nearline Storage: 資料庫備份，一直相當恆定，慢慢變大
- Regional Standard Class A Operations: 應該就是圖片與影片的讀取、寫入等等
- Standard Storage Asia Regional：應該就是圖片與影片等等佔用空間的費用。


### 重複影片
山崩
- https://cofacts.tw/article/Fosi5YMBv5it-Cx_TmDT
- https://cofacts.tw/article/RItR6IMBv5it-Cx_XWL1

Nature 流感疫苗防 covid
- https://cofacts.tw/article/P4sx6oMBv5it-Cx_v2Tx
- https://cofacts.tw/article/YYtXzoMBv5it-Cx_Ukh0

分析
- 分享時不會有 binary 差別
- 應是下載後重新上傳
- 影片下載重新上傳的狀況應該比較少，因為檔案很大 [name=bil]

## Interview
From Strait Times
Deadline: 本週五中午

- 4000
- bil

## 本週違規檢舉
> [name=mrorz]
> 最新這幾篇檢舉有點難判斷
有點可疑但又沒有二次詐騙 LINE ID
https://docs.google.com/spreadsheets/d/e/2PACX-1vRdcwXdC36xfgXfSMSk527Zbel9A-__vwRXkQ0NjkzSXoSPETCFc7sI7SoaAFdPCfskugtQL-Md8JgH/pubhtml
>
> [name=cai]
> 劉起洪系列嗎
有幾篇查核的文字丟 google 會發現都是複製其他網站內容又沒附該網頁連結
可以再觀察 
>
> [name=cai]
> 最新查核又是類似情況的出現了
這次把要查核的原文挑幾篇點開看，都是複製新聞改當事人名稱www
> * https://cofacts.tw/article/19xs9h37paqdh 原新聞 ： 為父親辦後事貸款　孝女險遭騙手續費10萬 裡的林女 改掉
> * https://cofacts.tw/article/6hgryvgkb1p9 原新聞 ：警破求職詐騙集團拘女成員
> * https://cofacts.tw/article/f84f96dtlmt2 原新聞: 詐騙集團謊騙投資房地產 婦人險遭詐財300萬  這篇只有改標題
> * https://cofacts.tw/article/1lgis9b8sl5gp 原新聞: 網路4大陷阱解密 上半年網購詐騙最猖獗

- 不喜歡這些回應，因為 SEO 好，spam 會被看到 [name=bil]
- LINE 上沒人查，像是在蹭 SEO 流量 [name=mrorz]
- 但卻又沒有附連結，所以不是單純 SEO [name=mrorz]
- Follow cai 的意見，再觀察看看 [name=mrorz]

https://cofacts.tw/article/1xh8d9i1gxbp8
- 刪單一回應，不用 block 使用者 [name=mrorz]

## g0v 十週年系列活動
> 上週：https://g0v.hackmd.io/000c8SvUQXKOVKIgIzNpXg#g0v-%E5%8D%81%E9%80%B1%E5%B9%B4%E7%B3%BB%E5%88%97%E6%B4%BB%E5%8B%95


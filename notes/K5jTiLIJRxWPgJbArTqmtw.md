---
title: "台灣正名器 http://nameistw.herokuapp.com/"
tags: g0v.us,g0v us,hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/RRUz1822aga)


## 專案簡介

### 專案說明

留學生申請簽證或學校，海外開戶，申請工作，填寫申請各式文件時，國籍時常找不到台灣 (Taiwan/ROC) 而被迫選擇 PRC (中國) 或者 Taiwan, Province of China。

台灣正名器的目的，是提供海外台人一個通報的平台，來改善這個狀況，集結群眾的力量為台灣正名，我們收到通報之後，經過查證屬實，將以北美FAPA (Formosan Association for Public Affairs)名義向該機關提出正名要求，並追蹤該機構是否回應我方訴求．這些年北美FAPA致力於正名活動，已向許多官方及民間機構提出訴求並成功正名，其中包含：移民署，FDA，Apple…等等。

許多公司甚至政府部門的報名網站等等，會在國籍列表上面把應該要是Taiwan的部份打成Taiwan, province of China之類的，這個專案讓我們能更有效率的要求這些單位做出更正！

**發起人/拋磚人**：Alysa Chiu (FAPA 台灣人事務會)

## 目標與功能（什麼問題，要如何解決）

### 預定功能

1.  提供網友回報哪些機構、公司把台灣顯示成Province of China，並製作成公開的清單。
2.  提供現成專業信函，甚至是自動幫網友寄信對該機構施壓。
3.  追蹤該機構或該公司的回應


## 要解決的問題

需要網路平台可以提供回報、發函
相關專案：
台灣國籍爭議資料蒐集 [https://g0v.hackpad.com/NgPsAXzKYzl](https://g0v.hackpad.com/NgPsAXzKYzl)

使用資料
FAPA 署名信函

### 專案目前狀態


(9/27/2015 G0V.us @ NJ Hackathon) 已有Prototype, 請看下方成果展示。

FAPA是長期關心台灣政治事務以及台美關係的台灣人組織。長久以來，FAPA長期對將台灣列為中國一省的組織寄出抗議信函，並已經成功修正許多網站的列表。這個計畫希望能將FAPA長期已經在做，並且獲得初步成果的工作，藉由網路平台與網友的合作得到更大效果。FAPA目前現成的東西有：

- FAPA正式署名，有各種舉證資料的抗議信函
- FAPA的經驗




## 徵求協作者

發起人/拋磚人：
分工與成員
- [ ] NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
- [ ] NeedsDesigner: 需要介面設計
- [x] NeedsData: 需要資料（擷取、清理）
- [ ] NeedsTech: 需要技術支援（程式、架站 etc)
- [x] NeedsProcess: 需要幫忙設計作業流程
- [x] NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡
> 設定成 project registry 中的 tags，需要幫忙的會自動 promote 到 g0v project hub
> [name=ET B]



## 實作細節（非技術背景可跳填）

協作工具
- github repo：[https://github.com/kiya69/not-prc](https://github.com/kiya69/not-prc)
- hackfoldr 工作資料夾網址：[https://notprc.hackpad.com/](https://notprc.hackpad.com/)
- google drive 共用資料夾網址：

進度與 to-do
> 僅供參考
> [name=ET B]

- [x] product planning（recommanded procedure from justin lee / 李易修）
    - [x] strategy
    - [ ] scope
    - [x] structure
    - [ ] wireframe
    - [ ] visual
- [ ] web front-end
- [ ] web back-end
- [x] ui / visual design


## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）


台灣正名器
[http://nameistw.herokuapp.com/](http://nameistw.herokuapp.com/)
Repo: [https://github.com/hsin421/nameisTaiwan](https://github.com/hsin421/nameisTaiwan)
如何通報？
Step 1: 發現需要改正的機構網站，事由填入『報案區』的表格
Step 2: 將台灣誤植為中國，或是找不到台灣為國籍的的選單畫面，擷取上傳到『報案區』
Step 3: 提供該網站或該機構官方網站，並且提供該網站機關聯絡人
Step 4: 附上您的姓名及email，方便我們與您聯繫
Step 5: 按下Submit鍵，您會收到一封認證email，請讀取後按確認，我們認證後會向該機關提出正名訴求
Step 6: 通報步驟完成後，『已知案件』區會看到您上傳的案件，狀態會為『等待認證中』。等FAPA再次認證後會寄出正式信函，此時專案狀態轉為『已寄出，等待回應』。

徵填坑：
Graphic design, UI UX, new wireframe
### Mobile Responsive (design and code)

還有許多在Github Issue上
[https://github.com/hsin421/nameisTaiwan/issues](https://github.com/hsin421/nameisTaiwan/issues)
MIT License



## 附錄：給一般使用者的客服信件範本收集區


### 範本一、村長提供的客訴信



[https://gist.github.com/clkao/894b225566168dfb8b3e](https://gist.github.com/clkao/894b225566168dfb8b3e)


### 範本二、et 寄給 gw2 客服的信件

可將==螢光色==部分替換成適合的字

```
Hi,
I'm about to purchase gems and see my billing country is displayed as "Taiwan, Province of China"
It's not true, or not even close.
I'm really unhappy to see this. Taiwan is an independent democratic country with its own government and territory.
Please fix how the country is displayed.
FYI:
http://meta.stackoverflow.com/questions/170143/taiwan-is-not-a-province-of-china

```
#### FYI, gw2 官方回應如下


```
Hi Etblue,

Thanks for contact us regarding this issue.

We understand that the sovereign status of Taiwan is a sensitive political issue and often the answer to the point you raise normally depends on who is being asked the question. The reason for how Taiwan is displayed may have to do with how the sales agreements were set up in your region. However, I thank you for your feedback and for your input and will forward this to the proper parties to review.

Regards,


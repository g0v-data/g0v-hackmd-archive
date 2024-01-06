---
title: "COSCUPer - COSCUP Personal Data Center"
tags: hackpad
---

# COSCUPer - COSCUP Personal Data Center

> [點此觀看原始內容](https://g0v.hackpad.tw/apyH3KIENaa)


### 緣由

開源研討會工作人員動輒上百人，彼此不認識的 conf staff 需要互找，又需要保持隱私。然而，用 trello 或 google docs 分享的資料只能一整份文件全有全無，沒有細緻的權限管理，造成文件必須去除機密/敏感資料後複製出去，但複製出去的又常常 merge 不回來，導致資訊不同步的囧境。因此需要一個超彈性權限的共用聯絡簿，讓所有工作人員在同一個平行宇宙裡做事，但又可以保持自身個資的安全。

### 功能

- 前台頁面看起來基本上像是一個內建 COSCUP 客製化分類的超級聯絡簿
- 不同於以往的 COSCUP 以組認人，2015 的 team 一個人可多組，所以分組不是 class，而是 mixin，要用 tag
- 後端據說要每個欄位都可以單獨設定權限……加油 XD
- 初期先以整合 staff 資料為第一優先目標，行有餘力再處理講者、贊助商、媒體與外包商資料

### 授權

MIT (mockup)
> 我自己的部分是 MIT，其他部分看各自執行的人決定
> [name=ET B]

> 我也先選擇 MIT 囉 :p 
> [name=Li-Han C]


### 協作平台

[github (mockup)](https://github.com/ETBlue/COSCUPer)
> mockup repo 先開在我自己的帳號，之後再看要 transfer 到哪個 github org 去
> [name=ET B]

[google drive](https://drive.google.com/folderview?id=0B0NsS2a-Qx8ZakgzTFVzeWhIcWM&usp=sharing)
[github (backend)](https://github.com/nfsnfs/COSCUP-System)
預定：
- Flask
- MongoDB
> backend repo 我也先開在我自己帳號 :p 我跟 BlueT 和 Bob 應該會在年初時候 con call 開會
> [name=Li-Han C]

> \+\+ 我 mockup 純參考，到時請任意修改或砍掉重練 XD
> [name=ET B]


### 現有成果

- [mockup:](http://etblue.github.io/COSCUPer/public/) [http://etblue.github.io/COSCUPer/public/](http://etblue.github.io/COSCUPer/public/)
- [https://s](https://staff.coscup.org)[t](https://staff.coscup.org)[a](https://staff.coscup.org)[f](https://staff.coscup.org)[f](https://staff.coscup.org)[.c](https://staff.coscup.org)[o](https://staff.coscup.org)[s](https://staff.coscup.org)[c](https://staff.coscup.org)[u](https://staff.coscup.org)[p](https://staff.coscup.org)[.o](https://staff.coscup.org)[r](https://staff.coscup.org)[g](https://staff.coscup.org)

### 工作項目

- [ ] mokcup
    - [ ] 生 json 假資料
    - [ ] 用假資料生 html (javascript? jade tamplate?)
    - [ ] 讓 filter 選單起作用

- [x] 工作人員登錄
    - [x] 填資料 API
    - [x] UI
> 此大項一月底要做完
> [name=Li-Han C]


- [ ] 組長加註
- [ ] 和 Roboconf 整合
- [ ] 追蹤已邀請名單
- [ ] 顯示修改歷史

### 參與者

坑主: COSCUP 2015 team (小畢 CrBoy, nfs, bobchao, shadowcrow, )
UI: ETBlue,
frontend:
backend: nfs, Ly
> 圍觀 owo)//
> [name=Poren C]

> 發嘍  ._./
> [name=Lee]

> 純推～
> [name=Paddy H]


### 利益揭露

合作或相關組織/團體：COSCUP 2015 team
專案成果預計用途：初期將以 COSCUP 2015 為範本開發，也會給 COSCUP 2015 team 使用
已知商業利益/金錢物質報償：無

## 附錄


### 資料區

[https://docs.google.com/forms/d/1naZxGijhd-dyQv0lg\_lnsg0\_70kEAGm95Em8o4VZbFA/viewform](https://docs.google.com/forms/d/1naZxGijhd-dyQv0lg_lnsg0_70kEAGm95Em8o4VZbFA/viewform)
COSCUP 2015 分組 (以上述表單內容為主)


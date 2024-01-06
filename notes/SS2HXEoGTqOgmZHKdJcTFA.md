---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20221123 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：nonumpa, cai
- Workis: bil, mrorz, NHK*3
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :globe_with_meridians: Site
- iOS does not pop-up video now https://github.com/cofacts/rumors-site/releases/tag/release%2F20221119

## 小聚檢討

> 小松果 https://g0v.hackmd.io/@mrorz/HkD98EPUo

- Time control
  - 2:35 ~ 45 評價
  - 3:05 ~ 3:19 補充資訊、準備自我介紹
  - 3:42 自我介紹完畢，介紹回應
  - 4:10 ~ 4:40 練習回應
- 因為有影片，所以可以提醒大家帶耳機 [name=mrorz]
  - 也可以大家一起聽，或是請它 mute [name=bil]
  - 還好
- 來的人很好，可能不好相處的人都去參加政黨活動 (?) [name=bil]
- 大家都有登入 [name=mrorz]
- 桌子排列 [name=mrorz]
  - 一列 3 張桌子 6 人、5 排
  - 聽課模式，但也不會擠
- 長輩接受度 [name=cai]
  - 3 位
  - 都很好而且很認真 [name=bil]
  - 以前參與的長輩，比較不會要求他們查證，可能只是來看看，但這次都有試著查證 [name=bil]

## Updates to CCPRIP

https://g0v.hackmd.io/@mrorz/cofacts-rd/https%3A%2F%2Fg0v.hackmd.io%2FBRsJOevWSbyUMBSZEVVWrA
- 重新分組
  - 技術方面採用 google cloud run 會簡化很多，故合併 infra 與 application
    - risk: 不確定 performance 如何，cloud run ram 與 CPU 都小小
  - 加入 operation(governance; 拒絕垃圾) 與 community (build capacity with offline activities and the aid of technology)
- Image / video retrieval
  - https://g0v.hackmd.io/aJqHn8f5QGuBDLSMH_EinA?both#Elasticsearch-vectors--documents

## Anti-SEO

New design doc: https://g0v.hackmd.io/@mrorz/cofacts-rd/%2FXBJS-KEtScWyVCuQ9P_iNQ

## 重複圖片回報

假冒貨運公司故事 (整理：cai++)
- 源頭與澄清：https://www.facebook.com/permalink.php?story_fbid=pfbid0A8cXHrQHwSXSVcoRkHtsfLgyoR1G913qFJw7ZmssXapTPfKt6fV1yKZFpPTbhzAkl&id=100070029936340
- https://cofacts.tw/article/cfqEn4QBC7Q3lHuUmVQH
- https://cofacts.tw/article/LfpXn4QBC7Q3lHuUm1RL
- https://cofacts.tw/article/Afoun4QBC7Q3lHuUK1TF
- https://cofacts.tw/article/1vr5noQBC7Q3lHuUv1Mm
- https://cofacts.tw/article/s_rgnoQBC7Q3lHuUlFM_
- https://cofacts.tw/article/HfrimoQBC7Q3lHuUgVDb
- https://cofacts.tw/article/NvpwnoQBC7Q3lHuUw1Mt
- https://cofacts.tw/article/E_pJnoQBC7Q3lHuUE1PB
- https://cofacts.tw/article/M_qXnYQBC7Q3lHuUNFJw
- https://cofacts.tw/article/QfqYmYQBC7Q3lHuUN054
- https://cofacts.tw/article/w_oImoQBC7Q3lHuU1U5U
- https://cofacts.tw/article/2fpQnYQBC7Q3lHuUI1FU
- https://cofacts.tw/article/jfognYQBC7Q3lHuUP1FN
- https://cofacts.tw/article/ZPpsmoQBC7Q3lHuUo09t
- https://cofacts.tw/article/b_oKnYQBC7Q3lHuUbFG6
- https://cofacts.tw/article/O_rinIQBC7Q3lHuUcFEW
- https://cofacts.tw/article/E_rMnIQBC7Q3lHuU2lE8
- https://cofacts.tw/article/_fq7nIQBC7Q3lHuUP1AP
- https://cofacts.tw/article/8_q1nIQBC7Q3lHuUNFDR
- https://cofacts.tw/article/LfpHmoQBC7Q3lHuUrE82
- https://cofacts.tw/article/rfptnIQBC7Q3lHuUEFDs
- https://cofacts.tw/article/WfpCm4QBC7Q3lHuU9lAq
- https://cofacts.tw/article/P_oJm4QBC7Q3lHuUgFBR
- https://cofacts.tw/article/EPrGmoQBC7Q3lHuUt1Ay
- https://cofacts.tw/article/UfpgmoQBC7Q3lHuUsk88
- https://cofacts.tw/article/e_rMmYQBC7Q3lHuUaE4v
- https://cofacts.tw/article/Zvq3mYQBC7Q3lHuUDk5w
- https://cofacts.tw/article/QfqsmIQBC7Q3lHuUwU1Y

---

素面口罩 (cai++)
- https://cofacts.tw/article/2fqenIQBC7Q3lHuUkVBW 
- https://cofacts.tw/article/_vo9noQBC7Q3lHuUslIv
- https://cofacts.tw/article/cPoKnYQBC7Q3lHuU1VH8
- https://cofacts.tw/article/UPpllIQBC7Q3lHuUTUk9
- https://cofacts.tw/article/u_r2k4QBC7Q3lHuUDkgm
- https://cofacts.tw/article/2_q0koQBC7Q3lHuU6EZK
- https://cofacts.tw/article/mPqdkIQBC7Q3lHuUlEVU
- https://cofacts.tw/article/CvrEnIQBC7Q3lHuU1FFd

---

- 確實是不同圖（crop 不同），但同樣文字
- 若實作 OCR 應可找到相關圖片
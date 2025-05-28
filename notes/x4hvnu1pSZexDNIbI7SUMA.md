---
tags: Disfactory, 
---

# 違章工廠回報系統_第196次小聚

###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：20250528 19:30 (GMT+8)
地點：地球公民基金會
線上：https://meet.google.com/coc-vuaa-ykz
小聚共筆：

新提案：再裁罰的回報相關的小聚共筆
- 違章工廠回報系統第192次小聚 20250305
- 違章工廠回報系統第193次小聚 20250402
- 違章工廠回報系統第194次小聚 20250416
- 違章工廠回報系統第195次小聚 20250430

:::info
文件目錄
[TOC]
:::

## 參與者簽到


線上：





---

# [disfactory新提案](https://www.canva.com/design/DAGg17NISDA/zIM6iFSHSs5SH9HK-VftQw/view?utm_content=DAGg17NISDA&utm_campaign=designshare&utm_medium=link2&utm_source=uniquelinks&utlId=h49962145f6)

![](https://g0v.hackmd.io/_uploads/HJOPApHskl.png)

**Challenge**: 非工廠（倉庫）已被裁罰的，需要有人去確認，讓連續裁罰的機制動起來（上圖右下角），在罰金壓力下才會做出改變恢復農用。

peii:
- 想要讓民眾協助確認被裁罰的農地上倉儲是否已經改善
- 讓未改善的裁罰動起來
- 也許可以用尋找寶藏的方式？
- 
![](https://g0v.hackmd.io/_uploads/Hk-tKi56kx.png)

裁罰紀錄：來自國土署的 single source data
違反非都市土地使用管制案件查處情形表
- 按照地號
- 目前只有流水號，還沒有專屬編號




## 本次會議紀錄



### 工廠分類
簡化分類，讓「可以連續裁罰的工廠」被強調
![](https://g0v.hackmd.io/_uploads/Hkz-A9yggl.png)

大家回饋：
- 再檢舉會給改善時間，不一定會裁罰
- 預設善意：對方可能真的有改善
- 現在的分法會全部都變成紅色ＸＤ

### 使用者回饋
ael: 建議還是跟使用者聊過確定現場回報需求再設計
想請 @peii 從願意被聯絡的人裡面，撈有重複檢舉單一工廠的人 1-3 人。想要知道會連續檢舉的人，是什麼樣貌，通常是怎麼觸發，怎麼使用這個平台。怎樣會想要連續檢舉？怎樣通知他們最好？

SL: 也可以訪問只上傳一次的人


先提出打電話這個issue，細節架構可以再討論

## 上次小聚紀錄
- 


### 考古目前各種回報狀態的資料欄位


最原始後台 admin page 資料欄位設計：
https://github.com/Disfactory/Disfactory/issues/268


factory_status:
https://github.com/Disfactory/Disfactory/issues/527

cet_review_status:


cet next tag:

gov_status:
https://github.com/Disfactory/Disfactory/issues/389

display_status: https://github.com/Disfactory/Disfactory/pull/410


### 白板整理相關裁罰關係

```mermaid
stateDiagram-v2
    state "尚未審查（A)" as A
    state "已審查-不檢舉(O)" as O
    state "已審查-需補件(P)" as P
    state "已審查-待檢舉(Q)" as Q
    state "已審查-已生成公文(X)" as X

    A --> O
    A --> Q
    Q --> X
    A --> P
    P --> A
```

```mermaid
flowchart TD
    subgraph "裁罰（可獨立持續進行）"
        direction LR
        CF[首次裁罰] --> CR[再次裁罰] --> CR
    end

    subgraph "處理階段（線性狀態）"
        direction LR
        A[待處理] -->|需先裁罰| B[停工] --> C[停水停電] --> D[排程拆除] --> E[已拆除]
    end

    CF -.-> B
```


![](https://g0v.hackmd.io/_uploads/r1tQeVTCJx.png)

違章工廠的處理順序

```py
cet_review_status_list = [
    ("A", "尚未審查"),
    ("O", "已審查-不檢舉"),
    ("P", "已審查-需補件"),
    ("Q", "已審查-待檢舉"),
    ("X", "已審查-已生成公文"),
]
```

- 待處理
- 裁罰（可連續裁罰）
- 停工
- 停水停電
- 排程拆除
- 已拆除


小結：連續金錢裁罰（地政或是都發）跟排拆（建管單位）是分開的流程，可以分開記 `status`

但是連續裁罰的時間要怎麼記錄呢？
需要整理到：https://github.com/Disfactory/Disfactory/issues/655

討論：



### 目前用政府公開資料遇到的問題

1. 希望每個案件都有獨立編號
2. 有些資料有缺漏
3. 有跳號
4. 歷次查處情形也怪怪的

連續再裁罰相關的有哪些資料呢？ => 只有一份
https://github.com/Disfactory/Disfactory/issues/656

### 攝影計畫？

等攝影師來聯繫 ~
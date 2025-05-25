---
tags: vTaiwan小松
---
# 20240904 vTaiwan 小黑客松
時間 Time ：19:00-20:30
地點 Location ：線上 Online
參與者 Participants：josh, peter, eli,翊婷, lily, yu-ting, ronny
線上參與連結 / Link：https://meet.jit.si/vTaiwan

歡迎大家提案想做的事情！！！！

### 自我介紹
- Peter: 法律、vTaiwan、審議
- Ronny
- Josh:瑞士、投票選擇、計算社會學
- eli 
- 翊婷:政治學、博士班、實驗
- lily: 
- Yu-ting: 人機互動（目前主軸是研究人和AI的互動與合作）、社會學、前端工程師

## 小小的分享
- 昨天參加 FNF Foundation 舉辦的 [hacking democracy conference](https://www.freiheit.org/taiwan/2024-hacking-democracy-conference-how-make-ai-helpful-participation-and-deliberation) ，聽完分享後，邀請 Ronny 分享 AI 審議工具箱的[提案](https://docs.google.com/presentation/d/1m6BPKa-eb_GH864-2dbtoSks-YlF04Rctm21PBeawLQ/edit?usp=sharing)
### Ronny 的 AI 審議工具箱 project
- 審議工具箱的想法：
    - 產出影音紀錄
    - 利用人工智慧產出逐字稿
    - 人別辨識與分段
    - 逐段摘要
- 希望將功能放在區分發言者這件事
    - 希望利用人人都有手機的優勢來做到。
- 流程：
    - 桌長建立會議，得到 QR code
    - 參與者掃描 QR code 進入會議討論，輸入基本資料。
    - 在會議中，參與者可以舉手，表示我要發言。
    - 利用參與者的手機來做語音辨識，同時也可以做到人別辨識。
    - 參與者可以於現場進行修正
    - 逐字稿生成之後，送到 LLM 來做摘要。
    - 摘要結束後，就能夠生產出逐字稿（類似 sayit）
    - 可以在遇到使用者的時候
- 與史丹佛工具的比較：
    - 鎖定在線上審議，實體使用會很干擾
- 與 Talk to the City 的比較
    - 利用 What's App
- 如何利用手機來實作相關的活動？
    - 同時利用 whisper 與手機收音來比較看看
- 目前的目標：
    - 先生產出一個雛形
    - 可以在11月的活動上發表
    - 目前利用 JQUERY / Vanilla JS 
    - 
### Hacking Democracy Conference 的參與
- 分享昨天參與 hacking democracy conference 收集到的 insight
- [Heptabase筆記](https://app.heptabase.com/w/f93254d2eefdde0a7678e701d873e92cb26734e34f349961de7bcf72104bef44)
- 有收集到新的受訪者
### 數位公共參與工具調查
- 分享數位公共參與工具調查的最新進度
    - 完成審議民主課程
    - 新增[工具盤點表格](https://airtable.com/invite/l?inviteId=invhhPuP781q4OHYH&inviteToken=d3ee8e33d5cfbe2dff5c587bbe325fba19dbbffaccd7bc966ce02df59175f982&utm_medium=email&utm_source=product_team&utm_content=transactional-alerts)
    - 初步整理遇到的問題：
        - 工具本身會應用在審議的不同階段，這一點要區分
        - 工具的數量比想像中更多
        - 有很多的工具目標是用在企業與組織決策上。
- people powered 的表格是否有機會應用在台灣的表格上？
    - 目前目標：9/29 大松前完成所有工具的初步討論
- [All our ideas](all-our-ideas.citizens.is) 之前決定排序的時候有討論到，但是 All our ideas 後來被買走後，有開發一些新的功能。
- 新增欄位：
    - 是否可以立刻使用
    - 是否要付費
    - 使用時需要提供的個人資料
        - 這個考慮點？[name=josh]
            - 收集個人資料本來就會
- 權限要調整
### 小英基金會的分享
- 拜訪小英基金會的分享：
    - 初步成果：有機會可以獲得小英基金會的捐款，來執行議題小聚與數位公共參與工具的專案。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e6db2a6ac49347a7da229742050548c4.jpg)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c8956c5a6404462531c7422d4379a5fb.jpg)


## 議題小聚
- [vtaiwan議題小聚](https://g0v.hackmd.io/GUe0KXMsQBC-6KTIUPBVnA?both)
- 需要討論的部分
- 有機會爭取到小英基金會的贊助，所以要討論看看活動費用的部分。
- TWNIC 合作 [name=翊婷]
    - [vtaiwan 與TWNIC 合作](/g4UGYbeLSt2hfkXhBCLPOg)
    - 與 TWNIC 合作，舉辦網路的意見徵集與討論
        - TWNIC：具有官方性質。
        - 需求：網路政策建議的白皮書，可以透過審議方式來收集意見。
        - 審議結果的影響力會影響民眾參與的意願
    - 挑戰：網路政策上，如何做多元利害關係人的討論
    - 方法：隨機抽樣
        - 我覺得隨機抽樣不是問題，重點是多元利害關係人是否有被邀請。[name=peter]
        - 可能要看政策的特質來決定 [name=peter]
        - 或許可以並行？[name=josh]
            - 可以舉辦分開的兩個場次來試試看？
            - 我也覺得兩者不衝突 [name=yuting]
            - 好奇兩者的差別 [name=ronny]
            - 流程要一樣 [name=yuting]
    - 議題與形式可能會再來討論。
        - 社群這邊能夠一起參與題目決定嗎？[name=peter]
            - TWNIC 希望透過民主審議來做網路政策
:::info
大家好！我是之前有在一次線上小聚（Peter: 其實還有一場實體小聚）見過各位的翊婷，現在正在就讀政治學博士，我的博士論文會聚焦在「使用數位工具的政策審議過程」如何改變參與者對民主審議的想像，並且主要會採政治學實驗的方式（即透過建立控制組和對照組來探索變數之間的因果關係）。

目前預計明年一月開始跑實驗，也正在洽談與TWNIC合作針對台灣網路相關法規進行類似vTaiwan的民主審議過程，實驗研究的結果也規劃會登在TWNIC年底的網路政策建議白皮書中（刊登形式待定）。目前也規劃會由問卷平台進行隨機抽樣及邀請參與者，希望能達到能反映台灣整體人口組成的樣本（這部分我會與指導教授再行討論，審議民主的文獻中一個很常被辯論的議題就是到底應該以mini-public的形式、或是只找stakeholders來deliberate？我想這點在網路政策上兩者有一點重疊，因為只要是網路使用者都算是stakeholder，基數也很大，達到能反映台灣整體人口組成的抽樣也可能可行）。

主要希望可以跟大家討論，若TWNIC在明年上半年舉辦3-5場審議（議題會跟他們討論再行決定）。能不能邀請熟悉vTaiwan的社群參與者來操作過程呢？如果有可能是正式的合作那就太好了！但這部分是很有彈性的～

:::

## 數位公共參與工具
- [數位公共參與工具比較協作共筆](/@Pno233SAS8G5UfL5OvSRmA/SkXZk8UdR/%2FqJ460ImBQHi8vjNBQclhzA)
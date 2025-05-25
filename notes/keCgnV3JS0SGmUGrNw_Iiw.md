---
tags: vTaiwan小松
---
# 20250416 vTaiwan 小黑客松
時間 Time ：19:00-20:00
地點 Location ：線上 Online
參與者 Participants: Tim, Tofus, Peter, Allison, Josh, yuting, Allen, 承哲
線上參與連結 / Link：https://meet.jit.si/vtaiwan

![](https://g0v.hackmd.io/_uploads/rkmvneRAye.png)


## 自我介紹與新手導覽
- [新手簡報](https://docs.google.com/presentation/d/1ELAVIpaPVCmAx7nq-7e8-SVrckZ4ohRwn3V-TSpe78U/edit?usp=sharing)
### 自我介紹

## 小小的分享
- 利用 AI 修飾意見 [name=josh]
- 網站更新 [name=peter]
    - [網站成果](https://vtaiwan.zeabur.app)
    - 討論網站管理

## Argdown 

## 5/23 議題小聚
- [facebook貼文](https://www.facebook.com/vtaiwan.tw/posts/pfbid0Xua6ajGWgURbS3XGqU5vubpXwonnorrR3vCqsRiv2AAtu8DFYocb74q7wSkYFkTUl)
- [報名表單](https://forms.gle/MLrDbFghTJuvLD4m7)
- [polis 連結](https://polis.tw/87nnxrrj5d)
### 利用 AI 修飾意見
- 緣起：希望透過 AI 處理的程序，避免特定意見中因為每個人表達方式不同，或者是定義不同，讓討論失焦。
- 理想中是所有的意見，在被加進Polis之前，都跑過一樣的程序做處理，讓參與者新增的意見也都有對齊達到同一個標準，比較不會有什麼因為有情緒或是邏輯不通或是有錯字而影響大家投票，所以建議從一開始種子意見也都跑過一次一樣的程序整理過，達成一定的公平性。
- 目前 Josh 使用 Claude
- prompt寫：
:::info
將以下意見轉換為有效的Polis意見，該意見應：
- 使用清晰、簡單、易讀的語言以及邏輯（少於200字）
- 清楚定義任何複雜的概念以及主動被動的角色關係
- 僅包含一個可同意/不同意的概念
- 如果一則意見有兩個以上的概念，拆成不同Polis意見
- 去除情緒化或指責性語言
- 避免絕對詞（「總是」、「從不」、「每個人」）
- 著重於解決方案而非僅描述問題
- 保持中立表達，不假設共同價值觀 
格式： 原始意見： [意見] Polis意見： [轉換後的意見]  
”
然後新增了一列整理過的意見在種子意見google sheet上面，大家可以看看。其實還滿有趣的，舉幾個例子，雖然原本的種子意見已經寫得很好了，還是有一些被整理的痕跡：

例子1：

原始意見： 社交平台不應該以反詐之名強制實名制，因為這可能危及個人隱私與匿名權利。
LLM整理過的意見： 保護用戶隱私和匿名表達權利比實施實名制防詐騙更為重要。
// 讀起來邏輯上更簡單直接，但也確實抓出了那個價值取捨的點。

例子2:

原始意見： 詐騙受害者不應獲得政府賠償基金的補助，除非是弱勢群體。
LLM整理過的意見： 政府的詐騙賠償補助應僅限於經濟或資訊弱勢群體，而非所有受害者。
// 原始意見大家同意不同意的焦點可能會放在前面或是後面，但是整理過之後就比較清楚要同意或不同意什麼。
:::
- 針對其他使用者新增的意見，可以如何處理？[name=peter]
    - 利用 polis 的審核功能，讓管理者可以針對提交的意見進行處理。
- 處理前與處理後的意見都可以保留，來進行回溯性的意見 [name=josh]
- 甚至可以做比較，讓大家針對 AI 修飾過的意見與修飾前的意見提供建議與看法。[name=peter]
- 補充資料：[安全性與中立性的評測](https://github.com/thu-coai/Safety-Prompts/blob/main/README.md)
- 為了聚焦討論，在活動的過程中，可以先詢問大家對命題模糊性的意見，現場直接根據大家意見進行修改。[name=Tim]
    - 活動前的種子意見、與活動後的現場討論結果，都可以用 AI 進行修飾、聚焦論點。
    - 但在活動過程中，可能不適合與 AI 結合，避免干擾活動節奏。
### Action List
- 在 Polis 上加上說明 [name=peter]
- 思考做獨立測試的方法
### 利用 AI 結合議題小聚
- 活動前：利用 AI 來潤飾意見
- 現場：利用現場討論來提供 prompt 的方向
    - 因為人工來修改，不一定有說服力。
- 活動後：針對大家討論的內容，
## 網站
- [vTaiwan 網站改版，啟動！](/Q3_hgovyRHusEq8-3nomPQ)
- 目前有一個預部署的[成果](https://vtaiwan.zeabur.app)
- 小小的問題：後台的 CNS 很容易爛掉，
- 介紹：https://blog.huli.tw/2024/04/14/zeabur-introduction-deploy-service/
- 目前伺服器部署在東京。
### 網站結構


## TFGA 活動提案
- vTaiwan 有跟 [Tech for Good Asia](https://www.techforgood.asia/)合作，拿到一筆款項，預計來做 AI 與民主參與的題目！
- [vtaiwan x Tech for Good Asia 合作](/PdvNjkLlSd-WytXN_otWbQ)

## 4/30 聚會
- 實體聚會＋討論
- 目前預定出席
    - peter
    - tofus
    - josh
    - 承哲
    - 翊婷
    - T
    - joey
    - (allison)
    - (yuting)
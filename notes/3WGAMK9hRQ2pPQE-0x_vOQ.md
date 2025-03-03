---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20250303 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- NPO Hub：bil, mrorz
- 線上出席：T
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API

(On hold)

#### :robot_face: rumors-line-bot
https://github.com/cofacts/rumors-line-bot/releases/tag/release%2F20250302


### :rocket: Staging
Same as last week, let's review experiments first

## LLM-based AI transcript

- Langfuse v3
- Dataset & experiments https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/datasets/cm7ri4we80004ql0bfu6lvtoi
- Hallucination
    - ex: https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/16143cbf-02df-46cd-88e9-dd86b9cb81ab?observation=b0ab72fe-c7f2-4fe1-a53d-6398dbaf7a64 , https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/1dffcadb-2afb-436d-a108-3fe8bdc4d639?observation=988b5ef6-920d-4d79-8bcc-9dbf7ec504a4
    - `finishReason: "MAX_TOKENS"`
- Gemini-2.0-flash vs Gemini-1.5-Pro-002 ![](https://g0v.hackmd.io/_uploads/rJecNLCzj1e.png)
    - 2.0-flash 更容易 hallucinate
    - 2.0-flash is 1.5x slower
    - 2.0-flash 在遇到字幕不合 or 翻譯的時候，較可能會聽打+字幕並陳 
        - 假字幕https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/54b80adb-20a7-46a7-b155-0bc85618e283
        - 翻譯 https://langfuse.cofacts.tw/project/cm3e6a2190001fdga2ruendgd/traces/8987ddbd-2648-4c19-8216-9dfe869c4a7c?observation=5541c147-c185-4c36-9b0b-7427ec5cb11a （好像沒翻完）
    - 還沒遇到 Gemini sensorship 的問題 or [recitation error](https://g0v.hackmd.io/wkx286lmTDaFUpgRhnUawQ?view#Gemini-Flash-15-Vertex-AI)
- TODO
  - add more test cases 重跑實驗

## RightsCon & Satelite Events 檢討

- [x] 寄信：RSF、ASL19
- [ ] 等來信：Google、採訪者
  - 有一組不太講英文的日本
- [ ] 波蘭智庫 NASK
- 藝術家很棒
  - g0v 社群藝術家可能比較容易 burn out
  - 有人因為攤位而來要名片
- 愛因斯坦貼紙很夯
  - 爾康國外看不懂

## Communications

- 生命力新聞
- Sitcon
    - 3/8 8:30~17:00 中研院擺攤
    - ![](https://g0v.hackmd.io/_uploads/HJUo-aGskl.png)
    - ![](https://g0v.hackmd.io/_uploads/B1slMTfjkg.png)
    - ![](https://g0v.hackmd.io/_uploads/SJcZMazoyl.png)

Sitcon 材料

https://drive.google.com/drive/folders/1U-etbZSOiFzpXgOr0GtBxkwYKk666nni

- [ ] CCC 的 Cofacts 遊戲
- [x] 文宣更新與印刷
  - [x] 中文（achoo）
    - 250 張起跳 http://www.soho8d.com.tw/Form2/F102.aspx?csubid=73
    - 要更新 QR code
    - 背面有疊影 --> fix 四色黑問題
  - [ ] 「利用語言模型協助查證」傳單
  - [ ] 「查核志工募集」傳單
  - [ ] 豆腐版
    - 再排 / figma
  - [ ] 新北青年簡章 QR code 文宣
- [ ] 宣傳用：Logo 貼紙（透明）
  - 川普貼紙
- [ ] iPad

## 大松
- [ ] 台南好想
- [ ] 要脫鞋，建議帶拖鞋




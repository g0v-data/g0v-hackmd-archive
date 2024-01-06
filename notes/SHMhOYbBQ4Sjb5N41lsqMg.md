---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20230503 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：bil, mrorz
- 線上出席：nonumpa, cai, 4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :robot_face: rumors-line-bot
- https://github.com/cofacts/rumors-line-bot/pull/350

##### Testing checklist

https://lin.ee/1QUzEX4nI

- [x] 輸入問候，應會得到 Dialogflow 問候回應

##### ⛔️ Release Blockers
##### 未竟項目

### :eye: Under review

- https://github.com/cofacts/rumors-line-bot/pull/350
- https://github.com/cofacts/rumors-deploy/pull/23

## CCPRIP

### [Comm] Crowd-source transcript
> https://g0v.hackmd.io/@cofacts/rd/%2FOhGIQzoxR5eF6audQuS_FQ
> [name=nonumpa]
> 

https://github.com/cofacts/hocuspocus-server
Repository 名字有要改嗎

#### Build 問題
> Ref: https://github.com/ueberdosis/hocuspocus
src/index.ts 是 app
hocuspocus-extension-elasticsearch/src 是 package

目前的想法是讓 hocuspocus-extension-elasticsearch 可以輸出成 package

production/deploy 應該就跟 rumors-api 一樣 dockerize
- server host / port --> env var
- Elasticsearch index / type 應該要可以指定

### [Comm] LLM-aid fact checking

看完了 ChatGPT prompt engineering 教學 https://learn.deeplearning.ai/chatgpt-prompt-eng 來試試看

> https://g0v.hackmd.io/@cofacts/rd/%2FmU8qi721RZeAQ9PDfj7XRA

新增 scenario #3, scenario #4

#### Scenario #3 - categorization

> https://docs.google.com/spreadsheets/d/e/2PACX-1vQSOFMGdiiHSXzh7j3ZpKnMRtSNDhKip1xrtxxW3wiF2CbISz3tipNw6Uw2uKTsH5oL4Rv8qtVSqQNq/pubhtml#

- Spend 2k tokens to specify categories (2k for article left)

#### Scenario #4 - Document QA

> https://docs.google.com/spreadsheets/d/e/2PACX-1vQSOFMGdiiHSXzh7j3ZpKnMRtSNDhKip1xrtxxW3wiF2CbISz3tipNw6Uw2uKTsH5oL4Rv8qtVSqQNq/pubhtml#

- Create reply from existing article in DB
    - Similarity can be lower than chatbot (otherwise the user can choose from chatbot directly)
- Hopefully can extend 詐騙 case from existing ones
- Still seeking good cases


## 小聚籌備

### 台南新芽

- [x] 地點：
  - 2023/5/27 2pm - 5pm
  - 台南新芽 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_467d6f751c9c90edbde9615261ce0983.png)
三張大桌子，坐15人以內舒適，有延長線跟飲水機和廁所，開門即會場。當天會有新芽工作人員陪伴
- [ ] 食物？統編？
- [x] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Slido 暖身
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [x] 投放目標：台南、高雄、嘉義 57,000 人
- [x] KKTIX:https://cofacts.kktix.cc/events/cofactseditor37
- [x] 誰會來呢：bil, mrorz, nonumpa
    - 需使用實體車票
- [x] LINE 文案: 
「台南市被列入全台10大疫情危險縣市？」假的！！中央流行疫情指揮中心並沒有列出10大疫情危險縣市。
活動不該只辦在台北，Cofacts 真的假的要到台南舉辦志工培訓活動啦！！5月27日(六)14:00-17:00 歡迎沒有經驗的你，用一個下午的時間當鍵盤志工，一起對抗假新聞！請自備水杯、筆記型電腦與充電線唷！
台南新芽地址：台南市中西區成功路29號4樓(賀聲助聽器樓上，一樓有電梯）

### 台南新營區

- 等 Rosalind
- 可能是講座
- 可能是[曬書店](https://www.facebook.com/2booksite/?locale=zh_TW)

### 高雄場地

場勘結果(可能辦在九月或十一月)
- [駁二共創基地](https://www.pier2base.tw/)
  - 要電話預約才能看場地
  - 沒有延長線
  - 不能吃東西
  - 前台報到桌帶到教室
  - 三四樓，只是教室2開頭
  - 桌子可以移動，但桌子桌腳分開
  - 學員沒有插座，只有講者有
  - 缺點：內有其他商務公司，門禁嚴謹，不太容易進入，需要搭電梯上樓在前台報到。
- [Pinway](https://pinway.kcg.gov.tw/)
  - by 青年局
  - 房間：青創講堂
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_25322afa4ffc8cad9bc0b265929d63fe.JPG)
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_864d7bb51d72065093afaca37fcad487.JPG)
  - 配備
    - 10張桌子可移動
  - 費用
    - 1800/hr（預估場地費用9200） --4hr+cleaness
    - 清潔費 2000
    - 場佈需要 1hr 排桌子
    - 以報價單為主，回簽後附頭期款 50% 才算是有訂到
  - 可以吃東西不要弄髒即可
  - 沒有延長線要自己帶
  - 10 插座

## 文宣準備

- 活動出席：哥斯大黎加、韓國
- Acho A4 文宣雙面
- ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_765283f647ae0c5e9f5ca99c940965b8.png)
  - 平常影印紙大概 80p [name=cai]

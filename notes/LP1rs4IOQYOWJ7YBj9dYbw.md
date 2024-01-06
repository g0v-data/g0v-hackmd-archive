---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20210825 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, nonumpa, mrorz, 4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :globe_with_meridians: Site

- https://github.com/cofacts/rumors-site/pull/445

##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [x] Article detail
    - [x] 找一個「含有正確/不實資訊」的訊息，看出處標題是否為「資料佐證」
        - [x] 使用「分享」按鈕複製文字貼上到他處，出處標題亦為「資料佐證」
    - [x] 找一個「含有個人意見」的訊息，看出處標題是否為「不同意見出處」
        - [x] 使用「分享」按鈕複製文字貼上到他處，出處標題亦為「不同意見出處」
    - [x] 框選回應文字複製後貼上到他處，文字均有翻譯

登入自有帳號後檢測：
- [x] Article detail
  - [x] 撰寫回應時，選擇「含有正確訊息」，出處輸入框標題應為「資料佐證」
  - [x] 撰寫回應時，選擇「含有個人意見」，出處輸入框標題應為「不同意見出處」

##### ⛔️ Release Blockers

無

##### 未竟項目

無

### :eye: Under review

- https://github.com/cofacts/rumors-line-bot/pull/280

## 商標狀態

2021-08-18 0:00:00 已送出至[智財局](https://twtmsearch.tipo.gov.tw/OS0/OS0201.jsp?l6=zh_TW&isReadBulletinen_US=&isReadBulletinzh_TW=true)，現已可查詢
- 「Cofacts 真的假的」申請號：110059474、110059475
- 「標章圖」申請號：110059476、110059477

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cf5f14863c3fbe8cfba0d19a769a3e11.png)

## 大松檢討

- 線上的缺點就是滿容易沒有人，其他坑主也反應凝聚力變辛苦 [name=bil]
    - 實體松比較適合一定要跟人講到話，線上的就會比較容易沒有人
    - Gather 很類似 clubhouse，在門口聽一下就出去
    - 坑主變成要持續的吸引人、有聲音
    - 不是很好一起工作，除非本來就有決定想做一些事情的人
    - 有寫 python, go 與純 JS 的參與者
        - JS --> good first issue [name=mrorz]
        - python, go --> sorry, 請闢謠 [name=mrorz]
- 時間已經縮短、人也沒有那麼多 [name=bil]
    - 印象中最多 60 幾人而已 [name=mrorz]
    - 參與相當有限
    - 可以舊人帶新人 [name=bil]

9/25 小聚可否實體
- NPO hub: not yet open
- 疫情底下不好意思去問場地，除非對方主動邀請 [name=bil]
    - 除非直接租小樹屋
- 因為無法排除操作上的困難，所以遇到挫折就會關掉
- 可能還是無法實體

## Article LIFF

Target: receive input (feedback, reply requests) from outside of Cofacts chatbot

https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/?node-id=3004%3A224
1. [x] 實作 common component storybook
2. [x] 實作 feedback form + 使用在目前的按鈕上
3. [x] 實作 article page 的 article 部分
4. [ ] 實作 article page 的 reply - ongoing
5. [ ] 實作 article page 的 reply request form + 使用在目前的按鈕上
6. [ ] 實作 article page 的 reply request list
7. [ ] 實作 article page 的 related article

本週開發：article reply data loading 與外觀（不含 feedback 互動）

## 採訪共筆

https://docs.google.com/document/d/1J8EVhWkJxHkRkRuoatfQRTQF_ZAPkCkf/edit

## 真的假的 <> 防詐達人

- Cofacts 協作平台 --> 「真的假的」協作平台
    - 中文語境下希望用這個字比較友善 [name=bil]
    - 前一步驟的卡片也是使用「真的假的聊天機器人」 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_28870ca07aea7d92438099b399019b89.png =x200)
    - 不過好像沒講前一步的按鈕是什麼 [name=mrorz]
- 若需全名，再用小字加註「Cofacts 真的假的 - 訊息回報機器人與查證協作社群」
- 多一步 redirect
    - 這樣我會想按「放棄前往」 [name=bil]
    - 理論上在前一步卡片按下「看詳細」的人，都有滿明確的看詳細的動機，來到這一步的時候，又看到一次「真的假的」確定要去的地方，就會按下「前往」了 [name=mrorz]

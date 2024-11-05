---
tags: 拉人更輕鬆
title: 基礎建設更新進度回顧與未來目標
---

# 拉人更輕鬆 -- 基礎建設進度回顧與未來目標

經過社群成員與台大堉璘計畫「拉人更輕鬆」組員在[第貳拾肆次基礎建設松](https://g0v-jothon.kktix.cc/events/infrath24n)當日和後續的討論、協作，[更新計畫](https://hackmd.io/t97cH7tFQPyUCgwmfCsFiw)中多數的官網小規模修正目標已經完成，非常感謝社群夥伴們的貢獻！

而「拉人更輕鬆」專案日前通過台大堉璘計畫的審核，將獲得一筆經費，我們想以有償方式徵求社群中有意願和相關經驗的成員協助近一步完成 [C. 官網目前需求](https://g0v.hackmd.io/mZ-LeFr1QJ6CuO6R3eeHnw?view#g0v-%E9%A6%96%E9%A0%81%E7%A4%BE%E7%BE%A4%E6%B2%BB%E7%90%86%E6%A9%9F%E5%88%B6)段落中的目標。

也想邀請有興趣的社群成員一起參與其餘專案目標！

## 檢核點

基礎建設完善檢核點一
- [x] 完成社群專案導覽頁嵌入新手指南
- [x] 完成心得分享頁面
- [x] 更新最新消息頁面

基礎建設完善檢核點二
- [ ] 新增 slack bot
- [ ] 調整官網資訊層級與介面


## A. 召集 g0v 首頁治理成員
在今年四月的基礎松，「拉人更輕鬆」專案小組和社群成員討論並完成了 [g0v 首頁社群治理機制](https://g0v.hackmd.io/mZ-LeFr1QJ6CuO6R3eeHnw?view#g0v-%E9%A6%96%E9%A0%81%E7%A4%BE%E7%BE%A4%E6%B2%BB%E7%90%86%E6%A9%9F%E5%88%B6)；我們預計將在後續以粉專貼文和 slack 訊息等方式發表這篇治理機制，並召集願意參與首頁治理、擔任 Reviewer 的社群成員。

## B. 撰寫新版 Slack Welcome Message
目前預期由「拉人更輕鬆」專案小組擬出草稿，發表於社群中相關頻道，再由具相關權限者協助更新。現況與相關討論參見[此筆記](https://g0v.hackmd.io/@jothon/S1pZe539_)。

## C. 官網目前需求
### 1. g0v 官網新增與修改
#### 1-1 心得分享頁：
本小組成員對心得分享頁的介面提議：做成 notion gallery view 的模式，可以一覽近期更新、參與者關鍵字、心得關鍵字、專案關鍵字等段落
為了徵集更多參與者的心得，我們也希望可以做出方便社群成員投稿的**心得分享頁**
> ronny 建議可以用 g0v hackmd 搭配特定 tag
> 開放場域，由眾人共同監督

https://github.com/g0v/landing-page/tree/community_insights
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4cf5c3c118fe8f4833cd1e2dc64ce720.png)


- [ ] 建立 hackmd 心得模板 -> 要看揪松帳號能不能建立
    - 目前模板：[這是一篇社群心得測試 - HackMD](https://g0v.hackmd.io/JVeeNYF3TN6_Jz9XXscbVA)
    - 目前用的 tags: `insights for g0v.tw`
    - 目前遇到問題：無法自動抓到編輯者
- [ ] 發文教學（要雙語版）：[如何寫一篇心得分享文 - HackMD](https://g0v.hackmd.io/YUhZ_ApjRX6-AtqC6M1qvw)
- [ ] 用 slack 當資料來源可行嗎？
    - 優點：利用 slack 的資料，可以抓到照片、名字等資訊，會比抓 hackmd 資料簡單
    - 缺點：發文門檻比較低，有被大量發文、洗版的疑慮。

#### 1-2 g0v.news 與「最新消息」更新
g0v.news 目前已久未更新（目前已移除連結），希望能將「最新消息」區塊直接連結facebook 最新貼文的標題、kktix 黑客松報名標題等，並使其可以自動更新
> 目前以接 google calender 跟 社群九分鐘的 api 為主
> 可能要調整說明內容

> g0v.news 後來轉型為 [OCF Lab](https://lab.ocf.tw/2022/04/20/closestatement/) 且該專案已經結束。建議跟揪松討論如何呈現最新消息～ [name=RS]

#### 1-3 g0v 官網資訊層級與介面優化
目前主頁上目錄與新手指南的位置較不顯眼，希望可以調整目前過於複雜的 g0v 官網資訊層級與介面
> 翻譯問題（目前只有導覽、dashboard、首頁有翻）、有前置作業（新增目前文字 yaml 檔
> 一場基礎松拿來處理翻譯
> 首頁 如何參與 > 新手指南，比對內容整合

#### 1-4 增加目前專案的能見度
將 g0v 社群所有專案的導覽頁面嵌入新手指南頁面（與 g0v 現有 ARAY 專案合作），使新手一眼看到近期推動專案簡介與專長需求，即可提升立即進一步了解、參與專案的意願。
> [ARAY進度](https://hackmd.io/@8s4CF8IIRk2zYKTOm0VyxQ/BkC2aS05R)

### 2. 建置 g0v slack bot 
我們建議可以建立 slack bot 以步驟說明引導新手循序漸進，認識各專案頻道以及與協助社群夥伴更好的利用此軟體協作。（例如：也加上關於 shoutout bot 的使用說明與推薦）

## D. 其他
- 徵集心得分享
目前心得文章篇數較少、大部分心得的撰寫日期也較早，我們期望可以在大松等社群活動中蒐集新的心得。

- 更多基礎建設專案推坑
本專案期望能持續關注相關專案，如 [Aray](https://aray.g0v.tw/)，也歡迎社群中有興趣的成員提出意見或加入本專案！

- 把社群治理、頻道 list 餵給 GPT，這樣有問題比較容易找到答案

## E. 下次活動
- g0v 第貳拾伍次基礎建設松
- 時間：2024年10月6日星期天（下週！）下午14:00-17:00
- 地點：NPO HUB
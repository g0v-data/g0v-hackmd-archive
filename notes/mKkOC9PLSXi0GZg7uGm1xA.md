---
tags: digital-resilience, resilience, internet-shutdown, digiresi, civil-defense, 民防, 數位韌性松, DigiResiTh0n, hackathon
image: https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9aa673c0b93c735b650f81208b0d2bdb.png

---

# 20231230 DigiResiTh1n 第壹次數位韌性松
:::info
[↩️ 回到籌備文件](https://g0v.hackmd.io/@paulpengtw/DigiResiTh0n-home)
:::

:::success
# 報名流程及注意事項
1. 當您參與本活動，即代表您已經同意 [g0v 宣言](https://g0v.tw/intl/zh-TW/manifesto/zh-TW/) 並願意遵守 [行為守則 Code of Conduct](https://g0v.hackmd.io/s/COC)。
2. <font color=#D60202>_**NPO hub 因為連假已經把垃圾桶收起來了，請大家自行帶走垃圾喔 XD（hub 樓下右轉人行道上有公共垃圾桶）**_</font>
    - 謝謝 Ying 提醒 XDDDDDD
4. **若欲報名活動，請直接在 [g0v 後勤中心臉書社團貼文](https://fb.com/groups/g0v.general/posts/6804552242954457/)留言區 +1 即可。**
    - 若不願使用臉書或不想在公開留言區留下紀錄，請直接透過臉書或 g0v slack @paulpengtw 私訊報名，謝謝！
    - 這次是想 hack 看看臉書演算法，想實驗透過增加互動來把演算法推送的機率升高
:::

:::warning
- 加入 [Slack 線上討論區](https://g0v.hackmd.io/fKrjZ3BlRfWmQ471wcSdBg) (辦帳號超快超簡單）
    - 安裝好後再點[ #civic-defense 頻道](https://app.slack.com/client/T02G2SXKM/C056EHM42B1)
- 線上遠端與會連結 [請點此](https://meet.jit.si/g0v-digiresi)
- [大合照！](https://drive.google.com/drive/folders/1LOczvWW8cSQaKtZJl7TNXhj2vZTA09J7)
:::

## 時間地點

- Dec. 30 2023 Sat. 
- 1300 - 1700（UTC+8）
- [NPO HUB Taipei 台北NPO聚落](https://maps.app.goo.gl/XPrvzSdqgszbfRBV8) 4F 廚房
    - [「如何入場」及場地使用規定](/9pwDPOXLTr6IJKiLofl3qg)

## 活動流程

| 時間 | 活動名稱 | 備註 |
| -------- | -------- | -------- |
| 1230 - 1300 | 活動入場 | 歡迎帶午餐或點心來享用 |
| 1300 - 1315 | 介紹 | 介紹完記得拍大合照XD |
| 1315 - 1345 | 提案 | |
| 1345 - 1630 | Hacking | a.k.a. 開始做專案 |
| 1630 - 1700 | 成果發表 | |

## To 不確定自己幫的上什麼忙但很關心這個議題的朋友
- 歡迎[參考這篇文章](https://chengpeng.substack.com/p/ig)
- 若有任何問題、建議或操作上的疑問歡迎到 [g0v Slack 討論區](/fKrjZ3BlRfWmQ471wcSdBg) 的 [#civil-defense 頻道](https://app.slack.com/client/T02G2SXKM/C056EHM42B1)，或是寄信給 [籌備夥伴 Ronnywang](mailto:ronnywang@gmail.com)，也可以私訊 [籌備夥伴 Paul 臉書](https://fb.com/paulpengtw) 詢問

## 提案區
歡迎自由編輯～
也可以先[看上次的提案](https://g0v.hackmd.io/oyNRfe4lTuaZ5RbcPSS7TQ)，看看哪些地方可以繼續做～


## 本日成果
- ggwave：可透過聲音傳遞資料
    - 網頁版 https://waver.ggerganov.com/
    - 有分三種資料傳輸速率：Normal 11B/s, Fast 16B/s, Fatest 33B/s
    - 聲音的頻段有
        - [U] utrasound：15kHz - 19.5kHz 
            人類聽覺在 20Hz-20kHz，一般難以聽到這頻段的聲音 
        - [DT] dual tone：1125Hz - 2625Hz
        - [MT] mono tone：1125Hz - 1825Hz
    - U 模式可以用人耳聽不到的高頻
        - > 一定年紀底下的人聽得到QQ 超尖銳 [name=paul]
        - 可能會干擾寵物聽覺
    - 目前只允許傳 140bytes 並且只能傳英數字，不能傳中文
    - 應用情境
        - 可以透過 FM/AM 廣播聲音後，直接用手機接收聲音轉換成資料，不需要額外建置任何新硬體和走不同的傳輸管道
        - 可以把內容大量傳到目標端，因為人類無法記憶太多當下的語音內容
        - 一些情境發想：
            - 解完一包是最新的
- chewei: 從中正紀念堂站走到 npohub 拍照路過的防空避難所
    - 「防空避難處所、防災避難據點」共筆：https://g0v.hackmd.io/JzB6MXZRThm6hIgS0OHEdQ
    - 防空避難所
        - 中正紀念堂至 NPOHub 沿線外觀拍照：https://photos.app.goo.gl/BYcLneADj73YArEv7
            - 20231230 週六下午路過 9 個點，現況統計：
                - 1 個南門市場週六下午有開
                - 3 個店面週六下午有開
                - 2 個店面週六下午沒開
                - 1 個有管理員且管理員知道此處為防空避難處
                - 2 個住宅大樓，不確定一樓大門是否常態打開
                - 整體來說，地下室入口明顯程度：3 個在門口看得到樓梯，其他的從外觀看不曉得地下室樓梯在哪
        - 防空避難所資料地圖，參考 kiang 製作的地圖：https://g0v.hackmd.io/Bo2u7eEcQg6pOuEoOPCADQ
    - 防災避難所
        - 各縣市公布 PDF 避難地圖
            - 議題：
                - 需要數位化地理資料！
                    - 目前有嗎？
            - 中正區各里 PDF
                - 總查詢頁面 https://zzdo.gov.taipei/cp.aspx?n=0DE5F70690B4A156
                - 中正區南福里、中正區龍福里、中正區龍光里 https://www-ws.gov.taipei/Download.ashx?u=LzAwMS9VcGxvYWQvMzE4L3JlbGZpbGUvMTI4NjYvMjkzMS80NWIyZTI0Mi01YzVjLTQ4NGItYTExOC1jMDlmNDgwOWNjOGUucGRm&n=MDE45Lit5q2j5Y2A6b6N5YWJ6YeMX%2bS4reaWhy5wZGY%3d&icon=..pdf
    - 整合討論
        - 許多村里沒有「防災避難所」，仍然會有「防空避難所」
            - 但地震、水災(應建議垂直避難)，不一定適用地下樓層式避難(防空避難)
            - 以「南門市場大樓」為例，並非防災避難所，而是防空避難所，且建築物年份新，樓層高，有公共設施樓層，適合評估作為「備用防災避難所」，中正區的南門市場，屬於防空避難，其實建築才剛落成，也屬於公有建築物，很適合水災情境的垂直避難處所，或是地震情境時，此建築物理當相對安全，或是考量南門市場臨著羅斯福路非常空曠的道路空間，適合地震後餘震期間的戶外避難，因為餘震期間街區建物狀況不一，無法確保建物室內是否安全，以及地震後建物火災機率提高
            - 評估方向：
                - 從「防空避難所」清單中，挑選出適合作為「防災避難所」的地點
                - 戶外空間檢視輔助 http://hanshack.com/figuregrounder/
- Reily: 防空避難地圖圖資
    - https://g0v.github.io/adr.npa.gov.tw/
        - 防空避難所的定點資料 更新 >> [done] (但還有一些資料是空缺的)
    - 還可以再增加的部分:
        - 抓個人的定位資訊，顯示最近的防災位址
        - 防空資料定時更新 (CSV更新)
    - 之後想要做的功能：
        - 及時收容人數
            如果收容所被炸毀，可以即時更新 (ㄎ)
        - 實際周邊狀況
            可以實際更新
        - 可以用 Ranking 的方向，針對每個防空或避難所的品質和提供的服務進行評分
            - 「Gather 聚集」似乎會成為主要的特性，交流物資、資訊等
            - 縣市政府投入人力也會需要聚集在特定位置，不太可能均勻配置
            - 有特殊技能的人可以事先標註自己會出現在哪個避難所
                - 避免不同技能者集中存在同一個避難所
                - 分配有防災知識技能的防災士、黑熊學院訓練員
                    - [防災士](https://eoc.gov.taipei/News_Content.aspx?n=4BAE0D2E2DC8254B&sms=02478FA99D47D451&s=A04762FFE8B4A891)
- Paul：Meshtastic 測試
    - [Meshtastic](https://g0v.hackmd.io/0bR8-LvHRMaNaR97YaXpnQ)
        - 測試經驗
            - 第壹次數位韌性松用三台裝置測試開多個新頻道
                - LoRa 裝置三台硬體 spec
                    - Adafruit Feather nRF52840 Express 
                    - Lora SX1262	
                    - NEO 6M GPS	
                    - SSD1306 OLED	
                    - 僅 PCB 不同
                    - Firmware 2.1.11
                - Meshtastic App devices
                    - 2 androids, 1 iOS
                - iOS 開新 Channel 有機會 fail 接收訊息和傳送訊息
        - 找洞
            - 如果無法順利把訊息傳出去或接收
                - 重開 LoRa 裝置
                - 關掉手機 App 重開
                - 關掉手機藍芽重開
                - 若以上都不行，請直接重新用 QR CODE 傳送所有頻道訊息重設
            - app中的頻道數量似乎只能單一決定，要新增頻道或更改頻道只能全部重設
            - 除了2人私頻外，3人以上的通訊似乎只能在公開頻道
- Paul：數位韌性情境分級 (wip)
    - [數位韌性情境分級 (wip)](/SYTBWVohTyuCgPGUqfAl9g)
        - a simple alphanumeric system that starts with a letter representing the category
        - 代號方案 
            - C for Congestion 塞車, D for Disruption 中斷, B for Barrier 障礙, S for Special Situations 特殊情況
- 或許可以參考的資料
    - [318 時期的在會場中建立可靠的訊息傳遞網路共筆](/mEeZehwDQGm74C5cWkogbQ)
    - [318 線路松](https://g0v.hackpad.tw/ep/pad/static/4AKHvZRwM59?fbclid=IwAR1OUBSa-e4HmvYuaRdBr8RvMW3_ajI4tnNptgv0JPrym8f-gQFzlTpOJjE)



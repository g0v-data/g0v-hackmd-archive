---
tags: g0vernance
---

# g0v 行事曆治理.txt

源自[這串 Slack 討論](https://g0v-tw.slack.com/archives/CHPAZECAV/p1677073235709679)：

> [name=chewei]
> 討論：
四個 Google Group 的各自成員 email 名單，有些是公開，有些應該不是公開的？(待確認)
如果發生「咦活動被刪除或更改了！」
Ronny 有設定「一旦有人更動日曆內容，系統就寄 email 給 Ronny」
若收到了日曆變動的通知，要通知誰呢？寄信給四個 Google Group 嗎

> [name=ddio]
> 腦洞發想，是否該來串個 github -> google calendar ，把所有事件都轉成 yml ，之後要新增或修改，就送個 PR 。
> 這樣的好處是：
> 1. 所有編修都有紀錄、可版本控制
> 2. 所有人都可以提交編修，管理員只需要負責審核就好
> 但要看一下怎麼做就是...我....好像....週六...會去...基礎松...

> [name=chewei]
> 哦哦!!
這樣的話，GitHub 作為本體，似乎其他社群也可以打包匯入該社群日曆中？
近期 da0 社群日曆，有討論到融入 g0v 社群日曆活動，討論串如下
https://g0v-tw.slack.com/archives/C03RAK46BEC/p1677739796430289
>> [name=n0ah]
>> The Public Web3 共用行事曆:deployparrot: @頻道
歡迎大家訂閱這個日曆，可以看到 da0、FAB DAO (都由 @Yian 逸晟主導)、Web3 For All（@Liying Wang 主導）、da0 Learning（由 @billy3321 主導）的包括讀書會、共同工作、社交等各項活動日曆 @Peter @Jacky 我們是不是也可以融合 g0v 跟 BZD 的活動在這個日曆中，以激勵社群間的互相交流？

## 目標

現有 Google Calendar 版本: https://g0v.tw/intl/zh-TW/event/

1. 
1. 減少人為失誤，失誤了也易於復原
   > 所有編修都有紀錄、可版本控制
3. 減少維護成本
   > 所有人都可以提交編修，管理員只需要負責審核就好
2. 加分題：降低跨社群同步行事曆的成本

## 流程

1. 坑主以文字檔登記想要辦的活動
   1. 加分題是可以做成 GUI ？
3. 送交審查（git pull request）或在＃g0v-landing-page 中提供下列資訊：
    1. 專案資訊：授權方式 + 專案連結（hackmd, website......。）
    2. 活動頻率（每週、每月第幾週等等）
    3. 抽籤出 2 位 reviewer
    
4. 審查規則：
    *  在大小松提案
    *  成果開放授權   

5. 管理員審核通過
   - 管理員抽籤機制^[[SNS 抽籤網頁](https://ronny.tw/g0v-sns/?type=calendar)]
    2 位 reviewer ++
6. 由程式自動同步到 google calendar 上

## 要解決的技術問題

1. 如何用文字檔順利描述各種事件的週期
   > cronjob 很難寫阿..
   > 0 0 * * 2#1,2
   > ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0752b4b9b5a55d230c1cba47fa53c790.png)
3. 如何將文字檔同步到 google calendar
   > 需要處理人為介入，像是有人直接新增/刪除/修改了 google calendar
   > 可以是全自動或半自動，只要能減少維護成本即可

## 參考資料

1. [SNS 社群治理](https://g0v.hackmd.io/@chihao/Hkm9tPaxr)

### Google calendar 自動化工具

關鍵字（參考自 ChatGPT）

- https://github.com/insanum/gcalcli
  > interactive(TBD) python cli tool
- https://www.npmjs.com/package/gcal
  > similar tool, node version
- https://vcftools.github.io/
  > cpp + perl version XD
- also check zapier?

### 用文字描述週期事件

> [name=ChatGPT]
> 
> Sure, here are some alternative document formats that you can use to describe periodic events similar to cronjobs:
> 
> "Quartz Cron Expression" - This is a popular and widely used format for scheduling periodic events, similar to cronjobs. It uses a combination of six fields to describe the schedule, including seconds, minutes, hours, day of the month, month, and day of the week. Quartz is a Java-based library that provides support for parsing and generating cron expressions in various languages, including Java, .NET, and Node.js. You can find more information and usage examples in the Quartz documentation: https://www.quartz-scheduler.org/documentation/quartz-2.3.0/tutorials/crontrigger.html
> 
> "ISO 8601 Duration" - This is a format for representing durations of time in a standardized way. It uses a combination of letters and numbers to describe the duration, including years, months, weeks, days, hours, minutes, and seconds. It can be used to describe periodic events by specifying the duration between each occurrence. For example, "P1D" represents a duration of one day, and "R/P1D" represents a repeating event that occurs every day. You can find more information and usage examples in the ISO 8601 documentation: https://en.wikipedia.org/wiki/ISO_8601#Durations
> 
> "Human Readable Interval" - This is a format for describing intervals of time in a human-readable way. It uses phrases such as "every day", "every week", "every month", etc. to describe the schedule. It can be used to describe periodic events that occur at regular intervals, but it is less precise than the other formats. You can find more information and usage examples in the human-readable interval documentation: https://github.com/jmoiron/humanize#timedeltas

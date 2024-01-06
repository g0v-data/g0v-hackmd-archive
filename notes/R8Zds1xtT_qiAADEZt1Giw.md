# 20220409黑客松進度

- /api/term/10/speaker API 改成 /api/term/10/speaker/0 (立委) 和 /api/term/10/speaker/1 (非立委) 兩個不同的 API ，並增加分頁功能。這是為了可以因應 speakers.html 頁兩個 pager 的需求
- /api/speaker/{name}/meet API 增加使用者資訊 person_data ，這樣子 speaker.html 就不需要額外呼叫 speaker api 來抓了
- /api/speech API 增加了 persons 的資料，這樣子 speech.html 也不需要呼叫 speaker api 抓使用者頭像
- 從 [質詢記錄](https://docs.google.com/spreadsheets/d/1ZCCvVlcwchX9QY6O-ZHondBLKoz1jM-mzcU3slqoJ8M/edit#gid=0) 把一些非委員的資料倒進 person data 了，現在非委員也會有顯示頭像了
- 更新了最新資料，把 1005 的新公報也補進來了
- 同步也把前端照 API 修改改好了
- https://g0v.github.io/lysayit/speech.html?id=LCIDC01_10910001_00004#line-271


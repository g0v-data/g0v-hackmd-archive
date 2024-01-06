---
title: "第壹次基礎建設松 - 2016/6/12"
tags: hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/%25E7%25AC%25AC%25E5%25A3%25B9%25E6%25AC%25A1%25E5%259F%25BA%25E7%25A4%258E%25E6%259D%25BE)


**第壹次基礎松 KKTIX 報名:** [http://g0v-jothon.kktix.cc/events/infrath1n](http://g0v-jothon.kktix.cc/events/infrath1n)
上層資料夾：[http://beta.hackfoldr.org/g0v-infras](http://beta.hackfoldr.org/g0v-infras)

### 什麼是基礎建設松？

g0v 社群由「人、坑、松」組成，如何讓參與者容易串連協作，需要更多好用的工具與平台。兩年前曾經召開過第零次基礎建設松，時光悠悠過去，社群還是人很多，專案也越來越多，揪松團決定來重啟社群基礎建設，揪碼農筆農一起長期耕耘。

- 2014/05/13 第零次基礎松：[https://g0v.hackpad.com/uYTuvXo3atq](https://g0v.hackpad.com/uYTuvXo3atq)

### 活動形式

砍 g0v 已經砍下來的柴、拆解各種未完成基礎建設專案大魔王，變成不同的小關卡，並鼓勵參與的人認領成為小坑主（或社群小天使 PM），~把坑挖得更容易讓人掉下來~，並到大松提案。

### 預定流程 6/12 週日

- **上午 10:30**
- 檢視目前關卡、可能的解決方案、加入新點子，以及了解各類別的坑進度

- **中午 12:00**
- Pizza + **各個小坑**分組，**釐清**流程與前置準備

- **下午 16:30**
- 互相了解其它組別的預計的計畫

- **下午 17:00**
- 決定下次基礎松 / hangout 的時間


## TO-DO


    - [x] 發 KKTIX
    - [x] 發報名表
    - [x] 怎麼玩
        - [x] 流程
            - [x] brief 待解決的幾個大坑的分類
            - [x] 釐清問題
            - [x] WHAT IS 基礎建設

        - [ ] 曾經遇到的問題是什麼呢？
            - [ ] 沒有 PM / edior
            - [ ] 大松衝刺完之後，缺少後續維護
            - [ ] 想做的還沒有開始做
            - [ ] 缺少把散落的 ideas/experiments 整合，推出 Release 版
        - [ ] 為了解決這上述問題的解決方案
            - [ ] jothon 團 PM
                - [ ] 開發一些工具 or 定義 workflow
                - [ ] tickets 整理、標籤
            - [ ] 長期 remote 維護
                - [ ] jothon community hangout
                - [ ] bring in 小天使 PM / editor
            - [ ] idea pool / project hub 大魔王
                - [ ] 定義清楚製作的 workflow & 原則
                    - [x] 架構
                    - [x] 如何溝通
                - [ ] 拆成好幾個 component 小魔王
                - [ ] 找幾個 jothon 團當小 PM 認領


## 四大基礎建設類別

歡迎新 idea ++

1.  **指南類別（如何參加 g0v）**
    - g0v.tw 優化 ++
    - 新手指南一頁化 4.0 ( hack.g0v.tw )
    - 不同 target user 的 landing page
    - 社群指南 / COC
    - 如何開松
    - 專案開放量表 bluepa
        - script -> 圖
    - 不同捐款頁面整合
    - 發起新專案 SOP
2.  **專案孵化池類別**
    - **見** [projecthub redux](https://g0v.hackpad.tw/9U6DLtdZc48#projecthub-redux)
3.  **幫助整理各種協作資料的工具**
    - hackpad 無效頁面
        - 加入警語：「本內容已被標註為過時或未維護。如果三十日內沒有更新，將會被移除。原有內容仍可在 [https://github.com/g0v-data/hackpad-backup-g0v](https://github.com/g0v-data/hackpad-backup-g0v) 找到。」
> 這樣實在太嚴格了！備份沒有辦法帶著所有編輯資訊吧？（假設須以備份重新建立 hackpad 不會完全一樣 ），建議使用管理權限切換成  Moderation mode，這樣至少坑主和管理者都能恢復成可編輯狀態。
> [name=nchild]

        - 加入 [outdated collection](https://g0v.hackpad.tw/ep/group/oXnRUkvpIAP)
        - tool: 檢查 outdated collection 內的 hackpad, 三十日無更動則刪除
        - tool: 請大家 review 一年未更新的 hackpad, 一鍵加入上面的警語與 outdated collection
    - 搜尋 hackpad / 以及有連結的 hackfoldr 快速找到想找的東西（或先看看有沒有人做過）
        - 搜尋 index 坑挖好了：[https://github.com/g0v/search-hackpad-g0v](https://github.com/g0v/search-hackpad-g0v)
        - 匯出至 [graphcommon](https://graphcommons.com/graphs/a7ec343d-2a0c-47bb-9658-bb8315e8a096?auto=true&show=analysis-cluster) (保留標題、collection、最後更新日期)
            - collection api (rss): curl -D - [https://g0v.hackpad.com/ep/group/feed?groupId=sFEb2advmeh](https://g0v.hackpad.com/ep/group/feed?groupId=sFEb2advmeh)
            - 可持續更新
        - 關聯性資料庫　可以把各種專案　各種原創概念　互相描繪在一起　以利人類查&照

    - hackpad title emoji 功能（例如 title 加上電燈泡會進入 idea pool ... etc）
    - 爬蟲類圖鑑（瀕臨絕種的 ... ）
        - data.g0v.tw
        - g0v.json: parserFor:foo.gov.tw
        - 瀏覽器外掛，到 gov.tw 網站可以說：這個有爬蟲或資料

1.  **大松等實體工作的優化**
    - 一鍵開大松 ([https://www.amazon.com/uxcell-Switch-Mushroom-Button-Station/dp/B008ZY9CXE](https://www.amazon.com/uxcell-Switch-Mushroom-Button-Station/dp/B008ZY9CXE))
    - **REPO:** [https://github.com/g0v/OneButton](https://github.com/g0v/OneButton)
    - 想法：先開一個 hackpad，裡面照資料填。填好之後執行某個指令，就 boom 做完了。
        - 填表單後自動開 KKTIX, hackpad, hackfoldr, google sheet ... etc

            - [x] 填日期
            - [x] 填大松命名
            - [x] 填第幾次數字
            - [ ] 填短文案

        - [x] **自動開 KKTIX 活動**
            - PoC 在  [https://github.com/g0v/OneButton/blob/master/js/kktix.js](https://github.com/g0v/OneButton/blob/master/js/kktix.js)
            - Clone **g0v-hackath19n**
                - [http://g0v-jothon.kktix.cc/events/g0v-hackath19n](http://g0v-jothon.kktix.cc/events/g0v-hackath19n)

            - 修改：
            - 活動名稱：g0v hackath**{NUM}**n | 台灣零時政府第**{CHI_NUM}**次**{TITLE}**黑客松
                - 例如：g0v hackath==19==n | 台灣零時政府第==拾玖==次==飛彈試射==黑客松
            - 活動網址：g0v-hackath**{NUM}**n
            - 活動簡介 100 字：短文案
            - 活動日期
            - 報名時間：**活動時間 -12 天中午** **12:00**

            - 活動內容：[KKTIX TEMPALE](https://gist.github.com/ttcat/187164d51c50ff58f8696bb9cf7b6d5c) html on gist
                - template 要改：
                    - 開放報名時間固定為==**活動時間 -12 天**==**（**大松前兩週的週一中午 12:00）
                    - LINE 2: ==文案文案文案文案文案==  **填入短文案**
                    - LINE 11: ==2016/6/6==(Mon) 中午開放報名
                    - LINE 46-47: hackath==19==n  URL 修改成這次的數字（4 處）

            - ~活動時間固定：9:00 - 18:00~
            - ~活動人數固定：110~
            - ~活動地點固定：中央研究院資訊科學所~
            - ~票種？~
> clone 的話上面四個不用動
> [name=ttcat]

> 需要喔，因為票種有時間設定
> [name=良斌 薛]

> 抱歉抱歉，補充了
> [name=ttcat]

> 有一個會動的版本了，沒有以下票種設定
> [name=良斌 薛]


            - **6/12 21:30 補充票種**
            - 一般票（日期，開始報名日～活動當日，時間固定）
                - 2016/==06/06== 12:00 ~ 2016/==06/18== 09:00
                - TWD$0
                - 數量 100
                - 票種狀態：顯示
                - 販售數量 1 ~ 1張。
                - 販售單位 1張。

            - 邀請票（日期，開始報名日～活動當日，時間固定）
                - 2016/==06/06== 12:00 ~ 2016/==06/18== 09:00
                - TWD$0
                - 數量 10
                - 票種狀態：顯示
                - 販售數量 1 ~ 1張。
                - 販售單位 1張。
                - 勾選「必須使用邀請碼購買。」

        - [x] **自動開 hackpad 行前閱讀**  [**https://github.com/lkosak/node-hackpad**](https://github.com/lkosak/node-hackpad)
            - hackpad 名稱 hackath==19==n
                - 空白模板：[hackathxn](https://g0v.hackpad.tw/2ucl5ftrzot)
                - 範例 [hackath19n](https://g0v.hackpad.tw/yhTSPTHQ8H7)

###                 填入：

                - hackath==x==n 標題，第==xx==次==xxxx==黑客松
                - 本次hackfoldr網址
                - 日期
                - 報名網址
                - hackfoldr
                - 專案構想 = 登記處 = google sheet

        - [ ] **自動開 google doc 提案表**
            - [~https://developers.google.com/sheets/reference/rest/~](https://developers.google.com/sheets/reference/rest/)
            - 改用 Google Drive API 的 Copy  比較簡單[https://developers.google.com/drive/v3/reference/files/copy](https://developers.google.com/drive/v3/reference/files/copy)
            - 文件儲存在 location g0v drive [https://drive.google.com/drive/u/0/folders/0B00j8_vTJFGUdmJKT0NsS2lHbHc](https://drive.google.com/drive/u/0/folders/0B00j8_vTJFGUdmJKT0NsS2lHbHc)
            - 標題修改 hackath==19==n |  g0v 第==拾玖==次==飛彈試射==黑客松 專案列表
                - 貼上此範例：[https://docs.google.com/spreadsheets/d/12](https://docs.google.com/spreadsheets/d/12P8HzwMW41wXTFApmjeqw5SUg_smjJrzfi3JWQQk6Cc/edit#gid=1)[P8HzwMW41wXTFApmjeqw5SUg_smjJrzfi3JWQQk6Cc](https://docs.google.com/spreadsheets/d/12P8HzwMW41wXTFApmjeqw5SUg_smjJrzfi3JWQQk6Cc/edit#gid=1)[/edit#gid=1](https://docs.google.com/spreadsheets/d/12P8HzwMW41wXTFApmjeqw5SUg_smjJrzfi3JWQQk6Cc/edit#gid=1)
                - ~修改所有日期 2016/6/18~
                    - ~ROW 3~
                    - ~ROW 23~
                    - ~ROW 36~
> 改 spreadsheet 的值好困難喔
> [name=良斌 薛]

> 已刪 XD
> [name=ttcat]

            - [ ] **要把 google doc 的長網址丟到 bit.ly 變成短網址**
                - 命名：bit.ly/**g0v-hackath**==**19**==**n**
                    - 非付費用戶目前不能使用 API 建立 user-defined name 的縮址，據說是因為濫用被拔掉了。
                        [http://stackoverflow.com/questions/2991358/is-it-possible-to-generate-custom-bit-ly-urls-through-their-api](http://stackoverflow.com/questions/2991358/is-it-possible-to-generate-custom-bit-ly-urls-through-their-api)

        - [ ] **自動開 hackfoldr**
            - beta.hackfoldr.org/g0v-hackath==19==n/
            - **TEMPLATE:** [**http://beta.hackfoldr.org/g0v-hackath19n/http%253A%252F%252Fbit.ly%252Fg0v-hackath19n**](http://beta.hackfoldr.org/g0v-hackath19n/http%253A%252F%252Fbit.ly%252Fg0v-hackath19n)
                - **修改地方**
                    - B2: g0v第==拾玖==次黑客松共筆
                    - A4: 剛剛產生的 hackpad url
                    - B4: ==2016/6/18== 活動資訊
                    - A5: KKTIX 報名網址 url
                    - D5: ==6/6== 正午開始:warning
                        - 活動時間 -12 天
                    - A11: google doc / bit.ly 的網址

        - [ ] 到 github 同步更新 hack.g0v.tw
        - [ ] 產生 typeform（typeform 須優化）
        - [x] hackfoldr-iOS 上架
            - [x] 更新元件
            - [x] 上架


- [ ] [https://github.com/g0v/hack.g0v.tw/blob/master/app/partials/home.jade](https://github.com/g0v/hack.g0v.tw/blob/master/app/partials/home.jade)
- LINE 6:
```
a.btn.btn-large(href='http://beta.hackfoldr.org/g0v-hackath19n') 當期黑客松共筆
```
- LINE 15
```
| ▸ 第拾捌次開放資料日黑客松將於
```
- LINE 17, 20
```
b 2016/6/6
```
- LINE 37:
```
a.btn.btn-success.btn-large(href="http://g0v-jothon.kktix.cc/events/g0v-hackath19n") 報名 6/18 黑客松 (2016/6/6開放)

```
- [ ] [https://github.com/g0v/hack.g0v.tw/blob/master/](https://github.com/g0v/hack.g0v.tw/blob/master/app/partials/nav.jade)[app/partials/nav.jade](https://github.com/g0v/hack.g0v.tw/blob/master/app/partials/nav.jade)
```
li
 a(ng-href='/g0v-hackath19n') 飛彈試射/20160618

```
        - [ ] Google calendar
        - cpcf6iv5pt9l6gl2ue3svo63e8@group.calendar.google.com
        - [https://calendar.google.com/calendar/embed?src=cpcf6iv5pt9l6gl2ue3svo63e8%40group.calendar.google.com&ctz=Asia/Taipei](https://calendar.google.com/calendar/embed?src=cpcf6iv5pt9l6gl2ue3svo63e8%40group.calendar.google.com&ctz=Asia/Taipei)

        - **新增活動：**
        1.  報名活動（大松日期 -12 天）全天
            1.  hackth==19==n 開始報名
            2.  **活動描述：「中午 12 點開放報名：**KKTIX 報名頁面 URL」
        2.  大松日期
            1.  hackth==19==n ==飛彈試射==黑客松
            2.  **活動描述：「活動共筆：**hackfoldr URL」

        - [ ] 為行前通知開一個 g0v hackpad
            - [ ] [KKTIX 行前通知 TEMPALTE](https://g0v.hackpad.tw/9DXkirm9e92#KKTIX-行前通知-TEMPALTE)
            - **修改內容：**
            - 標題 g0v hackath==14==n 黑客松行前通知
            - 感謝大家熱情參與「==野百合==黑客松」。
            - 請務必到  [http://g0v-jothon.kktix.cc/events/g0v-hackath](http://g0v-jothon.kktix.cc/events/g0v-hackath14n)==[14](http://g0v-jothon.kktix.cc/events/g0v-hackath14n)==[n](http://g0v-jothon.kktix.cc/events/g0v-hackath14n) 取消您的報名
            - 時間：2015/6/==13== （六）
            - 活動共筆：[http://hack.g0v.tw/g0v-hackath](http://hack.g0v.tw/g0v-hackath14n)==[14](http://hack.g0v.tw/g0v-hackath14n)==[n](http://hack.g0v.tw/g0v-hackath14n)
            - 或準備跳坑：[http://bit.ly/](http://bit.ly/hackath14n)[hackath](http://bit.ly/hackath14n)==[14](http://bit.ly/hackath14n)==[n](http://bit.ly/hackath14n)


    - Ping 工作人員流程
    - g0v 大使 SOP
    - 電子報發送 / 電子報收稿
        - 需求：

開了一個 medium 打算拿來當專案定期 status report [https://medium.com/g0v-tw](https://medium.com/g0v-tw)



## 成果紀錄

- kirby: aweson md
- 子龍: 檢查 g0v.tw 動線 （畫在 sketch 上）

- superbil: iOS 版 hackfoldr，今天上架
- hlb: one button 一鍵開大松 [https://github.com/g0v/onebutton](https://github.com/g0v/onebutton)
- Lee:
    - 爬 g0v hackpad 資料「專案模版」 [https://gist.github.com/jessy1092/0025f7638792f2bc34e382bc969e43fe](https://gist.github.com/jessy1092/0025f7638792f2bc34e382bc969e43fe)
    - 產生 One Button  hackathxn 模版
- Shelling: blah blah blah ..... 沒有出來
- poga: g0v.json 表單介面 [https://poga.github.io/metadata-editor/](https://poga.github.io/metadata-editor/)
- ttcat: hackpad 搜尋器 ...
    - [https://github.com/g0v/search-hackpad-g0v](https://github.com/g0v/search-hackpad-g0v)

[projecthub redux](https://g0v.hackpad.tw/9U6DLtdZc48)




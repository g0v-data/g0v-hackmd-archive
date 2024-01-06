---
title: "g0v 人力資源部"
tags: peopleware,hackpad
---

# g0v 人力資源部

> [點此觀看原始內容](https://g0v.hackpad.tw/9IbgS6xfHZA)

人找坑，坑找人

## 來龍去脈

### 主旨

g0v hackfoldr 裡面的 people, projects, tags

### 相關組織單位

- [sample](https://github.com/g0v/hack.g0v.tw/blob/master/g0v.json)

## 實做細節

### 現有成果

- [http://hack.g0v.tw/people](http://hack.g0v.tw/people)
- [http://hack.g0v.tw/tag/hackath3n](http://hack.g0v.tw/tag/hackath3n)
- g0v project meta data & display  sample: [https://github.com/g0v/ha](https://github.com/g0v/ha)  [ck.g0v.tw/blob/master/g0v.json](https://github.com/g0v/hack.g0v.tw/blob/master/g0v.json)
- [http://g0v.github.io/g0v-tour-guide/public/hack-panel-pit.html](http://g0v.github.io/g0v-tour-guide/public/hack-panel-pit.html) <-UI 改版 mockup

## 開發者

### 第一期分工與成員

- web front-end / web back-end / prototype - [Chia-liang Kao](https://g0v.hackpad.com/ep/profile/-xi6GyN0qfe1m0Vi3coZUo)
- web front-end - fukuball
- ui design - [ET Blue](https://g0v.hackpad.com/ep/profile/1J58IcIJNw5JiAl9D0Vrqr)
### hackath5n team:

- jeffhung, 小浣熊, isac, ipa,
### hackath6n team:

- isacl, paddy, ipa


## Hackath6n 討論記錄

- 可改善的
    - 從首頁找不到專案列表（目前是「成果」）
    - 坑人 mapping 的文件找不到（我是設計師，我適合xxx工作）
    - 專案列表缺少專案的簡介
    - 各專案頁面上有個 link ，連回 [http://hack.g0v.tw/project](http://hack.g0v.tw/project)  的該 project 介紹
-  人力兩大部份
    - Part 1: 新手怎麼開始，該參加什麼
        - 線上客服直接引導
        - 新手文件 step by step 教學
    - Part 2: 坑與人的 Mapping 系統 (比較適合對 g0v 已有一定了解的人)
        - eo4 人力銀行
> 對於雖然某人有A專業，但是他想經過參與或學習後擁有B專業或是A+B變成C專業這樣的人力該如何整理好?
> [name=曼 奧]

> 例如應該有些非資訊領域的人，加入g0v後開始學coding之類的
> [name=曼 奧]

- 天馬行空
    - 類似放在各專案頁面的 Fork Me 旗幟，另外弄一個 Ask Me 或 Help Me，點選後直接對 「客服 channel」 中的人聊天


todo
- 首頁行動參與頁修改成類coscup step by step 手冊
- 手冊增加我是xx專業，適合xx專案

## hackath5n目標

- 整合以下：
    - people tag分類：[https://docs.google.com/file/d/0BzGJ4qvz2D3EbVNZMlJIUjhEMm8/edit](https://docs.google.com/file/d/0BzGJ4qvz2D3EbVNZMlJIUjhEMm8/edit)
    - [http://hack.g0v.tw/project](http://hack.g0v.tw/project)
    - [http://miau715.github.io/eo4/related_job.html](http://miau715.github.io/eo4/related_job.html)
    - 圖像類上傳介面和授權中心整合 [http://g0v.github.io/moc-license-center/index.html](http://g0v.github.io/moc-license-center/index.html)

## hackath5n 討論記錄

Issue 的整理可以分成 people-centric 與 project-centric 兩種模式－前者以人為中心，用各種方式列出跟「某一個人」相關的 issues；後者以 project 為中心，用各種方式列出跟「某一個 project」相關的 issues。我們將先處理 people-centric 的部分。

- 人力資源部另開 github repository，不要跟 hack.g0v.tw 混在一起。
> 不過現階段大部份的實作還是會先住在 hack.g0v.tw 裡。
> [name=Jeff H]

    - [x] 建立 [g0v/e04](https://github.com/g0v/e04) 專案
> Utility scripts 會放在這邊，未來再研究怎麼把 UI 從 hack.g0v.tw 搬過來 (並與原來的 hack.g0v.tw 整合)
> [name=Jeff H]

- [eo4 人](http://miau715.github.io/eo4/related_job.html)[T](http://miau715.github.io/eo4/related_job.html)[力銀行](http://miau715.github.io/eo4/related_job.html) － miau715 之前做的 mock up。
- people頁面re-layout
    - 關鍵字grouping : [g0v/hack.g0v.tw#47](https://github.com/g0v/hack.g0v.tw/issues/47) , [g0v/hack.g0v.tw#13](https://github.com/g0v/hack.g0v.tw/issues/13)
        - 關鍵字使用小圖示  [tag](https://g0v.hackpad.tw/6rlOq2DO1cD)
    - simple profile： [g0v/hack.g0v.tw#6](https://github.com/g0v/hack.g0v.tw/issues/6)
    - hover 人像後出現 pop up 人資卡
    - 點選人像後出現人資卡
        - 人資卡上方為基本資料
        - 人資卡下方為專案列表/task list/任務表/我參與的專案(用miau715之前做 mockup)
        - 我參與的工作->關注中->如果有新issue，則會有未讀的勾勾
        - 關注中 -\> issue可以按accept/resolved
- [ ] 文化部授權中心整合
    - [ ] 上傳介面
    - 上傳檔案自動化
    - Commit 自動化
    - 接受非圖檔格式
- project 頁面 re-layout
    - 增加\[適合的專案\]tab
    - 整合subproject進primary projecdt [g0v/hack.g0v.tw#31](https://github.com/g0v/hack.g0v.tw/issues/31)


## 開發手札

以下複製自 [g0v pre hackath3n](https://g0v.hackpad.tw/Y9xV1sIIuTt)

### 人物列表 | people registry

- people.g0v.tw - 簡易 people registry (取代原來鄉民列表 spreadsheet), 讓人自己加 tag (如：環保、醫療、前端、後端), 也許每個 tag 可以成為一個 disq.us 討論區?
    - 開發: [http://github.com/g0v/hack.g0v.tw](http://github.com/g0v/hack.g0v.tw) branch: hub
        - (gem install sass compass)
        - npm i
        - ./node_modules/.bin/brunch w -s
    - people 的 tag 可以包含幾種不同的類型
        1.  熟悉哪些 domain knowledge（環保、醫療、社福、經濟、食品安全、都市規劃）
        1.  擁有哪些實做技術（介面、視覺、web 前端、web 後端、手機 app、資料分析）
        1.  熟悉哪些政府或民間單位（公督盟、司改會、苦勞網、泛科學、醫勞盟、醫改會）
> 以上感覺不大會彼此重複，所以應該不用特別分類，就直接標上就好？
> [name=Chia-liang K]

> 的確耶XD
> [name=ET B]

        1.  參與過哪些 g0v 專案
> 人跟人之間、人跟專案之間、專案跟專案之間需要使用統一的 tag 以方便媒合
> [name=ET B]

    - 除了 tag 跟 email、sns 以外，可以有個欄位附上個人 github 帳號... XD
> about.me 好像有 api, 如果 user 已經有用也許可以直接 pull 所有資料過來？不過基本上就是 github/twitter/email 為必要吧，其他就... 都好 :p
> [name=Chia-liang K]


### 專案列表 | project registry

- 專案、成果、構想（包含拋磚、發想）
    - 新增構想 = 先使用 hackpad，有成案再輸入 project registry
    - 新增專案或 = webui
        - 輸入後，順便按照專案模版產生 hackpad page
    - 新增現有成果 = import from github json
- 定義 g0v project meta data & display
    - sample: [https://github.com/g0v/hack.g0v.tw/blob/master/g0v.json](https://github.com/g0v/hack.g0v.tw/blob/master/g0v.json)
        - project 和 成果 好像應該分開來顯示
            - 專案可以有個 project field 表示所屬專案。
        - 例如 立院專案 有自己的說明，各成果又各有不同產出（公報文字檔、API、網站、etc）。又如萌典，有 data source、各類 app 等成果。
    - id alphanumerical
    1.  專案名稱 name, name.zh
    2.  簡短說明 description, description.zh
    3.  狀態: status: idea, sketch, alpha, beta, production
    4.  預定產出的格式是什麼（json  / csv / api / website / mobileapp / browserext / XSS） product
> 知道產出格式是什麼，就可以知道需要哪些人幫忙，比方說產出 json 檔的專案就不需要 ui designer 的加入了，這樣 designers 進來的話可以直接找 web / app 類型的專案參與
> [name=ET B]

> [Kong Kao](https://g0v.hackpad.tw/ep/profile/nVv4sU5YxXQ) 加上了XSS ，因為覺得跟 website 還是不一樣
> [name=Kong K]

    5.  東西可以給誰用（programmer / 一般民眾）audience:
    6.  要怎麼用（去哪裡取用資料 / 去哪裡下載安裝什麼東西）
    7.  專案牽涉到的專業領域 tags（同 people XD）
> 不會寫程式的朋友，可以根據自己擅長的領域挑選想加入的專案
> [name=ET B]

    8.  專案採用的語言/工具 tags（d3.js, the noun project, iconmoon, sass/compass...）
> 攻城屍還沒有特定偏好的主題的話，可以根據實做技術來挑選可參與的專案
> [name=ET B]

> 發現工具好像不用下 tags = =" 不然沒完沒了 orz
> [name=ET B]

    9.  專案牽涉到的政府或民間單位 tags
> 有特別聯繫管道的朋友，可以根據自己熟悉的人脈挑選想參與的專案
> [name=ET B]

> c,e,d 為 keywords
> [name=Chia-liang K]

> 理解，就跟 people 的 tags 一樣不用分類直接標就好對嗎 -\> right, 然後就可以和 people match 了 :p -\> hooray XD
> [name=Chia-liang K]

> 如果這麼多種 tag 全標, 分類可能比較好看/好search? either tag 有 namespace, 或是另外弄 tag category. 不過可能等 tag 太多時再考慮
> [name=Kuang-che W]

> 的確，今天上完阿修的課以後發覺某些有特別用途的tags也許需要分類，不過要等g0v首頁的策略定完再來深究 @@"
> [name=ET B]

    10.  專案分工與認領清單
> _可以提供一組常見的分工方式讓大家改，很像是之前的那些 neadxxxx tags，想認領的人自己寫上去。_
> [name=ET B]

        - parser
        - web back-end
        - web front-end
        - ui design
        - visual design
        - writer
    11.  聯絡窗口 contact (mailing list, irc)
    12.  hackpad
    13.  專案的 github 網址
> 是否要建議每個專案開一個 group 設定 members，還是在自己帳號也行？（用自己的可能會比較亂）
> [name=ET B]

> 要是看到有人認領了某工作但很久沒 commit 了其他人可以考慮接手XD
> [name=ET B]

- 我是專案Owner，應該如何設定？
    - 新增g0v.json \[[sample](https://github.com/g0v/hack.g0v.tw/blob/master/g0v.json)\]
    - commit到project底下，github project應該會有這個檔案 gov/**hack.g0v.tw/g0v.json**
    - 到 hack.g0v.tw/people 登入後，點選 projects 按右邊「新增專案」
    - 按 add from github, 輸入 github 上的 user/repo, 如 g0v/twangry
    - 按 save


### IRC 聊天室整合 ( znc/subway)

-  原始issue
    - [https://github.com/g0v/dev/issues/10](https://github.com/g0v/dev/issues/10)
- 目前進度
    兩個選項：
    1.  znc [https://github.com/yhsiang/znc](https://github.com/yhsiang/znc)
        1.  create user script
> 想整合kiwirc然後加github login
> [name=Yuan C]

    2.  subway [https://github.com/yhsiang/subway](https://github.com/yhsiang/subway)
        1.  github login based on firebase SSO
        2.  替socketio新增一個 /authz for github login
        3.  新增一個logout的圖示
> 有一個subway 原始的bug，就是如果使用者不勾選keep connection下次登入就什麼都下次登入就什麼都看不到。
> [name=Yuan C]

> 然後現在都用onclick 硬作，應該要寫到js裡面，但是不太想破壞本來的code，雖然已經自己加了authz
> [name=Yuan C]




各種現有資料：
1.  [https://groups.google.com/forum/#!topic/g0v-general/bp6nZlNTXls](https://groups.google.com/forum/#!topic/g0v-general/bp6nZlNTXls)
2.  [http://community.g0v.tw/category/5-category](http://community.g0v.tw/category/5-category)


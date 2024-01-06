---
title: "零時廣場 aka 路人松 user story"
tags: 線路松,CongressOccupied,hackpad
---

# 零時廣場 aka 路人松 user story

> [點此觀看原始內容](https://g0v.hackpad.tw/dw3SAk6gdcb)

> 教學與筆記已整理至空白模版：[User Story Socialtext Style](https://g0v.hackpad.tw/mvxkbtlXlDf)
> [name=ET B]


## meta

> kickoff:決定要做什麼的人是誰 pm dev qa各一，如果使用者看得到的多一個 design 最多不超過4人，最少dev + qa(實做) (sample: beautiful testing ch16) ko十三邊合寫，pm level1, dev 問支線，pm回答下一步驟，qa說有沒有辦法測（問定義）pm要一直修到手上資源可以測的程度
> [name=ET B]

> ko一小時, 三邊寫完以後（符合需求、可以測、可以開發）三方契約，從此接替的人只要照做即可
> [name=ET B]

> 讓三個不同時區的人可以協作
> [name=ET B]

> design跟pm最好同一時區（都是設hls的人）
> [name=ET B]

> 等dev跟qa雙勾完pm測成品，sign off-> release，
> [name=ET B]


### Summary

> why (一段文字)
> [name=ET B]

讓立法院內、外的現場民眾，可以即時知道主要的有排節目的地點目前的狀況、接下來的行程、以及直播並提供場內g0v夥伴（任何後台夥伴）即時的回應。

### High Level Scope

> how (一句話)
> [name=ET B]

- 讓每個地點的工作人員（主持組）可以事前登錄
    - 節目名稱、開始、結束時間、哪個單位
    - 議程變動時可以即時調整
    - 有額外網址可以附上（跟直播網址分開）
- 讓直播組工作人員可以即時登錄
    - 目前的直播網址
    - 目前需要的支援
        - 包含但不限於排班表，即時訊息發送
- 讓現場民眾可以瀏覽資料並上傳文字訊息
- 讓遠端的觀眾可以
    - 瀏覽資料
    - 回報直播串流問題

### Sample User Case

> 誰會來怎麼用 (一句)
> [name=ET B]

- 小明今天到青島東路散步，看到g0v攤位，好奇之下走進去…~就出不來~ 就發現手機提示連上加入開放的ap g0v.today。
- 小明久仰g0v大名所以就連上了，於是跳出青島場的節目表，自動顯示目前時間、他所在的位置以及其他兩場正在進行的節目。
- 小明發現濟南場的比較好玩可是人太多走不過去，他就拿出耳機開始聽濟南的節目。
- 小明聽到一半，發現柴油發電機開始亮紅燈逼逼叫，於是按下即時回報系統，說發生了需要處理的狀況…好心的g0v小天使就聯絡上糾察隊排除情況。

### Preq

> 需要的東西（誰要先做完才能作）清單但不一定有
> [name=ET B]

- 三個場地都要有自己的ap
- 有輪班的直播人員管理直播網址維護

### det

> 時間估算（可以不用寫）
> [name=ET B]


## Spike

Read \[SPIKE\]


## Mockup

> 純圖，互動在上面指出，抓圖，而非互動站
> [name=ET B]


![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_728c1bf1861c2e78e716c023bb56f0cc)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_674937d175bda222f112d5c8054f2365)

mobile ui [http://g0v.github.io/g0v.today/osdc/public/](http://g0v.github.io/g0v.today/osdc/public/)


QA 新增 feature sample
- [ ] if thief want to break in, sound alarm too
    - [ ] ...



## Dev \+ QA

> issue (spec) , 打勾的表示可測, hls每個是一區，每區一個checkbox，面寫使用者做一件事情的每個步驟 (使用者跟系統的互動) (對話樹) 
> [name=ET B]

> qa測時留言吵架...hls測完以後加上 :+1:
> [name=ET B]

> qa發生新問題不在scope內，在qa區自己加checkbox，如果沒有這個真的沒辦法上線才做…
> [name=ET B]


- [ ] 讓每個地點的工作人員（主持組）可以登入後，可以...
    - [ ] 登錄節目場地、節目類別、節目名稱(optional)、講者們(optional)、開始&結束時間
        - [ ] 場地可以從現有的清單用選的
            - [ ] 青島東路場次
            - [ ] 濟南路場次
            - [ ] 中山南路場次(?)
            - [ ] 林森南路八巷場次
            - [x] \[000\] 其他（手動輸入可新增選項）
> [資料 \- 建立 event1 的場地](https://www.ethercalc.org/map:event1)and [呈現](http://g0v.github.io/conference-map-main/#map:event1)
> [name=isacl]

        - [ ] 節目類別可以用選的
            - [ ] 公民課
            - [ ] 學生論壇
            - [ ] 音樂會
            - [ ] 其他（手動輸入可新增選項）
        - [ ] 節目名稱如果懶得輸入就放他去，畢竟大家都很忙
        - [ ] 講者也是沒時間輸入就算了
        - [ ] 開始跟結束時間可以用選的…
            - [ ] 預設日期是今天
            - [ ] 預設時間是下一個沒節目的整點
    - [ ] ...\[001\] 即時調整變更的議程。按下編輯按鈕後…
        - [ ] …就可以重選或重填上面表單的所有東西
> [資料修改](https://www.ethercalc.org/map:event1:r1) (event1:r1)
> [name=isacl]

    - [ ] ...有額外網址
- [ ] 讓直播組工作人員可以即時登錄
    - [ ] 目前的直播網址
    - [ ] 目前需要的支援
        - [ ] 包含但不限於排班表，即時訊息發送
- [ ] 讓現場民眾可以瀏覽資料並上傳文字訊息
- [ ] 讓遠端的觀眾可以
    - [ ] 瀏覽資料
    - [ ] 回報直播串流問題

## Dev Journal

### \[001\]

- 讓每個地點的工作人員（主持組）可以做到「議程變動時可以即時調整」
    - sample data source url: [https://www.ethercalc.org/map:event1:r1](https://www.ethercalc.org/map:event1:r1)
### \[000\] 主持組 - 登錄場地、會議室位置、會議室名稱

- As a event owner, I want to 設定「會議室位置」與「會議室名稱」於地圖上
    - sample data source uzrl: [https://www.ethercalc.org/map:event1](https://www.ethercalc.org/map:event1)
### \[SPIKE\]

- **確認開發環境**
    - Demo page : [http://g0v.github.io/conference-map-main/](http://g0v.github.io/conference-map-main/)
    - Repository: [https://g](https://github.com/g0v/conference-map-main/)[i](https://github.com/g0v/conference-map-main/)[t](https://github.com/g0v/conference-map-main/)[h](https://github.com/g0v/conference-map-main/)[u](https://github.com/g0v/conference-map-main/)[b](https://github.com/g0v/conference-map-main/)[.c](https://github.com/g0v/conference-map-main/)[o](https://github.com/g0v/conference-map-main/)[m](https://github.com/g0v/conference-map-main/)[/](https://github.com/g0v/conference-map-main/)[g](https://github.com/g0v/conference-map-main/)[0](https://github.com/g0v/conference-map-main/)[v](https://github.com/g0v/conference-map-main/)[/](https://github.com/g0v/conference-map-main/)[c](https://github.com/g0v/conference-map-main/)[o](https://github.com/g0v/conference-map-main/)[n](https://github.com/g0v/conference-map-main/)[f](https://github.com/g0v/conference-map-main/)[e](https://github.com/g0v/conference-map-main/)[r](https://github.com/g0v/conference-map-main/)[e](https://github.com/g0v/conference-map-main/)[n](https://github.com/g0v/conference-map-main/)[c](https://github.com/g0v/conference-map-main/)[e](https://github.com/g0v/conference-map-main/)[-](https://github.com/g0v/conference-map-main/)[m](https://github.com/g0v/conference-map-main/)[a](https://github.com/g0v/conference-map-main/)[p](https://github.com/g0v/conference-map-main/)[-](https://github.com/g0v/conference-map-main/)[m](https://github.com/g0v/conference-map-main/)[a](https://github.com/g0v/conference-map-main/)[i](https://github.com/g0v/conference-map-main/)[n](https://github.com/g0v/conference-map-main/)[/](https://github.com/g0v/conference-map-main/) (branch: static)
        - assets/ls/*
        - index.html
- As a developer, I want to run "零時廣場" on gh-pages
    - 將 [http://](http://map.unisharp.com)[m](http://map.unisharp.com)[a](http://map.unisharp.com)[p](http://map.unisharp.com)[.](http://map.unisharp.com)[u](http://map.unisharp.com)[n](http://map.unisharp.com)[i](http://map.unisharp.com)[s](http://map.unisharp.com)[h](http://map.unisharp.com)[a](http://map.unisharp.com)[r](http://map.unisharp.com)[p](http://map.unisharp.com)[.](http://map.unisharp.com)[c](http://map.unisharp.com)[o](http://map.unisharp.com)[m](http://map.unisharp.com)  中不需要的功能拿掉
    - 後端改從 ethercalc.org 拿資料
    - 頁面轉為靜態，架在 gh-pages
- 定義基礎結構
    - 名詞定義
        - event - 活動
        - room - 會議室
        - schedult - 議程
    - URL 結構
        - ethercalc/map:{event}
            - 描述 event 資訊，例如：活動名稱、主辦單位、活動時間、報名方式
            - 描述所有會議室資訊
        - ethercalc/map:{event}:{room_id}
            - 描述 room_id  這一個會議室的議程
                - 時間
                - 講者
                - 主題
                - 其他資料





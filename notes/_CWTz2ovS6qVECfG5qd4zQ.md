---
title: "立院 UI 工作筆記"
tags: g0v ly,hackpad
---

# 立院 UI 工作筆記

> [點此觀看原始內容](https://g0v.hackpad.tw/UWNX2mDAnCc)


## 架構


立院會議類型
- 依與會委員身份分類
    - 全院院會 \- 所有人都有表決權
    - 各委員會 \- 屬於該委員會的人才有表決權
> 其實所有委員都可以參加，只是所屬委員才是「應參加」。投票效力應該也是所屬委員才算
> [name=Chia-liang K]

        - 經濟
        - 教育
        - 財政
        - 外交國防
        - 內政
        - 司法法制
        - 社福衛環
        - 交通
    - 特種委員會
        - 程序
        - 紀律
        - 修憲
        - 經費稽核 (會開, 討論立法院本身的預算. 可是從來沒放上記錄過)
- 依會議形式分類
    - 審議 \- 要決議的
> 應該是「要決議的」，有爭議才用表決，如果都都同意就會通過
> [name=Chia-liang K]

        - 一讀
        - 付委
        - 二讀
        - 三讀
        - 黨團協商
    - 質詢 \- 找各部會機關首長來電他們
    - 公聽會 \- 找外面的人來演講
    - 國是論壇 \- 個人閃電秀
    - 各機關來函查照 \- 被告知但什麼都不能做
- 依內容屬性分類
    - 法律
    - 預算
    - 人事
        - 彈劾
        - 罷免
        - 不信任
    - 程序 (meta)
        - 復議
        - 取消復議
        - 逕付二讀
    同意權？

公報內容
- 書面質詢內容
- 立院實體開會內容

非公報內容
- 立委個人考察
- 立委個人與各單位舉行會議

物件關連
- [ ] google docs drawing


## 頁面


- [ ] 首頁 \- 即時訊息
    - 立院現況：live stream / 處理中案件
    - 熱門話題：瀏覽人次最高的議案 / 檔案 / 立委 / 統計
- 找議案 \- 以內容為主軸
    - [x] 議事大亂鬥 \- 依日期、狀態、類型、委員會、關鍵字…綜合搜尋
    - 議案個別頁面 \- 不同性質的議事內容有不同的呈現方式
        - 決議性質的內容（可能會附帶表決結果）
            - [ ] 新法案
            - [ ] 修法案（完成一半了）
            - [ ] 預算案
            - [ ] 程序案
            - [ ] 人事案
        - 質詢性質內容（有問答往返）
            - [ ] 書面
            - [ ] 會議現場
        - [ ] 公聽會（包括影音、文字摘要）
        - [ ] 國是論壇（多人發言、每個人短時間）
        - [ ] 來函查照（單方面告知，只有文字內容）
- 找立委 \- 以個別立委為主軸
    - [ ] 立委總覽（類似 tisa / 綠盟，以選區分類）
    - [ ] 立委個人頁面
        - 行事曆
        - 擔任第一提案人的議案
        - 擔任第二以上提案人的議案
        - 擔任連署人的提案
        - 支持的提案
        - 反對的提案
        - 基本資料
    - 參考 [http://www.ly.gov.tw/03\_leg/0301\_main/legIntro.action?lgno=00090&stage=8](http://www.ly.gov.tw/03_leg/0301_main/legIntro.action?lgno=00090&stage=8)
- 找資料 \- 把先前各專案成果整合進來
    - [ ] 行事曆
    - [ ] 立院影城
    - 公報閱讀器（用現成做好的）
    - 法律亦毒氣 \- 法規本身與版本比較（extend 現成做好的）
    - 雲端預算（用現成做好的）
    - 投票箱（用現成做好的）
- 統計分析 \- 部分可參考公督盟的統計方式
    - [ ] 議案
        - 最近更新
        - 最熱門
        - 被拖延最久、被擋最多、進展最不順利
        - 和民意背離最嚴重
    - [ ] 立委
        - 出席率 vs 個人行程 - 有沒有認真工作，還是整天跑應酬喝花酒
        - 媒體放話 vs 實際投票 - 有沒有呼嚨公民
        - 政見 vs 政績 - 有沒有呼嚨選民
        - 針對同一議題在不同時間的態度轉變
    - [ ] 委員會
        - 各委員會召委排議程偏好
        - 程序委員會排議程偏好


## 工作筆記


### user story

使用者、意圖、需求
- 關注特定議題的人/社運團體
    - 需要方便地搜尋、追蹤特定議題的每個時間點和進展，以便發新聞稿或到現場抗議
- 以公民老闆身份監督國會的人
    - 需要評估立院成員的整體工作表現，發掘立法體制的結構性問題
- 有投票權的人
    - 需要評估特定立委的個人工作表現，做為選舉的參考
    - [ ] 找公督盟資料

### todo

- [ ] 單一 bill overview 也許可以順便顯示 diffstat
- [ ] 除了顯示快速跳到某一條之外，還有該條改了多少 (因為多版本的話，可能會有很多是沒改的)
- [x] 要有個簡要的提案、連署人 chart.. 可以在 /sittings 那種列出的時候顯示... 可能就是上下兩排小小的色塊 (上面是提案，下面是連署） 然後點了再顯示詳情.. compact mode 就不顯示文字跟圖了...只是小小色塊... 點開再看詳情... 疑 還是要沿用 kirby 超小頭?\
- [x] bill - 我加了些 print mode improvement... 那些提案人小頭好像可以 hide 掉 但是這樣 text 會變成沒有 padding
- [ ] 每次委員會會換不同的召集委員，會排不同議程，有個 overview 的話，可以看各黨召委愛排什麼議程，目的是觀察不同政黨的召集委員安排議程是否有特定偏好
- [x] 好心人來點精美圖檔吧，目前只有小鴨可愛
- [ ] 單一法規的頁面…bill頁面->通關流程圖，法規頁面->visualisiert生命紀錄圖
- [ ] sidebar 1223 (最後一個 item 消失了)
- [x] sider 在 mobile 會悲劇
- [ ] [http://ly.g0v.tw/bills/1011130070300200](http://ly.g0v.tw/bills/1011130070300200) 這個多版本的 style 有點不對... 變成每個都是綠的了 應該是只有 active 的是綠的
- [x] search 改成 single column
    - [x] search result 那些 item 有辦法設 height 然後 ellipsis 嗎？
    - [x] vertical ellipsis 我也不會弄... semantic ui 好像沒有現成的 就是那些 item 一樣高... 過長的後面變成 .... 刪節
    - [x] (search) infinite scroll 外面的 div 看能不能變得更服貼一點
- [ ] progress bar
    - [ ] [http://ly.g0v.tw/bills/1434L12953](http://ly.g0v.tw/bills/1434L12953) , [http://ly.g0v.tw/bills/335L15406](http://ly.g0v.tw/bills/335L15406)
    - [ ] 程序委員會有四個相關提案，應該是併在一起才對 [http://ly.g0v.tw/bills/9L13518](http://ly.g0v.tw/bills/9L13518)[,](http://ly.g0v.tw/bills/9L13518,)  [http://ly.g0v.tw/bills/23L13514](http://ly.g0v.tw/bills/23L13514)[,](http://ly.g0v.tw/bills/23L13514,)  [http://ly.g0v.tw/bills/23L13515](http://ly.g0v.tw/bills/23L13515)[,](http://ly.g0v.tw/bills/23L13515,)  [http://ly.g0v.tw/bills/23L13516](http://ly.g0v.tw/bills/23L13516)
    - [x] progress bar 串假資料 - done
    - [x] progress bar mobile - done, tkirby++
    - [ ] 也許 steps 旁邊有個 (?) 按鈕？因為可能有人會覺得「疑這不是通過了」
    - [ ] details 是不是應該改成 inline? 不然 mobile 上，再下面展開了應該也不會看到
    - [ ] [http://ly.g0v.tw/bills/468G13016](http://ly.g0v.tw/bills/468G13016)
    - [ ] 合併法案的 progress bar 顯示及切換方式
        - [ ] 單一 =\> 多案 按一下往右邊 slide 出並陳法案 好像不賴
        - [ ] 還有一種情況是：兩案併案審查，然後另外一個新的提案逕付二讀；於是二讀是三個提案一起...委員會決議「不予審議」是一個新的案號，然後還可以對這個決議提出復議，又是一個新的案號...結果復議也是 many to many.. 一個復議案可以針對多個提案決議、一個決議可以被多個不同人復議 orz
- [ ] 資料的更新時程可能要想辦法圖解一下.... 新的法案會在週二被提出，週五被一讀，但是要等到隔週的週五，前一次議事錄確定後，才會進到資料庫
- [ ]  bill page infobox 是個 vertical menu, 但是 semantic-ui 會讓他無法 text select... 這樣就無法 copy 案號了

### ideas

- [ ] 把立院各會行程全部弄成 public google calendar 好像也不賴
- [ ] 是不是所有 bill 都可以有這種標籤 [http://ly.g0v.tw/debates](http://ly.g0v.tw/debates) 這樣就可以把標籤跟立委連結，就可以從標籤查到說我想要推某個領域的法案什麼的，該找哪個立委，有點像是 g0v 的 people hub - 目前單一 bill 只有一個大 tag
- [ ] 待審案件

### data

- 新聞稿大全集 [http://www.ly.gov.tw/01\_lyinfo/0103\_legnews/legnewsList.action](http://www.ly.gov.tw/01_lyinfo/0103_legnews/legnewsList.action) 目前沒抓，因為感覺是委員自己放的。雖然自辦公聽會會在那邊，但是沒有 structural
- 立委資料 [https://github.com/g0v/twlyparser/blob/master/data/mly-8.json](https://github.com/g0v/twlyparser/blob/master/data/mly-8.json)

### improve semantic ui

- [ ] 沒有亮橘色、量黃色、咖啡色，green 跟 teal 太接近，orange 跟 red 太接近…應該來把 illustrator 的 rgb 預設色票挑幾個經典的塞進去
- [ ] 有可能規劃一個從零直接進入 sass/jade/semantic-ui 的課程嗎？感覺這樣下線可以長很快

### use git

try git pull --rebase before git push

### ref

馬來西亞政府架站問人民對 2014 年預算的建議 # [http://www.1malaysia.com.my/bajet2014/sub_topic.php?cat=7&filter=recent&lang=en#view](http://www.1malaysia.com.my/bajet2014/sub_topic.php?cat=7&filter=recent&lang=en#view)
原來蠻多國家憲法都整個砍掉重練 # [http://comparativeconstitutionsproject.org/chronology/](http://comparativeconstitutionsproject.org/chronology/)

### bill progress bar styling rules

1 完整流程 = 7 步驟
1 步驟 = 1 箭頭 + 1 圓圈
箭頭顏色
    白 = 還沒到此步驟
        圓圈顏色：白
    黑 = 在可預見的未來即將到此步驟（已排程，未執行）
        圓圈顏色：白
    綠 = 已經到此步驟，一切順利（已執行）
        圓圈顏色
        白 = 此步驟雖然已執行，但下個步驟還沒排程，還可能有變數
        綠 \+ 打勾 = 下個步驟已經排程了，此步驟的結果定讞，不會再翻盤
    灰 = 已經到此步驟，不順利（已執行）
        圓圈顏色
        紅 \+ 棒槌 = 此步驟走上了歧路，需要注意
        白 = 此步驟雖然過程不順，但已經回到正軌，只是還沒到終點，所以還可能有變數
        綠 \+ 打勾 = 此步驟雖過程不順，但已經到終點，且下個步驟已經排程了，不會再翻盤
想要給使用者的感覺
    白色 = 靜觀其變
    黑色 = 安心一半
    綠色 = 安心
    紅色 = 緊張，大難臨頭


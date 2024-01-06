# 違章工廠回報系統第84次小聚
###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：20210707
地點：線上
線上：https://gather.town/app/4KcewWQLKPx6YPlV/Disfactory

## 參與者簽到：

線上：

## 近期update
- 空拍圖比對計畫
    - [計畫整體樣貌](https://g0v.hackmd.io/@yukaii/Disfactory/%2F5QH2TlaXQR21wMo3UIKZug) 
    - [spec](https://github.com/Disfactory/satellite/issues/2#issuecomment-866704442)
    - [wireframe](https://www.figma.com/proto/TVAEC28E3ojabGHc8BawbI/%E8%A1%9B%E6%98%9F%E7%A9%BA%E7%85%A7%E5%9C%96?node-id=50%3A2&scaling=min-zoom&page-id=0%3A2)
    - [prototype](https://www.figma.com/proto/TVAEC28E3ojabGHc8BawbI/%E8%A1%9B%E6%98%9F%E7%A9%BA%E7%85%A7%E5%9C%96?node-id=473%3A405&scaling=min-zoom&page-id=457%3A331)
- 回報數匯總

| 月份 | 回報件數 |
| ---- | ---- |
|2020.11|24|
|12|46|
|2021.1|49|
|2|55|
|3|53|
|4|110|
|5| 65|
|6|109|
|7|20|



## 待討論
- disfactory維運
    - django
        - 經濟部資料
    - 前端
        - i18n
        - cluster
        - 地號[討論](https://github.com/Disfactory/frontend/issues/96#issuecomment-871349791)

- 空拍圖比對
    - 新[prototype](https://www.figma.com/proto/TVAEC28E3ojabGHc8BawbI/%E8%A1%9B%E6%98%9F%E7%A9%BA%E7%85%A7%E5%9C%96?node-id=473%3A405&scaling=min-zoom&page-id=457%3A331)設計 @tin @Lydia
    - DB @yeefun
    - 圖資api @littlewhiteYA

- 零時小學校合作
    - deeper寫的[腳本](https://www.notion.so/agrifactory/_gis_disfactory-27ee8b87e9e94e85bef7a0832bb8471c#ba9109bf732142d68fcb5caff50ef25f)

## 會議記錄
### onboard
- eric有遇到什麼問題嗎？
### 空拍圖
- 上次確定
    - 設計
        - 兩張圖
            - 現狀：免費又不花力氣的狀況下，舊圖會清晰，新圖才清晰，最好還是兩張對照
        - 其他建議
            - 強迫看教學
            - quit增加門檻
            - 有瀏覽紀錄者+跳過教學按鈕
            - 教學時可以教，新圖一定有建物，請分辨舊圖是否有建物
    - 圖資
        - 外接api
            - 小白：加marker會較簡單
            - 速度如果表現太差，再想辦法調整

### 維運

**後端**

1. EasyMap 壞掉， 貌似 server 被擋掉了（return 500）
production 和 staging 都先把這個功能拿掉。取段號、地號會先關掉。關掉後要人工查地號

現在解封了，兩台 server 都可以連了
取消 1 min retry

可能手工在後台 save 一個工廠資料觸發
比較不容易 ban IP

task:
- @deeper @ael 去確認過去一個月有多少筆沒有地號
- 觀察接下來兩個禮拜的回報會不會有地號
- 也可以寫每天只 query 一次（optional）

2. 經濟部資料(swind 需要再兩週)
3. staging -> production 自動化 => backlog
4. 給 @eric Good First Issue #554

**空照圖**

1. Intro：
    - 前面 intro clip，最好是 CSS 動畫，載入速度會比較快
    - 設定要如何觸發，滑了就自動影片播放
    - YeeFun 自動播放的秒數很難抓，是不是可以自己控制的，往旁邊滑到下一張
    - 圖像可以用動畫呈現
    - 跟小海討論文字
    - ael 覺得可以用滑的控制
    - 文字：工廠 -> 違建

    => Tin 會跟 deeper 和 小海做確認

```
<video autoplay preload loop muted playsinline playsInline disableRemotePlayback></video>
"autoplay" is needed for iPhone Safari to work
```

2. 教學頁面：

    主要在討論要使用者比對的空照圖，資料格式是用類似爬蟲瀏覽器截圖，還是直接 call canvas 放在我們的網頁裡。
    
    結論：
    
    1. Yen-Chia 建議：資料和 UI 分開
    2. 要在空照圖上做任何標記，例如 pin 、固定的方框，不在取 API 的時候處理，是顯示時額外一層的 CSS 處理。
    3. ael 希望小白可以先研究一下用瀏覽器把該工廠經緯度放在正中央截圖的技術（目前小白是用 canvas 拉中央大學 SPOT 的資料）
        - 截圖穩定性比較高，不容易因為瞬間流量太大被中央大學 auto ban，或是突然連不上中央大學 server。
        - 有空照圖截圖影像資料可以直接補充進現有 disfactory.tw 資料庫，作為舉報依據，不需要舉報時再另外截圖。
        - 有空照圖截圖影像，可供未來影像辨識機器學習的 training data （這部分還需要 @ael 去跟慈忻確認）
        - 參考資料：
            https://github.com/CMU-CREATE-Lab/smell-pittsburgh-thumbnail-server/blob/master/application.py
            https://github.com/CMU-CREATE-Lab/timemachine-thumbnail-server
    4. 資料 DB flow @YeeFun 大概弄好了，等小白那邊確定圖資近來的方式後再開工


    待討論：
    - 有可能地號框框加上去，方便使用者辨識要在哪個區域內嗎？目前只有兩種來源，一種是跟地政所付費（一個地號一塊錢），另外一種是使用 ronnywang 五年前爬下的舊資料（會有失真的問題）。這需要 @deeper 決定。
    - 擴建的比例多嗎？我們會希望擴建怎樣被標注？如果擴建沒有被抓出來，會有什麼影響嗎？ @deeper



討論紀錄：
小白：方塊做太麻煩了，會用 pin 來做
Tin: 方塊就固定死放在那邊

Zoom in 倍率怎麼決定？
小白：先放到最大，資料最大給到 17 -> 18

要比對的圖片要截圖嗎？還是直接 call 地圖 canvas

用他們的 API 截圖會偏離，因為一個畫面是由很多 png 檔組合在一起的

Yen-Chia 之前截圖的 code
https://github.com/CMU-CREATE-Lab/smell-pittsburgh-thumbnail-server/blob/master/application.py

https://classicdesign053.carto.com/builder/cb8d4f39-eef0-40c2-acda-cf67e082ab77/embed?state=%7B%22map%22%3A%7B%22ne%22%3A%5B24.023607442553732%2C120.42577286716552%5D%2C%22sw%22%3A%5B24.030976440723798%2C120.43798228260131%5D%2C%22center%22%3A%5B24.027291994452145%2C120.43187757488342%5D%2C%22zoom%22%3A17%7D%7D

有一種想法是把資料和UI分開
所以data不包含任何UI

現在是資料是用網頁呈現，UI 也是網頁

要留影像來做影像辨識的資料嗎？

- 一個是顯示（需要 zoom in/out 嗎？）
- 一個是截圖（可以未來做 training）

ael 擔心載入速度和影像能不能留作未來影像辨識 training
(圖資來自中央大學)

2020 要用 mapbox? 用 mapbox 會很糊？
Mapbox 免費上限： Map load for Web, Free Up to 50,000

ael: 希望可以用截圖
1. 穩定
2. 進資料庫
3. 未來影像辨識

Yen-Chia 可以先截大圖，之後再細切
要存中心和四角的經緯度、zoom in level
才知道距離

小白：無法想像 Python 截圖的準確度多少，怎麼得到四角的定位

live 網頁的好處是

1. Zoom in/out
2. 可加上地號框線


swind: 可以查 element 的大小
Yen-Chia: 可以有轉換的公式
Back-end server 專門在做截圖
https://github.com/CMU-CREATE-Lab/timemachine-thumbnail-server
是截 Google Engine 轉換公式的圖

用網頁的話不用 Map Box，會超過上限


ael:
- 希望是截圖，但會需要再問一下慈忻（地理博士影像辨識標註）
- 希望小白有空還是可以研究地號框框（from ronny）可以再加上去嗎？

可以辨識出擴建嗎？
擴建的比例有多高？
找出擴建很重要嗎？

ael: 我們可以先用確定是擴建的測試，一般人的反應


ronnywang 之前爬下來的地號
https://twland.ronny.tw


**Cluster**
@yukai 和 @caleb 私下聊
ael 跟 caleb 達成共識不在共同討論的 session 中間特別轉換為英文關心他的進度。

### 零時小學校
- 作業教學
    - 把工廠分佈位置的csv放上googlemymap，並找出離自己最近的一間工廠
    - 截圖
    - 計算它的面積，並以籃球場（420m^2^）當比例尺，計算他是幾個籃球場大
    - 在地圖上找出離這間工廠最近的消防隊，並計算他們之間直線距離
    - 回到disfactory，找出那間工廠現在的狀態，並補充照片期狀況描述
        - 有無照片？
        - 查處狀態如何？
- 介紹影片
    - 文稿 -> 設想畫面 -> 完整腳本
    - 給一段文字就能再切分成必要的畫面
        - 150字/分鐘
    - 素材


## 待辦事項 To Do
    
- @Tin 會花1-2 週修改 wireframe，再 1-2 週做 mock-up，再請 @Lydia 幫忙了
- @LittleWhiteYA 會研究一下如何截圖
- @ael 會去跟慈忻確認截圖是不是未來影像辨識需要的資料，發現今天忘了跟 @chewei 確認這樣標註的影像辨識在 GIS 分析上有意義
- @Yeefun Lin 會等小白那邊確認要用圖片還是 canvas 做地圖圖片辨識之後，再來做後續動作。會先回頭看 about 的 issue
- @swind 目標在兩週內整理完經濟部資料
- @yukai 的地號調查的部分，剩兩種選擇，接 Ronny 五年前的資料，或付費使用政府資料，這個部分要問 @deeper 怎麼決定
- @deeper @ael 去確認在 disfactory.tw 上過去一個月有多少筆沒有地號，觀察接下來兩個禮拜的回報會不會有地號
- @Oriyar 想一下怎麼讓線上小聚變更好玩
- @deeper 給 motion graphic 素材
- @deeper 寫完腳本和畫完相對應的流程圖

## 待辦&待討論事項

- 累積待討論
    - [地號辨識 issue 96](https://github.com/Disfactory/frontend/issues/96)
- 累積待辦事項
    - GA
    - jiahe建議
        - GA/GTM排除坑友的數據
        - 線下活動宣傳的配合（含QRcode的實體和電子flyer用於流傳）實體 flyer++ 分類廣告？
            - peii負責
        - 怎麼做 LINE 行銷
    - 寄東西給未曾謀面的捧油
    - 開好真的spec
    - 都市計畫區可以改成填一個google表單
    - 問SPOT來源能否提供更細的倍率 @deeper

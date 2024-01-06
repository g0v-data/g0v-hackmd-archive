# 違章工廠舉報系統第62次小聚

###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：20210113
地點：地公
線上：https://meet.google.com/egx-zvjk-ouv

## 參與者簽到：
- yukai
- swind
- deeper
- littlewhiteya
- oriyar
- tin
- IU

線上：
- yeefun

## 待討論


## 會議記錄
- 本週GA數據
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ea508057250b822ffaf8520f49effcd2.png)

- dashboard
    - 設計
        - [figma連結](https://www.figma.com/file/dFuJKpdDcmHNDqdj1011Zo/Disfactory_UI_design_2021?node-id=1347%3A8394)
        - 文案
        - 數字
        - 圖片
    - 進程
        - 1/13 內容的基本資料都出來，開始討論作法
        - 1/20 確認設計，分工
        - 1/27 清issue
        - 2/3  清issue
        - 2/8  正式上線
            - edm
            - 臉書
        - 2/10 小年夜
        - 2/17 初六
        - 2/24 
        - 3/3
        - 3/10
        - 3/17 

- 後端
    - 簡化環境
- 前端
    - 想og image做的方式
    - https://stackoverflow.com/questions/26525584/facebook-open-graph-date-format/28899284 og:updated-time 不過 [og spec](https://ogp.me/) 上沒寫這個欄位
    - https://developers.facebook.com/docs/sharing/webmasters/faq#faq_1131343433556264
    > 變更 og:title、og:image 等內容，只會套用到之後分享的連結。
    > 用戶或粉絲專頁分享連結後，若該則貼文有超過 50 次互動（留言、讚、分享等），就無法變更其標題。此舉旨在避免網站在您與其互動後，變更了連結的詳細資訊，讓您認為自己是與其他網站互動。其他所有屬性則可隨時修改。
    > 
    > 如果已分享連結並更新圖像，除非您在原分享貼文重新整理圖像，否則貼文會繼續顯示舊圖像。
    > 
    > 若要重新整理貼文的連結圖像：
    > - 前往動態消息的該則貼文。
    > - 點擊貼文右上角的刪節號。
    > - 選擇重新整理分享的附件。
    - 手動用 Debugger 戳
    - 用 Batch Invalidator 戳
    - https://developers.facebook.com/docs/plugins/faqs#faq_1748179212062572
    > Facebook 會偵測網址的快取標頭，並依偏好設定尋找Expires 和 Cache-Control。不過，即使您指定更長的時間間隔，Facebook 仍會每 30 天抓取您的頁面一次。
    > ( <= 30 days)
    - https://developers.facebook.com/docs/sharing/best-practices#images
    > 使用分享偵錯工具測試抓取程式如何檢視您的網站。偵錯工具還能重新整理我們從您網站抓取的任何內容，因此，如果您需要比標準 24 小時更新期間更頻繁地更新網頁，這個工具非常有用。
    - 可能不會吃 meta
    ```html
    <meta http-equiv="last-modified" content="Sun, 10 Feb 2013 14:00:46 GMT " />
    <meta http-equiv="cache-control" content="Private" />
    <meta http-equiv="Expires" content="600" />    
    ```

- 待辦事項
    - tin繼續設計，deeper和oriyar跟進討論
    - 前端繼續預排方法

## 下次待討論事項
- 確認設計
- 分工
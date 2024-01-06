# 違章工廠舉報系統第61次小聚

###### tags: `Disfactory` `違章工廠` `違章工廠舉報系統`

時間：20201208
地點：地公
線上：https://meet.google.com/egx-zvjk-ouv

## 參與者簽到：
- ael
- yukai
- swind
- aaron
- sandra
- deeper
- littlewhiteya
- oriyar
- tin

線上：
- cph

## 待討論
1. 目標設定
    - 設計在過年前可以給工程實作，目標 3/18 前上線。
    - 排程
2. dashboard 跟 about page 
    - 上次結論
    - 是否兩個網頁的使用者入口體驗都要重新設計？
    - 確認不同部分的設計誰要負責？
3. 後台
    - 可以挑 2.3 milestone 裡面的 issue 做，或是工程師自開 issue


## 會議記錄
- 本週GA數據
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3b614fd151f0d6a4003000d0a019607f.png)

    - 來源
        - disfactory.tw
        - 
        - about.disafactory.tw
        - 

- dashboard進程
    - 1/13 內容的基本資料都出來，開始討論作法
    - 1/20 
    - 1/27 
    - 2/3  有個雛形
    - 2/10 小年夜
    - 2/17 初六
    - 2/24 
    - 3/3
    - 3/10
    - 3/17 正式上線

- 後端

後端今天確認分工的部分

@swind
接下來再請你幫忙：
OpenAPI
https://github.com/Disfactory/Disfactory/issues/384
https://github.com/Disfactory/Disfactory/issues/226
2. Document query 除了鄉鎮市外，也想要可搜尋地段地號
https://github.com/Disfactory/Disfactory/issues/468
@cph CD
@LittleWhiteYA cet_review_status 自動更新
https://github.com/Disfactory/Disfactory/issues/452
@jsaon92 soft-delete factory
https://github.com/Disfactory/Disfactory/issues/403


- 前端
- 設計
    - 綜合上次討論的dashboard草案
        - 目的
            - 讓住在鄉村的人想要進行舉報
            - 讓住在都市的人想要分享
        - 形式
            - interactive的地圖（還沒確認）
            - dashboard直接放在入口網頁（about.disfactory.tw）中
            - 入口網頁要
                - 重新架站，更自由
                - 議題介紹+數據視覺化
        - 內容順序（參考[miro](https://miro.com/welcomeonboard/jRL72A58Fx81gDDkQ8hrNLKlzyNcObVP3MLKOv6VRf7vHVesFoMGHuxm6sK2PCXT))
            - 違章工廠怎麼影響日常生活
            - 政府管理作法
            - 使用者可以進行的下一步：
                - 分享
                - 舉報
            - 系統使用教學
            - dashboard：
                - 回報成果、拆除數量
                - 每個地區有多少違章工廠
                    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_442192ac4c8dac27d7848c4a70e1efd2.png)

                - 被舉報工廠數量
                    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d3bc8071ef4edc6d3682193544396239.png)
                - 各個狀態的工廠數量
                    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9bdc3cebe9f5a442010e8564a680c75d.png)

                - 跨縣市比較
            - 貢獻者介紹（地球公民、g0v）

    - 可參考案例
        - 多倫多腳踏車停車通報：[網頁](http://dashboard.bikespace.ca/)
        - 武漢肺炎dashboard：[網頁](https://coronavirus.jhu.edu/map.html)
        - 海上清垃圾機器募資：[網頁](https://www.azure-ocean.tw/)

- 回報時的feedback
    - 寄email
    - 請tin繼續
- 繼續討論dashboard
    - about page和campaign page的不一樣
        - about比較長期
        - campaign：比較遊戲性、interactive的東西
            - 如，上線一年的campaign
        - 需要畫一張使用者旅程？
    - 加入他們本來的行為中
        - 問小胖
    - 定位TA
        - 農民
        - 憤青
        - 農民Ｘ憤青（如深溝、夏耘）
        - 返鄉青年
        - 某次討論的結果
            - 有違章工廠在旁邊ㄉ居民、農民
            - 上下班路上看到覺得不合理，也有看到在污染
            - 潛在使用者都是當地人
            - 過去的農業倡議團體
            - 農村社大系統
            - 農青們（參加過夏耘營隊的人們）
    - 動力鍊
        - 知道舉報是有用的，是個正向的動力，如：有被處理的數量
            - 可發展成過年的campaign
        - 返鄉青年的分享，求的是社群聲量還是真的舉報
            - 社群聲量（如分享在IG上）
            - 真的舉報
    - 素材
        - 你家方圓一公里內有多少疑似工廠？
            - 或是鄉鎮的搜尋
                - 透過郵遞區號，直接移動到該鄉鎮的中心點
        - 你家方圓一公里內工廠密度有多高？和其他地區比較
    - 結論：
        - 內容
            - 上面campaign，下面disfactory介紹
        - 時程
            - 過年前完成，為3/20準備
        - 分工
            - sandra畫了簡易wireframe
            - Tin這幾天補充細節
            - deeper先抓出所有可能的數據
            - 先跟yeefun說
- 待辦事項
    - 違章工廠EDM
## 下次待討論事項

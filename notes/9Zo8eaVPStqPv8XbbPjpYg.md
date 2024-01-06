---
tags: GIS, Disfactory, edu
---

# 第五堂：農地違章工廠回報平台專案

<iframe width=100% height="395" src="https://www.youtube.com/embed/S3qoaPtCM8Q" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
- ==課程影片：https://youtu.be/S3qoaPtCM8Q==
- 農地違章工廠舉報平台：https://disfactory.tw/
- 專案討論區：[g0v slack #disfactory](https://g0v.hackmd.io/@jothon/joing0vslack)

## 課程補充資訊
- 請問：全台哪一個「鄉鎮區」有最多的違章工廠呢？🧐 
    :::    spoiler 想好您的答案了嗎，點我看「解答」！
    答案：彰化縣和美鎮，共有 1480 家違章工廠！😮
    :::

## 作業解說區（也請同步參考影片內容）
- 作業準備
    - 請您下載 Google Earth Pro 單機版軟體，[工具介紹與下載網址](https://g0v.hackmd.io/O6NC1bKvQeGKXLiELbepKQ)
    - 請您下載您所關心的「XX縣市違章工廠位置」資料
        - [雲端硬碟](https://cettw-my.sharepoint.com/:f:/g/personal/pisces_cet-taiwan_org/EoT4xLMpnfJDpExssBGRrr0Bzp23wSoBtHwuepuX6Mdi1g?e=U1iBQs)
- 作業step by step
    1. 匯入資料
        - 檔案 > 開啟 > XX縣市v.csv
        - 匯入精靈
            - 第一步
                - 觀察檔案預覽，是否有開錯，否的話就點選下一步
            - 第二步
                - 選擇緯度欄位來源
                - 選擇經度欄位來源
                - 下一步
            - 第三步
                - 指定欄位資料類型（本次作業沒有特別需要設定的欄位屬性，可直接點選「結束」）
            - 第四步
                - 是否套用範本？ > 是 > 建立新範本
                - 設定名稱欄位 > 選擇自己認為有識別力的欄位
                - 名稱、色彩、圖示、高度也可以選擇自己喜歡的
                - 選擇完點選「確定」
    2. 找到一間自己關心的工廠位置
        - 可以是離你最近、離你家最近、離學校最近
    3. 使用「歷史圖像」功能
        - 點選工具列的![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b62baf9a2d5aa23b12ddb07eb6698e1f.png)
    4. 截圖
        - 找尋該點位出現變化的時機，截下變化前後兩個時間點的圖（截圖時記得截到左上角的年份顯示）
        - 如：
            -  ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_db6e5cc3bb97b84c6fa2840f0c75cafa.png)
            - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fa6631c1d2f1d7ffc5232e3007bbf621.png)
    5. 上傳
        - 確定該點位的經緯度
            - 選項
                - 右鍵點選點 > 取得資訊
                    - 得到的是  XX°YY'ZZ.AA"北
                - 但disfactory.tw只吃單純的數字，如XX.YYYYYY
                - 右鍵 >「從這裡出發的路線」或「到這裡的路線指示」，左上角的搜尋欄就會顯示經緯度
        - 在違章工廠回報系統上傳照片
            - 進入 disfactory.tw
            - 我想新增違章工廠 > 顯示經緯度 > 搜尋經緯度
            - 複製經度、緯度到各自的輸入欄位
            - 取消新增 > 放棄新增
            - 點選畫面正中央的pin > 補充照片
            - 上傳剛剛截下來的兩張圖 > 視個人情況留下聯絡資訊
        - 截圖，並將圖片放到 [您個人的作業頁面中](https://g0v.hackmd.io/@chewei/gis-camp-work)
            - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_06018570c1ab06efeaaa7f749d19e8bc.png)
    

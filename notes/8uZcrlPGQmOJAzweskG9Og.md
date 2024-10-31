---
tags: tree
---

# 空間願景拼貼網頁工具

:::warning
文件目錄
[TOC]
:::

## Tool Name: Collage 

### intro

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_34570778d7e1ec7539989c5fc0dd8944.gif)

:::warning
任翔建置的網頁工具：https://collage.collective.tw/#
GitHub：
- https://github.com/SeanGau/city-collage
- https://github.com/SeanGau/joinplus-collage
:::

### 裝置測試

#### 手機

手機直立畫面，底圖及儲存範圍，均會採用直立比例

iPhone 6s, iOS 15.8, Chrome 版本 125.0.6422.80
- 可以載入 物件素材，但底圖無法點選叫出
- 可以儲存
    - 雖然操作過程沒有看到底圖
    - 但儲存後，線上瀏覽，其實好像是有底圖的，但儲存的範圍只有底圖的一部分，與手機螢幕上的素材位置似乎是底圖的上半部

Sony Xperia 5III, Chrome 120.0.6099.231
- 底圖 OK，素材 OK
- 可以儲存
- 測試成果來源討論串：https://www.facebook.com/share/p/h9tj6ZmSMmHR9RKr/

#### 平板


#### VR 裝置

Oculus GO，用內建瀏覽器開啟網頁
- 可以載入 物件素材，但底圖無法點選叫出
- 操作畫面錄影 https://www.facebook.com/groups/295496753001414/posts/519526497265104/

### 素材擴充

- 2024.07 GIF 可以放入，並於使用者在網頁操作過程中播放 GIF 動畫
- png 素材希望可以鏡向
- 點線面的「結束」，目前是要按 icon，不容易自行摸索
- 20240829 由於目前尚未建構 點線面 繪製功能，所以可以先提供 單色色塊
    - 單斜邊的梯形
        - 用於製作地面
        - 例如用兩個單斜邊的梯形，應該就可以拼出一個有透視消點的地面
    - 1:20 的長條型色塊
        - 彈性使用
    - 20240906 已上傳單色色塊
        - https://github.com/SeanGau/city-collage/blob/main/app/static/source/000.png
        - https://github.com/SeanGau/city-collage/blob/main/app/static/source/001.png
        - https://github.com/SeanGau/city-collage/blob/main/app/static/source/002.png
        - https://github.com/SeanGau/city-collage/blob/main/app/static/source/003.png
        - 並且編輯「素材目錄文件」
            - https://github.com/SeanGau/city-collage/blob/main/app/static/source/_category.yml

### 成果存檔與展示區

- 2024.09.06 目前似乎物件的上下位置關係，沒有存到
- [短期] 能否「開關」
    - 呈現底圖
    - 疊上物件
- 成果頁面，可以改存 JPG 即可？
- [其他] 把使用者的的創作過程，錄製成 GIF XD
    - 靈感來源是每次 loading 到成果瀏覽頁面時，素材會陸陸續續載入


### 底圖地點測試：2023.08 總統府府前廣場

:::spoiler
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_58b9b42cfbd297fe19b929cb7709366d.png)

底圖種類：
- 這次有兩張照片透視
- 一張平面衛星影像

架一個入口頁面 Landingpage：
- 買一個網址：https://plaza.jointw.plus/
- 導引到：https://sites.google.com/view/plaza-tw/
- 介紹
    - 為什麼
    - 回顧廣場的變遷、過往的公眾討論 (曾有民眾徵件、專業者競圖)
    - 我們是誰
- 工具
    - http://bitcreative.cc:5000/
- 公眾繪製成果，如何分析？
    - https://www.facebook.com/groups/295496753001414/posts/310351334849289/ 

宣傳，讓公眾參與：
- 發 g0v sns 貼文
    - 圖片：
    - 文字：
- 邀請群體
    - 中正社大
    - 台北荒野
- 線上繪製
- 實體場次活動：
    - 挑日期
    - 宣傳


2023.08 國史館 建築物屋頂
- 相關評估：https://g0v.hackmd.io/METgKuIjTTKuKGjiozWBLg?view

中山足球場看臺
- 相關評估：https://g0v.hackmd.io/9KmM9n2ZQk2CifD4DDy6Ew

學校教室或區民活動中心室內裝修
- 開文件找地點案例

:::



---

## Tool Name: Unlimited Cities DIY 

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3c258a2d24bb70afe6260aa505252568.gif)

### Code

試用網頁：https://unli-diy.org/dev/DIY/#/gallery
程式碼
- Clément 分享 Unlimited Cities DIY 空間願景拼貼網頁工具，open source 是用 react app 寫的
    - https://gitlab.com/7billion-urbanists/unlimitedcities
    - 程式碼授權：AGPL-3.0
- Richard 有 clone 一份到 github
    - https://github.com/Monaludao/unlimitedcities

### 中文介紹
中文介紹文章：https://eyesonplace.net/2019/08/28/12416/
- 作者：Morgane / Clément 
相關演講：
- 演講影片：https://youtu.be/044OpAFvaXg
- 講者：Morgane / Clément 
- 議程介紹：https://summit.g0v.tw/2020/agenda/2020-12-05/5ef9c9cbba206b030d66a3b1

### 主題應用案例
- 臺北市文山區景美地區舊水路沿線空間改造構想蒐集網頁
    - https://www.unli-diy.org/dev/taipei/
    - 分析報告：https://wenshanoasis.wixsite.com/mysite/professional
        - https://issuu.com/wenshanoasis/docs/unlimited_cities_wenshan____
    - 應用於活動現場影片：https://youtu.be/9DDRMQKTYis
- 臺北市文山區木柵路三段和秀明路一段的閒置國有地，進行社區改造願景交流
    - https://www.unli-diy.org/dev/muzha/


## Method Name: Computer-generated Imagery + Inpainting
使用圖像生成及 Inpainting 方式，將透視圖畫面中指定出特定範圍，依據該範圍以及所提供的指令，生成圖像

### 討論
- 這個方法能蒐集到那些意見表達？
    - 使用者塗選的範圍
    - 使用者輸入的指令文字
    - 使用者認同的生成結果圖片

### 【免費】UltraEdit for Fine-Grained Image Editing
https://huggingface.co/spaces/jeasinema/UltraEdit-SD3

### 【免費】Stable Diffusion XL Inpainting
使用網站：https://stablediffusion.fr/inpainting
試作貼文與討論串：https://www.facebook.com/groups/295496753001414/posts/331868106030945

### 【收費】DALL-E 
How to create AI street transformations
(1) Choose a photo (2) Using DALL-E 
步驟教學文件：https://docs.google.com/document/d/1a0tbTewG9JpfIOwRn-IiiPd3Zg-svyXUYeGieOcaLAI/edit
洛杉磯河圖片案例來源 ：https://x.com/betterstreetsai/status/1661844363859701760

### Adobe Photoshop 

https://www.facebook.com/share/r/1CRLw3PvHQ/

### Leonardo 

https://vocus.cc/article/6571751dfd89780001fdb51d

### 【免費】針對道路人本化，生成相關圖像方案

#### 用 AI 繪圖工具表達無車街道空間願景，有步驟介紹與指令
How to create AI street transformations
(1) Choose a photo (2) Using DALL-E 
https://docs.google.com/document/d/1a0tbTewG9JpfIOwRn-IiiPd3Zg-svyXUYeGieOcaLAI/edit
相關主題共筆：https://g0v.hackmd.io/3dqTVh6SS9a4SIXMT3X1HQ?view

#### 街道無車化圖像生成器
https://dutchcyclinglifestyle.com/
https://www.facebook.com/dutchcyclingembassy/videos/3484419568491442
討論串：https://www.facebook.com/groups/295496753001414/posts/360673806483708

### 其他應用案例
- 室內傢俱：https://fb.watch/oM9eC5zcRI/

---

# 探討：以拼貼圖像方式<br>蒐集公眾對於空間營造的意見

## 方法發想與討論

### 從「發起者、蒐集公眾意見」角度來思考

底圖
- 透視圖
    - 挑選原則：
        - 如果有明確基地、改造範圍，應作為畫面主角，前景至中景的範圍
    - 自行上傳照片
    - 用 Google 街景，鏡頭高度為 8.2 英呎高，大約 2.5 米高；授權疑慮
- 平面圖
    - 似乎也可以讓使用者表達
- 用數位模型素模當底圖
    - 好處：
    - 課題：沒有背景資訊給使用者參考

素材
- 哪些素材，適合用「點線面範圍填入材質」？
    - 地面材質
    - 阿乾 有建議 光電板這個素材，除了 "物件 png" 之外，也可以採用 "材質填入的方式" 類似目前的草地可以用點線面來劃定範圍並填入

關於素材數量
- 總量有限
- 選項：不開放自行上傳素材圖檔
- 選項：是否能讓使用者，素材使用有數量限制，例如針對「設施」這個種類只能 10 選 3，針對「植栽」這個種類只能 10 選 3


所蒐集的每位創作者的創作成果，用 dataset 角度來應用到下一階段
- 透過開放資料，了解空間的利害關係人的組成樣態 (例如店家、住戶、學校、用地管理單位、用地維護單位、用地使用單位)
    - 藉此了解實際有繪製方案的使用者，屬於哪一種類的利害關係人角色
- 透過開放資料，輔助選擇 png 素材種類
    - 例如針對明確的基地位置，採用「在地化」的素材圖像
        - 某一塊用地，透過開放資料了解周邊的人口或人員組成 (學生、長者、上班族、族裔群體..等)，作為製作 png 素材的依據
        - 動物植物：
            - 臺北市「臺北市行道樹資訊網」分析8萬多棵樹的數據，找出最被應用前10名的行道樹，做為素材給民眾挑選。
            - 苗栗野生動物調查資訊，了解在地會出現的物種，做為素材應用。
        - 選用「在地化」的素材圖像的效益
            - 環境教育：雙向回饋，同時讓參與民眾了解在地化的物種、樹種，間接也達到環境教育的目的。
    - 素材本身的欄位資訊種類，結合其他種類的資料集
        - 預算：包含材料成本與施工費用
        - 碳排係數 https://www.lcba.org.tw/article/?article_item_id=114
    - 素材
        - 若採用 GIF 檔案格式，是否適合？
        - 圖像授權
- 「素材被運用的方式」也是資料集
    - 欄位：素材名稱、素材所屬的分類、素材被不同使用者使用的次數、素材擺放位置、擴充欄位
        - 素材名稱
            - 中英文
        - 素材所屬的分類
            - 其實可以想一下分類，應該是從後續分析所需，來界定分類
        - 素材被不同使用者使用的次數：
            - 以總統府廣場為例，有一位「小帥－民主夜市方案」，方案中僅使用一個攤位圖像素材，且數量很多
            - 所以整體統計時，應該採用的是「多少人有使用到此素材」而非「此素材總共被使用多少次」
        - 素材擺放位置：
            - 哪些素材，其擺放位置有意義？
                - 定點設施：設施類、定點類、鋪面類
                - 明確需要場所設施的行為類：
                    - 例如：滑著滑板的人
                    - 討論：考量到「滑板場所」其實可能不容易放入，而「滑著滑板的人」會比較容易選用
            - 關於位置，有哪些特徵
                - 水平兩等份
                    - 前景
                    - 遠景
                - 垂直三等份
                    - 畫面左區
                    - 畫面中區
                    - 畫面右區

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1ee93495629d893486eaa34f87f4ac74.png)


## 成果分析步驟

發想討論中
https://www.facebook.com/groups/295496753001414/posts/310351334849289/

- Collage 能蒐集到「交集意見」這個可以從數量統計上來作為依據，也可以知道什麼樣的方案是「獨特意見」素材鮮少被其他人使用，「交集意見」與「獨特意見」，對於綜合評估過程來說，各自能如何發揮效用？


## 成果表現方式

動畫方式
https://fb.watch/mDA3Un4sro/

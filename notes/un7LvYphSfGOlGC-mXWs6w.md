KOL 言論整理平台
==============
現在的社群網站因為同溫層效應，常會發生一個議題兩方各自隔空交戰，雙方互相截圖對方言論批評，而雙方支持者僅會看到自己認同的人的全文，難以促進對話，反而更加加深了雙方的對立。

這邊想討論一個機制，可以針對議題列出雙方論點，各 KOL 認同的觀點以及相關關係，以方便大家更容易從宏觀角度了解在社群平台上對這議題的 KOL 有哪些以及他們論點是什麼

這平台目標是要讓大家可以了解不同立場的人的論點是什麼，但希望不要轉換成讓人去出征不同立場的工具。

想法
----
* 分為客觀資料和主觀資料，post 為客觀資料，原文照貼不帶任何價值觀，point 論點為主觀資料，包含一些判斷
* 

資料架構
-------
* topic
    * 說明：單一大議題，一個有各方不同人馬在討論論點的議題，例如：藻礁公投、美豬 ...
    * 輸入來源：人工輸入想要討論的議題。
    * 關聯
        * topic has many posts
* post
    * 文章，可能是 facebook 貼文、新聞報導、談話節目內容
    * 輸入來源：
        * facebook: 可以輸入 facebook 網址、自動帶入內容和作者
        * 新聞報導：輸入新聞連結，自動帶入出版社
    * 關聯
        * person has many posts
        * topic has many posts

* person
    * 說明：人物，可能是 Facebook 帳號
    * 輸入來源：根據 post 自動判斷 person
    * 關聯
        * person has many posts
* point
    * 論點
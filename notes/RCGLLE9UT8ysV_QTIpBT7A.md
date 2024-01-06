---
title: "議員投票指南－架站流程"
tags: hackpad
---

# 議員投票指南－架站流程

> [點此觀看原始內容](https://g0v.hackpad.tw/uGplqkYholX)

    [各縣市議會透明狀況](https://docs.google.com/spreadsheets/d/1JB2zLj8ZZqvnv31NvfwlR7HO_b99AtTjO_Gj1qMilL4/edit#gid=0)
    - [最後呈現](http://councils.g0v.tw/)

    - **資料的一生**
        官方網站或文件中 =\> 經由**crawler** =\> json、csv、txt等 => 經由**parser**提取其中感興趣的資訊 =\> **database** =\> 由網站呈現
        註：這裡選擇不在crawler時直接將資料放進database，因可能需要從多個網站合併資料後再塞入database，另外有json檔也可方便他人利用，最重要的應是有利之後debug，畢竟來源資料常常不如我們的想像，常有例外發生。

    - **流程**
        要先有人的資料，之後在提案或表決的內容中才可辨別出"人"(議員/立委)的部分
        1.  **人的基本資料**
            1.  crawler：
            - 政治人物有一些基本欄位，[可參考](https://github.com/g0v/councilor-voter-guide/blob/master/crawler/taipei/items.py#L8)councilor部分。
            - 找來源網站時，請盡量先從有**歷屆**議員/立委的網頁抓起，如網站有提供人的唯一識別碼也可拿來使用，否則請自己拼湊出一些唯一識別的辦法（例本站以python uuid module）
            2.  parser：
            - 從json檔將感興趣的資料放進database，建議將人的database table分成兩個，**一個主表**，**一個存各屆的詳細資訊**，詳細table schema可參考（[主表](https://github.com/g0v/councilor-voter-guide/blob/master/voter_guide/councilors/models.py#L20-L24)、[各屆](https://github.com/g0v/councilor-voter-guide/blob/master/voter_guide/councilors/models.py#L28-L49)）。
            - 儲存各屆人的資訊時稍微注意term\_end、in\_office等容易忘記的欄位。
        2.  **議案/提案**（議案/提案和表決紀錄順序無固定，可自行決定）
            1.  crawler：
                議案/提案基本欄位[可參考](https://github.com/g0v/councilor-voter-guide/blob/master/crawler/tcc/tcc/items.py#L30-L60)，此部份各縣市差異頗大，請由該縣市議會官網提供的資料定義相關欄位。此部分建議先手動看10~30個議案再決定議案的欄位，有時會因議案性質不同而欄位不同。
            2.  parser：
            - 從json檔將感興趣的資料放進database，建議將database table分成兩個，**一個主表**存放議案資訊，**一個存議案和提案人的關係**，詳細table schema可參考（[主表](https://github.com/g0v/councilor-voter-guide/blob/master/voter_guide/bills/models.py#L6)、[關係](https://github.com/g0v/councilor-voter-guide/blob/master/voter_guide/bills/models.py#L43)）。
            - 議案和提案人的關係可以再多加利用，藉由政黨分布可以算出個別議案的提案人政黨分布百分比，也可算出每個人共同提案的政黨分布，依照上述步驟並加入[這段程式碼](https://github.com/g0v/councilor-voter-guide/blob/master/parser/bills/bills.py#L53-L108)即可算出。
        3.  **表決紀錄**
            這是其中最痛苦（最開心）的一段，因表決紀錄通常藏在議事錄會議記錄中，需要大量閱讀議事錄找出規則...
            1.  crawler：
                表決紀錄通常政府不會整理好給你，需要從會議記錄萃取，此crawler是抓會議紀錄檔案的。
            2.  建議將各會議記錄先合併為一個檔案，方便之後大量閱讀找規則，可用word或其他軟體合併檔案。
            3.  parser：
            - 會議記錄合併後，需有識別法將各次會議的會議紀錄分開，並取得該次會議基本資料（sitting_id、date...），[可參考](https://github.com/g0v/councilor-voter-guide/blob/master/parser/votes/votes.py#L114-L120)，會議名稱（sitting）請注意有常會、臨時會等。
            - 會議記錄通常有包含出缺席紀錄，抓出缺席紀錄可參考（[出席](https://github.com/g0v/councilor-voter-guide/blob/master/parser/votes/votes.py#L129-L131)、[缺席](https://github.com/g0v/councilor-voter-guide/blob/master/parser/votes/votes.py#L132-L134)）。
            - 上述抓出缺席紀錄用到一個等下也會用到的function，從一串文字中提取出是"人"（議員/立委）的部分，並轉換為該員的id回傳，[可參考](https://github.com/g0v/councilor-voter-guide/blob/master/parser/votes/votes.py#L114-L120)。
            - 重頭戲表決，首先需要一個function可以遍歷每個表決，建議先閱讀議事錄後開工，以台北市議會為例，表決內容和表決名單是連貫的，故這裡採用遍歷表決名單的方式，[可參考](https://github.com/g0v/councilor-voter-guide/blob/master/parser/votes/votes.py#L54-L68)。
            - 再來可利用上上樓的function抓出表決名單中的"人"的id，一般可分為贊成、反對、棄權，請自行決定贊成、反對、棄權要以什麼值表達，這裡使用1、-1、0來代表，方便之後運算脫黨表決。
            - 最後是最難的部分，取出表決的內容，各縣市、甚至同縣市各屆都建議分開來寫，常因紀錄者用字或習慣而有不同，以台北市第11屆為例，[可參考](https://github.com/g0v/councilor-voter-guide/blob/master/parser/votes/tcc/votes.py#L39-L52)。

    - **網頁共用template**
        網站大家各自有熟悉的方式實作，這邊不著重在技術上，而列出一些此類網站常會共用的template供大家參考
        - 人名以政黨著色：[範例](https://github.com/g0v/councilor-voter-guide/blob/master/voter_guide/templates/common/name_color_by_party.html)
        - 各顏色所表示的政黨：[範例](https://github.com/g0v/councilor-voter-guide/blob/master/voter_guide/templates/common/color_info_of_party.html)，可輸入變數調整合併多少欄（colspan）
        - 關鍵字搜尋輸入表單：[範例](https://github.com/g0v/councilor-voter-guide/blob/master/voter_guide/templates/common/search_keyword_form.html)，可輸入變數調整輸入框的提示（placeholder）

    - [**其他縣市議會網站**](http://www.ntp.gov.tw/content/link/link01.aspx)



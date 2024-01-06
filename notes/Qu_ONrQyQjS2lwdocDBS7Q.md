---
title: "變臉：國民小學國語數位教科書(讀學悠遊)提案"
tags: event,hackpad
---

# 變臉：國民小學國語數位教科書(讀學悠遊)提案

> [點此觀看原始內容](https://g0v.hackpad.tw/VUz4BYQTrOh)

資料和圖像授權為 CC0 公領域（國教院教科書）

### 五月萌典松

- 先從「[讀學悠遊\_Unit\_1_動物昆蟲篇](https://drive.google.com/folderview?id=0BwQiYWl6VooBfkpVbnhTN1IwcFpQSEFRLTNZWTJoX1Q2RDVnWkh3SmpJMXVOVnY5WE9GSXM&usp=sharing&tid=0BwQiYWl6VooBSFQxd2xHQkg3UjQ)」測試轉換為 ePub3

### 三月萌典松（討論紀錄）

- Google Drive: [http://goo.gl/jcrO6Z](http://goo.gl/jcrO6Z)
- ePub3 on Android: GitDen reader、on iOS/OS X: iBooks、on PC: Readium@Chrome
    - Tested with: [http://goo.gl/TdLZ8J](http://goo.gl/TdLZ8J)
    - ePub3 Export test: [https://isp.moe.edu.tw/resources/resources\_festival\_list.jsp](https://isp.moe.edu.tw/resources/resources_festival_list.jsp)
        - 目前似乎無法生成 ePub3
        - 由 NAER 與維護者連絡，看是否能把 react-odp 接上去
- 部件拆分原則:
    - 以不重疊的部件為準
    - 拆出來的單部件都要是國字（難字如「舛」是 OK 的）
        - 定義以簡編本裡有的為主
    - 筆順以整字為主，拆出來之後不需要筆順
- 同義字
    - 放在 notes 裡
    - 句型用 CKIP 的樹（不顯示給使用者），Nhaa Nab 可置換，其他 particle 保留
        - 這就是照樣造句的 template
- 仿作
    - 數位教科書可以做 parse tree
    - 學生自己寫時，給出 parse tree 裡不同的部份
        - 如果都一樣則視為照樣造句成功
        - 不然，以紅色標示不同處，但不判定為錯誤與否
- 量詞
    - 用 [http://120.127.233.228/Concordancer/](http://120.127.233.228/Concordancer/) 選 Nf，找最近的名詞（Nab），做成文字雲
        - Family resemblance, 不再取 ontological abstraction
- 疊詞
    - 萌典 regex 搜尋：
        - (.)\\1(.)\\2
        - (.)(.)\\1\\2
- 狀聲詞
    - 用 [https://www.moedict.tw/?q=](https://www.moedict.tw/?q=)"的聲音" 來找。
- 自動出題，由老師篩選 false negatives
    - 因果題
- 詢問「教育部數位教學資源入口網」(isp.moe.edu.tw/)有關「將勾選項目轉製成電子書」的功能。網站管理員回應：目前教育ISP僅提供資源轉製為電子書目錄，並無提供將各別資源內容轉成互動式瀏覽電子書服務。
- 規劃將完成的電子書公開於教育部的「教育雲」(cloud.edu.tw)及國家教育研究院網站。
- 標準上需要注意，IDPF與W3C以及IMS正在製作EDUPUB規範。製作教科書時，盡量希望能與國際標準接軌。這裏提供一些資料：
    - What is EDUPUB（[PPTX](https://www.google.com.tw/url?sa=t&rct=j&q=&esrc=s&source=web&cd=3&ved=0CDAQFjAC&url=http%3A%2F%2Fwww.daisy.org%2Fprojects%2Ftransitiontoepub3%2Fdocuments%2Fmeeting-documents%2FTIES-PP-FaceToFace-EDUPUB-Introduction_2.pptx&ei=AF8xVbaQBoXX8gX42ICgDA&usg=AFQjCNHXfjJfCuVh0cP07m2cvRag8A_1wg) by Markus Gylling, IDPF CTO）
    - [EPUB 3 EDUPUB Profile](http://www.idpf.org/epub/profiles/edu/spec/)
    - [EPUB Scriptable Components Packaging and Integration 1.0](http://www.idpf.org/epub/widgets/)
- 另外注音符號在Web上的呈現最近有些擱淺，是否能給予協助？（[Test Cases](http://binb.tw/bopomofo/case01/)）
- 暫時完成「讀學悠遊第1單元_動物昆蟲篇12課」Libre Office Impress ODP格式檔(2015.05.23)，在Google Drive: [https://goo.gl/Xrdr0o](https://goo.gl/Xrdr0o)
- 僑務委員會：僑教雙周刊（(針對兒童學習華語用的教材）：[http://edu.ocac.gov.tw/culture/biweekly/](http://edu.ocac.gov.tw/culture/biweekly/)


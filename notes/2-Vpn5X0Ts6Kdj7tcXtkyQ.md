---
title: "選舉黃頁 API (alpha)"
tags: g0v idea pool,選舉松,hackpad
---

# 選舉黃頁 API (alpha)

> [點此觀看原始內容](https://g0v.hackpad.tw/y3IHgVIYYSY)


選舉黃頁基本上是由兩棵 [MPTT](http://www.sitepoint.com/hierarchical-data-database-2/) 樹狀結構所組成， areas 為行政區、 elections 為選舉區，這樣子切割的原因是部份選舉區跟行政區需要額外對應，像是個別議員選區經常會對應到一個以上的行政區，因此切開來處理。 透過 api 取得的資料都會有 rght 與 lft 用在 MPTT 索引的欄位，只要 rght - lft = 1 就表示該節點為樹葉 (leaf node) ，它不會有下一層。

\*\* 如果需要大量存取，麻煩[直接跟我聯絡](http://k.olc.tw/%E8%81%AF%E7%B5%A1%E6%98%8E%E5%AE%97/) ，我可以隨時把資料庫匯出給你，機器超弱的...
\*\* 不定時會將所有資料備份為 json 格式放在 [https://github.com/kiang/elections_json](https://github.com/kiang/elections_json)

- [http://k.olc.tw/elections/api/areas/index](http://k.olc.tw/elections/api/areas/index/53c01bce-df94-4939-a456-5460acb5b862)[/53c01bce-df94-4939-a456-5460acb5b862](http://k.olc.tw/elections/api/areas/index/53c01bce-df94-4939-a456-5460acb5b862)
    - 取得單層行政區資料， index/ 後面可以接個別行政區 id 來取得下一層資料
    - index/ 後面沒有參數會顯示最上層（目前是縣市）
- [http://k.olc.tw/elections/api/elections/index](http://k.olc.tw/elections/api/elections/index/53c0202e-ed38-44bb-8e78-5460acb5b862)[/53c0202e-ed38-44bb-8e78-5460acb5b862](http://k.olc.tw/elections/api/elections/index/53c0202e-ed38-44bb-8e78-5460acb5b862)
    - 取得單層選舉區資料，index/ 後面可以接個別選舉區 id 來取得下一層資料
    - index/ 後面沒有參數會顯示最上層（目前是九種選舉類型）
- [http://k.olc.tw/elections/api/elections/candidates/53d7332e-2dec-4626-b782-1299acb5b862](http://k.olc.tw/elections/api/elections/candidates/53d7332e-2dec-4626-b782-1299acb5b862)
    - 取得個別選舉區下所有候選人資料
- [http://k.olc.tw/elections/api/elections/s](http://k.olc.tw/elections/api/elections/s/%E5%B9%B3)[/%E5%B9%B3](http://k.olc.tw/elections/api/elections/s/%E5%B9%B3)
    - 針對行政區名稱進行搜尋
- [http://k.olc.tw/elections/api/candidates/s](http://k.olc.tw/elections/api/candidates/s/%E5%B9%B3)[/%E5%B9%B3](http://k.olc.tw/elections/api/candidates/s/%E5%B9%B3)
    - 針對候選人名稱進行搜尋
- [http://k.olc.tw/elections/api/candidates/view](http://k.olc.tw/elections/api/candidates/view/53c02641-b430-4dcd-8512-5dffacb5b862)[/53c02641-b430-4dcd-8512-5dffacb5b862](http://k.olc.tw/elections/api/candidates/view/53c02641-b430-4dcd-8512-5dffacb5b862)
    - 檢視特定候選人資料

欄位說明：
- Area
    - id: uuid
    - name: 名稱
    - ivid: 來自 [地理資訊歷史變動紀錄](https://hackpad.com/gOc6ibdldTC) 的行政區代碼 =\> [https://github.com/g0v/twhgis](https://github.com/g0v/twhgis)
    - code: 來自 [行政院主計處](http://www.dgbas.gov.tw/ct.asp?xItem=951&ctNode=5485) 的官方行政區代碼，不過好像沒有太多單位使用...
    - lft, rght: MPTT 索引， rght - lft = 1 表示已經是樹葉
    - population: 103.09 人口數
    - population_electors: 103.09 滿 20 歲人口數
- Election
    - id: uuid
    - name: 名稱
    - lft, rght: MPTT 索引， rght - lft = 1 表示已經是樹葉
    - population: 103.09 人口數
    - population_electors: 103.09 滿 20 歲人口數
- Candidate
    - id: uuid
    - name: 姓名
    - image: 圖片網址
    - party: 政黨
    - contacts_phone: 電話
    - contacts_fax: 傳真
    - contacts_email: email
    - contacts_address: 服務處住址
    - links: 相關連結
    - gender: 性別 (m = 男, f = 女)
    - birth: 生日
    - birth_place: 出生地
    - education: 學歷
    - education_level: 教育程度
    - is_present: 是否現任
    - name_english: 英文姓名
    - no: 參選編號
    - stage: 階段（0=未登記, 1=已登記, 2=已當選）
    - vote_count: 得票數字
    - experience: 經歷
    - created: 建立時間
    - modified: 更新時間
    - platform: 政見

### 非動態資料

- 所有選區資料 \- [https://github.com/kiang/elections/tree/master/Console/Command/data/2014_areas](https://github.com/kiang/elections/tree/master/Console/Command/data/2014_areas)
```
id - 選舉黃頁uuid
url - 選舉黃頁網址
election - 選區
quota - 應選人數
quota_woman - 婦女保障名額
population - 人口
population_electors - 選舉人數量（滿 20 歲）
areas - 行政區 (
id - 選舉黃頁uuid
name - 名稱
ivid - https://github.com/g0v/twgeojson 的行政區編號
code - 主計處的行政區編號
population - 人口
population_electors - 選舉人數量（滿 20 歲）
url - 選舉黃頁網址
)
```
- 候選人名單 [https://github.com/kiang/elections/tree/master/Console/Command/data/2014_candidates](https://github.com/kiang/elections/tree/master/Console/Command/data/2014_candidates)
    - pdf 格式是從中選會下載的備份
    - csv 格式是透過程式初步處理結果
- 應選名額 [https://github.com/kiang/elections/tree/master/Console/Command/data/2014_quota](https://github.com/kiang/elections/tree/master/Console/Command/data/2014_quota)
    - 上面選區資料的子集合，主要針對應選名額匯出
- 候選人名單 [https://github.com/kiang/elections/blob/master/Console/Command/data/db_dump.csv](https://github.com/kiang/elections/blob/master/Console/Command/data/db_dump.csv)
    - 選舉黃頁裡面的候選人名單，只有選區、名字跟網址
- 候選人 FB 資料 [https://github.com/kiang/elections/blob/master/Console/Command/data/facebook_candidates.csv](https://github.com/kiang/elections/blob/master/Console/Command/data/facebook_candidates.csv)
    - 把個人資料裡有 FB 連結的匯出
- fb / google result [https://github.com/kiang/elections/blob/master/Console/Command/data/google_fb.csv](https://github.com/kiang/elections/blob/master/Console/Command/data/google_fb.csv)
    - 從 [https://github.com/chhsiao1981/candidate\_google\_data](https://github.com/chhsiao1981/candidate_google_data) 取得的資料進行一些比對工作，但資料正確性不夠高
- 政治現金帳戶資料 [https://github.com/kiang/sunshine.cy.gov.tw/blob/master/list_new.csv](https://github.com/kiang/sunshine.cy.gov.tw/blob/master/list_new.csv)
- 歷屆選舉候選人 [https://github.com/kiang/db.cec.gov.tw/blob/master/elections.csv](https://github.com/kiang/db.cec.gov.tw/blob/master/elections.csv)
    - 用代號欄位可以在 [https://github.com/kiang/db.cec.gov.tw/tree/master/elections](https://github.com/kiang/db.cec.gov.tw/tree/master/elections) 找到對應資訊
- 選舉公報 \- 在 CSV 最後一個欄位看到的 uuid ，可以在 pdf / pdf_103 目錄下找到對應的 pdf 檔案
    - 舊有 [https://github.com/kiang/bulletin.cec.gov.tw/blob/master/Console/Command/data/bulletin.csv](https://github.com/kiang/bulletin.cec.gov.tw/blob/master/Console/Command/data/bulletin.csv)
    - 103年 [https://github.com/kiang/bulletin.cec.gov.tw/blob/master/Console/Command/data/bulletin_103.csv](https://github.com/kiang/bulletin.cec.gov.tw/blob/master/Console/Command/data/bulletin_103.csv)

### 許願清單Wishlist



- [ ] 和真度計的資料匯合，成為csv或json，可以用http request撈到
> 真度計[http://disa.csie.org:5566/](http://disa.csie.org:5566/)
> [name=Bestian T]

> [https://github.com/averangeall/nose-meter/tree/master](https://github.com/averangeall/nose-meter/tree/master)
> [name=Bestian T]


- [x] 確認開放授權
> [http://k.olc.tw/elections/pages/about](http://k.olc.tw/elections/pages/about) 是用 CC0 喔
> [name=kiang]





# #decentralizehk

## 提案目標

將香港公民媒體的數位資料，備份至區塊鏈 (LikeCoin chain 及 IPFS)，避免珍貴史料因政治因素或外力涉入而消失。

#### [解散香港: 國安法下 至少49組織今年宣布解散停運](https://www.thestandnews.com/politics/解散香港國安法下-至少-49-組織今年宣布解散停運)


## 我們需要
- [ ] 前端（撰寫資料呈現頁面）
- [ ] 後端（撰寫爬蟲）
- [ ] 關心議題的夥伴（協助整理csv資料及測試testnet)

## 工作流程

1. 以爬蟲抓取欲保存的網站內容，儲存相關圖文影像等附件檔，並根據網站類型與需求，將 metadate 依照 [schema.org](https://schema.org/CreativeWork) 的分類，整理成 csv 格式。(**現階段工作重點**)
2. 使用 [pinata-python-util](https://github.com/edmondyu/pinata-python-util)，將附件檔上傳至 IPFS，再將 IPFS hash 紀錄在 metadata。
3. 使用 [iscn-batch-uploader](https://github.com/likecoin/iscn-batch-uploader)，將檔案的 metadata 上傳至 LikeCoin chain 的測試網路，測試資料是否可以被正確處理。
4. 提供 csv 資料給提案發起人，待正式上傳使用。

## 備份清單

- [x] 香港蘋果日報
- [x] 香港支聯會 
- [x] [獨立媒體官網](https://www.inmediahk.net/)
    - 爬蟲: [inmediahk-scrapper](https://github.com/flyinglimao/inmediahk-scrapper) by 狸貓
- [ ] [Studio Incendo Instagram](https://www.instagram.com/studioincendohk/)
- [ ] [獨立媒體Instagram](https://www.instagram.com/inmediahknet/)

## 工作日誌

### 47th g0v黑客松 (2021/12/11)
1. 目前還很難檢索已上傳至鏈上的ISCN，因此未來有需要使用likecoin-chain-indexer或其他資料庫形式對`contentMetadata`的欄位建立索引，以求能搜尋`publisher`或其他欄位。
2. 既有的CSV檔可以透過Edmond的python script產生靜態HTML檔，並上傳至IPFS，需要前端工程師對UI/UX進行優化。
3. 獨媒的爬蟲[inmediahk-scrapper](https://github.com/flyinglimao/inmediahk-scrapper)在爬取資料遇到error時會有進度中斷不易復原的情況，需要改善error handling。
4. 社群已經爬取部分獨媒資料，後續尚有上傳至Arweave及註冊ISCN的步驟需完成。

### 48th g0v黑客松 (2022/02/19)
與會者: Wei, Aurora, Kuan, 宏信, 雨蒼, Ken
1. 短期目標: 建立一個可以進行主題式瀏覽的策展網站，可以根據關鍵字檢索倚賴後端使用likecoin-chain-indexer對鏈上的資料進行索引，等待未來更新。
2. 今日工事: 建立策展網站repo，使用plain JavaScript建立ISCN清單和ISCN內容兩個頁面。
3. 討論發想:
    - Q: 頁面的呈現可以重用 app.like.co 嗎?
      A: 現階段先將兩者分離開來  
4. Figma: https://www.figma.com/file/LQcNhsmuJStcbzKuxyqFSk/Untitle
5. VS Code的Live Share好用，讚讚讚!!

### 50th g0v黑客松 (2022/06/18)
與會者: 宏信, Wei, Aurora, Ken, Kuan
1.提案目標: 製作iscn-rss-issuer,讓使用者/網站作者能即時方便地在更新網站後利用rss備份網站至  iscn達到持續備份的目的
2.今日工事: https://github.com/lancatlin/iscn-rss-issuer, co work撰寫前端view頁面, api upload iscn part
3.討論發想:
    -Q: 純前端頁面會碰到cors issue
    -A: 改用前端call api模式,搭配local cli
4..xml檔案example:https://wancat.cc/index.xml
5.(工具)Rss parser:https://www.npmjs.com/package/rss-parser

## 常見問答
### ISCN endpoints
- ISCN module的endpoint可以參考[Useful ISCN API](https://docs.like.co/developer/likecoin-chain-api/rpc-api/useful-iscn-api)。例如
- Cosmos原生的endpoint可以參考[Legacy REST and gRPC Gateway docs](https://v1.cosmos.network/rpc/v0.42.6)中的`/cosmos/tx/v1beta1/txs`，根據Doc設置query string進行查詢。例如 https://mainnet-node.like.co/cosmos/tx/v1beta1/txs?pagination.limit=1&events=message.module=%27iscn%27

### pinata-python-util
- https://github.com/edmondyu/pinata-python-util.git
- 主要用 pinFileInCSV.py
- 最近版本支援了如 Instagram 般一筆記錄有多於一張圖的 SocialMediaPost。filename 欄的 hash 儲在 "ipfsHash"，relatedFiles 欄的 hash 會以 comma deliminated string 的格式儲在 "relatedIpfsHashes" field


### iscn-batch-uploader
- Q: 如何使用 [iscn-batch-uploader](https://github.com/likecoin/iscn-batch-uploader.git)?
  A: 可以參考以下文章的例子
  [如何一口氣註冊《唐詩三百首》到區塊鏈](https://matters.news/@edmond/%E5%A6%82%E4%BD%95%E4%B8%80%E5%8F%A3%E6%B0%A3%E8%A8%BB%E5%86%8A-%E5%94%90%E8%A9%A9%E4%B8%89%E7%99%BE%E9%A6%96-%E5%88%B0%E5%8D%80%E5%A1%8A%E9%8F%88-bafyreiautxzy4r3axckcqkks4vlq7zd4rtehagsh3f4zdinlv6zbc3nuhy)
        
- Q: 如何連接至測試網路?
  A: 將 ./config/config.js 中的 `config.ISCN_RPC_URL`欄位設定為:
  ``` javascript
  config.ISCN_RPC_URL = 'https://node.iscn-dev-2.like.co/rpc/';
  ```

### inmediahk-scrapper
issues: 
- https://github.com/flyinglimao/inmediahk-scrapper/issues/2
- https://github.com/flyinglimao/inmediahk-scrapper/issues/3

## Repo

https://github.com/lancatlin/iscn-browser

* 策展網站
* 連接後端 indexer https://github.com/likecoin/likecoin-chain-tx-indexer
* pages
    * 一個列表
    * 一個 detail（ISCN data、embed IPFS content）
    * future: 搜尋
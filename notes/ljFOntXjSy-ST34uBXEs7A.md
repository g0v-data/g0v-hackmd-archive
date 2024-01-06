---
tags: 0archive
---
# 0archive 儲存空間處理方式

我記得之前 pm5 說的主要要處理兩件事，一個是確認已經有順利備份到了 s3 ，然後再來才是砍掉舊資料

> [name=chihao] 如果這週（6/28 拜一到 7/4 拜日）大家有空來同步的話⋯
> chihao 可以的時間：三、四、五晚上、週日下午
> [name=wenyi] 這週週三、四 晚上都 ok 或 周日下午
> [name=pm5] 台灣時間拜三拜四晚上 ok

## 2021-07-08

- 怎麼確認什麼資料可以刪
    - partition 總共只有 12 個
    - 刪除舊資料不要拖過一年 XD 不然新舊資料會出現在同一個 partition
    - 抓下來的 Snapshot 都有送進 S3 就可以刪了
    - 通常超過三四個月以上的舊資料才會刪
    - 每次硬碟不夠大概刪 2-3 個月就可以回到 70% 以下
    - 目前是 Ronny 有喊才會刪 xd
- S3
    - 怎麼看上面的資料
        - 其實是 Linode XD
        - 其實是公開的，但網址沒有公開 XD
            - http://us-east-1.linodeobjects.com/0archive/user_tainan-sun-500796/ArticleSnapshot20200622.jsonl.bz2
        - 每天會把當天所有 snapshot 壓縮上傳，上傳到 s3 後手動更新 [gsheet](https://docs.google.com/spreadsheets/d/12r5zuchGa76PVqWKZe1zrLexjqCncFODIsZIUga2krg/edit#gid=0)
            - 已經一陣子沒更新了
    - 怎麼傳上去
        - S3 credentials: [0archive gdrive](https://drive.google.com/drive/u/0/folders/18uDOhXBoxuiA0gyEy4U-i0ccpN-DN0bN) / team-only / Credentials
        - 把 credential 存成 ~/.s3cfg 以後，用 s3cmd 上傳
        - ZeroScraper 裡的 scripts/upload-mysqldump.sh 就是在做上傳這件事，middle2 的 cronjob 會每日跑一次
            - 會傳但不會自動更新 [gsheet](https://docs.google.com/spreadsheets/d/12r5zuchGa76PVqWKZe1zrLexjqCncFODIsZIUga2krg/edit#gid=0) XD
        - 我們可以在 local 用 `s3cmd ls 's3://0archive/user_tainan-sun-500796/ArticleSnapshot202101*'`
            - try try `| grep ArticleSnapshot202101`
        - 可以用 `s3cmd` 看檔案列表，就應該不需要再手動維護這個 [gsheet](https://docs.google.com/spreadsheets/d/12r5zuchGa76PVqWKZe1zrLexjqCncFODIsZIUga2krg/edit#gid=0) 了
- 怎麼刪資料 [過期 Snapshot 刪除](https://g0v.hackmd.io/lMQO37z6SbWNWo3R4-X_EA#%E9%81%8E%E6%9C%9F-Snapshot-%E5%88%AA%E9%99%A4)，從 Step 4 開始
    - pm5: 看最舊 2 個月有沒有進 s3，有就砍 partition
        - 之前會看有沒有 parse
            - 看 parser log
            - 對 google drive 裡面有沒有
                - 這個方式不太可靠 XD
                - 比較可靠：mysql 建 queue 追蹤每個 snapshot parsing 的狀況？？？
                    - 很久以前的 todo XD
    - 怎麼看 「最舊」？
        - https://middle2.com/phpMyAdmin/sql.php?db=user_tainan-sun-500796&table=ArticleSnapshot&pos=0
        - ArticleSnapshot table
            - 目前（2021/7/8 最舊 snapshot = 1/1）
            - 可以查 `SELECT FROM_UNIXTIME(MIN(snapshot_at)) FROM ArticleSnapshot WHERE 1`

### 清理空間下一步?
1. [最簡單] 寫一個 command 做上面的所有事
2. [最理想] 能夠在 db 上面看得出來是不是每一個 snapshot 都 parsed 好了, 沒有錯誤訊息

有沒有在用？
IORG = 每週

上傳 gdrive？
ArticleParser script

service acct
- pm5 svc acct 滿了
- 換成 wenyi (ntu) svc acct 但無法 overwrite pm5 的檔案
- 目前作法：無法 overwrite 的檔案直接 pass XD
- 有嘗試轉移 ownership 但沒有成功
- 很頻繁嗎？

public dataset 的 gcp project + 舊 svc acct 在 pm5 那裡 XD
project + wenyi + chihao

### 轉移公開資料集到其他地方?
- ~~維持現狀~~
- ~~GitHub~~
    - 需要開 LFS
    - Github 會把違反版權的東西拿下來，我們是部分內文不知道會不會被拿下來
    - 煩：每天要上傳新檔案時要把所有檔案 pull 下來 [崩～～潰～～～～]
- Linode S3
    - $5 250G
    - $0.02 +1G

### 轉移全文資料集？
- ~~維持現狀~~
    - 跟公開資料集有一樣的狀況
- ~~GitHub~~
- Linode S3 暫存 + 下載保存

### Action Items
- [ ] 手動刪除 2021/1-3 partition
- [ ] 寫一個清理空間精靈 XD script 自動做上面的所有事
- [ ] 開 2 個 Linode S3
- [ ] 改上傳公開資料集 script => S31
- [ ] 改上傳全文資料集的 script => S32

### 空間精靈 pseudo code


---
- 把 0archive 調整為各種型態的 archive 為目的的專案如何？不是只有産出 dataset 為目的，我覺得使用 Internet Archive 這些 know-how 與 archive 相關技術也可以納入
- 是不是要來找接下來的經費了？

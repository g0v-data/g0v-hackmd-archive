---
title: "g0v-tw slack 備份記錄"
tags: jothon
---

# g0v-tw slack 備份記錄 / 工作日誌

網址：https://g0v-slack-archive.g0v.ronny.tw/

slack 免費帳號只能上傳 5GB 檔案，而付費對於 g0v 來說不太可能（計費方式是以 active user 人頭計算），這個 pad 記錄為了解決現在無法上傳新檔案的解決方式

- 目前 g0v slack 是免費版，所以最多只能顯示和搜尋到前 10,000 個訊息（現在這時間點已經有24萬個訊息），所以可以考慮把超過一年以上的圖片移除節省空間，反正也看不到
- 移除檔案時，好像會把檔案附帶的討論和留言移除，所以要研究看看能不能一起備份
    - 已確認，如果刪除檔案附加的留言會一起被刪除，所以如果想備份的話也要備份對話
- 數據狀況
    - 目前 slack 上 file 數為 1704 ，API 抓到的 size 欄位加起來是 2.5G (推測可能另包含其他解析度縮圖所以總量才佔到 5.5G)
    - 更正， admin 能看到的只有 channel 內的圖片，如果是 direct message 內的就看不到也不能刪除..   From [https://twitter.com/SlackHQ/status/968890750388797445](https://twitter.com/SlackHQ/status/968890750388797445)
    - 如果超過一年的檔案，現在加起來數量是 868  ，size 加起來是 1.01G
- 在 2018/3/13 10:20 我砍掉了一年以上的檔案，848 檔 size 為 892M ，不過還沒看到後台顯示的 File Storage Used 有更新
- 2021/06/15 支援 emoji 備份
    - https://g0v-slack-archive.g0v.ronny.tw/index/channel/C01RDCVDGHZ/2021-06#ts-1623744221.1056
    - 回溯備份，所以過去的對話紀錄中有 feedback emoji 應該是都有備份、顯示在 archive 頁面

許願區
- thread 備份
- 發言後進行內容編輯則編輯後的版本不會被記錄
- 利用合作伙伴（如OCF等?）的閒置網路資源架設Mattermost伺服器，以長期解決問題？
---
tags: privacy, new-safeID
---

# new safeID／g0v 隱私之夜 2023-03-10

:::success
連結：[提案共筆](https://g0v.hackmd.io/yZd5nmZWRLqQ2R2kqvcNqg)、[線上會議連結](https://meet.jit.si/g0v-privacy)、[加入#privacy頻道](https://g0v-tw.slack.com/archives/C04P2TY1QSZ)
:::

## Discussion
晚上九點開始！

### 會有被打槍的證明嗎？
- 有申請書，如果書面申請的話，行政機關理論上一定會
    - 申請書範例
        - [嘉義縣民雄戶政事務所國民身分證統一編號重新配賦申請書](https://www.cyhg.gov.tw/News_Content.aspx?n=72A658876253DCD9&sms=F5641EE841FA61C7&s=12786C66D61C63A5&CSForm=1)
            - 可接受原因：含4不吉利，諧音不雅，影響身心甚鉅、特殊原因，影響身心甚鉅
        - [屏東縣政府](https://www-ws.pthg.gov.tw/Upload/2015pthg/138/relfile/13862/428715/8c28270e-91e6-407b-8394-5b329e4fcdae.pdf)
            - 只能用含有 4 不吉利
        - [花蓮縣玉里鎮戶政事務所](https://ws.hl.gov.tw/Download.ashx?u=LzAwMS9VcGxvYWQvNDA3L3JlbGZpbGUvOTI3Ny8yNjQyL3B0YV81NDAzNF8zNTE3OTU4XzYxNTk1Lm9kdA%3D%3D&n=cHRhXzU0MDM0XzM1MTc5NThfNjE1OTUub2R0), [連江縣北竿鄉戶政事務所](https://www.matsu.gov.tw/upload/f-20161005110021.odt)
            - 申請原因：與他人重複、不合邏輯、末碼為４、三位數字為４、其他_________
        - [彰化縣田中戶政事務所](https://house.chcg.gov.tw/files_house/86_20220511164119839_%e8%ba%ab%e5%88%86%e8%ad%89%e8%99%9f%e6%9b%b4%e6%94%b9%e7%94%b3%e8%ab%8b%e6%9b%b8.pdf)
            - 有 4 、其他____
    - [台中市戶政人員工作手冊-國民身分證統一編號配賦重複或不合邏輯處理](https://civilinfo.taichung.gov.tw/media/823458/%E6%88%B6%E7%B1%8D%E9%A0%85%E7%9B%AE-%E5%9C%8B%E6%B0%91%E8%BA%AB%E5%88%86%E8%AD%89%E7%B5%B1%E4%B8%80%E7%B7%A8%E8%99%9F%E9%85%8D%E8%B3%A6%E9%87%8D%E8%A4%87%E6%88%96%E4%B8%8D%E5%90%88%E9%82%8F%E8%BC%AF%E8%99%95%E7%90%86.pdf)
> 國民身分證遭冒領或身分證統一編號遭冒用屬實，戶政所可應當事人申請重新配賦國民身分證統一編號，並將重配之統號通報各相關機關。
                                                        
- 每個縣市要有種子圈去測試（要找一個先鋒部隊）
    - 先鋒部隊徵招：Paul（桃園市）、Ronny（新北市）、Bobby（台北市）
    - 申請事由：由於本人戶政資料已外洩，避免身分證字號遭濫用（詳如附件一）（附上天下雜誌專題報導紙本及[調查局公告](https://www.mjib.gov.tw/news/Details/1/839)）

- pofeng：台灣身分證字號終生不能變，在身分證後面有一個[檢核碼](https://zh.wikipedia.org/zh-tw/%E4%B8%AD%E8%8F%AF%E6%B0%91%E5%9C%8B%E5%9C%8B%E6%B0%91%E8%BA%AB%E5%88%86%E8%AD%89#/media/File:ROC_mibunsho_ura.jpg)（右下角綠色）
  - 單一 ID 可以被政府追蹤，也就是說我們不能反抗政府
  - 德國可以換了eID就換了卡號
  - 日本：mynumber一般民間公司不能搜集，只有政府可以，但台灣網購平台（連任何一個門禁警衛）都可以蒐集
  - "個人編號的個資提供對象，僅限於中央與地方公共團體、所屬公司、金融機關、年金及醫療保險單位"[[ref]](https://tsunagulocal.com/zh-hant/46250/)
  - 台灣用的是終身不可變更的 UID
 

## alternatives idea
#### why don't abandon 身分證字號？
- isabel：
  - 不如捨棄身分證字號這套國民識別機制，因為已經不可信了，機制已經崩潰，被歹徒給利用；應重新編碼
  - 為什麼政府機關沒有依照個資法通知被害者
  - 要求建立機制給受害者查詢
  - 來大松討論 join 提案

- Paul：把 join 的提案改成「捨棄身分證字號這套國民識別機制」

#### ronny：不如做民間版的「個資受害查詢平台」？
> 類似：firefox monitor 、https://haveibeenpwned.com/

- Paul：中華民國國民做民間版有法律風險
- isabel：或者是可以在查詢平台的 TOS 就先寫好查詢人放棄民事損害請求權
- pofeng：個資法第 41 條
  - 意圖為自己或第三人不法之利益或損害他人之利益，而違反第六條第一項、第十五條、第十六條、第十九條、第二十條第一項規定，或中央目的事業主管機關依第二十一條限制國際傳輸之命令或處分，足生損害於他人者，處五年以下有期徒刑，得併科新臺幣一百萬元以下罰金。
  - 第 42 條
意圖為自己或第三人不法之利益或損害他人之利益，而對於個人資料檔案為非法變更、刪除或以其他非法方法，致妨害個人資料檔案之正確而足生損害於他人者，處五年以下有期徒刑、拘役或科或併科新臺幣一百萬元以下罰金。
  - 台灣上一個做 "Have I Been Pwned" 的網站, 就被逼出國了 
( 被威脅告 , 所以移到國外 ) 
  - 補充資料： [「晶片國民身分證？」議題手冊](https://drive.google.com/file/d/1M5BwL49AUj-XkDHM7itUYM5hPIwyUuLi/view) p56-p79 有各國身分證制度整理 

- 繁嵐：
  - 幾年前臺灣有人做過類似的 HIBP
https://www.facebook.com/breach.tw/
https://free.com.tw/breach-tw/


## TODO
- 幫忙找認識的人和NGO
    - Isabel
- 介紹會打行政訴訟的NGO（台權會）
    - pofeng
- 找 TWNIC/TWCERT/CC Kenny Huang
    - Paul
- Join 提案初稿
    - Paul
- 宣導反詐騙圖文（對長輩說不要相信任何人）：
    - fb 粉專
    - ig
    - 抖音也可以XDDD
- 到天下的專題報導下面貼後勤中心的文，吸引更多注意和參與者
    - 「你可以怎麼加入我們」（可以參考cofacts怎麼做的）
    - Paul
- 整理各地戶政事務所申請書
    - ronny
      - 可以共用事由
- 看是否建立群組，slack / telegram，能看到先前對話記錄的都可以
    - 直接在 slack #privacy 討論共用事由內容
- 掃描天下雜誌專題報導為pdf
    - ronny
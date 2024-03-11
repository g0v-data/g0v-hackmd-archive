---
tags: g0vernance
---
g0v github 社群規範討論　
=====================

現況
----
* 64 admins, 276 members
    * https://github.com/orgs/g0v/people
* admin 都有權限可以砍光光所有 repositories (也可以順便把其他人都踢出 admin)
* members 都有權限可以在 g0v.tw 首頁塞入任何東西，跟在上面專案塞入任何有害程式碼
* 但也因為自由度很高，g0v 是在 github 上世界前三大的 civic tech 社群
    * https://www.ithome.com.tw/news/106629

可能作法
-------
1. 什麼都不管，等出事再說
2. 建立異地備援機制，如果真發生被砍光光還可以救回來
3. 增加程式碼的 review 流程，避免被塞惡意程式
4. 訂立較嚴格的 admin, member 規範

本日工作項目
----------
1. 如何備份 g0v repository
2. 開一個 g0v member repository 讓想要帳號的人可以來申請（以 PR 型式)
3. 擬定現有 admin 需要在期限內做自我介紹的流程
4. 整理 admin 權利義務
5. [g0v github 規範草案](https://g0v.hackmd.io/I4_oYRIvT9S0RKufKKKKvg)

規範草案
-------

- Owner

- Member

討論進度
------
- 2024/03/10 [g0v基礎建設更新計畫討論共筆](https://hackmd.io/t97cH7tFQPyUCgwmfCsFiw?view)
    - 討論ㄩ
    - 角色有哪些？
        - 提議者
            - 提議方式：
                - 於 slack 提議與描述 （general channel、g0v-landing-page）
                - 開 github Issue
                - 建立共筆文件
                - 或其他方式 表單
                - 希望能將內容明確化
                    - 草稿
                    - Mockup
                    - 手繪
                    - 也可以用簡報方便協作 
                    - 主要檢核：工程師看得懂或看不懂
        - 開發者
            - 把前端的問題寫成程式
            - 可以先製作一個展示網址
            - 送出 pull
            - 不需要有 github g0v 組織權限
        - 審核者／上傳者（要建立名單？）
            - 優先找曾經參與開發 g0v.tw 的 [contributor](https://github.com/g0v/g0v.tw/graphs/contributors)
                - 優先找也在 g0v Slack 的人 
                - 或通知 GitHub 上面的 contributor 加入 Slack 頻道
            - Review Code, push, merge
                - 技能建議：網站跑起來，修改網頁程式碼，瀏覽程式
        - 新增非同步的治理機制review提案文件，在大小松討論過再apply上來，名單提出與揪松團討論
        - 報修類可能就不用開基礎松，非同步方式？
            - 要再跟更多有興趣的貢獻者一起確認
            - github bug report sample: jQuery new issue
        - 官網條列新增，可能要開基礎松
            - 開發者（比較缺）、上傳者
            - 在基礎松現場確認速度比較快
            - 但人要到現場
        - Teemo (g0v-landing-page calendar reviewer)>
            - 日曆 reviewer 作法
            - 我想像能快速過審的模式：有一個測試的網址，直接截圖標記，告訴我差異，我點進去看確認，就會放行。
            - 我想像慢速過審：由我 run 起來，檢查差異，確認後過審。
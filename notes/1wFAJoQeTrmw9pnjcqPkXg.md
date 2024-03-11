---
tags: g0vernance
---
g0v github 社群規範討論　
=====================

:::warning
目錄
[TOC]
:::


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

規範草案 (討論中)
-------

- Owner

- Member

歷次討論進度
------
- 2024/03/10 [討論 g0v 官網治理機制共筆](https://hackmd.io/t97cH7tFQPyUCgwmfCsFiw?view)
    - 討論緣由：
        - 發現 g0v 官網內文連結失效，以及版面改動提議
        - g0v 官網的維護管理，涉及 GitHub 
        - 故於該次討論中，有進一步界定從官網維護管理的角度，需要哪些 GitHub 協作角色
    - 本次討論對於 GitHub 治理機制的助益
        - 從協作與治理的角度，界定角色，以下分項說明各個角色的工作重點與技能期待
        - 提議者 Suggester
            - 名單：
                - 不需要建立名單
            - 執行事項：
                - 提議
                    - 如何提議 (討論中)
                        - 於 slack 提議與描述 （general channel、g0v-landing-page）
                        - 開 github Issue
                        - 建立共筆文件
                        - 或其他方式 表單
                - 將提議內容明確化
                    - 工具 (討論中)
                        - 草稿、Mockup、手繪後拍照、使用 Google Slide 簡報製作提議解說內容也方便協作 
                    - 什麼是「明確化」
                        - 把提議內容貼到 g0v Slack 頻道
                        - 邀請 開發者 Developer 回饋意見
                            - 看得懂或看不懂
                            - 可行性
        - 開發者 Developer
            - 名單：
                - 不需要建立名單
                - 不需要有 github g0v 組織權限
            - 執行事項：
                - 把 Suggester 的提議，寫成程式
                - 可以先製作一個展示網址、測試網址，可加快　審核者　的工作流程
                - 送出 pull request
        - 審核者 Reviewer
            - 名單：
                - 需要建立名單
                - 優先找曾經參與開發 g0v.tw 的 [contributor](https://github.com/g0v/g0v.tw/graphs/contributors)
                    - 優先找也在 g0v Slack 的人 
                    - 或通知 GitHub 上面的 contributor 加入 Slack 頻道
            - 執行事項：Review Code, push, merge 網站跑起來，修改網頁程式碼，瀏覽程式，把關惡意程式混入




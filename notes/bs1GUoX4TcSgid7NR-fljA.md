# vTaiwan 教召

一個想簡化開活動流程的小小專案兒

### 定義

帳號池：具有開活動權限的活躍用戶


### 要做些什麼
半自動式：
* SlackBot: 帳號池隨機抓一個人Cue他開活動
* Email: 帳號池隨機Cue一個人寄信提醒他開活動
* UI呈現: 俄羅斯輪盤（花俏的東西兒）
    * 技術討論: 如何可以看到俄羅斯輪盤（在slack上？在email附件上？）

全自動：
* 按鍵精靈(Selenium)
    * github: https://github.com/ChingSheng/vtw_muster_call
    * 我有妹妹我超強，~~她有做過自動上班打卡程式~~
    * 技術細節
        * Debug: 由於Selenium 是模擬使用者操作瀏覽器，為了之後好維護，可以在每一個動作操作顯示在command上面。

* 進度
    - [x] 開一個新的hackMD，複製前週內容並清空（好像可以設範本）(V)
        * 缺輸入日期
        * 是說我開了g0v hackMD的account(可載入範本): vtaiwan.tw@gmail.com / password: {秘密}
    - [x] 每次開新的KKTIX活動
    - [x] 張貼在slack (已完成，使用slack bot hook鏈結即可) 
    - [x] 上到Heroku, 讓程式可以自己定期去跑（一週一次這樣）
        1. 因為Heroku上面的作業系統是Ubnutu, 在本機端的chrome環境與chrome web driver都要能與heroku上面吻合，粗略的細節請參考[這裡](https://elements.heroku.com/buildpacks/heroku/heroku-buildpack-google-chrome)
        2. 在heroku加入settings/buildpack的設定：
            - https://github.com/heroku/heroku-buildpack-chromedriver 
            - https://github.com/heroku/heroku-buildpack-google-chrome
        3. 在heroku加入settings/Config vars：
            - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d75fe49b494646e8e49918a0824febb8)
        4. 踩到的[bug](https://github.com/heroku/heroku-buildpack-google-chrome/issues/46)
            
    - [x] 定時設定APScheduler: 設定好台北時區

* 目前仍需要人力去做的事情
    - [ ] 張貼在FB社團
        * FB API, 研究一下權限
    - [ ] 把 hackMD 超連結更新在 vtw.link 目錄
        * Selenium表示：css樣式找不到對應的element...

        
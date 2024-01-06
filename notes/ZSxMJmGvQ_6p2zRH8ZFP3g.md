Telegram 接彈幕筆記
=====
* 初始
    * 申請 telegram 機器人帳號
        * 增加 [BotFather](https://t.me/botfather) 好友
        * 丟他 「/start」開始申請
        * 丟他 「/newbot」新增機器人
        * 輸入你的機器人顯示名稱和 username （後者必須要 bot 結尾）
        * 接下來會得到一個 access_token (勿外流)
    * 把機器人邀請進群組中
        * 需要幫機器人加入 admin 權限，機器人才能讀內容
    * 透過 https://api.telegram.org/bot{ACCESS_TOKEN}/getUpdate  API ，可以查到機器人所在的 group 的 chat_id，用在後面程式
* 程式
    * https://github.com/ronnywang/telegram-danmu
        * 需要用 env 指定 TELEGRAM_ACCESSTOKEN 和 TELEGRAM_CHATID
        * 可以用 「env TELEGRAM_ACCESSTOKEN=xxx TELEGRAM_CHATID=1234567 php -S 0:8080」在資料夾下執行，然後瀏覽器開 http://localhost:8080/danmu.html 看看能不能看到彈幕
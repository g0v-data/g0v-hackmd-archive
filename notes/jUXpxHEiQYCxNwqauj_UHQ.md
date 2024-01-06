多粉對談架構
==========

* [FB App](https://developers.facebook.com/apps/804221100152988/dashboard/)

* 由 fb-host.php 接收 FB 機器人送來的資訊，儲存在 files/ 資料夾下。然後 looper.php 處理 files/ 資料夾下累積的訊息，傳向 host.php。而 host.php 跑起主要核心功能，並把聊天功能執行在 wss://wss.fantalk.ronny.tw/fantalk。

* host.php
    * 跑起主要核心功能，並把聊天功能執行在 wss://wss.fantalk.ronny.tw/fantalk
* fb-host.php
        * 
    * 透過 https://dev.aws.ronny.tw/fb-host.php ，接收 FB 機器人送來的資訊，儲存在 files/ 資料夾下
        * 透過寫檔的方式是因為加速回應時間，避免超過兩三秒而被 chatbot 關閉連線
        * 程式碼說明： 
            * `file_put_contents(__DIR__ . "/files/fb-{$message->sender->id}-{$seq}", json_encode($message));` 是寫入訊息。
            * `file_put_contents(__DIR__ . "/files/fb-{$message->sender->id}-write-seq", $seq + 1);` 是寫入訊息的序號。
            * `file_put_contents(__DIR__ . "/files/fb.stats", microtime(true));`是寫下最新的訊息的時間，好方便 `looper`抓到最新的訊息。
* looper.php
    * 處理 files/ 資料夾下累積的訊息
        * `addPeriodicTimer` 是最主要的函式

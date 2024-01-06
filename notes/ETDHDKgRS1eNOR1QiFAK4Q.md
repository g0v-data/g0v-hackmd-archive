---
tags: jothon
---

20200523 g0v 大松的抖內通知
========================

上次線上大松之後，有想要再幫這次大松再多加點東西，其中一個想到的是可以加上抖內通知，這邊記錄加上抖內通知的過程和相關程式碼位置

即時通知
-------
* [捐款挺大松](https://ocf.neticrm.tw/civicrm/contribute/transact?reset=1&id=30) 是透過 neticrm 網絡行動所提供的付款介面，過去多年都是從這邊當作捐款管道，費用會再進入開放文化基金會的大松專案。
* 先前有請 OCF 協助詢問 neticrm 是否能有 API 可以拉或推捐款通知資料（拉：可以由我方每分鐘透過 API 查詢是否有新捐款、推：當有人有捐款時， neticrm 主動通知我方），不過目前 neticrm 都沒有現成功能，會需要額外開發，也會需要開發費用。
* 後來再給詢問 OCF ，當有人捐款時，是否能將捐款通知信多轉寄給一個信箱，OCF 說這是已經有的功能，所以就從這邊來做通知了
* ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fa3b69182c8242340a56c37829c9f6c5.png)
* ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_60e0ae004e6326fd89e947791297c244.png)
* 需要的資訊在通知信的「金額」「捐款徵信顯示名稱」「捐款備註」「是否為定期定額」都有

信件通知機制
----------
* 事先準備
    * 一個 Amazon Web Service 帳號
    * 一個可以跑 http 或 https 後端的伺服器
    * 一個你擁有的網域
* 採用 Amazon Web Service 的 Simple Email Service 內的 Email receiving 功能
    * 驗證網域
        * 為了確保你的信件可以透過 SES 處理，需要在 Domains 裡面 verify a new domain 
    * 建立 Rule Set
        * 選 Rule Sets 功能
        * Create a Rule Set
        * 在 Rule Set 裡面 Create Rule
        * 在 Recipient 指定你想要的收件信箱
            * 前一步驟 verify domain 的網域
        * Add Action 的部份指定 SNS
            * SNS 裡面選 Create SNS Topic
            * Action Encoding 選 Base64
        * 接下來一路確定到結束
        * 會到 Rule Sets 列表的地方，勾選你剛新增的 Rule Set，選 Set as Active Rule Set 才會啟用
    * 設定 SNS
        * 到 SNS 設定介面，選擇你前一步驟新增的 SNS Topic
        * Create Subscription
            * Protocol 選擇 https 或 http (建議 https)
            * Endpoint 輸入一個你想要在收到信時會通知的網址
            * 勾選 Enable raw message delivery
            * 按下 create subscription 按鈕
        * Confirm Subscription
            * AWS 要確定你的 endpoint 真的能收到通知，因此會對你的 endpoint 發一則 SubscriptionConfirmation，以 POST DATA 型式送出 JSON 格式資料，其中有個 SubscribeURL 值，只要打開這個連結就會確認成功，這個 Subscription 就會啟用。
            * 以 PHP 為例，只要在你的 endpoint 網址裡面的程式寫入如下，可以把確認網址寫入到特定地方，再去特定地方讀出網址，用自己的瀏覽器打開確認即可
                ```php
                    $post_data = file_get_contents('php://input');
                    $post_json = json_decode($post_data);
                    $url = $post_json->SubscribeURL;
                    file_put_contents('some-place', $url);
                ```
            * 如果你沒有成功記錄到 SubscribeURL 的話，在 Subscriptions 內可以選你的 subscription 並點選 Request confirmation 可以讓他重送一次

捐款確認後端程式
-------------
* 程式放在 https://github.com/ronnywang/jothon-donate-api
    * 詳細說明可見裡面 README
* 該程式是針對「neticrm 通知信格式」所開發，若是使用其他平台需要另外改寫
* 架設後請不要公開你的網址，以免被人直接偽造捐款通知
* 也不要將這 API 使用在公開對外的前端頁面上，以免惡意使用者可以透過 API 網址得到後端位置偽造捐款通知

捐款確認前端程式
-------------
* 程式放在 https://github.com/g0v/donate-checker
    * 詳細說明可見裡面 README
    * 預設串接 https://jothon-donate-test.ronny.tw/fake-donate-api.php 的 API，若想自行開發測試，步驟如下：
        * 開啟 https://g0v.github.io/donate-checker/index.html
        * 另外開啟 https://jothon-donate-test.ronny.tw/fake-donate.php ，在裡面輸入測試用的捐款資訊
        * 回去看看 index.html 有沒有跳出捐款通知
* 前端通知頁面是設計給 OBS 直播軟體使用
> 在OBS新增「瀏覽器」來源，輸入 https://g0v.github.io/donate-checker/ 即可
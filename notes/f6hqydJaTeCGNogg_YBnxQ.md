## 4
我們的系統名字叫做Bhitter，功能是統整銀行信用卡的優惠及利率的資訊，並使用LineBot和Website來呈現
這是我們的linebot可能會長的樣子，下面的按鈕是失憶寧之前設計的草圖，之後應該還會做更改

## 5
這是我們的系統的模組架構圖
我們將系統分為 linebot sever 及website這三個部分
linebot又可以再細分為 計算利率 NL自然語言處理 及linebot呈現 NLP底下則可以再分為NLP的套件與linebot串接和 nlp套件的相關設定
然後website的部分 分為 自動更新 資訊統整 和 網頁的呈現 自動更新底下又可以再分出 抓資料
然後這個紅色箭頭是指我們的資料流向 我們將各家銀行的資訊抓下來後 會先至website自動更新成最新資訊

## 7
抓資料的部分是使用beautifulsoup和pandas套件 油商肯豪、黃旻昱和詩意寧負責 商肯豪負責信用卡優惠的資料抓取、失憶寧負責沒有js的利率資料抓取、皇民籲負責有js的利率資料抓取

## 8
然後NLP套件與Linebot串接的部分就是由我跟淑貞負責
我們分別嚴借了兩種api 第一種是淑貞研究的dialogflow 第二種是我研究的olami 等等都會再詳細說明

## 9
接下來回答上次老師問的wordpress與heroku的差別
wordpress其實算是一個專門讓人架設部落格的網站，他提供一個後台來方便使用者管理他的網站外觀，並且擁有許多他人製作好的外掛及主體可以使用。他的好處就是即便是完全不會程式碼的人也能輕鬆建置自己的網站。然後他本身不具伺服器。
Heroku是一個雲端及平台服務，專門讓人放置他做好的網站。
所以說，Wordpress主要是讓你見老一個網站它的外關樣子，而Heroku則是讓你放置這個網站的地方
所以我們決定再Heroku上開伺服器然後連接至我們的網站跟LineBot

## 10
我們為什麼要使用Wordpress呢？第一因為他有很多外掛及模組可以讓我們直接用 然後他的使用者很多 全球約莫有四分之一的網站都使用wordpress，也因此他擁有的資源 也就是那些外掛及模組就很多 然後就是他很簡單 不會程式的人也能上手 這邊給老師看一歇使用wordpress的網站

## 11
我們為什麼要用heroku
因為他是免費的 並且他就長在雲端 所以我們不需要另外在自己架設伺服器
我們目前知道他的缺點就只有在一段時間不使用它 他會進入修眠狀態 要再啟動他他就會需要一點點時間 但我們有實際測試過 覺ㄉ還好不是很大的問題

## 20
這個系統就是方便開發者來管理他的聊天及回覆的工具，他是使用我剛剛說的OSL語言來自定義回覆的內容。在此系統中，我們可以建立模組來分類我們可能會得到的使用者輸入的文字。例如，假設我訂了一個模組叫做travel，此模組中可以定義許多關於travel的例句，例如，幫我查上海到北京的跟團遊，我要玩四天。OLAMI也有提供一些以建立好的公共模組給開發者使用。
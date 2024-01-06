---
title: "Excel 資料轉換工具"
tags: hackpad
---

# Excel 資料轉換工具

> [點此觀看原始內容](https://g0v.hackpad.tw/jkpco57DjJH)


之前 Peggy 提到有公務員有將單一個 Excel 的各分頁合成一個 CSV 的需求(各分頁的格式都一模一樣) ，但是除了人工一頁一頁複製貼上以外，不知道該怎麼處理。對會寫程式的人來說很好解決，但是會寫程式的人通常不用 Excel ，而會用 Excel 的人通常就是不會寫程式，因此這個專案的目的，是想要讓會寫程式的人，可以幫助公務員(或是其他 Excel 使用者) ，將一些常作的動作用程式解決。

> 補充一下背景：
> [name=羅佩琪]

> 1\. 在中央部會常會需要彙整「各縣市」的資料，[例如這種](http://www.hpa.gov.tw/BHPNet/Web/HealthTopic/TopicBulletin.aspx?No=201209200001&parentid=201110060002)，一個excel裡面有不同的sheet，分別就是台北市、新北市......等各縣市的資料。(我想像中縣市政府應該也有需要，要整理各區的資料等)
> [name=羅佩琪]


> 2\. 但是，如果要轉成開放資料，如果要直接轉成csv，目前excel或sheethub都只能一次存一個sheet，這樣的話的解法有兩個這樣的話的解法有兩個：
> [name=羅佩琪]

> (1) 存20次，把20個sheet分成20個資料集釋出 → 缺點：要處理20次、使用者也要處理20次
> [name=羅佩琪]

> (2) 用複製貼上，把不同sheet的資料內容貼到同一個sheet → 缺點：很容易出錯
> [name=羅佩琪]


> 3\. Ronny大大說：「合併不同sheet」這個功能應該30min就可以寫完...........XDDD 所以就產生這個專案了~~~
> [name=羅佩琪]

> 自己也寫了一個 [https://github.com/kiang/excel-merge-tool/blob/master/index.php](https://github.com/kiang/excel-merge-tool/blob/master/index.php) ，不過需要搭配  PHP 執行環境
> [name=Finjon K]


### 進行方式

統一整個專案都在 [https://github.com/g0v/excel-data-tool](https://github.com/g0v/excel-data-tool) 進行

需求者可以將自己的需求，寫一個 issue，希望能有什麼樣的小工具可以使用寫出來。
而認領者可以依照需求，將工具實作出來讓大家使用。

### 工具範例

[http://g0v.github.io/excel-data-tool/merge-sheets/](http://g0v.github.io/excel-data-tool/merge-sheets/)

### 可加上工具

- 合併儲存格拆解工具
- 樞紐分析表攤平工具
- Excel 格式乾淨度檢查程式
- 地址欄位透過 API 加上經緯度資訊程式



---
title: "Rails Girls 3rd Note"
tags: hackpad
---

# Rails Girls 3rd Note

> [點此觀看原始內容](https://g0v.hackpad.tw/6XVrKUuHEcx)

> 要不要 commit 到 [https://github.com/g0v/g0v.today](https://github.com/g0v/g0v.today) 讓大家可以跟著操作? :factory:
> [name=Audrey T]

> 需要分開 repo 嗎現在整個架構都不一樣惹 QQ
> [name=ET B]

> 不同的次目錄就好吧:question:
> [name=Audrey T]

> roger，那開一個 rails 目錄？
> [name=ET B]

> 突然發現你沒用到 master branch... 那當然就是放 master branch 啦 :+1:
> [name=Audrey T]

> 那樣要手動 merge 到 gh-pages 嗎？不過用 rails 以後 gh-pages 也不能動惹… QQ
> [name=ET B]

> 對啊所以才要放 master :8ball:
> [name=Audrey T]

> 好 ^o^
> [name=ET B]

> :dancers: :octocat:
> [name=Audrey T]

> 好像好了耶 @o@   :100: :smile_cat:
> [name=ET B]

> 似乎是裝完了... 軌道少女團的文件寫得真不錯
> [name=Audrey T]

> 而且只有大綱所以很有彈性，同一個教練教的組員之間進度可以完全不同… XD
> [name=ET B]

> rails server 會動了，之前沒有 git add bin/ (因為被上層目錄的 .gitignore 擋住)，現在修好了。
> [name=Audrey T]

> pulled! :octocat: 
> [name=ET B]

> :yellow_heart: 也太可愛了吧好多符號
> [name=ipa c]


### 安裝 Rails (Rails Girls 官方文件)

[http://railsgirls.tw/install/](http://railsgirls.tw/install/)

### 妳的第一個 Rails App (Rails Girls 官方文件)

[http://railsgirls.tw/app/](http://railsgirls.tw/app/)

### 安裝 slim-rails / semantic-rails / compass-rails / ...

依照官方文件打 gem 指令安裝
在 gemfile 加入官方文件的設定
指令 bundle install

### 使用 slim-rails

把 .html.erb 檔名改成 .html.slim

### 讓輸出的 html 排版便於 debug

slim pretty output: [http://stackoverflow.com/questions/17291030/rails-slim-source-output](http://stackoverflow.com/questions/17291030/rails-slim-source-output)
dev / production / test 三種不同環境有各自的最佳設定，比方說開發環境需要輸出好看的 html 方便 debug，但是上線環境不要，所以 slim pretty output 的設定只寫在 config > environment > development.rb 裡面

### 設定 css 檔案的順序

app/assets/stylesheets/application.css 中
 *= require 'semantic-ui'
> 開頭的 \*= 會被解讀成設定用的指令，如果把 \* 跟 = 中間加一個空白那就不會被執行
> [name=ET B]

 *= require 'global'
> 想要讓 global 蓋掉 semantic-ui 的話，要把 global 寫在後面
> [name=ET B]

 *= require_self
> 預設會有的，意思是 require 本檔案中這段註解結束後所寫的東西
> [name=ET B]

*= require_tree (相對路徑)
> 也是預設會有的，意思是抓取 (相對路徑) 目錄裡的所有檔案，依照檔名排序
> [name=ET B]

> 也因此會出現 semantic ui.css 蓋掉客製化的 global.css 的問題
> [name=ET B]

> 除非很知道自己在幹嘛，非常不建議使用這一行，建議用白名單，而非地圖砲
> [name=ET B]

 */
> css 註解結束
> [name=ET B]


### 設定 js 檔的順序

原理同上
//= require turbolinks
> rails 4 新功能，換頁時用 ajax 撈出想換的那一頁塞到這一頁裡面，不好掌控，會產生 data-turbolinks-track="true"  這段東西，不很知道幹嘛的話建議關掉
> [name=ET B]

> <script data-turbolinks-track="true" src="/assets/jquery_ujs.js?body=1"></script>
> [name=ET B]

> [http://geekmonkey.org/articles/28-introducing-turbolinks-for-rails-4-0](http://geekmonkey.org/articles/28-introducing-turbolinks-for-rails-4-0)
> [name=ET B]


### 更改專案名稱

folder name 直接改就可以了
code name 在 config > application.rb 裡面，通常習慣跟 folder name 一樣，但要分開也行…後來我放棄改 code name 了因為好像要改很多地方，怕爛掉 XD
> 改這個檔案要重跑 server
> [name=ET B]

> config 裡面的 env... app... 有改的話都要重開
> [name=ET B]

module G0vtoday
    config.time_zone = 'Taipei'
> 可以順便改個時區
> [name=ET B]

    config.i18n.default_locale = :"zh-TW"
> 可以順便設個 i18n 語系
> [name=ET B]


### 建立多對多關連

rails g migration (migration名稱，英文，字串，習慣用底線隔開，他會自動幫我們轉成 camel type)
> 會在db > migration 裡面新增一個 timestamp_name.rb 檔，空的
> [name=ET B]

到 _timestamp_name.rb 裡面_
  def change
    create\_table :sessions\_speakers do |t|
> 先寫 session 再寫 speaker 是因為 rails 的命名規則是按照字母順序排 ( se < sp )，否則他會找不到 table
> [name=ET B]

      t.references :session
      t.references :speaker
    end
  end
指令 rake db:migrate
> 把設定檔寫入 sqlite 資料庫中
> [name=ET B]

> migration （資料庫遷移）用來控制（新增欄位）跟紀錄（別人用同一個migration檔案可以跑出一樣的結果）資料庫的儲存格式，因為資料庫本身是被gitignore掉的，不然測試環境跟上線環境的資料會混在一起
> [name=ET B]

到 model > speaker.rb
  has\_and\_belongs\_to\_many :sessions
到 model > session.rb
  has\_and\_belongs\_to\_many :speakers
> 讓這兩個原有的 model 知道彼此的關連
> [name=ET B]


### migration

資料庫的設定檔
### rake db:migrate

讓 migration 設定檔生效
### model > xxx.rb

裡面放資料庫關連、自訂對資料庫的操作、驗證、儲存或刪除後要多做哪些事情(callback)
model 裡面純粹的 column 會自動對應到，所以增加欄位不用改，只有增加 relation 的時候需要額外改 model 的 .rb 檔

### 時段、子時段 (STI)

[http://blog.thirst.co/post/14885390861/rails-single-table-inheritance](http://blog.thirst.co/post/14885390861/rails-single-table-inheritance)

### 為什麼 rails new 以後要 bundle install


### 為什麼 bundle install 以後要 rake db:migrate


### 為什麼 rails generate scaffold 以後要 rake db:migrate


### class Xxxx < ActiveRecord::Base 的意思是…

class
- 以下鄭重宣布，有一個新品種 (的 ruby 物件) 要誕生了！
Xxxxx
- 新品種的名稱，開頭是大寫的英文字母
<
- 繼承
ActiveRecord::Base
- 功能是把 Xxxx 這個品種對應到資料庫中名為 xxxx 的資料表
::
- 在 AR 下面切一個命名空間出來


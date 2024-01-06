# Day 3 - 後端實作 & 前端初見面 

第一天有先建立了專案
第二天規劃了資料表

那今天目標就先以看到畫面來做收尾！

## 動手啦！
### Accounting

```bash
rails g model Accounting name amount:integer flow_type:integer ledger_id:integer
```

```
invoke  active_record
      create    db/migrate/20230918082505_create_accountings.rb
      create    app/models/accounting.rb
      invoke    test_unit
      create      test/models/accounting_test.rb
      create      test/fixtures/accountings.yml
```



### Ledger
同理生成即可

```bash
rails g model Ledger name amount:integer flow_type:integer
```

最後跑一下 `rails db:migtate`
(這邊 migrate 前手動改了一下 integer -> bigint，因為 command 不支援 bigint 

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d77f1dfc203871a4dc68802cd70c926b.png)


等一下！ 肖年a 記得用 Git 版控存檔！

另外自動生成很方便，但有注意到的話會發現 Rails 有幫忙做額外的事情
以 Test 的東西來說是目前不需要的，所以目前只會留下 Migration 跟 Model

----

## 下一步？
今天的目標可是要看到一點簡單的畫面啊！

所以下一步當然就是 MVC 中的 VC 啦

### Ledger

```bash
 rails g controller ledgers 
```
```bash
      create  app/controllers/ledgers_controller.rb
      invoke  erb
      create    app/views/ledgers
      invoke  test_unit
      create    test/controllers/ledgers_controller_test.rb
      invoke  helper
      create    app/helpers/ledgers_helper.rb
      invoke    test_unit
```

於是乎 Rails 又幫我把 View & Controller 做出來了

### Accounting
同理也把 Accounting 做出來
```bash
rails g controller accountings
```

然後隨意做一下 LedgersController 的 Index 求個畫面就好
```ruby
# app/controllers/ledgers_controller.rb

class LedgersController < ApplicationController
  def index; end
end
```

```html
# app/views/ledgers/index.html.erb

<div>Ledgers Index</div>
```

## 所以我說那個 Route 呢
因為是 CRUD，所以就先用 `resources` 套一個基本款的路徑給他就可以了 030

```ruby
# config/routes.rb

Rails.application.routes.draw do
  resources :ledgers
end
```

這樣就看到畫面啦！

![https://ithelp.ithome.com.tw/upload/images/20230918/20142040R1LYmSFKSs.png](https://ithelp.ithome.com.tw/upload/images/20230918/20142040R1LYmSFKSs.png)


明天就來針對 CRUD 做調整囉

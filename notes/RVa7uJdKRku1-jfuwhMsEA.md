# Day 8 - 我都唸 Devise，你呢？（一）
曾經有個專案剛好有 ｀Device｀ 的 ｀Model｀，跟同事在那邊繞了半天結果兩邊講的是不同東西，想起來是好氣又好笑，所以你都怎麼唸呢 ：）

今天的就要來利用 [Devise](https://github.com/heartcombo/devise) 來完成使用者的權限操控

## Devise 安裝
基於沒有要客製任何東西，實作 Devise 非常簡單！
原則上只要安照文件即可
要注意的是以往 Turbo 沒支援的情況已經在 4.9.0 的版本被解決了，有經歷過中間這段時期的人肯定理解其中的麻煩之處 :D

```
# Gemfile

gem 'devise', '~> 4.9', '>= 4.9.2'
```

```bash
bundle install
rails generate devise:install

# 生成 Devise 預設模板的 Model, 按慣例叫 User 即可
# 額外加一個 name 的欄位給他方便之後顯示用
rails generate devise User name:string

# 全部先長出全部模板，之後視情況調整
rails generate devise:views users 
```

這裡一直沒提 Migrate ，因為有關聯的部分需要加上去
```ruby
# db/migrate/

class AddUserIdToAccoutnings < ActiveRecord::Migration[7.0]
  def change
    add_column :accountings, :user_id, :bigint
  end
end


class AddUserIdToLedgers < ActiveRecord::Migration[7.0]
  def change
    add_column :ledgers, :user_id, :bigint
  end
end
```

```bash
rails db:migrate
```

這樣關於 Devise 的部分就算安裝完畢了

## 相依調整
安裝完之後肯定是需要針對整體關聯去做調整
接下來就是更新 model 關聯

```ruby
# app/models/accounting.rb

class Accounting < ApplicationRecord
  belongs_to :user
  belongs_to :ledger
  ...
end

# app/models/ledger.rb

class Ledger < ApplicationRecord
  belongs_to :user
  has_many :accountings
end
```

到這裡做完還差一步，前面這些實作上去之後，前端畫面因為送資料來後端時肯定不會帶著關聯需要的 `user_id`
所以這裡在 params 偷偷加上

```ruby
# app/controllers/accountings_controller.rb
# ledger 如法泡製

class AccountingsController < ApplicationController
  ...
  
  # 改取當前使用者的資料，這樣以後藉由 Devise 登入管控的 User 就會只拿到自己的資料囉
  def index
    @accountings_group_by_date =
      current_user.accountings
                  .includes(:ledger)
                  .order(created_at: :desc)
                  .group_by { |accounting| accounting.created_at.to_date }
  end
  
  ...
  
  def permit_params
    params[:accounting][:user_id] = current_user.id
    params.require(:accounting).permit(:name, :amount, :flow_type, :ledger_id, :user_id)
  end
  
  ...
end
```

最後一步就是更新 seed

```ruby
# db/seeds.rb
...
# 先隨便塞一下，方便開發
user = User.find_by(email: ...) || User.create(email: ..., name: ..., password: ...)
ledger = Ledger.find_or_create_by(..., user: user)

...

      Accounting.create!(...,
                         ...,
                         user: user)
 ...
end
```

然後重製一下資料庫的資料
```bash
# 清除資料重新跑 seed 塞資料
rails db:seed:replant
```

最後補充一下呢，因為到這裡為止都還是本地開發沒有上線，資料都隨便洗掉重來，不然其實在上 Migration 的步驟前會需要處理既有資料的部分，必須要當心

以上就是簡單套上 Devise 的部分

另外前面生成了大量的 View 模板還未作調整，再來就是套上 Devise 後的權限管理的流程也還未實際走過一次
明天就針對這部份來做完善！
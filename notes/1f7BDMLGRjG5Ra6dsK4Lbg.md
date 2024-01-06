# Day4 - Rails 初學必會！Let's CRUD!


本日目標為完成 `Ledger` 跟 `Accounting` 的 CRUD！

從昨天結束的地方接續開始！
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

## Create

首先，要造出一個帳戶，將昨天的畫面移除並新增到 Action new 的連結 

```html
# app/views/ledgers/index.html.erb

<%= link_to '新增帳戶', new_ledger_path %>
```

點擊之後就會發現出錯了

![https://ithelp.ithome.com.tw/upload/images/20230919/20142040ZCbUbIllaD.png](https://ithelp.ithome.com.tw/upload/images/20230919/20142040ZCbUbIllaD.png)


沒錯！根本還沒做 new 的 template，給他加上去

```html
# app/views/ledgers/new.html.erb

<%= form_with model: @ledger do |form| %>
  <%= form.label :name %>
  <%= form.text_field :name %>
  <%= form.submit '建立帳戶' %>
<% end %>
```

同時處理後端

```ruby

# app/controllers/ledgers_controller.rb

class LedgersController < ApplicationController
  def index; end
  
  def new
    @ledger = Ledger.new
  end
  
  def create
    @ledger = Ledger.new(permit_params)

    @ledger.save!
    redirect_to ledgers_path
  end
  
  private
  
  def permit_params
    params.require(:ledger).permit(:name)
  end
end
```
![https://ithelp.ithome.com.tw/upload/images/20230919/20142040OpQTquUFN0.png](https://ithelp.ithome.com.tw/upload/images/20230919/20142040OpQTquUFN0.png)

以上就完成 Ledgar 基本的 Create 了

## Read


```ruby

# app/controllers/ledgers_controller.rb

class LedgersController < ApplicationController
  def index
      @ledgars = Ledgar.all
  end
  
  ...
end
```

```html
# app/views/ledgers/index.html.erb

<%= link_to '新增', new_ledger_path %>

<ol>
  <% @ledgers.each do |ledger| %>
    <li>
      <div>
        <%= ledger.name %>
      </div>
    </li>
  <% end %>
</ol>
```

然後就可以做一個「現金餘額」的帳戶而且可以顯示囉

![https://ithelp.ithome.com.tw/upload/images/20230919/20142040tvxy5JUJe0.png](https://ithelp.ithome.com.tw/upload/images/20230919/20142040tvxy5JUJe0.png)


## Update
新增完成後就可以來做更新了

```ruby

# app/controllers/ledgers_controller.rb

class LedgersController < ApplicationController
  ...
 
  def edit
    @ledger = Ledger.find(params[:id])
  end

  def update
    @ledger = Ledger.find(params[:id])

    @ledger.update(permit_params)
    redirect_to ledgers_path
  end

  ...
end
```

```html
# app/views/ledgers/index.html.erb

<%= link_to '新增', new_ledger_path %>

<ol>
  <% @ledgers.each do |ledger| %>
    <li>
      <div>
        <%= ledger.name %>
        <%= link_to '編輯', edit_ledger_path(ledger) %>
      </div>
    </li>
  <% end %>
</ol>
```

```html
# app/views/ledgers/edit.html.erb

<%= form_with model: @ledger do |form| %>
  <%= form.label :name %>
  <%= form.text_field :name %>
  <%= form.submit '編輯帳戶' %>
<% end %>
```

![https://ithelp.ithome.com.tw/upload/images/20230919/20142040crdbW7flF5.png](https://ithelp.ithome.com.tw/upload/images/20230919/20142040crdbW7flF5.png)

![https://ithelp.ithome.com.tw/upload/images/20230919/20142040vR5PzopXgM.png](https://ithelp.ithome.com.tw/upload/images/20230919/20142040vR5PzopXgM.png)

## Delete

```ruby

# app/controllers/ledgers_controller.rb

class LedgersController < ApplicationController
  ...
 
  def destroy
    @ledger = Ledger.find(params[:id])
    @ledger.destroy
    redirect_to ledgers_path
  end

  ...
end
```



```html
# app/views/ledgers/index.html.erb

<%= link_to '新增', new_ledger_path %>

<ol>
  <% @ledgers.each do |ledger| %>
    <li>
      <div>
        <%= ledger.name %>
      </div>
      <%= link_to '編輯', edit_ledger_path(ledger) %>
      <%= link_to '刪除', ledger_path(ledger), data: { turbo_method: :delete } %>
    </li>
  <% end %>
</ol>
```

![https://ithelp.ithome.com.tw/upload/images/20230919/201420409Mf6jOZYpo.png](https://ithelp.ithome.com.tw/upload/images/20230919/201420409Mf6jOZYpo.png)

這裡要注意的點大概就是 Rails 7 之後 Turbo 已經變成預設取代 TurboLinks
所以 data 的屬性 `method` 要改為 `turbo_method`

----

以上先簡易的做出可操作的頁面，並把 `Accounting` 也一起完成

稍稍不一樣的地方是 Accounting 的後端開始碰到從屬關係，把關聯加上，`enum` 也順便一起處理
    
```ruby
# app/models/accounting.rb

class Accounting < ApplicationRecord
  belongs_to :ledger

  enum flow_type: { income: 0, expenditure: 1 }
end
```
```ruby
# app/models/ledger.rb

class Ledger < ApplicationRecord
  has_many :accountings
end
```


這樣今天就把基本的 CRUD 完成了

預計明天可以來豐富一下前端！

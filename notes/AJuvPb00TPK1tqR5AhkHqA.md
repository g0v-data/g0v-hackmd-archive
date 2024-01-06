# Day 6 - 拉皮工程（二）

## 玩轉 Hotwire

今天要來處理整個 `Accounting` 的拉皮，讓流程更加美觀

同時為了使流程順暢，順便加入 `Hotwire` 來整合 CRUD 的過程

說是加入，但 `Hotwire` 是 `Rails 7` 已預設的前端框架
也就是說，無須另外安裝

補充：這次沒有限定版本，所以工具與框架都是使用當下最新版

但這邊只會使用到 `Turbo` 的部分！

## 拆分零件！
### Create
因為預期在記帳首頁(Index)就可以新增一筆帳，所以原本新增頁(New)的部分就需要「借」畫面來使用

在借之前當然是要先刻出畫面

```
# app/views/accountings/new.html.erb

<%= form_with model: accounting, id: 'new_accounting', class:'grid grid-rows-1 grid-cols-3 w-1/3 mx-auto bg-gray-400 rounded-lg p-4 items-center text-black place-items-center gap-2' do |form| %>

  <%= form.label :ledger_id, class:'' %>
  <%= form.select :ledger_id, options_for_select(Ledger.all.pluck(:name, :id)), {}, class: 'w-full rounded-md col-span-2' %>

  <%= form.label :flow_type %>
  <%= form.select :flow_type, options_for_select([['收入', 'income'], ['支出', 'expenditure']]), {}, class: 'w-full rounded-md col-span-2' %>

  <%= form.label :name %>
  <%= form.text_field :name, class: 'w-full rounded-md col-span-2' %>

  <%= form.label :amount %>
  <%= form.number_field :amount, class: 'w-full rounded-md col-span-2' %>

    
  <%= form.submit '新增帳務', class:'col-span-3 bg-gray-500 mt-4 px-4 py-1 rounded-full text-green-300 w-1/2' %>
<% end %>
```

大概長這樣

![https://ithelp.ithome.com.tw/upload/images/20230921/20142040OKBgfUouy6.png](https://ithelp.ithome.com.tw/upload/images/20230921/20142040OKBgfUouy6.png)

接下來要拆出去變成 partial，因為 Index 會來借這個畫面
同時兩邊的 ID 對應到之後，之後再填完表單送出後的更新也需要它來重置畫面

```
# app/views/accountings/_new_form.html.erb

<%= form_with model: accounting, id: 'new_accounting', class:'...' do |form| %>
    ...
<% end %>
```

```
# app/views/accountings/index.html.erb

<%= turbo_frame_tag 'new_accounting' do %>
  <%= render "new_form", accounting: Accounting.new %>
<% end %>

...
...
```

### Read
這邊有先稍微重新調整一下帳務首頁的設計，然後先抽出 Partial 降低重複性
```
# app/views/accountings/_accounting_row.html.erb

# 單筆帳務
<%= turbo_frame_tag dom_id(accounting) do %>
  <div class="grid grid-cols-5 gap-1">
    <div>
      <div class="bg-gray-500 px-4 py-1 rounded-full text-orange-300 w-1/2">
        <%= link_to '編輯', edit_accounting_path(accounting) %>
      </div>
    </div>
    <div>
      <div class="bg-gray-500 px-4 py-1 rounded-full text-red-300 w-1/2">
        <%= link_to '刪除', accounting_path(accounting), data: { turbo_method: :delete } %>
      </div>
    </div>
    <div><%= accounting.ledger.name %></div>
    <div class="text-right"><%= accounting.name %></div>
    <div class="text-right"><%= symbol_amount(accounting) %></div>
  </div>
<% end %>
```

```
# app/views/accountings/_daily_accountings.html.erb

# 單日帳務
<div id="<%= date.strftime %>" >
  <div class="grid grid-cols-3 h-10 items-center">
    <div class="bg-white h-px w-full"></div>
    <div class="bg-white h-px w-full"></div>
    <div class="flex items-center justify-center w-full text-center">
      <div class="w-2/4"><%= date %></div>
      <div class="w-1/4 bg-white h-px"></div>
      <div class="w-1/4 text-right <%= total.positive? ? 'text-green-400' : 'text-red-400' %>"><%= number_to_currency(total, precision: 0) %></div>
    </div>
  </div>
  <div class="grid text-center gap-1">
    <% accountings.each do |accounting| %>
      <%= render 'accounting_row', accounting: accounting %>
    <% end %>
  </div>
</div>
```

```
# app/views/accountings/index.html.erb

<%= turbo_frame_tag 'new_accounting' do %>
  <%= render "new_form", accounting: Accounting.new %>
<% end %>

<div class="w-2/3 mx-auto">
  <% @accountings_group_by_date.each do |date, accountings| %>
    <%= render 'daily_accountings', date: date,
                                    accountings: accountings,
                                    total: daily_sum(accountings) %>
  <% end %>
</div>
```

除了能將帳務首頁整理得乾淨一些，在這邊可也順便顯示的規則建立起來
1. 以日為單位
2. 以帳務日期降冪排列

```ruby
# app/controllers/accountings_controller.rb

  ...
    
  def index
    @accountings_group_by_date =
      Accounting.order(created_at: :desc)
                .group_by { |accounting| accounting.created_at.to_date }
  end
  
  ...
```

畫面大概會長這樣

![https://ithelp.ithome.com.tw/upload/images/20230921/20142040kbLIxZqiny.png](https://ithelp.ithome.com.tw/upload/images/20230921/20142040kbLIxZqiny.png)

這邊要來整理一下後端讓剛剛前端抽出來的 Partial 跟 ID 能充分作用

```ruby
 # app/controllers/accountings_controller.rb

  ...

  def create
    @accounting = Accounting.new(permit_params)

    if @accounting.save
      date = @accounting.created_at.to_date
      render action: :create_success, 
             locals: { 
               date: date, 
               accountings: Accounting.by_date(date)
             }
    end
  end
  
  ...
```

這邊在成功建立一筆新的帳務之後，會去 render 名為 `create_success` 的 turbo_stream.erb

而這個 partial 就是用 Turbo Stream 來幫我更新畫面

```
# app/views/accountings/create_success.turbo_stream.erb

# 刷新新增表單
<%= turbo_stream.replace('new_accounting', partial: 'new_form', 
                                           locals: { accounting: Accounting.new }) %>
                                           
<% if accountings.size == 1 %>
  # 如果這是今天第一筆帳，則新增本日的區塊（包含第一筆帳）
  <%= turbo_stream.prepend('accountings_area', partial: 'daily_accountings',
                                               locals: {
                                                 date: date, 
                                                 accountings: accountings,
                                                 total: daily_sum(accountings) 
                                               }) %>
<% else %>
  # 如果不是今天第一筆帳，就更新本日區塊
  <%= turbo_stream.update(date.strftime, partial: 'daily_accountings',
                                         locals: {
                                           date: date, 
                                           accountings: accountings,
                                           total: daily_sum(accountings) 
                                         }) %>
<% end %>

```

雖然只是從無到生出第一筆帳的小小動作，但各處都必須互相配合
而且 `Turbo` 的 `Error` 在開發的過程，有時不是那麼好懂，會花上不少時間理解，所以今天就先做到這邊
明天繼續 UD 的部分


# Day 7 - 拉皮工程（三）

接續昨天的進度，已經完成 `Create` 跟 `Read`，今天來把 `Update` 跟 `Delete` 完成

開始前先補充一下昨天有先做的 `scope` ，拿來找當天的帳務

```ruby
 # app/models/accounting.rb

  scope :by_date, ->(date) do
    begin_time = date.beginning_of_day
    end_time = date.end_of_day
    where("created_at BETWEEN ? AND ?",  begin_time, end_time).order(created_at: :desc)
  end
```


### Update
因為想做到停留在原地單獨編輯，就會需要做到每一列跟編輯頁的替換，所以這邊先刻一個類似「帳務列」的編輯頁
```
# app/views/accountings/edit.html.erb

<%= turbo_frame_tag dom_id(@accounting) do %>
  <%= form_with model: @accounting do |form| %>
    <div class="grid grid-cols-5 gap-1 text-black">
      <div>
        <div class="bg-gray-500 px-4 py-1 rounded-full text-white w-1/2">
          <%= link_to '返回', accountings_path %>
        </div>
      </div>
      <div>
        <div class="bg-gray-500 px-4 py-1 rounded-full text-orange-300 w-1/2">
          <%= form.submit '修改' %>
        </div>
      </div>
      <div><%= form.select :ledger_id, options_for_select(Ledger.all.pluck(:name, :id)), {}, class: 'w-full rounded-md' %></div>
      <div class="text-right"><%= form.text_field :name, class: 'w-full rounded-md' %></div>
      <div class="text-right"><%= form.number_field :amount, class: 'w-full rounded-md' %></div>
    </div>
  <% end %>
<% end %>

```

大概會是這樣子

![https://ithelp.ithome.com.tw/upload/images/20230922/20142040WEtEfuiDFK.png](https://ithelp.ithome.com.tw/upload/images/20230922/20142040WEtEfuiDFK.png)

這個時候因為前面已經抽出來的 `accounting_row` 有 ID 的對應，點擊編輯連結就可以產生效果去達到替換

![https://ithelp.ithome.com.tw/upload/images/20230922/20142040MDOera4mFy.png](https://ithelp.ithome.com.tw/upload/images/20230922/20142040MDOera4mFy.png)

```ruby
# app/controllers/accountings_controller.rb

# @accounting 已經抽出 before_action 去 find 了
...
def update
  if @accounting.update!(permit_params)
    render turbo_stream: turbo_stream.update(dom_id(@accounting), 
                                             partial: 'accounting_row',
                                             locals: { accounting: @accounting })
  end
end
...
```

如此一來，更新成功後就能借用 `accounting_row` 重新渲染，在帳務首頁完成帳務更新

### Delete
這步跟 `Create` 差不多，在刪除之後要考慮當天是否還有帳務的情境
沒有的話就必須將日期總金額也移除
有的話只需要刪除單列
因為沒有畫面就直接切入後端

```ruby
# app/controllers/accountings_controller.rb

# @accounting 已經抽出 before_action 去 find 了
...
def destroy
  return unless @accounting.destroy

  date = @accounting.created_at.to_date
  accountings = Accounting.by_date(date)
  dom_id = date.strftime
  if accountings.size.positive?
    render turbo_stream: turbo_stream.update(dom_id, partial: 'daily_accountings',
                                                     locals: {
                                                       date: date, 
                                                       accountings: accountings,
                                                       total: daily_sum(accountings) 
                                                     })
  else
    render turbo_stream: turbo_stream.remove(dom_id)
  end
end
...
```

這樣處理完之後呢，就可以不跳頁的情況下更新所有帳務啦

基本上最複雜的就是 `Accounting`，`Ledgar` 相比之下容易得多，所以基本上比照辦理
![https://ithelp.ithome.com.tw/upload/images/20230922/201420404cLdgFesP1.png](https://ithelp.ithome.com.tw/upload/images/20230922/201420404cLdgFesP1.png)
![https://ithelp.ithome.com.tw/upload/images/20230922/20142040eR1IT6WN9L.png](https://ithelp.ithome.com.tw/upload/images/20230922/20142040eR1IT6WN9L.png)

這樣本日進度就結束啦！

明天預計開始導入 Devise 做使用者管理！
# Day 5 - 拉皮工程（ㄧ）

## 前置作業
工具的部分選擇用 `TailwindCSS`

至於用的理由？
**簡單**、**粗暴**、**隨寫隨到**
~~還有平常用的習慣~~

基本上，參照 [TailwindCSS官方文件](https://tailwindcss.com/docs/guides/ruby-on-rails) 就可直接安裝，開箱即用，不會需要做特別的設定
所以安裝的步驟就不贅述了

工具就準備好了，下一步！

## 動土大吉！
首先先切出本應用的靈魂 `Accounting#Index` 的介面
實際上也沒有太複雜，~~但九成的時間都在想該長什麼樣子~~
最後規劃成以天為基數的呈現，所以在後端把 accountings 給 group 起來了

```html
<div class="h-20 w-full flex items-center justify-center">
  <div class="bg-gray-500 px-4 py-1 rounded-full text-green-300">
    <%= link_to '新增', new_accounting_path %>
  </div>
</div>

<div class="w-2/3 mx-auto ">
  <% @accountings_group_by_date.each do |date, accountings| %>
    <% daily_total = daily_sum(accountings) %>
    <div>
      <div class="grid grid-cols-3 text-center h-10">
        <div></div>
        <div></div>
        <div class="row-span-2 flex items-cneter justify-center self-center divide-x w-full text-center">
          <div class="w-2/3"><%= date %></div>
          <div class="w-1/3 text-right <%= daily_total.positive? ? 'text-green-400' : 'text-red-400' %>"><%= number_to_currency(daily_sum(accountings), precision: 0) %></div>
        </div>
        <div class="border-t"></div>
        <div class="border-t"></div>
      </div>
      <div class="grid grid-cols-5 text-center gap-1">
        <% accountings.each do |accounting| %>
          <div>
            <div class="bg-gray-500 px-4 py-1 rounded-full text-white text-orange-300 w-1/2">
              <%= link_to '編輯', edit_accounting_path(accounting) %>
            </div>
          </div>
          <div>
            <div class="bg-gray-500 px-4 py-1 rounded-full text-white text-red-300 w-1/2">
              <%= link_to '刪除', accounting_path(accounting), data: { turbo_method: :delete } %>
            </div>
          </div>
          <div><%= accounting.ledger.name %></div>
          <div class="text-right"><%= accounting.name %></div>
          <div class="text-right"><%= symbol_amount(accounting) %></div>
        <% end %>
      </div>
    </div>
  <% end %>
</div>
```


對，又臭又長，有時候超過螢幕長度折行還不好看，還有有畫面雜亂的問題，又若都拉去 SCSS 管理會失去直接在畫面寫的好處，最後還是得做一些取捨

但整體而言個人還是喜好大於厭惡的

----

接著途中為了畫面呈現也造了 Helper

```ruby
module AccountingHelper
  def daily_sum(accountings)
    accountings.reduce(0) do |start, accounting|
      amount = accounting.amount
      amount *= -1 if accounting.expenditure?
      start + amount
    end
  end

  def symbol_amount(accounting)
    amount = accounting.amount
    symbol = accounting.income? ? '+' : '-'

    number_to_currency(amount, unit: symbol, precision: 0)
  end
end

```

----

同時因為畫面空空需要資料，暫時在建造一些假資料

```ruby
# db/seeds.rb

EXPENDITURE = %w[吃飯 飲料 購物 交通 房屋租金 孝親].freeze
INCOME = %w[薪資 利息 發票中獎 彩券中獎].freeze
TYPES = Accounting.flow_types.keys
BEFORE_DAYS = 7
MAX_ITEMS = 10
MAX_AMOUNT = 200
ledger = Ledger.find_or_create_by(name: '現金餘額')

BEFORE_DAYS.times do |n|
  time = Time.zone.now - n.day
  
  rand(MAX_ITEMS).times do
      type = TYPES.sample

      Accounting.create!(name: type.upcase.constantize.sample,
                         amount: rand(MAX_AMOUNT),
                         flow_type: type,
                         created_at: time,
                         ledger: ledger)
  end
end
```


----

## 本日成品

![https://ithelp.ithome.com.tw/upload/images/20230920/201420401vR5CfaanV.png](https://ithelp.ithome.com.tw/upload/images/20230920/201420401vR5CfaanV.png)

今天先這樣吧（汗
基於~~時間管理不善~~，所以寫的比較急不見得有經過大腦，就請多海涵，之後有空檔在來整理 (大概不會有?


明天預計會繼續來切相關的頁面，以上！
# Day 14 - 在少少的戶頭裡轉呀轉呀轉（一）


沒錯，今天要來做「轉帳」的功能，畢竟一個人不會只有一個帳戶。如果每一筆都要從 A帳戶支出 到 B帳戶收入，大概會是一件非常惱人的事情。所以緊接著要來做帳戶內部的金流移動！

## 功能
首先要來確認這個 「內轉」的機制要做到什麼樣的程度
1. 能自主辨識支出的對象為自己的帳戶
2. 自動生成一筆對應的「收入」
3. 要自動刪除對應的收支

以上就是初步的規劃，但達成需要一些方式與配合，可預期會需要一個 `ServiceObject` 來處理轉帳的問題

## ServiceObject
這裡預期會讓這個 Service 處理所有新增帳務與內轉的功能，所以需要做 `transfer?` 的判斷
前面也希望自動辨識對象，所以填入支出對象為本身的帳戶時視為轉帳，也就是說只要本身的帳戶有這個名稱就是轉帳的流程

```ruby
# app/services/accounting_process_service.rb

class AccountingProcessService
  attr_reader :accounting

  def initialize(accounting)
    @accounting = accounting
  end

  def perform; end

  private

  def transfer?
     transfer_leger.present?
  end
  
  def transfer_leger
    @transfer_leger ||= accounting.user.ledgers.find_by(name: accounting.name)
  end
end
```

接著開始做 `perform` 的部分，同時要完成「支出對應 A 帳戶，此時 B 帳戶也要一筆對應的收入」

要用 `transaction` 處理失敗要全部 rollback 的部分

```ruby
# app/services/accounting_process_service.rb

class AccountingProcessService
  attr_reader :accounting

  def initialize(accounting)
    @accounting = accounting
  end

  def perform
    if transfer?
      Accounting.transaction do
        transfer_accounting = build_transfered_accounting
        accounting.name = identify_name(accounting)

        transfer_accounting.save && accounting.save
      end
    else
      accounting.save
    end
  end

  private

  def transfer?
     transfer_leger.present?
  end
  
  def transfer_leger
    @transfer_leger ||= accounting.user.ledgers.find_by(name: accounting.name)
  end
  
  def transfer_flow_type
    @transfer_flow_type ||= TRANS_FLOW_TYPE_MAP[accounting.flow_type.to_sym]
  end
  
  # 方便辨認生成收支的兩筆紀錄
  def identify_name(accounting)
    type_wording = accounting.income? ? "From" : "To"

    "#{type_wording} #{accounting.name}"
  end
  
  def build_transfered_accounting
    transfer_accounting = accounting.dup
    transfer_accounting.flow_type = transfer_flow_type
    transfer_accounting.ledger = transfer_leger
    transfer_accounting.name = accounting.ledger.name
    transfer_accounting.name = identify_name(transfer_accounting)
    transfer_accounting
  end
end
```

這樣就先完成 Create 的部分，接著要處理 Controller / View 的微調
```
# app/controllers/accountings_controller.rb

class AccountingsController < ApplicationController
   
  ...

  def create
    @accounting = Accounting.new(permit_params)
    date = Date.current
    before_create_accountings = current_user.accountings.by_date(date).size
    sevice = AccountingProcessService.new(@accounting) # 主要改動，統一從 service 新增
    
    if sevice.perform
      render action: :create_success, 
             locals: { 
               date: date,
               prepend_partial: before_create_accountings.zero?,
               accountings: current_user.accountings.by_date(date)
             }
    end
  end
  
  ...
end
```

```
<%= turbo_stream.replace('new_accounting', partial: 'new_form', locals: { accounting: Accounting.new }) %>

<% if prepend_partial %> # 因應新增比數為兩筆，之前的判斷條件不合格了，稍做修正
  <%= turbo_stream.prepend('accountings_area', partial: 'daily_accountings',
                                               locals: {
                                                 date: date, 
                                                 accountings: accountings,
                                                 total: daily_sum(accountings) 
                                               }) %>
<% else %>
  <%= turbo_stream.update(date.strftime, partial: 'daily_accountings',
                                         locals: {
                                           date: date, 
                                           accountings: accountings,
                                           total: daily_sum(accountings) 
                                         }) %>
<% end %>
```

這樣處理完就可以產生下面的結果囉

![https://ithelp.ithome.com.tw/upload/images/20230929/20142040cnkdvkxOuj.png](https://ithelp.ithome.com.tw/upload/images/20230929/20142040cnkdvkxOuj.png)


刪除的部分 `Service` 應該無法單獨實作出想要的樣子，考量到設計的問題，所以改動會稍微多一點
只好明天再來處理，今天就先告一段落！
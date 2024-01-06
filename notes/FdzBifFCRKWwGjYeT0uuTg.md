# Day 19 - 開啟被動收入(四)

昨天已經將 `MpgInfo` 完成到只剩下 `Security` 還沒實作的狀態，再繼續之前，想先確認 `MpgInfo` 的屬性是否跟前端的 form 合用，所以先來設計一下 Controller 跟 View

因為價格是公開的有沒有登入都要可以看，所以要跳過認證使用者
```
# app/controllers/plans_controller.rb

class PlansController < ApplicationController
  skip_before_action :authenticate_user!, only: :price

  def price
    @mpg_infos = Plan.all.map do |plan| 
      Newebpay::MpgInfo.new(plan: plan, user: current_user)
    end
  end
end
```

```
# app/views/plans/price.html.erb

<div class="flex gap-4 items-center justify-center pt-12">
  <% @mpg_infos.each do |info| %>
    <div class="flex flex-col gap-4 items-center w-40 bg-gray-400 rounded-lg p-4">
      <div>方案： <%= info.name %></div>
      <div>價格： <%= info.price %></div>
      <%= form_with url: info.request_url, method: info.request_method do |form| %>
        <%= form.hidden_field :MerchantID, value: info.merchant_id %>
        <%= form.hidden_field :TradeInfo, value: info.trade_info %>
        <%= form.hidden_field :TradeSha, value: info.trade_sha %>
        <%= form.hidden_field :Version, value: info.api_version %>
        <%= render ButtonComponent.new(display_type: :green).with_content('購買') %>
      <% end %>
    </div>
  <% end %>
</div>
```

這樣就確定能看到畫面且表單送出後能確實打到藍星測試站，只是還沒做好加密內容所以不會成功

![https://ithelp.ithome.com.tw/upload/images/20231004/20142040dBUjuG9IT0.png](https://ithelp.ithome.com.tw/upload/images/20231004/20142040dBUjuG9IT0.png)

接著希望設定可以根據環境變化，原本是寫在 `MpgInfo` 的常數，這裡使用 [config](https://github.com/rubyconfig/config) gem 來做這個設定

把各種設定挪進去 `Settings`

```
# config/settings/development.yml

mpg:
  request_url: ...
```

```
# config/settings.yml

mpg:
  api_version: ...
  merchant_id: ...
```

透過 `delegate` 簡化可以更直接取用

```
# app/services/newebpay/mpg_info.rb

module Newebpay
  class MpgInfo
    attr_accessor :plan, :user

    delegate :name, :price, to: :plan
    delegate :id, :email, to: :user, prefix: true
    delegate :merchant_id, :api_version, :request_url,
             :return_url, :notify_url, :client_back_url, to: 'Settings.mpg'

    def initialize(plan:, user:)
      @plan = plan
      @user = user
    end

    ...

    def request_method
      'POST'
    end

    private

    ...

    def build_trade_info
      {
        MerchantID: merchant_id,
        RespondType: 'JSON',
        TimeStamp: time_stamp.to_i,
        Version: api_version,
        MerchantOrderNo: build_order_number,
        Amt: price,
        ItemDesc: name,
        ReturnURL: return_url,
        NotifyURL: notify_url,
        ClientBackURL: client_back_url,
        Email: user_email,
        LoginType: 0,
        WEBATM: 1,
        VACC: 1,
        CVS: 1,
        BARCODE: 1,
      }.compact
    end

    ...
  end
end
```

這樣之後只需在 Yaml 設定需要的資料即可！
明天來做 `Security` 完成之後就可以試打金流了
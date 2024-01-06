# Day 22 - 開啟被動收入(七)

昨天解完密之後，要開始拿資料做點事情啦！

這邊按照文件說明， `notify_url` 會期望我們再回應 http status `200`，不然會重試三次

```
class ApiController < ActionController::API
  def mpg_pay_notify
    head :ok
  end

  ...
end
```

而且依照觸發順序 `notify_url` 會是第一個被打的位置，所以這邊可以針對回傳的加密結果做一個初步處置
也就是建立訂單！

這一步建立的訂單還是未確認狀態，需要做二次確認

~~這裡還應該要有 Log 儲存起來，但礙於篇幅就先跳過ㄌ~~

```
# app/controllers/api_controller.rb

class ApiController < ActionController::API
  def mpg_pay_notify
    Order.create(order_attr(processor)) if processor.success?
	
    head :ok
  end

  private

  def order_attr(processor)
    {
      number: processor.result['MerchantOrderNo'],
      amount: processor.result['Amt'],
      state: 'uncheck',
      plan_id: processor.plan_id,
      user_id: processor.user_id
    }
  end
end
```

緊接著顧客刷完卡通過藍星處理完後，會打來 '/check_order' 

```
class ApiController < ActionController::API
  ...
  
  def check_order
    if processor.success?
      sign_in User.find(processor.user_id) 
      Order.find_by(number: processor.result['MerchantOrderNo'])&.paid!
    end

    redirect_to root_path, notice: processor.message
  end

  ...
end
```

確認完之後訂單就算正式成立了
接著根據訂單要來調整使用者可以使用的時間，至少會需要
1. 訂單購買的時長
2. 訂單成立的時間
3. 一個計算時間的 Service

訂單買的時長應該要根據 Plan 的設定，之前還沒設計到這邊，所以增加兩欄位

```
  def change
    add_column :plans, :service_amount, :integer
    add_column :plans, :service_type, :integer
  end
```

另外訂單成立時間就以訂單成功付款的時間為依據，所以也新增欄位

```
  def change
    add_column :orders, :pay_time, :datetime
  end
```

然後修正一下接收通知的地方

```
# app/controllers/api_controller.rb

class ApiController < ActionController::API
  def mpg_pay_notify
    Order.create(order_attr(processor)) if processor.success?
	
    head :ok
  end

  private

  def order_attr(processor)
    {
      number: processor.result['MerchantOrderNo'],
      amount: processor.result['Amt'],
      pay_time: processor.result['PayTime'],
      state: 'uncheck',
      plan_id: processor.plan_id,
      user_id: processor.user_id
    }
  end
end
```

有了 `pay_time` 跟可以計算週期的 `service_amount` / `service_type`
就可以來計算了

處理一下方便等一下計算

```
# app/models/plan.rb

class Plan < ApplicationRecord
  enum service_type: { day: 0, month: 1, year: 2, infinity: 3 }

  def period
    service_amount.send(service_type)
  end
end
```

先將之前關於顯示服務的地方修正並開個洞

```
# app/helpers/application_helper.rb

module ApplicationHelper
  def current_service_info
    return '尚未購買方案' if current_user.orders.paid.blank?

    service = PeriodCalculatorService.new(current_user.id)
    period = service.period_range
    period_range = if service.end == Float::INFINITY
      "終身"
    else
      "#{period.begin.strftime("%y/%m/%d")} ~ #{period.end.strftime("%y/%m/%d")}"
    end

    "服務期間： #{period_range}"
  end
end
```

也就是預期送入使用者 ID 可以取得使用者的使用區間

```
# app/services/period_calculator_service.rb

class PeriodCalculatorService
  def initialize(user_id)
    @user_id = user_id
  end

  def period_range
    @period_range ||= build_period_range
  end

  private

  def user
    @user ||= User.find_by(id: @user_id)
  end

  def build_period_range
    user.orders.paid.each do |order|
      plan = order.plan
      
      @begin_time = order.pay_time if @begin_time.nil? || Time.zone.now > @end_time

      break @end_time = Float::INFINITY if plan.infinity?

      if @end_time.nil?
        @end_time = @begin_time + plan.period 
      else
        @end_time += plan.period
      end
    end

    @begin_time..@end_time
  end
end
```

當然這會在數據變大的時候有效能問題，但先做出來比較重要：Ｄ

以上，關於金流的部分就結束了
明天就開始準備部署吧～

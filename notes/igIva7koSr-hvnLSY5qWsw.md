# Day 21 - 開啟被動收入(六)

昨天已經玩到可以送出表單讓使用者刷卡，那麼就要來處理回來的資料
等等！啊打回來卻因為還沒部署沒有 URL 怎麼讓人打過來呢！
有很多工具可以用，但今天就先選擇 [ngrok](https://ngrok.com/) 吧

安裝就不細說了，重點還是放在處理回傳資訊上

先生成一個 URL 放入之前已經設定好的 Settings 中，還沒有生成路徑，一個一個來處理

分別是 `return_url`, `notify_url`, `client_back_url`

## client_back_url
`client_back_url` 是如果使用者要不付款直接回來，會在藍星畫面上給他一顆按鈕導回網站

這裡就假設是想考慮一下換別的方案，就放回來 price 的頁面，所以路徑設定為 `/price`
之前已經在 `MpgInfo` 放好直接取用 `Settings` 的設定值，直接加上 Key value 即可

```
# config/settings/development.yml

mpg:
  request_url: https://ccore.newebpay.com/MPG/mpg_gateway
  client_back_url: http://.../price
```

很簡單就搞定了

## return_url

而 `return_url` 則是付款完成後藍星會以 `POST` 打回來的地方，開一個路徑來確認回來的資訊解密並創建訂單

```
# config/settings/development.yml

mpg:
  request_url: https://ccore.newebpay.com/MPG/mpg_gateway
  client_back_url: http://.../price
  return_url: http://.../check_order
```


## notify_url

最後還有一個 `notify_url` ，這裡可以做其他觸發或是驗證

```
# config/settings/development.yml

mpg:
  request_url: https://ccore.newebpay.com/MPG/mpg_gateway
  client_back_url: http://.../price
  return_url: http://.../check_order
  notify_url: http://.../mpg_pay_notify
```

接下來將對應的路徑設定完成

```
# config/routes.rb

Rails.application.routes.draw do
  ...
  
  get '/price', to: 'plans#price'
  post '/check_order', to: 'api#check_order'
  post '/mpg_notify', to: 'api#mpg_pay_notify'
end
```

如此一來就能接到來自藍星的 response，並針對其結果做處置

## 解密解密解密！

先做 Controller 的前置設定
```
# app/controllers/api_controller.rb

class ApiController < ActionController::API
  def mpg_pay_notify; end
  
  def check_order; end

  private

  def processor
    @processor ||= Newebpay::ResponseProcessor.new(permit_api_params)
  end

  def permit_api_params
    params.permit(:Status, :MerchantID, :Version, :TradeInfo, :TradeSha)
  end
end
```

處理送回來的加密資料，還是得靠 `Security` 解密，

```
# app/services/newebpay/response_processor.rb

module Newebpay
  class ResponseProcessor
    attr_reader :params

    def initialize(params)
      @params = params
    end

    private

    def data
      @data ||= Security.aes_decode(params[:TradeInfo])
    end
  end
end
```

而前面已經了解加密流程了，解密也就是倒著往回，所以先解開十六進制壓碼，然後解密得到 AES256 加密過的結果

```
# app/services/newebpay/security.rb

module Newebpay
  class Security
    class << self
   
      def aes_encode(data)
        cipher = aes_processor(:encrypt)
        padding_data = fill_padding(data)
        encrypted_data = cipher.update(padding_data) + cipher.final
        encrypted_data.unpack('H*').first
      end

      def aes_decode(encoded_data)
        decipher = aes_processor(:decrypt)
        decoded_data = [encoded_data].pack('H*')
        decrypted_data = decipher.update(decoded_data) + decipher.final
        ...
      end

      private

      # 跟加密差不多，就抽出來了方便切換
      def aes_processor(mode)
        processor = OpenSSL::Cipher.new('AES-256-CBC')
        processor.send(mode)
        processor.key = key
        processor.iv = iv
        processor.padding = 0
        processor
      end

      ...
    end
  end
end
```

下一步處理填充物，規則是最後一組紀錄著被填充了多少，所以取最後一個出來轉回數字，再從原始資料從頭取到填充物前，再解析出來就能得到回傳的資料囉

```
module Newebpay
  class Security
    class << self
   
      ...

      def aes_decode(encoded_data)
        ...
  
        strip_padding(decrypted_data)
      end

      private

      def strip_padding(data)
        padding_amount = data.last.ord
        json_data = data(0...-padding_amount)
        JSON.parse(json_data)
      end

      ...
    end
  end
end
```

回到 `Newebpay::ResponseProcessor`，把他做完整，之後在 Controller 好使用

```
# app/services/newebpay/response_processor.rb

module Newebpay
  class ResponseProcessor
    attr_reader :params, :user_id, :plan_id

    def initialize(params)
      @params = params
      @user_id = parsed_order_number[1]
      @plan_id = parsed_order_number[2]
    end

    def success?
      success_status? && correct_merchant_id? && correct_version?
    end

    def message
      data['Message']
    end

    def result
      @result ||= data['Result']
    end

    private

    def data
      @data ||= Security.aes_decode(params[:TradeInfo])
    end

    def parsed_order_number
      @parsed_order_number ||= result['MerchantOrderNo'].split('_')
    end

    def success_status?
      data['Status'] === 'SUCCESS'
    end

    def correct_merchant_id?
      result['MerchantID'] === Settings.mpg.merchant_id
    end

    def correct_version?
      params[:Version] === Settings.mpg.api_version
    end
  end
end
```

到這邊為止算是把金流的加解密都走完一遍（累
明天來把解完密的資料加以利用，來完成整套金流的來回，~~就能正式收到錢錢啦~~
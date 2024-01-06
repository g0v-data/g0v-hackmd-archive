# Day 18 - 開啟被動收入(三)

昨天做完還缺 `trade_info` & `trade_sha`
今天繼續完成 `Newebpay::MpgInfo`

## trade_info
根據文件需要塞入各種交易資訊

```
def build_trade_info
  {
    MerchantID: merchant_id,
    RespondType: 'JSON',
    TimeStamp: time_stamp.to_i,
    Version: api_version,
    MerchantOrderNo: build_order_number,
    Amt: plan.price,
    ItemDesc: plan.name,
    ReturnURL: ENV['MPG_RETURN_URL'],
    NotifyURL: ENV['MPG_NOTIFY_URL'],
    ClientBackURL: ENV['MPG_CLIENT_BACK_URL'],
    Email: user.email,
    LoginType: 0,
    WEBATM: 1,
    VACC: 1,
    CVS: 1,
    BARCODE: 1,
  }
end
```

這裡需要 `email`，所以 `initialize` 的時候塞入 `user`， `name` 跟 `price` 也改成帶入 `plan`，方便一些


```
module Newebpay
  class MpgInfo
    attr_accessor :plan, :user

    ...

    def initialize(plan:, user:)
      @plan = plan
      @user = user
    end

    ...
 
    def trade_info
      @trade_info ||= Security.aes_encode(url_encoded_query_string)
    end

    ...

    private

    def url_encoded_query_string
      URI.encode_www_form(build_trade_info)
    end

    def build_trade_info
      {
        MerchantID: merchant_id,
        RespondType: 'JSON',
        TimeStamp: time_stamp.to_i,
        Version: api_version,
        MerchantOrderNo: build_order_number,
        Amt: plan.price,
        ItemDesc: plan.name,
        ReturnURL: ENV['MPG_RETURN_URL'],
        NotifyURL: ENV['MPG_NOTIFY_URL'],
        ClientBackURL: ENV['MPG_CLIENT_BACK_URL'],
        Email: user.email,
        LoginType: 0,
        WEBATM: 1,
        VACC: 1,
        CVS: 1,
        BARCODE: 1,
      }
    end

    def build_order_number
      [time_stamp.strftime('%Y%m%d%H%M%S'), user.id].join('_')
    end

    def time_stamp
      @time_stamp ||= Time.zone.now
    end
  end
end
```

這樣大致完成 `trade_info`
可能有人會注意到 `Security.aes_encode(url_encoded_query_string)` 這行

這部分是後面會實作的 `Newebpay::Security` 只是先預期會這樣用， AES 則是文件指定的方式

## trade_sha
同樣的這裡文件也指定用 SHA256 再加密上面經過 AES 加密的資訊

```
def trade_sha
  @trade_sha ||= Security.sha256_encode(trade_info)
end
```

```
module Newebpay
  class Security
    class << self
      def aes_encode(query_string); end

      def sha256_encode(info); end
    end
  end
end
```

具體實作的部分則留待整個實作再處理
看文件確實會花不少時間，但隨著理解與實作的內容逐漸清晰
明天開始設計畫面，並利用 `config` gem 來做環境差異的設定
接著處理加密讓 request 能夠送出，再接著處理回傳後解密的資訊與行動
這樣金流的部分就算大致完成，就一步步完成ㄅ！


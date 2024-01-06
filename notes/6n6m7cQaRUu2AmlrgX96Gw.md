# Day 17 - 開啟被動收入(二)

昨天做了一些準備，所以今天就還只能針對文件的部分來設計 Object 的雛形

## Services

原則上會有一個頁面（尚未刻出）讓使用者送出表單，此時表單內根據文件(P.25)，要求攜帶下列四者
1. MerchantID
2. TradeInfo
3. TradeSha
4. Version

而準備這些東西需要的 `HashKey` ,`HsahIv` 以及 `MerchantID` 在這個階段都已經能取得，所以是可以先行實作的

而 Service 原本規劃兩個部分
1. 包裝處理 Response 的處理器
2. 加解密的處理器

這裡則因為 `TradeInfo` 跟 `TradeSha` 會有關係，為了方便，組成頁面表單需要資料的部分會再多一個 Service 來協助會比較合適一點
3. Request Info 的處理器

今天就先從表單需要的部分開始

## Newebpay::MpgInfo
主要是根據 Plan 的基本資訊來處理，所以開始帶入 `name` / `price`


```
module Newebpay
  class MpgInfo
    attr_accessor :name, :price, :model

    def initialize(name:, price:)
      @name = name
      @price = price
    end
  end
end
```

input 有了先預設 output 要給什麼，除了前面文件提到的四樣資訊，這裡還希望根據現在的環境配合生成與金流測試與正式站點的對應
1. MerchantID
2. TradeInfo
3. TradeSha
4. Version
5. URL
6. Method

```
module Newebpay
  class MpgInfo
    attr_accessor :name, :price, :model
    RESUEST_INFO = {
      development: {
        url: 'https://ccore.newebpay.com/MPG/mpg_gateway',
        method: 'post'
      }
      production: {
        url: 'https://core.newebpay.com/MPG/mpg_gateway',
        method: 'post'
      }
    }.freeze

    ...

    def merchant_id
      ENV['MERCHANT_ID']
    end

    def trade_info; end

    def trade_sha; end

    def api_version
      ENV['MPG_VERSION']
    end

    def request_url
      RESUEST_INFO[Rails.env.to_sym][:url]
    end

    def request_method
      RESUEST_INFO[Rails.env.to_sym][:method]
    end
  end
end
```

這裡有使用 `dotenv-rails` 這個 Gem ，協助放置這些個人商店的私密資訊

```
# .env

MERCHANT_ID=
MPG_VERSION=
MPG_HASH_KEY=
MPG_HASH_IV=
```

處理到這算是把 Service 內部簡單的東西都先處理掉了，關鍵的 `trade_info`，`trade_sha` 尚待「加解密的處理器」來協助處理
另外還有畫面未刻，以及看見藍星有測試正式站的區別，會需要另外的設定來幫助環境的區分
以上，下篇待續！


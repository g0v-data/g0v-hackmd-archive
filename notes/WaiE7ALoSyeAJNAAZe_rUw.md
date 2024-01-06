# Day 20 - 開啟被動收入(五)

這篇算是被動收入系列的大魔王了，範例是 PHP，研究好一陣子（苦惱
總之先按照文件的步驟一步步來組裝！

## 生成請求字串
先看成品預計要的樣子，其實就是組成 query string，這點已經有適合的 class 幫忙做，之前也已經先實作完成了

```
MerchantID=MS12345678&TimeStamp=1663040304&Version=2.0&RespondType=String&MerchantOrderNo=Vanespl_ec_1663040304&Amt=30&NotifyURL=https%3A%2F%2Fwebhook.site%2Fd4db5ad1-2278-466a-9d66-78585c0dbadb&ReturnURL=&ItemDesc=test
```

```
# app/services/newebpay/mpg_info.rb

module Newebpay
  class MpgInfo
    ...

    def trade_info
      @trade_info ||= Security.aes_encode(trade_params)
    end

    ...

    private

    def trade_params
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

```
# app/services/newebpay/security.rb

module Newebpay
  class Security
    class << self
      def aes_encode(query_params)
        query_string = URI.encode_www_form(query_params)
        # 到這裡是完成 Step 1
      end

      def sha256_encode(trade_info); end
    end
  end
end
```

## 將請求字串加密
> AES-256-CBC (使用 PKCS7 填充)，並將結果轉換至十六進制。
按文件給的關鍵字 AES256 / CBC / PKCS7填充 / 十六進制 ，稍微查詢一下
~~馬上就會發現好多範例~~，但還是嘗試一下自己來做
照著[文件](https://ruby-doc.org/stdlib-3.0.0/libdoc/openssl/rdoc/OpenSSL/Cipher.html)試試看
```
def aes_encode(query_params)
  query_string = URI.encode_www_form(query_params)
  # 指定演算法與模式
  cipher = OpenSSL::Cipher.new('AES-256-CBC')
  # 告訴 cipher 我要來加密ㄌ
  cipher.encrypt
  # 塞入 key / iv
  cipher.key = key
  cipher.iv = iv
  # 將 query_string 更新給 cipher 後告訴他加密結束了 
  cipher.update(query_string) + cipher.final
end
```

結果照做大概率會錯，因為 OpenSSL 默認 PKCS7 的填充法則，剛剛那段 `query_string` 出來之後還需要按照法則填到應有的長度，才能加密
而 `OpenSSL::Cipher` 提供了 `padding=` 來讓你設定要不要自行填充，且選擇 AES-256 等於長度要 32  
接著就要來處理填充的部分

```
def aes_encode(query_params)
  query_string = URI.encode_www_form(query_params)
  cipher = OpenSSL::Cipher.new('AES-256-CBC')
  cipher.encrypt
  cipher.key = key
  cipher.iv = iv
  
  # 選擇自行填充
  cipher.padding = 0
  # 填充完畢的 data
  padded_data = fill_padding(data)
  # 此時 AES 加密才算結束
  cipher.update(padded_data) + cipher.final
end
```

```ruby
def fill_padding(data)
  # 需要補填的長度
  pad_amount = 32 - (data.length % 32)
  # 加密機制會取最後一個字符按 ASCII 十進制回推填充數，用 chr 將之轉換
  pad = pad_amount.chr * pad_amount
  data + pad
end
```

修但喔，還有一個將結果轉換至十六進制還沒做
```
def aes_encode(query_params)
  ...
  encrypted = cipher.update(padding_data) + cipher.final
  encrypted.unpack('H*').first
end
```

這樣 AES 加密的部分就算完成了！

## 將 AES 加密字串產生檢查碼

```
# trade_info 就是剛剛 AES 加密完的東東

def sha256_encode(trade_info)
  # 先 key 夾 trade_info 後 iv
  encode_string = "HashKey=#{key}&#{trade_info}&HashIV=#{iv}"
  # 組完之後用 SHA256 在壓縮再轉大寫
  Digest::SHA256.hexdigest(encode_string).upcase
end
```


這步驟完成之後就可以看到之前先處理好的表單有帶入對應的資料，此時送出就會看到測試頁的刷卡畫面囉！！！！

這樣就能接著來處理刷卡成功與失敗之後的回傳資料處理，明天見 ：口

# p2p 通訊服務測試
> g0v slack 對外網路斷線時會掛掉QQ [name=irvin]

- 去了葡萄牙 Internet Freedom Festiva 現場看到的 demo，大家在假設烏克蘭的狀況發生，要如何維持通訊

## Keet 

- https://keet.io/ (Win/Mac/Android/iOS)

- G0v room 加入連結： pear://keet/yrb3xbejrmcn7ya1yw4i7bbhmrn1rnr3br7aw3aq9yt6pzhmfy51xs7a8x3c8q343p354dd9mw3hwjwtaprw1h64zeez5xiaayyrhca5iwppmxmf

    - 也是 P2P 通訊 （IM、Video/語音 Meeting）
        - 越多人使用越順暢
    - 以房間為基礎
    - 沒有 open source
      - 底層技術有開源 https://github.com/orgs/holepunchto/repositories [name=gasolin]
    - 加入非常快，剛進來會給一個亂數名稱，再到 profile 去改名字
    - 以 room 為 base ( 非instance-based) 
    - Linux AppImage 目前測試無法正常開啟
    - 上月 PlanB 活動中有開討論群，觀察同 Room 450 人 ok  [name=gasolin]
    - 對岸測試過 iOS 連線免翻牆 / Android 要接 VPN [name=gasolin]
    - 建議先增加MQTT部份,方便整合到其它工具上. [name=gavin]
    - 來測試： g0v room -[pear://keet/yrbhtdeejo3q664cehr1add5zko54y8sdskz8sdpm5jyft13a1jj477a8x3c8q343p354dd9mw3hwjwtaprw1h64zeez5xiaayyrhca5iwpfqsdf](pear://keet/yrbhtdeejo3q664cehr1add5zko54y8sdskz8sdpm5jyft13a1jj477a8x3c8q343p354dd9mw3hwjwtaprw1h64zeez5xiaayyrhca5iwpfqsdf)
- Briar
    - briarproject.org
    - 不需要網際網路，僅靠藍芽即可傳送文字訊息的通訊軟體。初次設定仍需網際網路。
- Bridgefy
    - bridgefy.me
    - 同上，但沒開源。


## newnode

- 是通訊協定、也有做成 app
    - Firechat 的新作 working proof
        > 目前收不到註冊簡訊 x 2
        >  [name=irvin]
        >  [name=jimmy]
    - 今天收得到了 
        >  [time=Sat, Jan 20, 2024 2:36 PM] [name=Irvin Chen]


## Quiet 

- "g0v" instance invite link - https://tryquiet.org/join#sik5h3fr7gzy4czjvllhtd7zgmljtrqrtwejlkr47h5s3s4e2tjksxid
    - join link 好像掛掉了 
    > [time=Sat, Jan 20, 2024 2:35 PM] [name=irvin]

- ~~P2P~~ 無中央伺服器 & over TOR 的 Slack
    - 以 instance 為基礎 （較接近 slack / discord）
    - 加入非常慢，因為要通過 tor，目前測試 Android、Linux 都有正常開啟 APP ，卡住在加入下面的 room
    - 有 open source [Github](https://github.com/TryQuiet/quiet)
    - 經過 Tor，但剛剛查台灣只有兩台
        > 35.221.182.226
        > 35.221.208.143
    > iOS 上無法選照片（可以送檔案） [name=irvin]

## 其他

- Briar 
    - briarproject.org
    - 不需要網際網路，僅靠藍芽即可傳送文字訊息的通訊軟體。初次設定仍需網際網路。
- Bridgefy
    - bridgefy.me
    - 同上，但沒開源。

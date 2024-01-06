g0v 網域工作小組 技術作業辦法
=========================

確認 IP 設定
-----------
* 確認該 IP 所在國家位置
    * 可透過 https://www.whois365.com/tw/ 查詢
    * 可在 UNIX-like 系統安裝 whois 查詢
    * * 指令範例： ```$ whois 8.8.8.8```
* 確認 IP 上是否有設定正確服務
    * 假如申請者想要將 airmap.g0v.tw 指向 122.116.59.198，可以用
```$ curl -i --resolve airmap.g0v.tw:80:122.116.59.198 http://airmap.g0v.tw/```
        確認是否能在該 IP 成功連入 airmap.g0v.tw

網域設定相關資訊
-------------
* nameserver 使用 Cloudflare 服務，申請帳號為 g0v.domain@gmail.com  
* 透過 [domain-sync](https://github.com/ronnywang/domain-sync) 可將 [github 上設定](https://github.com/g0v/domain) 與 cloudflare 做同步
    * 待補充：使用方式
    * 待補充：網域工作小組交換 api key 方式
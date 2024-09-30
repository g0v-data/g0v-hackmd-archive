---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240930 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :electric_plug: API
- Add `status` to replies https://github.com/cofacts/rumors-api/pull/349

#### :globe_with_meridians: Site

- [Fix type for codegen #578](https://github.com/cofacts/rumors-site/pull/578)
- [Reply detail and article detail revamp for blocked content #579](https://github.com/cofacts/rumors-site/pull/579)

##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

需注意未登入時，不應有任何有助於 SEO 的資訊露出（包含 tab title）

- [ ] Normal article detail https://dev.cofacts.tw/article/8xHSHpIBUOXjqM1AvRND
- [ ] Blocked article detail https://dev.cofacts.tw/article/zzovo5rubgqw
- [ ] Normal reply detail https://dev.cofacts.tw/reply/2F59iG8Bd3n3h-WYX0Kq
- [ ] Deleted reply detail https://dev.cofacts.tw/reply/2V5yiG8Bd3n3h-WYd0Ex
- [ ] Blocked reply detail https://dev.cofacts.tw/reply/lZYVx44BQ_PNHtDOjI7W


登入自有帳號後檢測：
需注意登入後，所有功能均應正常，包含 comment, upvote downvote 等；blocked reply 除外。

- [ ] Normal article detail https://dev.cofacts.tw/article/8xHSHpIBUOXjqM1AvRND
- [ ] Blocked article detail https://dev.cofacts.tw/article/zzovo5rubgqw
- [ ] Normal reply detail https://dev.cofacts.tw/reply/2F59iG8Bd3n3h-WYX0Kq
- [ ] Deleted reply detail https://dev.cofacts.tw/reply/2V5yiG8Bd3n3h-WYd0Ex
- [ ] Blocked reply detail https://dev.cofacts.tw/reply/lZYVx44BQ_PNHtDOjI7W

##### ⛔️ Release Blockers

##### 未竟項目


### :eye: Under review

## 大松

> https://g0v.hackmd.io/7UzK_kfzRWOcmJrXc7bxfA
> 

### Cloudflare 設定

> Cloudflare WAF rules 有一些設定是可以不用擋得這麼死到可能影響正常流量
> 可以設定的WAF Rules是
> - Allow All Verified Bots to skip all WAF rules
> - Block Known Threat Nations (俄羅斯/Tor/China?)
> - Block Admin Page Logins/Paths/Hostnames outside of Taiwan
> - Managed Challenge Not-Whitelisted Nations, where country not in HK, Macau, Malaysia, SG, TW (非中文國家)
> - 然後把/graphql endpoint加到API Shield的Schema(Logging)
> - 再把api.cofacts.tw配上WAF Fallthrough rule (Logging) 這樣就能看到route probing bots的heuristics 後續能擋下來
> 之後就剩Rate Limit的設定


- [Alex](https://www.linkedin.com/in/alexanderselikoff/)++
- Alex 希望有 Zone Level `http_request_firewall_custom` 的權限
- 看起來是指 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_012b25bf13a581c3f6788bfe185aaed1.png)




## Open165

- MIT --> AGPL https://github.com/Open165/site/pull/32
    - 但 AGPL 好像不只是換個 LICENSE 就好？

## 小聚籌備

- [ ] 日期：10/27 (日)
- [ ] 食物：
- [ ] 場地：NPO Hub Foundry（大的那間)
- [ ] 時間：
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
            - Slido 暖身
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：
  - 推播日：
  - 目標：雙北
- [ ] KKTIX: 
- [ ] 誰會來呢：
- [ ] 記得帶：貼紙、環保杯
- [ ] LINE 文案：
- [ ] VOOM 發文



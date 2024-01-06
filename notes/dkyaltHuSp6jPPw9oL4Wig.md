---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20230607 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：bil, cai, mrorz, nonumpa, 4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API

- [API logging](https://github.com/cofacts/rumors-api/releases/tag/release%2F20230607)

## DDoS report

### Progress in time

#### 2023/6/5 16:18


- Cloudflare 開始記錄分數很低的瀏覽器造訪 Cofacts，開始查問特定流量 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_68ae9beae4a255c035e3f56d4e99b955.png)
- 所有服務（API、chatbot、其他 site）都上不了或很慢
  - LINE Error statistics，圖中為日本時間 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9d96d1438543228e8e4b27fd46fbea12.png)

#### 16:42 發現倒站

LINE 信件通知一直 error，開始處理

##### server 狀況
- en site 吃滿 CPU 的樣子
- 重開 en site 之後依然會這樣
  ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4f45bb00a3705ce49bd2750bbb8cf89c.png)

##### 檢查 nginx log
> 4:34 開始有奇怪的流量，一直造訪 https://en.cofacts.tw//article/2h0ks48yprp3e?亂碼
> IP 均不同

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3d9fd93fefb094e37f8b7ee890344dda.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7aaf61c125c79cc3a30b1bd72d0a9862.png)

- URL 不同是在做 cache busting 使 Cloudflare cache 失效
- 但後來都一樣了，大概也是為何 Cloudflare 的流量在前半大多 uncached、而後半大多 cached ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1efa3c91694b4e5632ff0255535e34b8.png)

##### 檢查 Cloudflare security page

- 確認為 DDoS
- 每秒非常多 request 被 Cloudflare 擋住
- 但還是有流量進入 server 撐爆
- 查看各式 log
- 在 Cloudflare 觀察規律
- 調整 [Cloudflare security level](https://developers.cloudflare.com/support/firewall/settings/understanding-the-cloudflare-security-level/)，英文站設為 I am under attack 仍不足以阻擋

#### 17:20 手動設定 Cloudflare WAF 阻擋

- 針對 https://en.cofacts.tw/article/2h0ks48yprp3e 調整到「阻擋」
- LINE bot、網頁就可以正常顯示

#### 20:33 調降防火牆

> 防火牆規則調降為「造訪 en.cofacts.tw/article/ 圖上特定頁者，會接受 Cloudflare managed challenge」
> 所以造訪那一頁也無所謂了，真人互動可以進得去
> 防護等級
> - 全 cofacts.tw 網域與子網域：Security Level = High (攻擊開始前為 medium)
> - en.cofacts.tw 網域：Security level = I’m Under Attack!
> - 被攻擊的特定單頁：另外使用 WAF 指定 firewall action = Managed Challenge ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b79d5175f93bc289d67d2ceef9cb878d.png)

#### 23:19 再調降防火牆

撤銷 en.cofacts.tw 特別設定
- 全 cofacts.tw 網域與子網域：Security Level = High (攻擊開始前為 medium)
- 被攻擊的特定單頁：另外使用 WAF 指定 firewall action = Managed Challenge

#### Summary

總結一下 6/5 16:34 ~ 6/6 10:30 的這一波 DDoS 攻擊 https://en.cofacts.tw/article/2h0ks48yprp3e
Cloudflare 辨識的攻擊超過一億次。
設置防火牆阻擋或查問造訪該網頁的流量之後，發出接近 6 千萬次查問 (challenge)，含阻擋在內則有 7 千多萬次。
攻擊來源亦相當分散，辨認出超過 10 萬個不重複訪客。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2aaef8585b6657a58a61e42f8412e1d6.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f3abb4aef088f346047d0798a2d81182.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e40be36c018a80359b0a6536ff459db2.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bd33cee11d56497bd570d55ec8aa4f21.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_97c62c4751feeaaa09e489bf8af578c6.png)


### Analysis

#### System diagram
```
Internet --cofacts.g0v.tw--> nginx w/ HTTPS --> 301 cofacts.tw --> Cloudflare --> Cofacts website
         --cofacts-api.g0v.tw--> Cofacts API 
         --cofacts.tw--> Cloudflare --> Cofacts website
         --api.cofacts.tw--> Cloudflare --> Cofacts API 
```

#### Exposed routes and defense

Website
- Use cloudflare firewall
- If 301 redirect floods nginx, try using another 301 redirect service that supports custom domain

API
- Use cloudflare firewall
- Deprecate cofacts-api.g0v.tw, which is not protected
- API keys (see below)
  - 或許可以用 Cloudflare zero trust [name=4000]
  - Bil 去問 Cloudflare 是否可以發 API key [name=bil]

:::success
- In incident report https://hackmd.io/i0GcWSSVQNeDQ_OBebyk6Q
- Recorded to [CCPRIP](https://g0v.hackmd.io/BRsJOevWSbyUMBSZEVVWrA?both#DDoS-defense-with-Cloudflare)
:::

## CCPRIP

### [Comm] Transcript
> https://g0v.hackmd.io/@cofacts/rd/%2FOhGIQzoxR5eF6audQuS_FQ
> nonumpa

#### Server
collab staging server 不會動，需要看一下出了什麼問題

#### Site
[UI Design](https://www.figma.com/file/DvmAQjMJCncuPORWKnljM1/Cofacts-LIFF-and-new-designs?type=design&node-id=4514-923&t=30dzhfYvcFLsuOig-0) 沒有 desktop version?

目前先弄成這樣
> ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_33d4d4691e29925db312d29948673ac9.png)


- 按下 submit
    - 對 api server 送出 mutation
    - 對 collab server 送出 create snapshot 
- 按下 cancel
    - 如果沒有其他使用者在線上，collab server revert 回上一 snapshot
    - 有其他使用者在線上，什麼都不做

---

- 應該只要一個離開 transcribe 模式的按鈕 [name=orz]
  - 可以跟 transcribe 按鈕是同一顆
  - 在 onStore 的時候 create snapshot
  - 如果 UI 可以得知 onStore event，就告知使用者 your change has been saved
- AI transcription
  - ydoc as single source of truth; article text 是閹割版的 ydoc
  - AI transcript 產生後，戳 hocuspocus API 來寫入 ydoc [name=orz]
  - [name=nonumpa] 提供可以做這件事情的 hocuspocus endpoint

### [Op] 分身帳號處理
https://g0v.hackmd.io/ndNDmEkiSHyTRMOEIy2q2Q （Cofacts workspace owner only）

- 下週再修 CoC
- IP logging in place (6/7 中午開始)

### [Infra][Op] API management
- Design doc: https://g0v.hackmd.io/@cofacts/rd/%2Fj27XFAQ0R0Cuqi2jDLJuWw
- Research doc: https://g0v.hackmd.io/@cofacts/rd/%2F51wwLHgvSUqtBDaP-yAVnA
- Simple YAML file-based + API key client management
  - 先看 cloudflare
- Site API proxy, community-builder proxy

## Hallucination

> chatgpt 亂掰實錄+1
> https://cofacts.tw/article/ulqav0m1oszt
> 原文：「這是詐騙嗎，發票根本沒中獎」
> chatgpt：
> 好的，以下是節錄的訊息內容：
> 「恭喜您！您的手機號碼在本期發票中獎，獎金高達100萬元！請點擊以下連結領取獎金。」
> [name=cai]
> 上一篇是新光三越中獎

> https://docs.google.com/spreadsheets/d/1JQ2Av0Q7A_U84NEBRXWJW_tGBsDS1PU-gSy8j-F2Ypw/edit#gid=204242182

## 小聚籌備

時間：7/29（六）：coscup
7/8 or 9 (六/日)

## TODO items

> 六月還要投稿比賽跟寫報告，bandwidth 有限 [name=orz]

- [x] [Analytics] Rumors-api <> BQ script
  - [x] 研究為什麼 BigQuery 的 analytics 數字比 GA 少
- [ ] Rumors-api Typescript 

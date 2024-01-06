---
tags: cofacts, meeting note
--- 

20190731 會議紀錄
====
bil, 文武, lucien, orz,ggm 
>
> 上次開會紀錄：https://g0v.hackmd.io/s/ryxpCDrfB
> 

## 小聚準備

:::danger
今天要處理完！
:::

- [x] 主題：鬼門關（鬼差、搶孤、勇闖鬼門關 = 資料庫）
    - 勇闖謠言鬼門關
    - 用回應消口業、渡眾生
    - 西洋人怕鬼、台灣人也怕鬼
    - 在鬼月的尾聲，一起與好兄弟、好姐妹、回學校的小朋友、以及與資料庫裡的鬼話連篇說再見
- [x] 時間：8/31 14:00-17:00（青平台已經確認）
- [x] 人數：25
    - bil: 不要超過 25, 超過會認識不到人, wifi 會爆
- [ ] Banner 改舊的圖 - lucien
- [x] KKTIX
- [ ] LINE 推播（不要提到 g0v 否則會爆量，造成困擾）
- [x] 攜帶貼紙: bil - 殭屍
- [x] 場地：青平台
    - [x] 茶水
    - [x] 麥克風+插座+網路
    - [x] 投影機
    - [x] 延長線
    - [ ] 食物
    - [x] 垃圾的話大樓有垃圾車
    - [x] Talk - maybe coscup by mrorz
    - [ ] 青平台說樓下門禁變嚴格，需要簽到單 --> KKTIX 可列印
- [ ] 誰會來呢？orz, bil
- [ ] 開場使用材料更新：https://docs.google.com/presentation/d/1QCAPtwkxreQ4EUtIWsOgR4c8h4tkRs22Qvv7jBFNrfI/edit#slide=id.g1ffc87ef17_0_23

:::warning
TODO
Banner 圖
LINE 推播文案
:::

## Logo

:::warning
A~C 案選一個
:::

- A: GGM
- B: GGM, Bil, 文武, lucien
- C: 文武, Orz

lucien
為什麼你會喜歡 C

Orz:
A 像信用卡
C 很棒，東西放在一起很完整，而且很像鳥，對大家記憶上很友善
教學時可以「你就點那隻鳥頭」

文武：
B C 因為很像鳥

bil
啾啾啾
B 很像吹泡泡

lucien
F 字是 A 最明顯

orz
我後來沒在看字，我覺得放大鏡 C 還算明顯，也有點像錘子
灰階那塊是影子

lucien
很像鳥嗎 我覺得 B 也滿像的

bil
我要改支持 B 就好
因為 B 比較好畫

lucien
那選 B 怎麼樣

bil
我們可以跟鳥做連結嗎
像假新聞清潔劑與肥皂

lucien
twitter 嗎

ggm
學舌鳥嗎
鴿子（和平鴿）

lucien
鳥其實有滿多可以用的

orz
如果有什麼 metaphor 可能現在就要想出來

bil
飛鴿傳書
通風報信
鸚鵡學舌，機器人會學起來，問一樣的問題，就會一直回

:::success
B~
:::

## Facebook 教 NGO 打廣告的筆記
> by bil & g0v friends
> 
https://g0v.hackmd.io/lAw51JyLT5SaDxk3uRHqsw?both

- Instagram 藍海市場先行者
- 限時動態很重要
- 影片要拍直的

## 8/7 採訪
> 8pm~8:30pm 採訪

:::success
統計：文武, orz, bil, ggm
:::

## 9/7 大松

:::warning
Bil, MrOrz 不在台灣
:::

:::success
GGM, 文武應該會去
- 可以在 FB 廣告
:::

## Dev

### Migration - Clustering solution

1. ssh config 互通: `new-cofacts`, `old-cofacts`, `answerfamily`
2. docker-compose expose elasticsearch's [port](https://discuss.elastic.co/t/elasticsearch-port-9200-or-9300/72080/2)
    - `9200`: control
    - `9300`: nodes communication
4. docker-compose 加上 remote db:
    - See [cagataygurturk/docker-ssh-tunnel](https://hub.docker.com/r/cagataygurturk/docker-ssh-tunnel)
    - environment:
      - TUNNEL_HOST: cofacts-org
      - REMOTE_HOST: localhost
      - LOCAL_PORT: 9300
      - REMOTE_PORT: 9300
5. 設定 elasticsearch.yml
    - `cluster.name` 兩者一致
    - `node.name` 取不同名字
    - `discovery.zen.ping.unicast.hosts` 設 ssh tunnel 的 service 名字（docker-compose network 會用該名字設 host）


:::danger
db_1              | [2019-07-31T15:21:04,163][WARN ][o.e.d.z.ZenDiscovery     ] [new-cofacts] failed to connect to master [{VxKgRte}{...}{...}{172.19.0.9}{172.19.0.9:9300}], retrying...
:::

### FE UI revamp

- Next.js 9
  - Fix FOUC
  - Removal of custom server & next-routes
- Use Apollo client & local state management to replace Redux
- UI library
  - [Library npm trend](https://www.npmtrends.com/evergreen-ui-vs-material-ui-vs-semantic-ui-react-vs-antd-vs-react-bootstrap-vs-reactstrap-vs-baseui)
  - [Material-UI](https://material-ui.com/)
    - Supports any style library, like [emotion](https://material-ui.com/guides/interoperability/#emotion)
    - SSR support is doable but [a bit complex](https://github.com/mui-org/material-ui/blob/master/examples/nextjs/pages/_document.js)
    - 勝
  - [base-ui](https://github.com/uber-web/baseui) by Uber
    - Uses [styletron](https://baseweb.design/getting-started/installation/#styletron)
    - SSR [follow styletron example](https://github.com/zeit/next.js/tree/canary/examples/with-styletron/), more complex than Material UI SSR...
  - [Evergreen](https://evergreen.segment.com/components/) By Segment
    - Fixed color & design; provides sketch file
    - Override style with props (uses [ui-box](https://github.com/segmentio/ui-box) as CSS-in-JS solution)
    - Simple [SSR](https://github.com/segmentio/evergreen/blob/master/examples/ssr-next/pages/_document.js) -- so when will it dump SSR style cache? So mysterious...

- (optional) Gradually migrate to TypeScript 
- (optional) API server token based authentication
  - API <> UI: ID token dispatched by API.
    - The token can be encrypted, or it can be designed so that clients can read and verify (i.e. JWT).
    - The token is passed from UI to API using HTTP headers.
  - SSR website <> UI: UI passes ID token from API server to SSR
    - The ID token is passed to SSR website using cookie, so that it works even on 1st load after browser reloads
    - Cookie is set via client Javascript after login redirect from API server. It can be set under SSR website domain only.
  - SSR website <> API: Uses ID token passed through from UI
    - The ID token is retrieved from UI using cookies
    - The ID token is passed from SSR website to API using HTTP headers
  - Chatbot <> API: Still uses API keys
  :::warning
  We may choose to delegate the whole authentication mechanism to Auth0 instead. For chatbot servers, use [client credentials](https://auth0.com/blog/using-m2m-authorization/).
  :::


## TFD 問答
> Subject: Questions From TFD

https://hackmd.io/@mrorz/Hyw4eSh-B

:::success
orz 寫
:::


## 8/25 19:00~??:00 高雄
> GGM 會去

對方找了一群志工
地點還沒確定，應該在市區吧

bil
沒有必要太久，21:00 以前結束吧

ggm
是什麼活動，workshop 還是演講

bil
小聚吧
我們希望有人能來查證
他們找了一群人，希望有人來教如何查證

教他們不要把「含有正確訊息」與「含有不實訊息」標成「不在查證範圍」等等，因為有人會這樣做。

最重要就是學網站怎麼用、然後講好分類


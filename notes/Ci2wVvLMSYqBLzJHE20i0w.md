# RssHub.g0v.tw

## 專案簡介

## 緣由
萬物皆可 RSS，RSS 不能亡！！！
（為什麼會想發起這個專案，一些背景資訊）

## 要解決的問題
臉書粉絲專頁貼文不一定看得到


## 預定使用者
想要繞過演算法，訂閱粉絲專頁的人。
（成品要給誰用、在什麼場合用、怎麼用）

## 預定功能

>定義：
>RSS SaaS 用來泛指可以訂閱 RSS Feed 的網路服務
>如 Feedly, Inoreader, NewBlur, FeedBin...

- 給粉絲專頁網址拿到 RSS Feed
- 給粉絲專頁網址直接在 RSS SaaS 打開

（成品要有哪些功能來滿足上述使用情境）

## 現有類似專案
無
（現成的是否可以直接使用？或者有什麼不足之處？國外專案可參考？）

## 相關專案
本專案屬於通用型基礎建設？
（衍生自某專案/衍生出某專案/API串接自某專案.）

## 授權方式
MIT
（程式碼部分如 MIT/BSD /文件部分，如 CC-BY）

## 使用資料
無
（會使用到哪些資料來源、各是什麼授權）

## 專案目前狀態
生命會找到出路，而我找到 RssHub。
（構想 / 規劃 / 雛形 / 實作）

## 利益揭露
yellowsoar 自己在 Linode 架 K8s 運行 tor proxy
（牽涉到哪些組織團體、有哪些已知的或潛在的金錢或物質或無形利益報酬）


## 徵求協作者

- 發起人/拋磚人：yellowsoar
- 失聯的 g0v 網域工作小組成員
- Cooperator 
    - Git CLI + Github + Heroku
    - Linode K8s + tor proxy + reverse proxy + graylog + beats
- Sponsor (about 30$/month for now)
- Developer with browser plugin experience.
- Information or crawler related project owner. (cofacts,iorg... etc.)
- Javascript developer with web crawler experience.
- People with architect / UX experience on problem oriented project.
- Super user for Win/Mac/Linux or familiar with launchers. (keypirinha, alfred, launchbar... etc.)
- Not finished...

NeedsWriter: 需要文案幫手（撰寫基本資訊、報導專案etc）
NeedsDesigner: 需要介面設計
NeedsData: 需要資料（擷取、清理）
NeedsTech: 需要技術支援（程式、架站 etc)
NeedsProcess: 需要幫忙設計作業流程
NeedsTalkingToRealPerson: 需要有人幫忙和其他機關聯絡


### 實作細節（非技術背景可跳填）

1. Sync with [upstream repo](https://github.com/DIYgod/RSSHub) via GitHub action "pull".
    (Manual sync via bash script if GitHub action failed.)
1. Deploy to Heroku by GitHub Webhook.
    (Roll back automatically if deploy failed.)
1. Service runs as Heroku free dyno instance.
    (Tested since 2020/6)
1. Service restart by Heroku add-on "Heroku Scheduler" every 10 mins via Heroku api with token.
    (Sometimes I'll trigger it manually for testing or just for fun XD)
1. Monitor and keep instance alive by UptimeRobot for every 10 mins.
1. Logs send to Papertrail in free tier for debugging.
1. A rotating tor proxy on LKE (Linode Kubernetes Engine).  
    <https://github.com/mattes/rotating-proxy>  
    <https://www.linode.com/products/kubernetes/>
1. Rsshub@heroku forward `.*facebook.*` matched url to rotating_proxy@LKE.  
    With 30000ms timeout and 5 times retry policy.  
    <https://docs.rsshub.app/install/#pei-zhi-dai-li-pei-zhi>

Ref:https://github.com/g0v/domain/pull/51

### 協作工具

#### github repo
- upstream: https://github.com/DIYgod/RSSHub
- forked for deploy: https://github.com/yellowsoar/RSSHub
- tor proxy & logs on K8s: working on it!

#### Others 
hackfoldr 工作資料夾網址：https://beta.hackfoldr.org/rsshub


### 進度與 to-do
Working on it!

## 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）
Working on it!

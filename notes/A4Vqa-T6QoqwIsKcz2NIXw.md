---
title: "ChaceTix 售票系統"
tags: 黃牛, 售票系統, 文化部, 非營利組織
---
# ChaceTix 售票系統(暫)

# 緣由
- 現在售票系統都只有先搶先贏的部分,不過今年開始有嘗試抽選機制(不確定是否之後都有)。
- 票卷黃牛太多導致真正想看演唱會或是藝文活動的人沒有機會買到票。
- 尚未有健全的"會員實名制"與"交換票卷"制度的購票網站。

# 要解決的問題
- 預防黃牛
    - 建立實名制售票平台
    - 建立匿名交換票卷平台,希望可以跟現在各售票平台合作
- 成立反票卷黃牛宣導與推廣組織
    - 研究並跟進日韓售票方式,成立反高價販售黃牛票與抵制黃牛的組織 
      參考：[チケット適正流通協議会](https://ftaj.jp/) 
    - 推動票卷平台支援 實名制會員系統 與 抽選票卷機制

註解：
如果最後目前主流售票平台都支援＂實名制會員系統＂與＂抽選票卷機制＂時會結束此售票平台服務。

# 預定使用者
- 給社會大眾＂購買票卷＂與＂交換票卷＂使用
- 給想舉辦活動並售票的社會大眾

# 預定功能
- 實名制會員系統
- 記名售票系統 (先搶先贏制 與 抽選制)
- 匿名交換票卷系統

# 現有類似專案
- 實名制且記名抽選制 （[eplus](https://ib.eplus.jp/), [tixplus](https://tixplus.jp/)）


# 相關專案


# 授權方式
- 程式碼部分：AGPL-3.0
- 文件部分： CC-BY-SA

# 使用資料


# 專案目前狀態
目前已有基礎的售票網頁架構並且以部屬網頁,但因本人不是專業的網頁工程師透過網路自學,所以想找專業人員來幫忙修改更好的架構。
目前規劃：
1. 先把售票網頁基礎重新檢視架構與網頁案全確定是否合乎業界標準再陸續開放功能給大眾使用
2. 美化售票網頁

# 利益揭露
- 目前售票公司（[KKTix](https://kktix.com/), [拓元售票](https://tixcraft.com/), [遠大售票](https://ticketplus.com.tw/)）

# 發起人/拋磚人：
發起人：OKHand.ziyu

NeedsDesigner: 
    需要介面設計

NeedsTech: 
    需要技術支援（程式、架站 etc ...)

NeedsProcess: 
    需要幫忙設計作業流程

NeedsTalkingToRealPerson: 
    需要有人幫忙和其他機關聯絡

# 實作細節
- 語言：Typescript
- 網頁框架：React 18
- 全端框架：Next.js 14 (App Router)
- CSS：TailwindCSS
- UI：shadcn
- Auth：Next-auth@^5.0.0-beta.15
- ORM：Prisma
- State Maneger：zustand
- Deployment：Vercel
- DNS：Cloudflare
- 會員實名制採用預計採用 [TWCA - MID 門號認證](https://www.twca.com.tw/product/c0cf07bd-25ab-42d8-a1bd-3e6e71950113) 方式
- 抽選機制採用 [Random.org](https://api.random.org/) 的 API 功能提供隨機值

# 成果展示（規劃文件、雛形/草稿、原型/初稿、正式發佈/完稿）
- Web：https://www.chancetix.com/
- PPT：[ChanceTix 售票系統 - Google docs](https://docs.google.com/presentation/d/18wddOPBj_I-S17uo0DpoSuVStynUGLpaSg7ZcmCEZ44/edit?usp=sharing)
- GitHub：[chancetix-web-app - Github](https://github.com/OKHand-Zy/chancetix-web-app)
- Notion：[ChanceTix - Notion](https://okhand.notion.site/0fa4c780acd9451d8f02d090604fa67e?v=3034498d2e1143ef8a0cceb607adf9a4&pvs=4)
- 聯絡與溝通管道：
    - Discord：okhand
    - Telegram：@OKHandTw
    - Slack：OKHand ZiYu

## 參與專案 協助者/貢獻者：
- Cloud
- Tofus

## 提案相關問題討論區
Q. 
> [name=ichieh] 嗨，今天在大松的成果報告聽到你們在做這個，感覺超酷！我自己有在辦活動，因此會想到的是不確定售票平台在管理者端目前會有哪些功能，例如 kktix 可以有寄信給報名者、優惠碼設定、票種設定這些。

A. 
> [name=OKand] 目前現階段最小可行性是想先往＇匿名二手票卷流通平台＇前進，後面等我們認證方式等...考量問題解決時再繼續開發。不過依我現在開發完成的功能是有，1.查看活動參與者與持有的票卷的規格 2.舉辦活動時票種的設定(價格、種類)，不過如果有希望的功能或是覺得其他售票平台有那些不方便的點歡迎提出來！！
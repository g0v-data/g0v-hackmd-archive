---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20240812 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 線上出席：
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

## :potable_water: Release pipeline

### :star: Released to production

#### 👐 Open165
- index using host https://github.com/cofacts/open165/pull/15

### :rocket: Staging

#### 👐 Open165

- [Adds linter and CI #17](https://github.com/cofacts/open165/pull/17)
- [Install UI library NextUI #18](https://github.com/cofacts/open165/pull/18)
- [Layout and about page #20](https://github.com/cofacts/open165/pull/20)

https://layout-figma.open165.pages.dev/


##### ⛔️ Release Blockers

##### 未竟項目


### :eye: Under review
https://github.com/cofacts/rumors-api/pull/343
- Can directly ignore coverage of that endpoint [name=mrorz]
- docker 好像不會 build graphiql 頁面 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e29a03f11ee079177ea21e7278c1c93f.png)


## Open165

### Design
- Figma: https://www.figma.com/files/project/263380271
- Mockup: https://www.figma.com/design/wrgkgbbPtaopquHMRoBXnB/Open165?t=IHTzzsHIZUc0SMjg-0https://www.figma.com/design/F4cfllPkHZl8sAsYPcB3Op/NextUI-Figma-Kit-(Community)?t=IHTzzsHIZUc0SMjg-0
- Component copied from https://www.figma.com/design/F4cfllPkHZl8sAsYPcB3Op/NextUI-Figma-Kit-(Community)?t=IHTzzsHIZUc0SMjg-0

選擇
- 喜歡 Material Design 3 大塊留白
- 但 Google 官方 web 是用 web component 感覺很難與 React 整合
- 採用外觀類似、社群口碑不錯的 NextUI
    - 元件設計比 Shadcn 大
    - Shadcn 比較少更新了
    - 客製化選項多
    - 原生使用 TailwindCSS
- 設計：細線條、留白為主
    - 少色塊
    - Icon 亦選擇線條風格
    - 文件風格 (?)

### SEO

Analytics: Cloudflare

Search console


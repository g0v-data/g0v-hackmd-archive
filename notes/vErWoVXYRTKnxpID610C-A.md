---
tags: cofacts, meeting note
GA: UA-98468513-3
---

# 20201202 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- 出席：nonumpa, bil, mrorz, hsiao, 志超
:::

## 小聚檢討

文字紀錄見[小松果](https://g0v.hackmd.io/PUXRtdC2SNak8VYUSAb-Gg)

### 邀請人來闢謠的文案與視覺
- 「有人被騙了嗎？等你來幫忙」
- 「協作」可以用「更好的解答」來強調協作，多人的意見比一個人的意見更好
- 「查核」比較像是在詢問，「更好的解答」比較像是協作，所以用「查核」的話跟目的（找協作者）不同。
- 「一起來查」可能比「等你來提供」好

時間點的建議：在使用頻率較高（ex: 選舉）時招募

字數同下圖
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2dc278216f944c7d82ba1e01a38d8b3d.png =x200)

:::success
### 結論

兩個時機：
- Cofacts 裡沒有訊息 --> 請傳到 Cofacts LINE bot
	- 「要不要傳給真的假的機器人問問看呢」 - 接[之前的 wording](https://github.com/CarolHsu/rumor-checker/pull/39)
- 或 Cofacts 裡面有訊息但沒回應 --> 請登入 Cofacts 網站寫回應
	- 「有更好的解答嗎？一起來回應吧！」
:::

### 無法使用 bug
- 有人又遇到 [login issue](https://g0v.hackmd.io/Ha-SMCxJQuGzqx6EnrKanA#Login-issue)
    - iPad、Chrome 與 safari 都不行，無痕與非無痕都不行
    - 換用 iPhone 反而就可以 @@
- 有人無法使用（點入直接 an unexpected error has occurred）
    - iPhone 6S Safari, Chrome 都不行
        - 理論上 [#313](https://github.com/cofacts/rumors-site/issues/313) 已經解掉了？
        - New bug ticket: https://github.com/cofacts/rumors-site/issues/359
- iPhone 12 Pro + iOS 14.2.1 也會遇到一樣的問題 [name=clementtang]
    - 但 browserstack 無法重現該問題

### 流程問題
- 後來來的人沒有到 slido 就直接在網站開始做了
- 晚到的人，可能沒有經過第一階段，就到第二階段了
	> 遲到是一種人格缺陷 [name=bil]
- 沒有電腦(看投影片很困難)又晚到
	- 如果是不熟的人，會希望邊看投影片邊做，所以如果沒帶電腦會很難進行 [name=nonumpa]
	- 註冊的時候用「我會帶電腦」之類的 checkbox 或導引文字 [name=mrorz]
- 桌子很小，人不能到 25 個 --> 16 個

### 網站 UX
- 有些字沒翻譯，使用者會搞不懂每個區塊的文字是什麼用途
	:::warning
	待 landing page merge 後再 extract 一次翻譯
	:::
- 有使用者不知道“不同意見”代表編輯打的那段文字的 reference，以為是兩個 part、或是有人對這個回應有不同意見，但其實跟 title 字型大小也有關，但我覺得文字換回出處(reference)會更保險、不被誤會
	- --> 改成「不同意見出處」或「出處」
	- 可以只用「出處」[name=nonumpa]
	- Editor 如果也寫「出處」會讓編輯以為要放原文的出處，但我是希望一起放不同意見的出處 [name=mrorz]
	- 「請簡述訊息何處含有個人意見，以及提供其他意見」 [name=mrorz]
	:::warning
	mrorz proposal
	- Editor 的說明文字
	- 模板
	- 網站的 section title
	:::
- 還有可能是因為 reply 和 reference 太長，導致區塊區分看起來不是很明顯（以 facebook 來看，不同的 post 之間之間會有一點間格和 border 區隔開）
	- reference URL 太多 --> 折疊 URL，或
	- 出處也一起被折疊起來 [name=nonumpa, nick]
	- 如果覺得出處重要的話可能不會折疊，但其他 chatbot 確實不會折疊 [name=bil]
	:::success
	開票。要研究一下 `ExpandableText` 是否可以支援這樣的行為。
    https://github.com/cofacts/rumors-site/issues/360
	:::

### Google Sheets 無法 import
orz import 完之後，就可以 import 了，很怪
:::success
我開完之後先 import 一次只有一個 tab 的 (?) 然後再刪掉
先在小聚前的會議確認是否能 import
:::

## 台南 summit

攜帶川普貼紙與文宣
簡報[簡報](https://docs.google.com/presentation/d/1fUcjXUNu0gAihWguKo7MabXHSZn1n_DXWLLvS2uC_Zk/edit?usp=sharing&urp=gmail_link&gxids=7757)
工作坊：按讚+怦然心動的引言創作
大致上分四到五組，每組有一個jamboard頁面，由指導員負責協助(文武、鹿、orz、bil)
- 14:00-14:15 投影片介紹
- 14:15-14:25 登入讚讚 (指導員確認每個組員都可以登入，並且點讚，請依照簡報下filter，協助找到最新回應幫讚讚)
- 14:25-14:50 jamboard 寫引言
- 14:50 - end 討論分享

## Migration
:::danger
移至下周討論
:::

> - 改userId 的 migration https://gist.github.com/ztsai/f9445bb45bfa145a329fcfad51519346 [name=zoe]
> - 改avatarType 的 migration https://gist.github.com/ztsai/acc9c723b4254d2f31114c4959a2dfdc [name=zoe]


- 公告：幾號 要 migration，幾點到幾點下線
- Migration ：reverse SSH tunnel 接到資料庫操作
    - [ ] 準備 script 放在 rumors-api 下
    - [ ] 關閉 nginx 使 Cofacts 下線
    - [ ] 備份資料庫
    - [ ] 建立 reverse SSH tunnel
    - [ ] 確認 .env 內的 ELASTICSEARCH_URL 指向 ssh tunnel 開啟的 port
    - [ ] babel-node 跑 fixBackendUserIds.js
    - [ ] babel-node 跑 fixAvatarDataTypo.js
    - [ ] 關閉 reverse SSH tunnel
    - [ ] 開啟 nginx

## Dialogflow 設定

:::danger
移至下周討論
:::


> [Intent design](https://g0v.hackmd.io/kWuTnoC1TG-MONPhxp8rGQ#2020-Q4--2021-Q1-%E9%80%B2%E5%BA%A6%E7%A2%BA%E8%AA%8D)
> 參考資料(limited access)： https://datastudio.google.com/u/0/reporting/64c3b474-a306-40f5-86b9-2e894d028da6/page/lijmB
> - 問題類：請問(xxx)、(xxx)什麼(xxx)、資料庫…
> - 無意義類：謝謝、好的、了解、OK、測試、天氣、你好、國家、人名…
> 

## AI4SG

:::danger
移至下周討論
:::



## yegogo

下次用這個 GraphQL 直接抓要刪啥

```
{
  ListReplies(filter: {userId: "vA43ZHEBrhVJn3LNSSe8"}, first: 20, orderBy: {createdAt: DESC}) {
    edges {
      node {
        id
        createdAt
        articleReplies {
          articleId
          status
        }
      }
    }
  }
}
```

然後做出 Takedown PR https://github.com/cofacts/takedowns/tree/master/2020
以及 script
```
docker-compose exec api node build/scripts/removeArticleReply.js --userId=vA43ZHEBrhVJn3LNSSe8 --replyId=<> --articleId=<>
```

```js
// remove-yegogo.js
const fetch = require('node-fetch');

const USER_ID = 'vA43ZHEBrhVJn3LNSSe8';

async function main() {
  const result = await fetch('https://api.cofacts.org/graphql', {
    method: 'post',
    headers: {
      'content-type': 'application/json',
    },
    body: JSON.stringify({
      variables: { userId: USER_ID },
      query: `
        query ($userId: String!){
          ListArticles(filter: {articleRepliesFrom: {userId: $userId}}, first: 200, orderBy: {lastRepliedAt: DESC}) {
            edges {
              node {
                articleReplies(status: NORMAL) {
                  articleId
                  replyId
                  updatedAt
                  createdAt
                  user {
                    id
                  }
                }
              }
            }
          }
        }
      `,
    }),
  }).then(r => r.json());

  const articleReplies = result.data.ListArticles.edges
    .flatMap(({ node }) => node.articleReplies)
    .filter(({ user }) => user.id === USER_ID);

  console.log('------');
  console.log('Replies to remove');
  articleReplies.forEach(ar =>
    console.log(`- https://cofacts.org/reply/${ar.replyId}`)
  );
  console.log('------');
  console.log('Commands');
  articleReplies.forEach(ar =>
    console.log(
      `docker-compose exec api node build/scripts/removeArticleReply.js --userId=${USER_ID} --replyId=${
        ar.replyId
      } --articleId=${ar.articleId}`
    )
  );

  console.log('------');
}

main().catch(console.error);

```


## Tutorial & 動畫

- [Tutorial Figma](https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=2011%3A6)
- [動畫 Figma](https://www.figma.com/file/zpD45j8nqDB2XfA6m2QskO/Cofacts-website?node-id=3785%3A790)

## :potable_water: Release pipeline

### :star: Released to production

#### :electric_plug: API
[DIFF](https://github.com/cofacts/rumors-api/compare/aa7e7f89f84d9321f18d73ee3f505166a73ffdbb...cffc41c24d05bba13e19becb7510f6013e6904fa)

- #236 remove script

#### :globe_with_meridians: Site

https://github.com/cofacts/rumors-site/releases/tag/release%2F20201130

#### :robot_face: LINE bot

### :rocket: Staging

#### :electric_plug: API

[DIFF](https://github.com/cofacts/rumors-api/compare/cffc41c24d05bba13e19becb7510f6013e6904fa...5632c4532c11b30dd160c4dfab9adea500250d3c)

- #232 user profile related api changes
- #235 List reply requests
- #238 fix typo in openpeeps json

Migrations see "migration" this week

#### :robot_face: LINE bot

- #235 [dialogflow](https://github.com/cofacts/rumors-line-bot/pull/235)

##### Testing checklist

https://lin.ee/1QUzEX4nI

- Test if dialogflow accidentally captures rumor text

#### :globe_with_meridians: Site

- #356 landing page

See landing page and test if it functions well
- Login --> goes to hoax-for-you
- Check if search works
- Check if article list works
- Works on mobile / desktop, logged-in / not logged-in
- Check what will a spider see
- og-image 要用哪張？

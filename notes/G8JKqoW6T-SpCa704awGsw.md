---
tags: cofacts, meeting note
GA: UA-98468513-3
---

20221026 會議記錄
=====

:::info
- [所有會議記錄](https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/)
- Workis 出席：MrOrz, bil, crew * 5
- 線上出席：nonumpa, cai, 4000
- https://gather.town/app/z3x18KQFgZCX8MeZ/cofacts
:::

:::warning
今天有拍攝作業
可能 ~~8:15 ~ 8:20~~ 8:30 才會開始開會唷
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :globe_with_meridians: Site

- https://github.com/cofacts/rumors-site/pull/510 Lavi++
- https://github.com/cofacts/rumors-site/pull/512

##### Testing checklist
http://dev.cofacts.tw/

**未登入**下檢測：

- [x] "About" page shows 台灣吧 video and can play normally
- [x] Footer links to user agreement page
- [x] Login window shows link to user agreement page
- [x] User agreement page works
- [x] User agreement page links to Github for history

##### ⛔️ Release Blockers

##### 未竟項目

## 大松檢討

> 成果：https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2FI2IhD3wGS1OawGB1Tarfxg

- panel 比較少人
- pitch 順利
- 感謝大學生們回報 fix video popup 問題
    - 有一個 participant 說來幫修

## Facebook login issue

### 10/12 來信通知 violation

> 主旨 Your action is needed by 2022-10-19 06:00:00 PDT for: 真的假的 (719656818195367)
>
>  In working to create a great Platform experience for everyone, we ask developers to ensure the apps they build comply with our Platform Terms and Developer Policies. Your app 真的假的  (AppId: 719656818195367) doesn't comply with the following:
>
> Platform Terms 4.f: You will maintain publicly available links to your privacy policies in the privacy policy field in the settings of your App Dashboard, as well as in any App Store that allows you to do so, if applicable, and ensure the links remain current and up to date.
>
> Platform Terms 4.a: If you use Platform to process Platform Data, you will provide and comply with a publicly available and easily accessible privacy policy.
>
> During testing, we were unable to find a privacy policy on your website. Make sure that users are able to find and view your privacy policy, and that your privacy policy is accessible from any country so that we can access it for testing.

署名：
Meta Developer Operations Team

- mrorz: 這封淹沒在各種信裡面所以我沒讀到 QQ
- 想要換 email 到 cofacts@googlegroups.com 讓大家一起看到

### 10/19 來信通知 deactivated
> 主旨 Facebook Platform Policy - App Deactivated: 真的假的 (719656818195367)

### 10/21 ~ now: Appeal

- 10/22 Meta 回覆網址打不開、我 10/24 回覆打得開
- 10/24 Meta 表示：![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9c93dc1ca39ab4b185f20cfb79aaa199.png)
    我回信：![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5dd2298eba11fc175b3423b82f85f6d3.png)
- 10/24 Meta 表示：![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_642adb9361a9a5bcd5d6184a0debfae6.png)
    - 「the Privacy Policy belongs to another company that is clearly not affiliated with your app」
    - 所以對方覺得「放在 github 的 Cofacts privacy policy」是「github 的 privacy policy」？？！！ [name=mrorz]
  

## CIB 處理

提升 SEO 的回報
https://old.cofacts.tw/articles?searchUserByArticleId=1lgis9b8sl5gp&filter=all&replyRequestCount=1

Follow-up for: https://g0v.hackmd.io/@mrorz/cofacts-meeting-notes/%2FJPUb9EMATwGLBhgeECAskA

### User
- 乂活潑的六甲葛列格乂 (`j4S8C_LO8hbMHXx2JJGkLhlrJFIE3eilJW0mu2SGJScX1D1cE`)
- 註冊：`2022-10-10T06:02:55.631Z`
- https://cofacts.github.io/community-builder/#/editorworks?type=2&day=40&userId=j4S8C_LO8hbMHXx2JJGkLhlrJFIE3eilJW0mu2SGJScX1D1cE
    - 10/10 ~ 10/19 共計 58 篇

問題：
- 轉的訊息均為相似主題
- 以此文為例： https://cofacts.tw/article/1kik6hivfdr3j
    > 詐騙集團再現新手法，Coinexeco在果農臉書粉絲專頁訂購芒果，卻遇到詐騙集團偽冒果農小編，在貼文留言請民眾至連結處付款，但實際上該連結為釣魚網站，騙走民眾信誉卡卡號及手機等根本資料，詐騙集團隨後至第三方支付平台綁卡。
    - 該文沒有任何二次詐騙的 LINE ID，但卻是修改[現有文章主詞](https://www.thenewslens.com/article/168983) 插入關鍵字做 SEO。
- 其他問題 from cai++
    * https://cofacts.tw/article/19xs9h37paqdh 原新聞 ：[為父親辦後事貸款　孝女險遭騙手續費10萬裡](https://www.taiwanhot.net/news/focus/999686/%E7%82%BA%E7%88%B6%E8%A6%AA%E8%BE%A6%E5%BE%8C%E4%BA%8B%E8%B2%B8%E6%AC%BE+%E5%AD%9D%E5%A5%B3%E9%9A%AA%E9%81%AD%E9%A8%99%E6%89%8B%E7%BA%8C%E8%B2%BB10%E8%90%AC/131/%E7%A4%BE%E6%9C%83%E9%A0%BB%E9%81%93)的林女 改掉
    * https://cofacts.tw/article/6hgryvgkb1p9 原新聞 ：[警破求職詐騙集團拘女成員](https://std.stheadline.com/daily/article/2240958/%E6%97%A5%E5%A0%B1-%E6%B8%AF%E8%81%9E-%E8%AD%A6%E7%A0%B4%E6%B1%82%E8%81%B7%E8%A9%90%E9%A8%99%E9%9B%86%E5%9C%98%E6%8B%98%E5%A5%B3%E6%88%90%E5%93%A1)
    * https://cofacts.tw/article/f84f96dtlmt2 原新聞: [詐騙集團謊騙投資房地產 婦人險遭詐財300萬](https://ynews.page.link/xLpt)  這篇只有改標題
    * https://cofacts.tw/article/1lgis9b8sl5gp 原新聞: [購物、玩遊戲都可能被騙，資安業者揭網路4大陷阱：網購詐騙最猖獗](https://www.bnext.com.tw/article/71941/online-shopping-scam)
- 

:::spoiler Query to use in API

https://api.cofacts.tw/graphql
```graphql
{
  ListArticles(filter: {userId: "j4S8C_LO8hbMHXx2JJGkLhlrJFIE3eilJW0mu2SGJScX1D1cE"} first: 60) {
    edges {
      node {
        id
        createdAt
        articleReplies {
          userId
          user { name }
          createdAt
          reply {
            text
            reference
          }
        }
      }
      cursor
    }
    totalCount
  }
}
```
:::

回應者

- 似乎是自產自銷，專門 for SEO。
- Login using Google (註冊時間 10/14 ~ 10/20)
  - raglan werner: https://cofacts.github.io/community-builder/#/editorworks?type=0&day=40&userId=soue74MBv5it-Cx_PWgI
      - 證實網傳訊息
      - 複製貼上他處內容而不付出處 https://cofacts.tw/reply/7ovD74MBv5it-Cx__Gii
  - lewis nick: https://cofacts.github.io/community-builder/#/editorworks?type=0&day=40&userId=hotQ1YMBv5it-Cx_alBz
      - 有請人打 165 跟報案 https://cofacts.tw/reply/8IuE1YMBv5it-Cx_f1AR
      - 也有複製貼上文章不付出處如 https://cofacts.tw/reply/6IuA1YMBv5it-Cx_6FBy
  - selene raymond: https://cofacts.github.io/community-builder/#/editorworks?type=0&day=40&userId=h4tQ1YMBv5it-Cx_xVDM
      - 複製貼上他處訊息，但用另外的出處。出處應確實是防詐粉專。 https://cofacts.tw/reply/p4tk1YMBv5it-Cx_g1CP
  - violet horace: https://cofacts.github.io/community-builder/#/editorworks?type=0&day=40&userId=-Ivj9IMBv5it-Cx_b2zj
      - 僅一篇
      - 複製貼上無出處
  - bach coverdale: https://cofacts.github.io/community-builder/#/editorworks?type=0&day=40&userId=6ovP6IMBv5it-Cx_8WLQ
      - 僅一篇
      - 複製貼上無出處
- Login using Facebook (註冊時間 10/11~10/19)
  - Sedekahsessek: https://cofacts.github.io/community-builder/#/editorworks?type=0&day=40&userId=sYuc74MBv5it-Cx_p2gL
    - 註冊 email: outlook.com.vn
    - 幫 Obercoin 推廣其「防詐」訊息 https://cofacts.tw/article/296ig4x00l9pl
    - 都不付出處
  - Ghifer Pendi: https://cofacts.github.io/community-builder/#/editorworks?type=0&day=40&userId=MotoxoMBv5it-Cx_CkHM
    - 註冊 email: outlook.co.id
    - 聲稱為真、沒付出處 https://cofacts.tw/reply/SIt1xoMBv5it-Cx_IUGn
    - 僅兩則
  - Hassam Baloch: https://cofacts.github.io/community-builder/#/editorworks?type=0&day=40&userId=8os71IMBv5it-Cx_ik7o
    - 註冊 email: outlook.com
    - 僅一則；複製貼上，沒付出處
  - Paulo Cardoso: https://cofacts.github.io/community-builder/#/editorworks?type=0&day=40&userId=QYtwxoMBv5it-Cx_y0E6
    - 無 email
    - 三則
    - 複製貼上新聞網或內容農場連結
    - 葡萄牙人名 [name=nuno]++

----

- Considering: [name=mrorz]
    - 目的似乎為推廣特定關鍵字
    - 目前沒有針對 article 的下架機制
    - 有很多篇
- Article block 機制：
    - user block --> submit article "block"
    - article "block"：
      - 不會出現在列表（除非有特定 cookie / 在蜜罐裡的人）
      - detail page 也只有在 honeypot 的人看得到
        - wording 再說
    - 核心想法：反 SEO



## 11 月小聚籌備

> 上次檢討 https://g0v.hackmd.io/ysACleHDTBmVMbH_4mi8uQ#%E5%B0%8F%E8%81%9A%E6%AA%A2%E8%A8%8E

- [ ] 日期
    - 11/12 (六) - nonumpa 無法
    - 11/13 (日) - keyholder 無法
    - 11/19 (六) - bil 不行
    - 11/20 (日) - 詢問中
- [ ] 食物
- [ ] 時間
	- 活動時間：14:00 - 17:00
	- 時間分配
        - 2:00 - 2:20 開場
            - 影片
        - 2:20 - 2:40 引導註冊網站、介紹評價現有回應
        - 2:40 - 2:50 實作評價
        - 2:50 - 3:10 介紹補充資訊
        - 3:10 - 3:40 實作補充資訊、自我介紹、休息
        - 3:40 - 4:10 介紹撰寫新回應
        - 4:10 - 4:40 實作撰寫新回應
        - 4:40 - 5:00 介紹分類、RSS、合照
- [ ] 投放目標：雙北 + 基隆
- [ ] KKTIX：https://cofacts.kktix.cc/events/cofactseditor32
- [ ] 誰會來呢：bil, mrorz, nonumpa
- [ ] 無法來：
- [ ] LINE 文案 
假新聞四處亂竄，對於厭煩吵架與對立的你，如果用一個下午的時間，參與本次志工活動，將可以對社會創造偉大的貢獻！
Cofacts 真的假的 在9月25日本週日下午 2 點- 5點  ，徵求新的查核協作志工，活動完全免費，現場供應點心，邀請你的到訪與參與！用鍵盤與智慧，為周圍的朋友與大家帶來和諧的力量。
(記得帶筆記型電腦與充電線唷！)
時間：9月25日(日) 下午 2 點- 5點
地點：台北市中山區民權東路二段46號4樓-401房
最近的捷運站是中山國小站 
- [ ] [投影片更新](https://docs.google.com/presentation/d/1N9DxoN1NuxdtQILkcV67y_q8EM8CJF5GhoYLcCKFpAc/edit#slide=id.g13dfd29df0b_0_322)
    - [ ] 有提到個人貢獻圖，但可以加講列表，回來看其他人對自己回應的評價
    - [ ] community builder 增加「我想補充」的數字

## article list with video

list page 播放影片問題
- 喜歡自動播放 [name=bil]
  - 有圖但不自動播放也可以
- 播放的話會卡住、吃頻寬，希望只有封面圖 [name=cai]
- youtube: hover 才播放
  - cai, bil 覺得喜歡
  - 手機版另外想方法

:::success
短解：把 autoplay 先關掉
:::

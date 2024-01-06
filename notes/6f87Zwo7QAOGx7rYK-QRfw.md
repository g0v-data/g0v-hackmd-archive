---
tags: cofacts
GA: UA-98468513-3
---

Youtube scrapping alternatives
=====

:::info
相關討論
- [20200511 Slack](https://g0v-tw.slack.com/archives/C2PPMRQGP/p1589175218421000)
- [20200513 會議記錄](https://g0v.hackmd.io/@mrorz/BJ2GzyK9L#Youtube-API-audit)
- [20200520 會議記錄](https://g0v.hackmd.io/TfMlpKYhS3-boaLTgiriYg?view#Youtube-API-audit)
:::

:::danger
到期時間：2020/5/29 
（Youtube 通知時間為 2020/5/8，並給 15 工作天改善）
:::

## 需求

- **檢索**：能檢索到影片標題或 description 符合 query 的文章
- **存檔**：原始影片下架後，編輯仍然可以知道原本影片的標題與 description

## 目前實作
遭遇 youtube 網址時，使用 youtube API [`yt.videos.list()`](https://github.com/cofacts/url-resolver/blob/master/src/lib/fetchYoutube.js#L18-L21) 抓取該 youtube 影片 title & description

此 youtube title 與 description 會暫時儲存在 `urls` index。

- 若一天後沒有任何 articles 或 replies 引用到此 url，此 `urls` 文件就會被清除。
- 若帶有 youtube URL 的文章被存進資料庫，則該 `urls` document 會永遠保存。

例子：https://docs.google.com/document/d/1hlFszsLV9uUJl17L40o6AGZVtyAEoTcLA76wSz969QI/edit

## 目前用量

rumors-api 平均每 3 ~ 5 秒就會要呼叫一次 youtube API 查 title 與 description。
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_42fc489f1c9b6faf7f4e1805ed3b9547.png)

COVID-19 期間，我們每天幾乎都會把 Youtube API 的「20K query/day」 quota 用滿：

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5c9ce5d7830b5993d1cda0b6a76e9b0a.png)


## 遭遇問題

上週 Cofacts 配合  Youtube API Services Team 的 audit 調查，對方表示 Cofacts 在下面兩點不合格：
1. 沒有在 Privacy 與 ToS 中提及 Youtube ToS - [Policy #: III.A.1,2](https://developers.google.com/youtube/terms/developer-policies#a.-api-client-terms-of-use-and-privacy-policies)
2. 沒有每 30 天就重新更新爬到的 non-authorized 資料 - [Policy #: III.E.4.a-g](https://developers.google.com/youtube/terms/developer-policies#e.-handling-youtube-data-and-content)

第二項會影響 Cofacts 的使用——一但原始謠言影片被下架，30 天內資料庫被強制更新，那個影片的 title 與 description 就會被洗掉。

以 [audit 文件內的舉例](https://docs.google.com/document/d/1hlFszsLV9uUJl17L40o6AGZVtyAEoTcLA76wSz969QI/edit
)為例，謠言本體剛好是個被下架的影片，拿另一個被重新上架的影片去查，還能查到對應的訊息。

Cofacts 之所以製作 URL preview，其中一個目的就是為了保存訊息被回報的當下，連結裡面的內容，以供未來查詢比對。如果要求我們每 30 天要更新，效果會大打折扣，以上面這個 COVID-19 陰謀論的例子來說，甚至會影響到 COVID-19 的防疫。

## Mitigation

### Do nothing

Cofacts 在 Youtube 的 API client 會就此失效。

由於[目前程式](https://github.com/cofacts/url-resolver/blob/05400af9a22c52e178783967322bf6bfd01c01ee/src/resolvers/resolveUrls.js#L19-L20)一偵測到 youtube 就呼叫 youtube API，一但 API client 失效，所有 youtube URL 都會抓不到東西。

:warning: **檢索**與**存檔**兩個需求都無法達到。

### 每 30 天重爬所有 youtube

我們可以每天檢查 `urls` 、`articles.hyperlinks`、`articles.replies` 的 youtube 連結，如果 `fetchedAt` 超過 30 天就重新 fetch 新的。

:heavy_check_mark: 30 天內可以**檢索**與**存檔**
:warning: 一但內容下架 30 天之後，**檢索**與**存檔**兩個需求都無法達到。
:warning:  另外，這也會影響我們已經緊繃的每日 youtube API quota。

### 使用 url-resolver 存檔

不使用 Youtube API，直接用 url-resolver 針對 youtube 網頁存檔。

- 桌面版 youtube 執行 JS 後，HTML 約 2MB
  - 可抽取標題、正確的 `topImageUrl`
  - 抓不到 description
- 手機版 youtube (`m.youtube.com/watch?v=N-4jF62FpY8&app=m`) 執行 JS 後 HTML 約幾百 KB
  - 可抽取標題
  - `topImageUrl` 會抓到推薦影片的（錯的 `topImageUrl`）
  - 抓不到 description

:heavy_check_mark: 完全沒用到 Youtube API；爬蟲行為則是有被 [Terms of use 規範](https://www.youtube.com/t/terms)，只要遵守 robots.txt 應該就沒問題。
:warning: **檢索**與**存檔**兩個需求都達到一半（至少有標題）


### 使用 vector

在 articles & replies 不儲存影片標題與 description，改存 embedding vector

query 時使用類似 https://github.com/lior-k/fast-elasticsearch-vector-scoring 這樣的工具來進行檢索。（註：elasticsearch 7 [有內建 `dense_vector`](https://www.elastic.co/guide/en/elasticsearch/reference/7.7/dense-vector.html) 但是是 x-pack 好像要錢 QQ。第三方 vector plugin 好像可以支援到我們用的版本。）

:heavy_check_mark: 符合**檢索**功能（有待實測）
:warning: 不符合**存檔**需求。

### 嵌入預覽視窗

使用 url-resolver 抓取 youtube 網頁存檔（`html`），另開 API 直接輸出 HTML 本體。這樣就能直接做一個顯示網頁當時狀態的 iframe 視窗，讓編輯看看。

不過，由於 cofacts-url-resolver 不會儲存 CSS，所以存下來的 HTML 檔案，在顯示時，會變成下圖右邊這樣：

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8d9cd27c3964d3afe1b0a19749c1b02a.png)

如果需要一個「單檔包含 CSS 與圖片」的存檔機制，可以參考 [SingleFile](https://github.com/gildas-lormeau/SingleFile/tree/master/cli) (AGPL 授權)

:heavy_check_mark: 可能有些許**存檔**功能。可與其他 solution 搭配使用。
:warning: 無 CSS 的**存檔**功能，在 youtube 這種介面複雜的網站，可能讓編輯還是有看沒有懂；除非改用 SingleFile
:warning: 無**檢索**功能


### 使用 oembed 格式

[oembed](https://oembed.com/) 定義了分享給第三方嵌入的共享資訊格式，在不需要解析的情況下，能拿到基本的資訊。


例如： https://www.youtube.com/oembed?url=http%3A//youtube.com/watch%3Fv%3DM3r2XDceM6A&format=json

```
{
  "provider_name": "YouTube",
  "width": 480,
  "title": "Amazing Nintendo Facts",
  "thumbnail_width": 480,
  "author_url": "https://www.youtube.com/user/ZackScott",
  "version": "1.0",
  "height": 270,
  "author_name": "ZackScott",
  "html": "<iframe width=\"480\" height=\"270\" src=\"https://www.youtube.com/embed/M3r2XDceM6A?feature=oembed\" frameborder=\"0\" allow=\"accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture\" allowfullscreen></iframe>",
  "type": "video",
  "thumbnail_url": "https://i.ytimg.com/vi/M3r2XDceM6A/hqdefault.jpg",
  "thumbnail_height": 360,
  "provider_url": "https://www.youtube.com/"
}
```

:heavy_check_mark: 完全沒用到 Youtube API；
:warning: **檢索**與**存檔**兩個需求都達到一半（只有標題跟縮圖）

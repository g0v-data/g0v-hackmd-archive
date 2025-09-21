# 護樹開開放資料協作地圖


## 緣起

[樹下沒有陰影:揭開城市樹木修剪的隱憂](https://www.canva.com/design/DAGpomHu6do/w8b6bIKu0TZP4CxoTnYKtA/edit?utm_content=DAGpomHu6do&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)

## 使用者體驗流程 - 手機mobile UI為主


圖文說明：

[我有一棵樹P37-P91](https://www-ws.gov.taipei/Download.ashx?u=LzAwMS9VcGxvYWQvNjg2L3JlbGZpbGUvNTU0MzcvODMzODI5MC9lZmJhODgwNC1hM2NiLTRjN2EtODZkMC1iNjg4N2Q4ZDhlMGIucGRm&n=5qqU5qGIMS5wZGY%3d&icon=..pdf)


操作：

1. 看到被不當修剪的樹
2. 可以拍照、定位(使用GPS定位功能)、上傳資料庫
3. 提供樹木修剪、問題環境的選項
4. 可能染病的圖片參考介紹


## 類似專案


### 無麩質餐廳地圖
介面初稿：https://gf-tw.pages.dev/
原始碼： https://github.com/bestian/gf-tw

(差異點：需要上傳圖, 故比較適合用cloudFlare R2 + D1)


## 目前使用者流程與資料集中點


### facebook護樹的爆料公社
[facebook護樹的爆料公社](https://www.facebook.com/groups/treefighter/?locale=zh_TW)

問題點：facebook沒有開放API，資料難以直接抓取



## 另開資料集中點


工程架構：

## 1. **Cloudflare R2 + D1** （自建 API）

> 適合熟悉 Cloudflare Workers、希望長期擴展的專案。

| 項目         | 說明                                                      |
| ---------- | ------------------------------------------------------- |
| **文字資料**   | 存在 **Cloudflare D1** （SQLite-based serverless DB）。      |
| **圖片檔案**   | 存在 **Cloudflare R2** （S3 相容 Object Storage）。            |
| **API 介面** | 自己寫 Cloudflare Worker 提供 JSON API，例如： `/api/posts`      |
| **成本**     | R2 免費 10 GB / 月傳輸，100,000 次操作/月；D1 免費 5M rows。          |
| **難度**     | **中高**：需要自己寫 Worker，處理認證、API 規格、R2 簽名網址（presigned URL）。 |

**優點**

* 免費額度夠中小型專案使用。
* 整合度高：同一個 Cloudflare 帳號完成。
* Workers 可做 serverless API，擴充空間大。

**缺點**

* **必須自己寫後端程式**。
* 前期設定比較複雜，尤其是圖片上傳（R2 簽名 URL 流程）。

**簡單架構**

```
前端(Vue) <--> Worker API <--> D1 (文字)
                          <--> R2 (圖片)
```

---





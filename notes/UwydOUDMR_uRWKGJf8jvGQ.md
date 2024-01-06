---
tags: privacy, new-safeID
---

# new safeID have-i-been-pwned 換掉外洩的身分證字號

# Action Item
## P0 Issues
- 想有沒有更炫的名字
    - "被駭小夜市"（NightMarketPwned）：夜市是台灣文化的一個重要象徵。這個名字暗示這個服務就像一個小夜市，為你提供各種有關是否被駭的信息。
    - "網駭鹹酥雞"（CyberFriedChicken）：鹹酥雞是台灣的一種非常受歡迎的小吃，這個名字以此為靈感，象徵該服務是你在網路世界中的防護盾。
    - "駭客熊貓眼"（HackerPandaEye）：熊貓眼（Panda Eye）在台灣常用來形容熬夜後眼圈黑黑的狀態，這裡用來象徵你如果不保護你的個人資料，可能會被駭客攻擊，讓你熬夜擔憂。
    - "智駭豆花"（SmartTofuPwned）：豆花是台灣著名的甜品，這裡將它與智能（Smart）和被駭（Pwned）結合，形成一個有趣的視覺影像，表示該服務是用來檢查你是否成為黑客的目標。
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8120320b3be8795ce85217f4f6b3175a.png)

## P1 Issues
- 開 GitHub org
    - private repo 
    - 尊絕不凡 student developer pack
- notion 共用 page
- 把預期開發功能切出來
- 準備去大松
- 找類似功能的 repo 放上來參考

---

## contributor
Vincent550102、貝吉樂、Wancat、子期

## repo
https://github.com/Vincent550102/haveidbeenpwned

## 技術

* Python FastAPI
* Vue.js
* MySQL

Hash method: SHA256

### API spec

| Endpoint | Query | Response |
| -------- | -------- | -------- |
| /api/leak | id_number |  |

```json
{
      leaks: [
        {
          name: "2023台灣個資外洩事件",
          columns: [
            "姓名",
            "出生年月日",
            "性別",
            "身分證字號",
            "戶籍地址",
            "戶籍郵遞區號",
            "通訊地址",
          ],
        }
      ]
    }
}
```

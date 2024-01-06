---
tags : vTaiwan小松
---
#  20191127 vTaiwan 小黑客松
時間：2019/11/27 週三 19:00-21:00
地點：社會創新實驗中心 2F A9 會議室（ 地圖：https://goo.gl/maps/X65uN9PFXAo ）
待辦事項區：[vTaiwan 待辦事項（歡迎認領工作）](https://g0v.hackpad.tw/vTaiwan--AuHFzoOJk7o)
出席：Ronny, Scott, 乾庸, 伊庭, peace, 虹文, 孟翰, ddio, 哲輔, 怡孜、姵璇、仔魚
線上組：
線上參與連結：https://meet.jit.si/vtaiwan
Wifi：PDIS_Public_5G/ji394pdis、startup99/306306306

主持人(facilitator)：
Translation：[English](https://translate.google.com/translate?hl=en&sl=auto&tl=en&u=https%3A%2F%2Fg0v.hackpad.tw%2Fep%2Fpad%2Fstatic%2FleY4KC9wlOL&sandbox=1)

預定流程
18:30-19:00 報到 Arrival and Registration
19:00-19:15 開場、自我介紹
19:15-19:30 確認討論議程
19:30-21:00 討論&hacking
21:00-21:30 成果分享&決定下週主持人
下週主持人：

提案（自己的小松自己提案）
---
- 透明足跡計畫：掃條碼出奇蹟，揭開商品背後看不見的資訊
    - 綠色公民行動聯盟（反核、能源轉型、透明足跡）
    - 透明足跡，四年前開始啟動／兩年前網站上線。
    - 從資料開始，推動企業環境表現改變／補上政府管制漏洞
    - APP構想，透過條碼，得到背後的食安／衛生／環境／勞工資料／產品內含成分
    - 食安資料：各地政府開放程度相當不一，針對食安資料的具體內容，目前尚在盤點中。
    - 勞動資料：同食安資料，需要去看什麼樣的勞動資料，勞權相關的比較查得到。
    - 跨領域cross-check：例如賣飼料油的公司勞動紀錄也很糟糕。
    - 條碼資料：[GS1公司前置碼查詢](http://www.gs1tw.org/twct/web/codesearch.jsp?REGIST=01) ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8e732e0b8f0ef783e0be1399e36d02bd)
    - 智財局有整理商標登記資料，可以看使用上有沒有需要納入一起作為識別方式。
    - 商品成分（塑膠微粒、食品添加物、重金屬含量等）
    - 商品比較功能
    - LINEBOT使用可能性？
        - 是否有產品比較的需求？
    - 階段性成果：使用Python [GITHUB](https://github.com/Coopathon2019/13_thaubing/blob/master/main.py)
        - api: https://thaubing.gcaa.org.tw/json/corp/%7B%E7%B5%B1%E4%B8%80%E7%B7%A8%E8%99%9F%7D
    - 客群設定：APP與LINEBOT的取向不同
        - 對使用者的想像是什麼
        - 呈現結果要如何處理
    - 資訊呈現的前台設計
        - 針對不同商品是否要有不同的呈現
    - 要不要針對一個商品去執行
    - 社會學與心理學的脈絡去設計使用者的一天，來決定怎麼規劃產品。
    - 問卷：詢問群眾對於不同產品的想像
        - 需要什麼樣的反饋結果。
        - 使用者什麼時候會想要掃。
        - 使用者回饋機制
    - 有沒有設計網頁版的需求？
    - 條碼對應到特定的公司，條碼是看不出產品的
（公司名稱是公開資料／可以看出產品，只是是非公開資料）
    - 美國類似的app - [buycott](https://www.buycott.com/campaign/browse)：可以訂閱關注不同議題去自訂自己的filter 
    - 台灣類似的app - [冰的啦](https://play.google.com/store/apps/details?id=com.oriand.whosbad)



- Steven：其實我們還沒認真討論過「人臉辨識」這題
    - 有哪些討論面向？
    - Pending
    - 針對私部門的限制
    - 針對公部們的限制
    - 便利商店的鏡頭做人臉辨識
    - 從個資法角度切入？
        - 個資法定義上的個人資料：指自然人之姓名、出生年月日、國民身分證統一編號、護照號碼、特徵、指紋、婚姻、家庭、教育、職業、病歷、醫療、基因、性生活、健康檢查、犯罪前科、聯絡方式、財務情況、社會活動及其他得以直接或間接方式識別該個人之資料。
        - 想討論的是蒐集？處理？利用？
        - 人臉不是個資？
    - Ronny：比起禁止個人覺得更應該讓私部門負揭露義務
        - 告知的方式
    - ddio：同意的程序可能要比照血液研究
    - 資料的處理和利用
    - 要討論的話應該找[國發會個人資料保護專案辦公室](https://www.ndc.gov.tw/Content_List.aspx?n=726A44EA5D724473)
    - 開議題共筆：https://g0v.hackmd.io/kNrhqh7VR8KJ1uoCwJjfIw?view

- Ronny：應該要來研究一下Decidim
    - 目前西班牙的某個城市（馬德里？）有實際使用
        - 查一下他們的case
    - 台灣比較常用 polis （只有徵集和分類意見）， vTaiwan 可以討論的政策也有限
    - 可以推廣一套容易透過網路政策討論的工具
    - homework大家回家試玩一下
    - 邀請小班帶卡片來分享一下
    - [多倫多也有用 decidim 討論](https://www.i-media.tw/news/detail.html?id=14469)

- [Social Value International](https://svic2019.socialvalue.org.tw/)
https://www.sametri.ca/
IMPACT REPORTS
https://www.sopact.com/
Impact Measurement
https://www.shanzhai.city/


分享
---


todo（想在小松完成的事情）
---

小松果
---
- 綠色公民行動聯盟來介紹透明足跡，尋求建議或入坑：
    - 你在購物時，會因為什麼因素會特別花時間挑選該買什麼牌子呢？ 
    - 太多討論了～詳見共筆：https://reurl.cc/nVypGd
- 人臉辨識技術之管制（名稱暫定）議題開坑：
    - https://reurl.cc/L1V2G4
- Decidim：
    - 請小班有空來分享
    - 大家回家試玩一下
    - 連結在這裡：https://decidim.org/
- Social Value International Conference
    - 有想要提供介紹方向的，請寫在共筆！

vtaiwan 基金餘額
---
* 本日花費:
* 本日現場贊助: 
* 捐款: 
* 餘額:






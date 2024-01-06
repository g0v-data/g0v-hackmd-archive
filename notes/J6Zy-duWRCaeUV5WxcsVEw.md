---
title: "薪資與租屋居住品質關聯調查"
tags: 土地,居住,hackpad
---

# 薪資與租屋居住品質關聯調查

> [點此觀看原始內容](https://g0v.hackpad.tw/hZwt2iPr78w)


主旨：運用各項官方薪資數據，分析台灣勞工合理可負擔租金的實際居住品質

說明：居住權是重要人權指標，《經濟、社會與文化權利國際公約》第11條規定締約國應以適當步驟確保人民擁有適當的居住權。美國於1969年通過「住房及城巿發展法案」(Housing and Urban Development Act)修正案，明訂合適租金應占租戶收入的25％，1981年再將25％的上限提高到30％，被稱為「30％經驗法則」(註一)，意即租金超過所得的30%已屬租金壓力過大將對其他生活支出造成資源排擠，25％至30％則為可承受範圍。

簡報：
- 提案簡報
    - [https://docs.google.com/presentation/d/1ys5ZXO2tPly0sxVNnDEhNYJVgMoARyjTmUGUIzI6uH0/edit#slide=id.g345520f6c2\_0\_18](https://docs.google.com/presentation/d/1ys5ZXO2tPly0sxVNnDEhNYJVgMoARyjTmUGUIzI6uH0/edit#slide=id.g345520f6c2_0_18)
- 20180726「六都居，易不易！？」勞陣公布六都基本工資租屋能力調查
    - [http://labor.ngo.tw/news/news-now/800-news20180726](http://labor.ngo.tw/news/news-now/800-news20180726)

**專案想法**：運用**官方各主要薪資數據**(ex.基本工資、薪資中位數、家戶可支配所得...)，以**25%至30%為可負擔租金**範圍，**搜尋大型租屋網站**資料Data進行台灣各縣巿薪資所得與租屋居住品質關連調查分析。
ex.用基本工資22K計算出可負擔合宜租金為5500(22000X25%)~6600(22000X30%)元，調查各縣巿的平均空間坪數／租屋房型(頂加/木隔間)／租屋的區位分布／房東對房客的十大限制或要求......
→591租屋網 [https://rent.591.com.tw/rent-detail-6084140.html](https://rent.591.com.tw/rent-detail-6084140.html)
> 這裡有 591的歷史資料： [https://www.591.com.tw/webService-market.html?type=1](https://www.591.com.tw/webService-market.html?type=1)
> [name=ddio J]

> 租屋相關資料可看這篇 [https://g0v.hackpad.tw/x1M9qr6Syqw](https://g0v.hackpad.tw/x1M9qr6Syqw)
> [name=ddio J]

→好房網快租 [https://rent.housefun.com.tw/](https://rent.housefun.com.tw/)

**範例**：運用2018年基本工資22,000元，以5500元至6600元為租金條件，調查台北巿部分區域在此條件內的租屋物件，
591：[https://rent.591.com.tw/rent-detail-6034072.html](https://rent.591.com.tw/rent-detail-6034072.html)
好房網：[https://rent.housefun.com.tw/rent/house/1360935/](https://rent.housefun.com.tw/rent/house/1360935/)
即可獲得租金／押金／坪數／樓層／ 樓型／屋型／房東要求條件／租屋提供設施／居住區位／屋況....等數據資料，運用這些數據資料進行統計分析，用來調查當前租屋勞動者的真實居住品質。

**專案需求**：邀請爬蟲高手協助爬出租屋網內的物件資料，依資料欄位轉為excel以便進行統計分析

延伸閱讀：鏡周刊 台北不是我的家 租屋黑巿大揭露
[https://www.mirrormedia.mg/projects/rent-house/](https://www.mirrormedia.mg/projects/rent-house/)

(註一：引自維基百科條目：Brooke Amendment，瀏灠網址[https://en.wikipedia.org/wiki/Brooke_Amendment](https://en.wikipedia.org/wiki/Brooke_Amendment))


### 需要的資料

需要 591 的即時資料，因為需要這些資料
- 案號
- 六都
- 照片
- 頂加、地下室、隔間（查得出來嗎 XD）
- 刊登時間、更新時間、關閉時間
- 租金
- 坪數
- 身份限制（學生、上班族）
- 性別
- 提供的設備
- 特色說明
- 大概的地點（591 會給 gps ）

### 資料勘誤追蹤

- [資料來源](https://drive.google.com/drive/u/0/folders/1BduObGhc4d2aHEn6ZXpOTyWA5aBB0cJW)
- 結構化資料（rental_house.zh.76k）
    - 問題：
        - [x] 有3896筆無縣巿及鄉鎮巿區
        - [x] 額外費用_清潔費？似有誤判，如6301745及6301857及6302245：原始資料均為\['含清潔費', '第四台', '網路', '水費'\]，但額外費用＿清潔費均登錄為1
        - [x] 身份限制:編碼類型有誤(限上班族及限家庭,與限上班族均計為1)
            - [x] 新增591專屬欄位
        - [x] 可炊、寵物:按理應該有部分房東未填(coding碼視為99),但全部都是可(1)與不可(0)
            - [x] 未填算未填 =\> -
        - [x] 無隔間材料、法定用途,但身份限制在(欄位CD)重覆出現
        - [x] 物件時間其實是網址
        - [x] 格局編碼字串
        - [x] 交通
            - [x] 刪除「近  公車站」 ex: 6295308
            - [x] 高鐵均為0,有誤
            - [x] 新增有公車/捷運
            - [x] 公車有結尾為「路」的
        - [x] Boolean 改成 True: 1 ,  False: 2
        - [x] 提供家具 =\> boolean list
        - [ ] 平面車位
        - [ ] 最短租期
        - [x] 押金沒抓到 1,000 -> 0,  6348330
        - [x] 面議押金有金額 5916005, 6329580
    - 建議：
        - [x] 提供家具(CE)比照額外費用模式做coding(只呈現1,0)
        - [x] 附近交通，只呈現1,0(即有與無,不再以數量計算，因為數量認定有爭議)
        - [x] 需要管理費(Q)：591網頁上有些呈現為管理費：無，有些未列，原始資料應呈現"無"(coding碼為0)與"-"(coding編碼為9)，予以區別。
- 原始資料（rent591.60k）
    - 問題：
        4.  無法法定用途
        5.  樓層(G)會變成X月X日,但不影響

## 有意思的案例


1.  各種身份限制系列
    1.  不要小孩
        1.  [適合~單身外派主管~兩人租用...或~新婚夫妻~小家庭..無小孩.....](https://rent.591.com.tw/rent-detail-6355345.html)
        2.  [不適合者: 有養寵物者,抽菸者,有小孩者,55歲以上者,. 不便之處請原諒](https://rent.591.com.tw/rent-detail-6355330.html)
        3.  [14\. 不適合者: 抽菸者, 有寵物者, 有小孩者, 無職業者, 55歲以上者, 不便之處請原諒](https://rent.591.com.tw/rent-detail-6355334.html)
        4.  [不適合者:抽菸者,養寵物者,有小孩的家庭,55歲以上年長者,不便之處請原諒](https://rent.591.com.tw/rent-detail-6306773.html)
    2.  「青年」住宅
        1.  [入住年齡限滿20歲不得超過45歲](https://rent.591.com.tw/rent-detail-6349068.html)
        2.  [入住年齡限滿20歲不得超過45歲](https://rent.591.com.tw/rent-detail-6315965.html)   again
        3.  [歡迎上班族與學生預約看屋，不抽菸，年齡18~50歲尤佳， (預約看屋請優先以電話聯絡，房東太太不太會用網路)](https://rent.591.com.tw/rent-detail-6296728.html)


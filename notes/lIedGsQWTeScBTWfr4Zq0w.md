---
tags: cofacts
GA: UA-98468513-3
---

# User Profile Page Pilot Study

## 實驗進行方式

- 使用 rumors-site
    - 版本：[PR#375](https://github.com/cofacts/rumors-site/pull/375)
    - 數字資料僅有「replied messages」、「voted replies」
    - 內容僅有「Replied messages」分頁
        - Filter：時間 filter、reply type filter、主題
        - 排序：「最近被查詢」、「最近被回應（不限正在看的 editor）」、「最多人詢問」
    - editor 可以編輯自己名字、URL、bio，但尚未實作更改頭像功能
- 對象：4 位編輯
    - 等級為 Lv.14（ㄅ）, Lv.14 (ㄆ), Lv.17 (ㄇ), Lv.16 (魔人啾啾)、Lv 16 (尚未整理)、Lv 0 (negi)
- 進行方式
    - 使用即時通訊軟體（messenger/slack）問答
    - 先使用開放式問法問「有什麼想法」，然後引導往不同的方向（社交價值 or 自我實現）抒發想法
    - **收集參與者「自主提出」的想法**來驗證 hypothesis；若沒有提出，可能就是目前的 profile page 不支持該 hypothesis。
    - 最後將對話整理為列表，向參與者確認
        - 是否願意公開在此份報告 or 僅限內參
        - 若願意公開，則在此份報告想使用的名字 or 匿名


## Hypothesis

Profile page 的設計希望提供使用者三大價值，假設參與者可以接收到下面價值：

1. 社交價值假設：公開的 Profile page 對編輯有正向的社交價值，好處大過風險。
2. 自我實現假設：Profile page 讓編輯獲得成就感或其他心理價值。
3. 正向循環假設：Profile page 提供的社交價值與自我實現，會鼓勵編輯繼續貢獻。

## Pilot study 結果

以下為受測編輯在被問到「有什麼想法」時，自主提出的觀點。

### ㄧ、社交價值假設

1. public profile 的好處
    - 找工作時可以作為經歷 [name=ㄅ]
        - 專欄寫作的經歷可以附上專欄網址，Cofacts 這裡也可以有一個 profile 網址可以付的話會很好用
        - 其他編輯若想要，可以把 Cofacts profile URL 放在自己 FB 個人資料中，作為自己的 about me
    - 整體來說公開 profile page 沒有問題，都是既存公開資訊 [name=ㄅ、ㄆ]
2. public profile 的 risk [name=ㄅ]
    - 之前寫了有些逆風的回答，還沒有想太多，但集中在一個地方公開，確實可以被有心人看出價值偏好，使自己有些 hesitate
    - 自己的 Mitigation: 會把名字改為不那麼直接連結到自己的匿名。
    - 建議給社群 mitigation 空間：先個別告知編輯們此功能在何時對外公開，讓大家有幾天的時間思考與組織自己的 profile page，比較不會有突然被看光光（？）的感覺。
3. 看到其他人的 profile 的感受 [name=ㄇ]
    - 覺得新鮮
    - 不用登入就能看到任何人的數據很方便
    - 看自己的 profile 與看他人的 profile 時，想看到的資訊沒有差別。
4. 在看了其他人貢獻之後，會好奇他加入 Cofacts 的時間 [name=魔人啾啾]
5. 提出「本週編輯王」的發想，不過認為對新編輯的激勵效果可能不大 XD [name=魔人啾啾]
6. 幫回應按讚時有遇到好像亂回的，此時會想要看他的 profile page [name=negi]
    - 看自己的 profile page 的時候又擔心會讓人在私底下找到自己 [name=negi]


### 二、自我實現假設

1. 偶爾會想知道自己付出的影響力 [name=ㄅ]
    - 認為下面的兩個數字可以作為影響力的回饋：
        - 最多人評價的回應
        - 回應過的訊息的瀏覽量最高的
2. 會希望知道哪些回應沒有回到點、被按「覺得沒用」 [name=ㄅ]
    - 目前沒有其他自動化的方式知道自己的回應被按「覺得沒用」
    - 會希望 profile page 的篩選條件可以做到這些（以及上面影響力的部分）
3. 覺得不錯，看到了想看到、但很難自己去計算的資訊，例如自己的 [name=ㄇ]
    - 回了多少訊息的數字
    - 按了多少讚
4. 看到自己 profile 的感受 [name=魔人啾啾]
	- 覺得 Profile page 很可愛。跟自己比較，看著自己能量值不斷累積，覺得能量值上升。
	- 看到自己稱號覺得有趣，過去只會默默地出現在旁邊，現在則可以看到自己的表現力。
5. 希望對每種主題都有獎牌（badge）[name=魔人啾啾]
	- 鼓勵編輯橫向涉獵新領域的知識，擴展自身視野
	- 前提是預設編輯真心想要了解未知領域，而非為了拿 badge 而亂回
6. 持續在 Cofacts 的動力：獲取知識、親友互勉 [name=魔人啾啾]

### 三、Usability suggestion & bug reports
1. reply type filter 過濾後會出現不符合的 reply type (known issue) [name=ㄅ]
2. 希望換頭像時，依序嘗試點按了 (1) 圓形圖片中央、(2) 右邊的 edit 按鈕 [name=ㄅ]
3. banner 上顯示 voted reply 總數，會想點按看看，希望可以看到自己對哪些回應評價過 [name=ㄅ]
4. 針對 profile page 的正面描述
    - 很棒很清楚 [name=ㄆ]
5. 針對現有 Cofacts 網站其他部分的建議
    a. 時間「N天前」可以用確切時間，不然都要自己算 [name=ㄆ、ㄅ]
        - 在尋找自己過去寫的闢謠時，因為寫了兩次所以想要用時間找，但都寫 N 天前很難辨認 [name=ㄅ]
        - 查看什麼時候回應的時候，相對於「約 3 年前」，「2018/4/2」更明確 [name=魔人啾啾]
    b. upvote / downvote 有網軍利用洗評價的可能 [name=ㄆ]
        - 之前就注意到，一直有擔心
        - 已經用[編輯認證制度](https://g0v.hackmd.io/naJGBDO0QFW4b4H4M9ElIw#%E6%B4%97%E7%89%88%E8%A8%8E%E8%AB%96)回應其擔憂
6. filter 因為自己要做「還未有有效查核」希望放在前面，「我查核過」因為是自己查過的，會想要在後面 [name=negi]
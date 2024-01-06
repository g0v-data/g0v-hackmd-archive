---
tags: AI
---


# LLM 我的家鄉
###    專案開始日:2023/8/26(六)
####    歡迎大家在這裡分享LLM相關的資訊及專案相關的內容~



##    專案簡報連結如下:
現有問題:
- 沒回答到重點
- 提供錯誤回答 (幻想)
目的: fine-tune LLM(Taiwan Llama)，期待輸出符合使用者期待又正確的內容
簡報    https://docs.google.com/presentation/d/1HDAzdcQ9iSkrPAx1ULOAmUHUJWlgmNXB9v54P2LOG0M/edit?usp=sharing

## 如何讓訓練資料符合使用者需求: 
藉由google搜尋自動完成功能, 使用爬蟲以"地名 + keyword"方式建立搜尋關鍵字清單
都市名 + 種子詞
種子詞清單 = ["熱門", "最好", "最棒", "好玩", "推薦", "必去", "旅遊", "景點", "美食", "購物", "娛樂", "文化", "歷史", "特色", "活動", "旅行", "探索", "體驗", "介紹", "親子"]
例:
- 台中 探索
- 台中 熱門

###    以下連結先是台中市的清單(爬蟲goolgle自動完成得到的搜尋關鍵字)後續會再增加其他城市的清單
####    整理模型訓練資料大家一起來
可以參考裡面第一筆紀錄繼續添加喔~
台中:
https://docs.google.com/spreadsheets/d/1uMLXt3ArVLV6bu22nLrtstnMogThnQooe5zZ5TuL3GA/edit?usp=sharing
台北, 新北, 桃園, 台南, 高雄 coming soon


內容建立方向：以未來2-3年仍適用的內容為方向, 不包含經常更動的資訊
如: 活動、天氣預報

## 期待內容
- 實用內容
- 在地化

benchmark: [Taiwan llama spaces demo](https://huggingface.co/spaces/yentinglin/Taiwan-LLaMa2)

##    訓練資料收集:
另外：
也可以讓使用者在使用後可以回饋(cache response)
也可以從FB社團爬評論


##    營運成本考量
後端server成本高
- 雲端託管
- 自架server
    - T4
- CPU

## Alternative Method
爬蟲 + 摘要
向量資料庫
LangChain Q&A



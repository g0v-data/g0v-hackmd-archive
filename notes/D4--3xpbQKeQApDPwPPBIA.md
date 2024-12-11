---
tags: vTaiwan小松
---
# 1108小松 1108 Meetup 
參與連結 / Links：https://meet.jit.si/vTaiwan
參與者簽到 / Participants：Peter, Shu, eli, crystal, T,
本週議題 / Issues：

TttC 應用/上週五討論報告
翻譯與分享進度


## TttC 應用/上週五討論報告
- 下一次大松提案，會提 TttC 的相關的提案
    - [共筆](https://g0v.hackmd.io/@Pno233SAS8G5UfL5OvSRmA/H1OqH1zQ6)
    - 目標是把 TttC 變成社群工具
    - g0v/vTaiwan/AIA/MODA 建立一個新的g0v slack channel 來做。

- Ronny 有測試過 TttC 對 JOIN 平台上意見分群的功能。
    - [成果](https://ronnywang.github.io/tttc-join-test/report3/)
    - [資料來源](https://join.gov.tw/policies/detail/ce9a5e5f-85ab-4cac-9c8d-cf2e5206ea7c)
    - [設定檔](https://github.com/ronnywang/tttc-join-test/blob/gh-pages/example-join.json)
    - [資料](https://github.com/ronnywang/tttc-join-test/blob/gh-pages/example-join.csv)
    - 目前問題：
        - 原先的 sample 是針對 AI 主題並且用英文寫死，為了處理 join 我有改寫兩個部份，其中中文處理用了 [jieba 斷詞](https://github.com/ronnywang/tttc-join-test/blob/gh-pages/clustering.py)，不確定我這邊修改有沒有造成錯判
        - 看起來cluster 還不是很準，他是只看詞的關聯而不是看語義，所以 "我支持同性婚姻"跟"我不支持同性婚姻" 兩句意思完全相反，但是因為只差一個字，因此會被誤認為兩句是同一群 （以上是我粗淺對 machine learning 的了解後做的猜測，不確定我猜測對不對）
        - 五個 cluster 有四個都叫做「同性婚姻合法化」，效果不佳
            - 這個在 eli 整理出的結果也有類似的情形？[name=peter]
                - 資料沒有預處理，可能要去除掉雜訊
                - 也就是說其模型本身是否能夠做出有意義的 cluster
                - 看看能不能拿到 Recursive Public 的資料？
                - 有LLM 的 polis(polis 本身不用靠敘述本身分群) 
                - 或許可以比較看看 TttC 跟 ChatGPT 的摘要與分群方式 [name=josh]
                    - 也可以比較看看不同語言的比較[name=josh]
                    - 可以一併試試看 [name=eli]
    - [測試紀錄共筆](https://g0v.hackmd.io/EMMTcvJRRdG1TbxL7gHrNw)

### 結論
- 可以先開一個文件紀錄與回報相關的問題與改進方向？[name=eli]
    - 可以先試試看 high level 的結果有什麼不一樣，之後再來 pull request [name=josh]
    - 

### 新的想法
- 是否要嘗試其他的質化分析工具：新的工具探索？[name=peter]
    - Input: 探索以生成式人工智慧為基礎（或許不用？）的質化分析與分群工具，以 vTaiwan 與 Join 平台的案例作為測試，然後比較目前各自工具的優劣勢。
    - Output: 整理好之後可以作為文件或報告發布。或者是可以為之後社群自己開發質化分析工具！
    - [Talk to the City](https://github.com/AIObjectives/talk-to-the-city-reports)
    - [Nvivo](https://lumivero.com/products/nvivo/)
    - 幾項指標：技術門檻、分群精準度、摘要精準度、是否開源、費用
        - 合規性、風險管理可以列為指標？ [name=crystal]
            - 個資保護（GDPR）
            - 資料侵權
            - 透明度
                - Stanford 的訴訟風險指標 OpenAI 
    - 要完成的事情：
        - 人工資料集
        - 繼續做議題
            - 生成式人工智慧草案？
            - 校園內生成式人工智慧規範
                - [校園人工智慧誤判抄襲案例](https://www.facebook.com/photo?fbid=10168561071105694&set=a.10150632405965694) [name=crystal]
                - 人工智慧時代下的，證明人類產出的舉證責任。
                - 有潛力XD [name=peter]
            - 司法院人工智慧判決生成系統
            - （即將到來）人工智慧基本法
            - （即將到來）各部會的人工智慧規範



## 目前 OpenAI 
- [OpenAI blog post draft](https://docs.google.com/document/d/1vIWrtpoTxplxyckil5akKNTyRa6d42XgltWpSyZ7Jt4/edit)
- 9/24 會議 highlight 的結論？[name=shu]
    - eli 透過 TttC整理的結果
    - 透過那一份結果自己整理一份報告
    - 結論：三個人分工完成[name=peter][name=shu][name=eli]
        - 個資 [name=peter]
        - 歧視 [name=eli] 
        - 在地化 [name=shu]
        - 11/29 前完成

- 對於歧視議題可以再 run 一輪
    - 看eli 要不要規劃比較細節的構想？
    - 感覺在議題設計與相關問題討論上

- 針對國科會推出的
    - AI 基本法
    - 

## 翻譯與分享進度
- 看 josh 那邊的工作進度
- 翻譯完成！感謝 josh!

## 12/20 小聚
- Teddy Lee 12/18-12/24 會在
- 12/20 小聚實體進行，有 hybrid 模式
- 最近開始來處理場地 [name=peter]

## Todo list
- 把 Bruno 加進群組 [name=josh]
- 質化分析工具的比較(先暫緩)
- [法律爭議整理](https://docs.google.com/spreadsheets/d/1eOShGFv5BX9obg4utTorEcq4odFtIhEqUtejYbiHjpU/edit?usp=sharing)
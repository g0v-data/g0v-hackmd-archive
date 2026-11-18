---
tags: vTaiwan
---
# 20261118 小松

時間 Time ：19:00 - 20:00
地點 Location ：線上 Online
參與者 Participants: Peter, Soth, Tim, shu, Allison 

自我介紹：



https://www.vtaiwan.tw/jitsi 
(請用Google登入以參與視訊並啟用轉錄功能)


::: success
## 專案儀表板：目前 vTaiwan 社群在進行的事情 
以下是 vTaiwan 目前正在進行的幾個不同的專案！如果有興趣，可以在取得共筆編輯權限後+1，或者是
1. [vTaiwan議題小聚](/GUe0KXMsQBC-6KTIUPBVnA)
    - 適合對審議、公共討論有興趣的人加入
    - 活動咖的最愛
    - 如果有公民團體與組織想要合作也可以看過來！
    - 目前也在進行 [AI 用於數位公民參與經驗](/nJUYukWFSWuEsG-XQalHcA) 的收集！
3. [vTaiwan 網站改版，啟動！](/Q3_hgovyRHusEq8-3nomPQ)
    - 目標是打造新的 vTaiwan 網站
    - 結合 blog、媒體資源、活動發佈、建立線上活動與討論等功能
    - [vTaiwan 網站更新後的治理機制](/HxWF11d4Tz-AfHb3yjwQKg)也在建立中
    - 讓不會寫程式的人也可以加入貢獻者！
4. [vTaiwan 主視覺更新](/UqGh6pAUTwuNFr1RE21Rtw)
    - 目前已經設計完成！
    - 會發佈到新的網站，並在社群媒體上完成更新！
5. [Frankly 測試](/HVEdPVQqQHqVwvFECg7sRg)
    - 目前正在測試一個新的線上會議
6. [Civic Talk 測試](/AOQfOmJmS-mcgr2LR4dLQA) 
    - 目前正在測試一個新的線上公共議題討論平台 
8. [vTawian Github Project專案儀表板](https://github.com/orgs/g0v/projects/2)
9. 如果想要提案怎麼辦？
    - 目前的 vTaiwan 很歡迎與數位工具相關的公共討論！
- 如果想要成為協作者或者是貢獻者，我們正在努力讓說明更清楚，介面更友善！
- Q: 對用 AI vibe coding 的人想貢獻怎麼做？
    - 歡迎，vibe coding 建議可以從前端開始入手。
    - 建議步驟：
        - 開一個分支(branch)，在上面寫新進度
        - 進度好了發 Pull Request 回主線
    - 和 AI 講「幫我開分支解決 issue 72」，做好後，請 AI 幫忙發 PR 
    - 負責維護的工程師朋友會幫忙檢查
:::


## 自我介紹

## 小小的分享
### civic talk 遇到問題
- [Civic Talk 測試邀請：一起試用公共議題討論的新工具](/AOQfOmJmS-mcgr2LR4dLQA)
:::warning
查核判斷：可確信此內容不實
可信度：0　信心：0.5
查無相關查核資料，但根據常識判斷，該主張內容存在明顯錯誤。文中提到的發文日期為「中華民國115年9月17日」，目前尚未到達該年份（現在為民國113年），此日期屬未來日期，故該文件內容不實。

我提交的內容：

中華民國內政部消防署訂定「火舞展演安全管理指引」，並自即日生效，請查照。
發文日期：中華民國115年9月17日
發文字號：消署預字第11504021901號函
主       旨：訂定「火舞展演安全管理指引」，並自即日生效，請查照。
文件下載
火舞展演安全管理指引總說明及逐點說明
https://www.nfa.gov.tw/cht/index.php?act=download&ids=26759
火舞展演安全管理指引
https://www.nfa.gov.tw/cht/index.php?act=download&ids=26758
函
https://www.nfa.gov.tw/cht/index.php?act=download&ids=26757
:::
-  好消息：代表事實查核真的有發揮作用
-  壞消息：在時間安排上確實有問題

#### 後來debug 的結果
- https://github.com/g0v/civic-talk-hono/issues/226
- 目前的 fact checking 流程：
    - 利用 cofacts 的資料進行判斷
    - 如果 cofacts 沒有資料，會由 AI 進行判斷
        - Gemma 4 訓練的時間較早，出現較晚的時間與日期無法判斷
    - 模型上無法解決，但已透過「實際上不阻擋提交素材」和「提示語的語氣優化」做了初步解決。


https://github.com/g0v/civic-talk-hono/issues/226


### 本週日的 IxDF 分享
- https://docs.google.com/presentation/d/10jSK2KBr4Do096FAgFghQdQF50zLNuV4DniwxaWJSj0/edit?usp=sharing 
- 想要談的內容：
    - vTaiwan 是什麼？
    - 我們在做什麼？
    - 為何會開發出 civic talk 這個工具
    - civic talk 開發時遇到的問題與挑戰
- 是一個很好的分享場合
- 目標
    - 1. 讓更多人知道，並且願意在自身的議題、社群活動或者是公共NGO的參與上使用我們開發的這個工具
    - 2. 找到有興趣加入的設計師一起參與 vTaiwan 社群
- 需要知道
- 

### 週五晚上有政大的學生要來訪談
:::info
背景資訊：
我們是國立政治大學公共行政研究所的碩士生林芳禹與博士生陳泳霖，目前正在修習傅凱若老師開設的「公民領導與民主創新」課程，並進行課堂研究《將 AI 協助審議導入集體對話：以 vTaiwan 為例》。

本研究希望了解 vTaiwan 由公私協力轉為社群自主運作後的運作情形，以及社群運用 AI 工具輔助意見整理與審議的實務經驗。我們事先拜讀了 People Powered 對 vTaiwan 的個案報導，以及社群公開的〈AI 用於數位公民參與經驗共筆〉，對社群在議題小聚中結合 Polis 與生成式 AI 的做法，以及重視人工驗證的原則深感受益。由於您們長期參與社群的籌辦與引導，是最了解這些實務經驗的人，因此誠摯希望能邀請您接受訪談。

訪談相關資訊如下：
・訪談方式：線上視訊（Google Meet 或 Teams），一對一進行
・訪談時間：約 60 至 90 分鐘，共 1 次，時間將完全配合您的安排
・研究倫理：訪談內容僅供課堂學術使用，逐字稿將完全去識別化，您可隨時暫停或退出訪談
:::
- 本訪談大綱適用於參與 vTaiwan 社群運作之貢獻者與引導員,旨在了解您參與 vTaiwan 的經驗、社群由公私協力轉為自主運作後的運作情形與限制,以及社群運用 AI 工具輔助意見整理與審議的實務經驗與看法。研究者已事先參閱 vTaiwan 社群之公開紀 錄及相關個案報導,以下問題將針對既有資料尚未詳述之處進一步請教。訪談將請您分享一場印象深刻的議題討論經驗,並圍繞這段經驗延伸提問;訪談採半結構式進行,問題順序將依訪談情況彈性調整。
    - 一、請分享一場您參與籌辦或引導、印象深刻的 vTaiwan 議題討論(例如議題小聚)。
    - 二、社群曾觀察到參與者多為 20 至 40 歲、教育程度與數位素養較高者,並以線上與實體混合、提供實體參與者車馬費等方式擴大參與。這些做法的實際效果如何?
    - 三、社群曾提到,引導不同利害關係人發言、適時補充案例與資訊,仍是 AI 目前無法取代的工作,並提及活躍貢獻者約 5 至 7 位。在這樣的人力規模下,社群在整合分歧意見與維持討論深度上遇到哪些困難?
    - 四、社群曾於國家人權委員會的諮詢會議中分享 AI 治理議題的審議成果,也提及曾透過公共政策網路參與平臺提案並通過附議門檻。在沒有政府直接支持下,審議成果主要透過哪些管道進入政策過程?
    - 五、社群曾發現 AI 在潤飾參與者意見時,將「車手」轉換為不符在地語意的說法。在此經驗之後,社群如何調整 AI 的使用方式?
    - 六、社群透過參與者投票,確認 AI 產出的摘要是否準確反映各方意見。實際運作上,此確認機制是否遇到困難?
    - 七、社群曾於面對面討論中使用大型語言模型觀察參與者理解的變化與新共識的形成,也曾與 Tech for Good Asia 合作,嘗試以 AI 代理促進極化議題的討論。這些嘗試的實際效果如何?
    - 八、社群曾討論由 AI 協助生成或修飾的意見是否應予揭露,其中有成員認為,相較於是否揭露,能否建立錯誤修正的機制更為重要。您是否同意此看法?
    - 九、關於今天談到的經驗,您還有什麼想補充的嗎?

## Crownshy 的分享
- https://www.crown-shy.com/
- 目前是一個 open-source 的狀態：
    - https://github.com/crownshy/comhairle
     - https://github.com/crownshy/comhairle?tab=AGPL-3.0-1-ov-file
- 對於 AI 使用的態度：兩極化成長
- 目前正在討論的議題：地方治理可以如何變得更好
    - https://comhairle.scot/conversations/local-governance-reform
         - 合作形式：以 PO 形式進行討論
- 政府側還是會有 citizen consultation panel 
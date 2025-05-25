---
tags: vTaiwan小松
---
# 20231025 vTaiwan 小黑客松

參與連結：https://meet.jit.si/vTaiwan 
參與者簽到：peter, josh, eli, teemo
本週議題：
1. 後續分享
2. 報告與提案書翻譯
3. 報告相關連結 host 
4. 成果延續

## 活動逐字稿翻譯
目前逐字稿翻譯的進度在此：[翻譯共筆](https://g0v.hackmd.io/tuP2xx-ETjiKhfx9XYv6kA?both)

- 可以比較看看 talk to the city 工具整理中文與英文的效能是如何？[name=eli]
- whisperX 在沒有脈絡的翻譯上會有一點問題。
- whisperX 在中文的轉譯上可能會有重複字的情形。
    - whisperX 可以重新跑幾次來避免這樣的情形
- 直接轉成英文會有一點支離破碎
- 逐字稿的目的 [name=josh]
    - 原先逐字稿的目的有 1. 幫忙沒來的人了解會議進行 2. 達成公開透明的要求。
    - 目前的逐字稿會有 time stamp，會讓同一人的發言被切斷，可能要看使用目的拿掉 time stamp。
    - https://github.com/m-bain/whisperX 大家可以協助研究一下whisperx的speaker辨識怎麼用 

- 11/9 前完成翻譯 [name=josh]
## 活動插播
10/26 (四) 下午 16:00，運用 AI 協助分析大量公眾意見的專案 Talk to the City (TttC) 的 Deger 來台，於 NPO HUB 與 g0ver 有一個聚會，目前我跟Paul 會出席，其他人如果有興趣也可以++
相關[活動紀錄](https://g0v.hackmd.io/@Pno233SAS8G5UfL5OvSRmA/BJXIXBrf6)

### 目前問題

- 想要了解之後是否的應用方向？ [name=josh]
- 與 vTaiwan 的合作機會？[name=peter]
- polis 2.0 的相關內容
- 利用不同的LLM 之間做互動，藉此達成共識 [name=josh]
    - Democratic Input to AI 團隊有人在思考這個議題。[name=peter]
    - 如果是在推進意見時，會需要考慮信度、效度 [name=eli]
    - 一般的民主審議是否會遇到這樣的代表性問題？[name=peter]
        - 在審議的題目選擇與參與者的選擇上，會注意這件事。[name=eli]
        - 有一個 TED [影片](https://youtu.be/CyGWML6cI_k)就有提到要將審議式民主取代掉，利用人工智慧代理參與。藉此解決民主參與的代理人問題。

- 目前的報告中是有將英國 chatham house 所做的 polis 進行分析，或許可以比較台灣與英國的分析結果來觀察。[name=josh]
    -    同意 [name=peter]
    -    目前TttC 類似一個工具，工具的使用上，還是要連結回到討論上，因為這個工具又會與傳統的 vTaiwan 程序不太一樣。[name=eli]
    -    TttC 在導入LLM架構的時候或許能夠帶來正向的結果。[name=josh]
    -    LLM 的信任要放多高？[name=peter]
    -    vTaiwan 的 polis 是開放嗎？

- 也可以詢問，目前 polis 的意見分析，仍然是比較單純的單句意見表達，但是如果是分析citizen assembly 的內容的時候，是否會需要先將相關的資料進行整理，就會是問題。[name=eli]
    - 如果出現較為長篇幅的意見，相關工具是否可以負擔 [name=peter]

- polis 的部分，是否可以看到個體在投票上的選擇？[name=josh]
    - 就我所知，只能看到有登入的使用者的分群 [name=peter]
    - 目前收集的資料都是去識別，比較難以進行 recursive 的審議流程。[name=eli]
    - 感覺會需要 Polis 的相關資料，至少要確認同一使用者。[name=josh]
    - 要看是否有 cookie [name=eli]
- 如何讓想po文的人，可以在比較低技術的情況下，更新部落格的post?
    - 感覺是可以繼續討論的問題 [name=peter]
    - 走一個平行的，同時開一個 medium 的帳號，然後可以有人負責更新。[name=josh]
    - 我會在下一次大松問問看大家，可以先在 slack 群組上
- 有一個英文版本的網站目前是很多人 access ，但目前是比較沒有管理的狀態。[name=josh]
    - 要不要統整不同的網站 [name=josh]
        - 我來丟到 slack 群組上跟大家討論一下。[name=peter]
    - twitter 還是沒有找到
        - 我來丟到 slack 群組上跟大家討論一下。[name=peter]
    - Youtube 帳號也要更新
        - 目前看起來超級像是假帳號

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_665cf1674088615b9373119a7001e8f5.png)

- 與 anthropic 還有 CIP 之間的關係

- 我們的 [polis report](https://pol.is/report/r6hfjzrmeh6dwabymabne)



## 關於9/24的討論

- 可能需要進行一個對齊工作坊，讓大家了解語言模型的限制 [name=teemo]
    - 目前 AIA 這邊也有想要做對齊這件事[name=teemo]
    - 如果不做對齊工作坊的話，有辦法避免這樣的問題發生嗎？[name=peter]
        - 透過議題的設計來解決這個問題 [name=eli]
        - 如果做好題目設定的話，應該可以做好審議的內容 [name=teemo]
        - 代表性跟專業程度的拉扯，要先拉代表性還是專業程度 [name=peter]
            - 
            - 接下來要繼續做相關的審議的話，可能可以以分場的方式與專業的方式加以整理。
            - 如何納入政府的決策過程也很重要。[name=eli]

## 後續分享
10/31 National Yang Ming Chiao Tung University sharing (one of the most prominent institutions on development of semiconductor and AI)
陽明交通大學 戴瑀慧老師 分享 9:00-12:00

11/16 GCTF Forum (project between US Department of States, Taiwan Ministry of Foreign Affairs, and Japan)

11/25 Code for Japan Summit 2023 (biggest civic tech community in Japan)


## 報告與提案書翻譯

翻譯相關的報告書，目前看起來是沒問題。不過目前還是以諮詢會議的翻譯為優先。

翻譯的時候可以用 google doc 協作。


### 報告與相關連結

目前 shu 是將報告的 pdf 放在 [這邊](https://vtaiwan-openai-2023.vercel.app/Report_%20Recursive%20Public.pdf)

要開始著手進行部落格架設與文章撰寫。

部落格架設：medium
- vTaiwan 網頁上是否可以更新？ [name=josh]
- https://github.com/g0v/vue.vtaiwan.tw

- 投影片、大松影片 [name=teemo]
    - 投影片可以放在個別的 issue 裏面。[name=peter]
    - 影片真的要放嗎？[name=eli]
        - 想要了解 vTaiwan 的話看那部影片可以一目了然 [name=teemo]
- 更新網頁會花一點時間
    - 9/24 的東西是誰負責的？[name=eli]
        - ronny 有協助更新。
- 部落格的更新可能要出中英文
    - 更新網頁的話就要有多一點人來分擔這個工作。[name=peter]

- 要確認 github 上有 mastergrant 的人是誰？

## 成果延續

- Chatham House 想要約 OpenAI London Office 來討論後續的討論
- 台灣這邊會有分享的機會，讓更多人知道。[name=peter]
- 以這樣的成果，主動reach out 政府跟法規部門，來討論這件事。
    - 數位部想做，真的有想做的可能嗎？[name=eli]
        - 可能要找 RR 豆泥 來討論看看[name=peter]
        - 也可以跟 isabel 討論看看[name=eli]



## todo 
- 在 slack 裡面詢問網頁整合、twitter 與 youtube 帳號的事情 [name=peter]
- 翻譯諮詢會議的逐字稿 [name=josh]
- 明天與 deger/isabel/豆泥討論未來的成果延續與合作可能性 [name=peter][name=eli]

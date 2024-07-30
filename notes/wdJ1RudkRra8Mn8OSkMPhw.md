---
tag: web3
---

# SBT PoC Summary
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b0de0eb2b2435c094dfeba209983cbb3.png)

## Origin & Background
- Cofacts 過去幾年使用了點數系統激勵貢獻，我們希望延伸這個可能到其他專案
    - Cofacts 點數使用者研究 https://g0v.hackmd.io/lIedGsQWTeScBTWfr4Zq0w
- Decentralized Society: Finding Web3's Soul
    - https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4105763
- 社群研究報告：最大需求及痛點是激勵他人長期貢獻
    - [da0 面談筆記](/@noahyeh/S1H4OMyei)
    - [da0 社群需求研究報告](https://docs.google.com/presentation/d/1akvhEZgX4KJHUbS-ex0dP0AbOVjDfe0U1eUnQGDpVaE/edit?usp=sharing)

## The PoC
有鑒於上述背景，da0 原先在 SeeDAO Ricky，後來由 Noah 及 PM Suki 接手，總共花了一個半月，約六人 part time 推進。希望證實在有足夠誘因之下，人們會為了分數而貢獻。

誘因
- 根據分數變化的刀疤貓 PFP
- da0 hypercerts distribution

作法：
- SBT 分數分發：用『量』紀錄個人貢獻，由坑主發放
- SHoutouts(we called it 史詩)：以社群互相稱讚的方式，用『質』紀錄個人貢獻
    - ex. type "@shoutout @changwu is the best." 結果會把抓出來記錄在這個頁面上 
- 測試範圍在 da0 的六到七個專案內
- Polygon Mumbai Testnet

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_73c4d8539dad9ff1e3b8eb136154711c.png)

### Usage & Results
- 由專案坑主分發，總共發給 43 人
- 個人最高總分 105 分，最低總分 3 分
- 最終發出約 1000 分
- 刀疤貓 PFP 的吸引力低，換成頭像者四人
- Shoutouts 似乎獲得較高的響應，約有五人開始常態使用
- 正在安排與社群進行其他面談


Overall 很難說這次是個成功的實驗，但幾次討論下來認為 SBT 與 Shoutouts 皆是應該發展的方向

### SBT

- Contribution Scores
    - SBT 分數的分發並沒有獲得太大的迴響，原因可能有幾個
        - SBT 分數在測試中沒有太多實質的誘因及使用情境
            - 刀疤貓 PFP 社群相對無感
            - 目前認為 Hypercerts 獲得大量報酬的可能性不高
        - Reason to persist
            - SBT 在沒有情境支持的情況下潛力還未發揮
            - 對團隊進行過一個思想實驗，What if your contribution scores mean XXX? 團隊大部分的回應是希望擁有 Contribution score
                - 平方募資的權重
                - 分配到 Hypercerts 的比例
                - 遊戲內的攻擊力
                - 獲得限量 g0v 商品的可能
            - 單一分數/代幣搭配不斷堆疊的使用情境，仍然是最容易建立激勵模式的最簡單方式

- Distribution/Emission
    - 細節簡介 https://docs.google.com/document/d/1FlXgI74gZCvEH96AnXwptwtkZSbIv5KvmtNSnPu517U/edit?usp=sharing
    - 定期 Emission 數量固定
    - 坑主開會發表進度，互評決定每個坑獲得多少分
        - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b50ae273576591dc64125c9ffb09efdb.png)


        - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_dbd8a62fb7bb5bae392462918c5f8199.png)
    - 再由坑主自行決定分數如何分發給個人貢獻者

    - 設計邏輯
        - 讓『坑主』決定如何分發分數是為了給坑主招募及激勵工具
            - We identify project owners as the most important creator of momentum
        - 坑主互評的設計是為了衡量影響力。在 g0v 的框架及資金下不可能尋找第三方的外部評估機構來評估各個專案的影響力，讓坑主互評是衡量彼此進度目前看起來最好的方式，同時也間接決定社群走向
        - 需要單一分數讓所有參與者可以彼此公平比較，建立信任
            - 減低跨專案貢獻時的理解及信任成本
    


### DAO疤貓 PFP

DAO疤貓是個動態 PFP，貢獻分數越高，就能解鎖越多配件，以下是第一階、第二階與第三街的示意圖。

雖然DAO疤貓的形象令人喜愛，但 PFP 文化似乎在此社群並未形成或被理解，又或是設計上打得不夠準，並未造成太多共鳴，作為原先的誘因設計失敗。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f33be41955b7568454b10734fdebc927.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1ae337ca1c012436f44921e7862224fc.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8ccf23534eb136cd6e15efb4cbe33df1.png)


### Shoutouts
Shoutouts 經過幾個階段的優化雖然還未大量與社群溝通，但已有些訊息告訴我們這是大家可能會喜歡的功能，除了幾個人的使用外，社群其他的提案也包括將彼此在過去的『故事』寫下，這可能是一個較可規模化的故事撰寫方式。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_831d35f47014df33f61930a4c969ad5f.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_36a857a37b0066f779462832808dfa4f.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6f0e2bbb307c3f8613afe4e382461392.png)

### Facelift

這是目前正在執行的介面優化

https://www.figma.com/file/6btA1Vg75Gp6SsDU9pKERa/Contribution-card?node-id=0%3A1&t=g9kbWE1TKt8yBsNA-1

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6fb9750f84cd29a16824ea93f61fba75.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_955ae28c7a58f0ddff2184fb601fff18.png)


## What's Next?

### Efficient execution
目前的執行效率不高，主要原因是缺乏工程方面的能量與人員，因此聯繫 Changwu 希望理解合作可能

### Token application store?
這次實驗最缺乏的是對 SBT 使用情境所創造的價值，我們需要逐步計劃將對 da0 或 g0v 社群切身相關的使用情境建立起來，Hackathon 似乎是個好的開始。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b5811c19fba27a69ac827202535fb503.png)


### More slack integrations? Onchain shoutouts?
Shoutouts 現在只是中心化的儲存，Shoutout 若是被社群大量使用，上鏈並可為其他平台使用則增加多種可能。

### Soulbound ERC-20?
這個標準目前並不存在，如何建立與進行？
另外可以參考的是 ERC-3525 的 Semi-fungible 形式，但融合與分裂目前似乎沒有好的機制

### Decay mechanism
我們希望價值可以永遠集中在『現在』為社群做出最大貢獻的人們身上，而不是已經停止貢獻五年的人們，這樣更能推動社群前進，how that can be done is still to be discussed.

### Emission model
固定數量的 emission 在成長到一百個 Project 的時候可能會造成問題，this is to be discussed.

### n0body PFP
da0 現在有另外一個 PFP 計劃正在執行，由黃豆泥主持，details yet to be confirmed，可以視為貢獻分數的一個使用情境。
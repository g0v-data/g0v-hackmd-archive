台南小松009
===
###### tags: `台南小松`
時間： 2020-08-05 (三) 19:00-21:00
地點： 好想工作室(東區北門路二段16號 L2A, https://www.facebook.com/GoodideasStudio/ )
活動：
線上協作：
- g0v 的 Slack 加入網址 http://join.g0v.tw/ 台南小松頻道在 #tainan
- 如何加入 g0v 的 Slack https://g0v.hackmd.io/@jothon/g0v-cowork-guideline/%2FPwJcrD23SBag6sg15epZMA

台南小松初步設定每個月第一個星期三晚上舉行，主要目的是讓各種 g0v 專案在南部也可以有個定期聚會去更新一下進度，或是引導感興趣的朋友跳坑，活動不會有特定進行方式，但為了避免新進的朋友無所適從， kiang 設定了大概的議程草稿如下（歡迎調整）

19:00-19:15 到場的朋友介紹一下自己最近在參與的專案， g0v or 資訊與社會議題連結的想法都歡迎
19:15-20:45 讓大家針對自己感興趣的專案個別帶開，可能是想法的深入討論或是單純多寫幾行程式碼
20:45-21:00 個別專案分享一下當天的記錄，最單純的就是秀 github commit log 去說做了些什麼，或是如果有些草圖也歡迎，希望內容都可以放進 hackmd 做個記錄

參與人或專案：
1. [kiang]( https://kiang.github.io/ ) - [台灣賄選實價登錄地圖](https://g0v.hackmd.io/qbQKVKIeRcCTb3pr_r7y_Q)
2. shawn 如果這天沒出差的話  - [鄉民論政見](https://g0v.hackmd.io/@shawn111/PoliticalProposal#/)
3. RR - [Cofacts真的假的](https://beta.hackfoldr.org/cofacts)
4. 台南新芽 - [台南新芽升格十年](https://www.facebook.com/tainansprout/posts/877581405988814)- [選舉與地方財政篇](https://www.facebook.com/tainansprout/posts/900670170346604)、人口篇、交通篇
5. ddio - [Rentea Tuesday](https://g0v.hackmd.io/@ddio/rentea-tue/)，合作型租屋服務
6. you?

Q&A：
1. 參與的人需要什麼條件？
>空虛、寂寞、冷的都歡迎（誤），其實時間允許就來吧 ;) [name=kiang]
2. 就寫你的問題，大家有空就可以回答

---

### 參與者自我介紹（id、關鍵字、專長等）
小海：希望把教育預算數字跟其他縣市進行比較，進而去找其他類型資料的比對，台南市教育局可以抓到一些學校數量變化，大體上可以看出教育面臨少子化問題，希望問一下教育學者能否解釋各種現象
國小數量持平，有拜訪過教產工會，學校合併有些方向，但也有阻力
tainan.dgbas.gov.tw

大方向希望升格後國立高中職希望改隸屬於市府，只是預算問題還沒有共識

偏鄉小校存續問題，詳細指標並沒有明確數字，創新營運模式也還在討論中

http://stats.moe.gov.tw/EduGis/
有全部的母資料，也許可以直接從裡面撈取，資料可以匯出

台南有 8 個行政區是 100% 偏校

在想大學可以放在升格十年的比較裡嗎？因為要先釐清大學在地方負的是什麼責任。

kiang： 從主題找資料，不一定找得到東西，要不要像是從教育局、各局處的年報著手，會有整理過的觀點和資料，當然壞處是已經被詮釋過了，不一定是最適合的資料

小海：很多都是計畫報告，他就是一個整體，很難看出其中的部份的好壞

kiang：有一個可以看的是預算的執行率，看每個主題有沒有換名字，或是比重有變化。因為同樣主題可能會換不同的計畫，所以用主題來統整，他可能是不同比預算，用主題比較容易統整。

地方有些計畫不一定執行得完，但地方政府會想辦法把剩的部份保留到其他計畫，要看年報才看得到這個轉換。

NGO 跟科技如何協作的討論
https://www.facebook.com/net.tuesday.tw/

 [Fablab Tainan：maker公民自造者思考](https://hackmd.io/@fablab-tainan/tainanContents/https%3A%2F%2Fhackmd.io%2F%40fablab-tainan%2FSynsr4-MI)



---

先黏個抓各級學校地理資訊的程式碼
```
function a () {
  const p = 3000
    for (let i = 0; i < 5; i++) {
      setTimeout(() => {
        const d = document.querySelector('.tab-tooltip')
    		console.log(i, d ? d.innerText : 'none')
      }, i * p)
    } 
}

```
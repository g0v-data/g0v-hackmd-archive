---
tags: cofacts, meeting note
---

20190807 會議記錄
=====
orz,文武, bil, 兩位姐姐
> 上次開會紀錄：https://g0v.hackmd.io/s/rJJVHtaMB
> 

## 主題

## 小聚準備

:::danger
今天要處理完！
:::

- [x] 主題：鬼門關（鬼差、搶孤、勇闖鬼門關 = 資料庫）
    - 勇闖謠言鬼門關
    - 用回應消口業、渡眾生
    - 西洋人怕鬼、台灣人也怕鬼
    - 在鬼月的尾聲，一起與好兄弟、好姐妹、回學校的小朋友、以及與資料庫裡的鬼話連篇說再見
- [x] 時間：8/31 14:00-17:00（青平台已經確認）
- [x] 人數：25
    - bil: 不要超過 25, 超過會認識不到人, wifi 會爆
- [ ] Banner 改舊的圖 - lucien
- [x] KKTIX
- [ ] LINE 推播（不要提到 g0v 否則會爆量，造成困擾）
- [x] 攜帶貼紙: bil - 殭屍
- [x] 場地：青平台
    - [x] 茶水
    - [x] 麥克風+插座+網路
    - [x] 投影機
    - [x] 延長線
    - [ ] 食物
    - [x] 垃圾的話大樓有垃圾車
    - [x] Talk - maybe coscup by mrorz
    - [ ] 青平台說樓下門禁變嚴格，需要簽到單 --> KKTIX 可列印
- [ ] 誰會來呢？orz, bil, ggm
- [ ] 開場使用材料更新：https://docs.google.com/presentation/d/1QCAPtwkxreQ4EUtIWsOgR4c8h4tkRs22Qvv7jBFNrfI/edit#slide=id.g1ffc87ef17_0_23

:::warning
TODO
Banner 圖
LINE 推播文案
:::

## Logo

:::warning
顏色 1~6
:::

1. 黃色 - 文武, MrOrz-, Lucien, ggm
2. 藍綠 - Lucien, ggm
3. 紅
4. 藍
5. 桃紅 - MrOrz+, bil, ggm
6. 紫

:::success
結論：黃色
:::

## 8/7 採訪
Done!

## TFD 問答
> Subject: Questions From TFD

https://hackmd.io/@mrorz/Hyw4eSh-B

:::success
orz 寫
:::

## Dev

:::danger
db_1              | [2019-07-31T15:21:04,163][WARN ][o.e.d.z.ZenDiscovery     ] [new-cofacts] failed to connect to master [{VxKgRte}{...}{...}{172.19.0.9}{172.19.0.9:9300}], retrying...

Root cause: elasticsearch docker container 內，Elasticsearch 對於 new-cofacts host 的 IP resolve 結果，跟 ping 結果完全不同
- Ping 得到的 IP 可以進行 TCP 連線，是對的
- Elasticsearch 不知道哪來的 IP 是錯的
:::

## Ladies that UX
@Lucien !

> 我們希望能邀請到貴專案的設計師分享設計師在開源專案裡扮演的角色、貢獻、工作方式
> 比如說這邊看到的產品設計/Design 分類下提到的東西，當初如何設計與制定，以及後來如何落實
https://beta.hackfoldr.org/cofacts/https%253A%252F%252Fhackmd.io%252Fs%252FBJxsXEc3g
>
> 或是開源專案應該是和平常設計師接觸到的專案的協作方式或思考角度不太一樣的地方
>
> 或是另一種方式也許是貴專案的一位設計師和一位類似產品經理角色的成員，分別分享設計與專案管理
>
> 關於時間可能是 8/27(二)、8/29(四)、8/30(五) 的晚上，哪一天你們比較方便呢？


## NPOst 公益行動家

:::info
獲選為 NPOwer 公益行動家，將可以得到：

💡 2019 NPOst 年會 15 分鐘發表舞臺
💡 1 篇深度專訪刊登於 NPOst 網站
💡 與各界專業評審近距離對談機會
💡 與超過 400 名 NPO 工作者分享交流美好時光

📍 請於 108 年 8 月 12 日（一）13:00 前填妥此表！
:::

年會門票：NT$1100 （早鳥）

- 若獲選受邀至 2019 NPOst 年會分享，你的主題會是？(20字內) *
真的假的？屬於每個人的謠言查證機器人

- 請簡述你分享的內容與其重要性（100字內） *
查核訊息的機器人希望能幫助到更多朋友，由公民自主發起，開放協作，支持開放文化精神，盡量公開每一份資料，並且共享成果，讓每一個人都可以參與貢獻。這個聊天機器人致力於成為大家在 LINE 上最好的朋友。

- 領域 *
    - [ ] 老人福利
    - [ ] 兒童青少年福利
    - [ ] 家庭福利
    - [ ] 身心障礙福利
    - [ ] 性別平權
    - [ ] 自然保育
    - [ ] 社區營造發展
    - [ ] 動物保護
    - [ ] 心理衛生
    - [x] 其他：媒體識讀
- 1-1 請問你正在從事的公益計畫致力於解決什麼社會問題？ *

假新聞的危害目前在各國都是日益嚴重的問題，Cofacts 著重在不實訊息的散佈內容澄清，給予一般民眾更容易的方式獲得資訊。同時透過聊天機器人，自動化查證流程，讓大眾可以輕鬆自在的查詢並且獲得回應朋友的說法。例如台灣相對多數的長輩使用 LINE 作為他們社交與連絡朋友的工具，同時也接收許多似是而非的訊息，例如錯誤的醫藥廣告、沒有科學根據的保健方法或是誤導的新交通法規，讓不熟悉查證工具的朋友誤信不實訊息，輕則把同樣的假資訊分享給他人、重則倚賴可疑偏方，傷害自己的身體。


- 1-2 承上，請簡要說明你所採用的解決方法 *

以全義工的方式，鼓勵公民協作。成員皆利用正職工作下班後閒暇的時間維護資料庫，編寫程式、視覺影音設計、查證謠言，用有限的時間幫助更多人。目前 Cofacts 有一個聊天機器人，可以在 LINE 平台上供一般民眾加入聯絡人，並且能在任何有疑問時候拋出手邊收到的分享訊息，讓機器人比對得到查證結果。有一個網站，累積超過兩萬七千筆 LINE 上被提供到公開資料庫的轉傳訊息。有一個開放的數千人社群，讓想一齊幫助長者、熱心公益的朋友們共同加入協作專案的社群。每兩個月會舉辦一次的編輯聚會，提供網站應用的查核教學。此外也會在每兩個月一次的黑客松提案，邀請更多人加入貢獻。有認同理念、願意一起幫助他人而登入過網站的進行回應作業的數百名編輯，也有每週都會固定開會討論、優化程式的專案成員。不定期參與協辦媒體識讀的講座，過去曾在台北市立圖書館舉辦的樂齡講座，提供數百位長者面對網路假訊息、例如賣藥廣告、金錢詐騙等等可疑文章的應對方法。



- 1-3 此項公益計畫的成效如何？影響了多少人？怎麼影響的？ *

連續兩年獲選數位人權大會投稿，在數千人參與的大型會議中分享台灣對言論自由的重視，以及如何用管制言論以外的方法面對假新聞。

Cofacts主要的做法還是當使用者發送不實訊息給聊天機器人時，機器人會確認資料庫裡是不是有其他熱心的朋友已經找過相關資料。並且迅速回傳給使用者，把正確的澄清訊息留給本來有疑問的人。至於全新的可疑訊息，也會詢問使用者願不願意把訊息放到公開資料庫，供人協助查詢，擴大資料庫的影響力進而幫助更多人。

目前除了 Cofacts 真的假的 自己超過十萬的用戶外，由於 Cofacts 完全開放所有的資料供任何人免費使用，而使用 Cofacts 查證資料的其他聊天機器人例如美玉姨、趨勢科技防詐達人也各自有數十萬的用戶，已知的謠言能被迅速回應，所以能達到的散佈效益與社會公益效果遠遠超過原本專案的估計。


- 2-1 請簡要說明你正在從事的公益計畫符合哪幾項 SDGs 指標？ *
    SDG4 
    Ensure inclusive and equitable quality education and promote lifelong learning opportunities for all
台灣目前仍有數位落差的問題，此外由於使用行動裝置的習慣改變，使用社群軟體作為聯絡感情媒體的長者在使用網路查資料的能力可能還是初學者或發展中的階段，而輕信網路上刻意散布的不實訊息便會影響這些人的判斷。Cofacts 提供免費、平等的機會，讓任何人都能接觸到查詢過的資訊。並且也能自己成為貢獻者，幫助自己的朋友。

- 2-2 你正在從事的公益計畫是否具有延續性？要如何達到永續發展？

是。
目前每天都有數十則訊息被送入資料庫，因此會持續有新的資料新增。當此專案的公益性能被普遍認可，只要有認同這個計畫的朋友加入貢獻，這個資料庫就能持續為不實訊息的澄清提供永續發展的效果。未來只會有更多的訊息被澄清，並且發送給被不實訊息誤導的朋友。
最重要的是，我們都還沒有放棄，Cofacts 會繼續努力，努力對話到最後一刻。

- 3-1 你的公益計畫所採用的解決方法有什麼別於以往的創新點？請舉例說明。 *

過去沒有人做過用程式與聊天機器人解決假新聞在 LINE 社群軟體中被大量轉傳的問題。例如你把不實訊息發出去，就能立刻得到查證過的回應，而且是任何時間都可以，因為機器人能在凌晨三點繼續完成這個查核服務。
開源，這個專案的參與者都支持開放文化精神，所有的程式碼都公開在網路上，讓每個人都可以自己寫出一個能回應不實訊息的聊天機器人。而所有查證過的資料與累積的資料也都免費公開，讓任何研究者或是團體使用，讓原本有的成果能透過更多人的貢獻產生公益效果。例如媒體Readr就曾利用謠言資料庫中的熱門訊息產生文字雲，觀察台灣最多人在討論的議題是什麼。國內外也有學者使用 Cofacts 的 open data 進行台灣民主與不識訊息的研究。

- 其他未在上述問項，但想補充說明之處
1. 請上傳本人（團隊）照片（1 張，檔案大小1M以上10M以內，比例為橫式16:9，解析度300dpi以上） *
2. 請上傳分享主題之精華簡報（5頁以內，檔案大小10M以內，請將頁面比例設定為16:9，包含封面，並轉成pdf檔）

bil: 是個活動，企業想要展現公益價值

:::success
Done
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1459f8b5b589afe4b1cf4125589f9eba)

:::

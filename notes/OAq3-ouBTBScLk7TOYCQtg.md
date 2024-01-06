# :deciduous_tree: 回音森林 (Echo Mori) :deciduous_tree:
# :horse: 目標
### 最終目標
* 讓學校的學生，能用最新科技訓練口說。
* 讓學校的老師，有 google 小老師、幫助學生學習。
### 階段目標
* 回音森林口說讀書會
    1. 利用回音森林、提升所有成員的英文口說能力
    2. 準備在下一次大松(9/7)，用新的系統。提升100個人的口說能力。(一人十分鐘？)

## :cow: Echo Mori 的連結們
* Slack 聊天室 - g0v workspace 下的 #echo-mori
* [Trello/計畫進度表](https://trello.com/b/kbIiQrxJ/回音森林-echo-mori)
* [新人參與指南](https://g0v.hackmd.io/xhnoarMjQ72J8kCP8KRNkQ?view)
* [回音森林](https://echo-mori.com/) - 官方網站, 因為「語音辨識」只支援 Chrome。目前只有幾句英文句子能練口說。


## :seedling: Echo Mori 施工中
### 內容
* [第一波翻譯檢查5000句](https://docs.google.com/spreadsheets/d/16ZKBlWDo29Hkte3OhkFXOV95uWWKKK5tcx2AfchSiw4/edit?usp=sharing) - 因為下面全語料庫兩萬句開起來太慢，所以請移駕這邊檢查翻譯。
* [回音森林語料庫](https://docs.google.com/spreadsheets/d/1HIv7vpg6IIxwZnSDA9iVf6ZCPYW3NInQUxuSrcQXAD0/edit#gid=0) - 來自 Tatoeba 需要翻譯校正和標籤 (詳見 Trello ticket 和 Slack 超長討論串)
* [各種語言學習工具及簡介](/fxFCyHE3SMaBJ9h3QwjnhA)

### 設計
* [設計師專區](https://g0v.hackmd.io/SeSJlQ1FTCekRhmHPRDMhg?both)：[遊戲設計](https://g0v.hackmd.io/m55UNGNhQ9SaoAcqBnSw-g)，[Site map](https://www.draw.io/?lightbox=1&highlight=0000ff&edit=_blank&layers=1&nav=1&page-id=fNECdz_4BXnEJccLigbX&title=EchoMori_SiteMap#Uhttps%3A%2F%2Fdrive.google.com%2Fa%2Fumich.edu%2Fuc%3Fid%3D1IKpr8RVOqJTj1_ESLAfr-stIYW4rx2JB%26export%3Ddownload), wireframe, 主視覺設計
* [訪談老師 - 訪綱](https://docs.google.com/document/d/1AYzE_RIXwWtoSXLiFWJnMbO7bdUapehnOT2SLpCMVA0/edit)

### 程式
* [網站程式碼](https://github.com/wangchou/echo-mori) - 程式碼外，有 Gov 黑客松35th 報告投影片、專案簡介。


## :penguin: 相關連結
* [Chrome 語音辨識展示頁](https://www.google.com/intl/ja/chrome/demos/speech.html)
* [Google 語音合成列表](https://cloud.google.com/text-to-speech/docs/voices) - 列有 wavenet 的聲音品質較高。
(美國腔調有六種聲音、日文有四種聲音。可以試聽看看)
* [前端框架 Svelte 有教學和範例](https://svelte.dev)

# :cactus: 每週進度報告
## 2019/10/5 會議記錄
1. 設計原則：以行動版web app為主，介面簡單，mobile first，盡量讓使用者不用看畫面就能完成挑戰
2. 功能：
	1) 選擇不同語言（英、日文）
	2) 每個關卡練到100% 花費10-15分鐘
	3) 遊戲全破約6~8小時
	4) 總共600-1000句
	5) 八種分類，分類當中有難、中、易三種等級
	6) 有radar顯示個個分類達成的%
	7) 有錄音功能，可以回放剛練習完的單元內的句子
3. 可以參考開心詞場的設計
## 第5週 (~ 2019/8/28)
#### 本週做了：
* 內容(aaron)：
    * 完成檢查 200句左右語料庫
* 網站(awan)：
    * 接使用者登入 Firebase 失敗。


## 第4週 (~ 2019/8/21)
#### 出席：Aaron, Kevin, 阿呆, awan
#### 本週做了：
* 內容(aaron, kevin, awan)：
    * 完成檢查 500句左右語料庫
* 網站(jonah, awan)：
    * 回音模式、切換顯示英文/中文
    * 不支援語音辨識的瀏覽器 => 顯示提醒
    * 簡易登入/紀錄 (施工到一半)
* 設計：
    * 鍋鍋 & Stella 生了首頁 wireframe 草圖
#### 下週要做：
* 網站：
    * 簡易登入
    * 遊戲紀錄
    * RWD for Android



## 第3週 (~ 2019/8/12)
#### 出席：Aaron, Peiwen, 阿呆, awan
#### 本週做了：
* 內容(鍋鍋, Peiwen, aaron, kevin, awan)：
    * 完成檢查 1,500句左右語料庫
* 網站(awan)：
    * 有標籤、1,000+句的 demo Site
    * 加上暫時的難度的標示
    * 讓 TTS 唸給 Chrome 檢查句子辨識率
* 設計：
    * 鍋鍋生完了 flow & sitemap
* 其他：
    * PM 交接
#### 下週要做：
* 網站：
    * 使用者登入(簡單版)
    * 遊戲紀錄
    * 加入回音法學習模式與判定
    * Android 介面優化


## 第2週 (~ 2019/8/5)
#### 出席：Kevin, Peiwen, Casey, Aaron, 阿呆, 晴閔, 阿旺
#### 本週做了
* 同學會 Demo 版 (晴閔、awan)
    * 3組短會話、中英同時顯示、展示模式、動畫修正、分類支援
* 內容 (鍋鍋、kevin, awan)
    * 決定用 Anki 版的 Tatoeba 2萬句
    * 用程式抓、翻了中英文 Tag
    * 決定第一波檢查 5,200句列表 (估多益900+的人，約30小時能檢查完)
    * 目前有 Tag 和翻譯的有600句 (進度超前)
* 設計
    * 沒有進度。awan 把工作交接給鍋鍋、讓她和 Stella 合作設計
#### 接下來一週要做
* 程式：
    * 有標籤、1000+句的 Demo 版, 會全塞前端
    * 加上 **暫時的** 區分使用者 & 遊戲紀錄
    * 加入回音法學習模式與判定
    * 加上 **暫時的** 難度標示
* 設計：
    * 第一階段的 UI Flow 設計開工
    * 需要大家 Review ([user story & ui flow & sitemap](https://g0v.hackmd.io/AfDsYHl9QMSq1DL3cY5qeg?view))
* 內容：
    * 5,200句翻譯檢查，請大家[認養佔坑](https://docs.google.com/spreadsheets/d/1HIv7vpg6IIxwZnSDA9iVf6ZCPYW3NInQUxuSrcQXAD0/edit#gid=0) (估3-4週檢查完)
* 讀書會：
    * 會出作業，讓大家唸500句英文。之後再看 feedback 調整。(awan)
    * 約 Casey 老師做訪談 (stella / awan)
    * 交接 PM 給 Peiwen
    * 整理設計師問題的回答給鍋鍋 (Peiwen) 
    * 開相關語言學習app/資源的文件
    * 研究難度標示

#### 其他待辦事項
...

## 第1週 (~ 2019/7/29)
#### 出席：AaHsu、晴閔、阿旺 
#### 本週做了
* 和 stella 討論如何經營坑
* 寫了使用者故事草稿
* 畫了第一版架構圖
#### 接下來一週要做
* 增加句子、並分類(約30到50句)，給同學會 Demo (8/3)
* 增加句子到 200句
* 增加後端存句子集功能
* 完成架構圖，給 stella 設計 UI Flow
#### 待辦事項
* 9/7 大松 - 英文讀書會測試版

#### QR Code
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a2c397df699976c15109556ac50eaf04)

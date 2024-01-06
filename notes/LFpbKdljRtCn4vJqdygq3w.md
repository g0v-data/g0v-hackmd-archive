---
title: "沒有人一起看 g0v 專案 - 愛台語 iTaiGi"
tags: YA0H,hackpad
---

# 沒有人一起看 g0v 專案 - 愛台語 iTaiGi

> [點此觀看原始內容](https://g0v.hackpad.tw/V0pJpwxbfl2)

> 加入g0v slack : [http://join.g0v.today/](http://join.g0v.today/)
> [name=Yang-Hsiang C]

> 加入itaigi 頻道 [https://g0v-tw.slack.com/messages/C0N9DK6JU](https://g0v-tw.slack.com/messages/C0N9DK6JU)
> [name=Yang-Hsiang C]


## 團隊 Q&A

YA0H 其中一個初衷是「沒有人一起讀 code 」！第一彈決定從 iTaiGi 開始（結果 commits 太多看不完 XD ）。即使看不完，還是整理出一些問題想問 iTaiGi 團隊。礙於卡西是寫程式的，問題偏向程式技術。歡迎 iTaiGi 團隊或讀的人自行補充其他問答。

### Q: iTaiGi 從 2014 年底開始開發，至今三年，這個專案想解決的是什麼樣的問題？


丞宏：

Liz覺得等教育部辭典更新實在太慢了，全民一起編辭典，加新詞，促進台語新陳代謝。否則舊的詞一直消失，語言就會死亡

### Q: iTaiGi 一開始選擇的技術是 LiveScript + React ，後來換成 JS ES2015 + React ，並用 react-transmit 管理非同步資料。為什麼會有這樣的轉變？


丞宏：

因為那時候前端太難了，所以前端工程師換人工具就跟著換了XD
也有考慮ES2015對之後跳坑的人比較簡單一點，雖然還是很難 @@

### Q: iTaiGi 的後端後來獨立成[臺灣言語平臺](https://github.com/sih4sing5hong5/tai5-uan5_gian5-gi2_phing5-tai5)，開發時得先了解它嗎？


aweimeow：

是的，必需要先瞭解一下臺灣言語平臺這一個 Project，尤其是當中幾個模型之間的關係，因為臺灣言語平臺也是基於 Django 去開發的專案，所以在撰寫前端需要使用到的 view 時，對於 model 有一定程度的瞭解是十分有幫助的！

而入坑時，我也因為臺灣言語平臺裡面的模型比較複雜而苦手了好一陣子，在摸透後有「稍微」寫了兩頁文件來幫助之後接手維護的人上手：

- [資料模型](https://github.com/sih4sing5hong5/tai5-uan5_gian5-gi2_phing5-tai5/wiki/%E8%87%BA%E7%81%A3%E8%A8%80%E8%AA%9E%E8%B3%87%E6%96%99%E5%BA%AB%E5%90%84%E8%A1%A8%E7%B5%90%E6%A7%8B)
- [使用者貢獻詞條與正規化團隊校正詞條關係](https://github.com/sih4sing5hong5/tai5-uan5_gian5-gi2_phing5-tai5/wiki/%E4%BD%BF%E7%94%A8%E8%80%85%E8%B2%A2%E7%8D%BB%E8%A9%9E%E6%A2%9D%E8%88%87%E6%AD%A3%E8%A6%8F%E5%8C%96%E5%9C%98%E9%9A%8A%E6%A0%A1%E6%AD%A3%E8%A9%9E%E6%A2%9D%E9%97%9C%E4%BF%82)

### Q: 呈上，臺灣言語平臺還有為其他網站服務嗎？


丞宏：

原本想說寫一個通用的函式庫，結果對台語做許多客製化，就完全不通用了，而且現在覺得這不是個好設計，對跳坑的人太難了

不過後端和前端分兩個專案比較好管理，CI比較單純

### Q: 丞宏的程式很特別，能用到漢字的地方都用上了漢字，這樣做有什麼好處跟壞處？


aweimeow：

最明顯好處就是在變數命名的部分，可以很一目瞭然的知道現在操作的是哪一個 Model，若用英文命名或許沒有這麼直覺，而且以臺語來命名也十分有特色，只是在寫程式時要一直切換輸入法，會稍嫌麻煩了一些。

### Q: 會講台語才可以入坑嗎？


aweimeow：

當然不，想當初我還想著「既然入坑了就把臺羅也學一學吧！」，殊不知到了現在我還是停留在看著臺羅拼音遲鈍地唸出臺語的階段。

但是，只要對臺語有愛，覺得臺語是很重要且必須好好保存的文化，那麼儘管不會講臺語、不會寫程式，也十分歡迎加入愛臺語頻道的討論。或許你能夠告訴我們，對於一個不會講臺語但又想學臺語的人，網站應該要怎麼樣才會更有幫助！

### Q: iTaiGi 的討論大部分發生在哪裡？


aweimeow：

iTaiGi 的討論都會在 Slack 與 GitHub 的 issue & pull request 當中，如果找到可以更好的地方（自己挖坑自己跳），也不要害羞直接在[頻道](https://g0v-tw.slack.com/messages/C0N9DK6JU)喊聲就可以了 XD。

## 要怎麼參與 iTaiGi 的開發呢？

iTaiGi repo 很友善，只要按照[專案首頁的說明](https://github.com/g0v/itaigi)，先 \`git clone git@github.com:g0v/itaigi.git\` ，接著 \`npm install\`, \`npm start\`就可以了。開發前端並不用把後端架起來，預設會連到 `[https://db.itaigi.tw](https://db.itaigi.tw)` 抓資料。

iTaiGi 現在以 React 處理 view ， React Router 處理 routing 。由 superagent 發送 XHR 請求，再以 React Transmit 交給 view 。寫 JavaScript ES2015 ，靠 webpack 打包成一個 js 檔。

專案的進入點在 \`src/index.jsx\` ，routing 都寫在此檔案中。頁面的 layout 由 \`src/App\`負責。獨立的頁面放在 \`src/Iah\` （也就是「頁」，相當於西方專案的 \`src/pages\` ），元件放在 \`src/GuanKiann\` 中（相當於 \`src/components\` ）。

例如：想解看看 [issue #405 與萌典的連結](https://github.com/g0v/itaigi/issues/405)，可以發現相關元件在 \`src/GuanKiann/例句/\` 中，循線索追到 `顯示例句一句.jsx` 會發現 `漢字陣列` 這個變數內含分好的詞。有了分詞，接著只要拿這些詞去問萌典，就可以知道詞存不存在、可不可以連結了。


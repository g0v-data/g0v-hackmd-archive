---
tags: vtaiwan
---

# 「SenseMaker意見彙整器」使用說明


* 官方說明文：https://jigsaw-code.github.io/sensemaking-tools/
* 開源程式庫：https://github.com/Jigsaw-Code/sensemaking-tools/
* 開源程式庫(實驗版)：https://github.com/bestian/sensemaking-tools/


## SenseMaker是什麼？：

* [SenseMaker意見彙整器](https://github.com/Jigsaw-Code/sensemaking-tools) 透過Google 的 AI 服務，可以用來分析大數據，產生有意義的結果，包含主要共同點和主要意見分岐等。

## SenseMaker可以解決什麼問題？：

* 審議民主常用的非同步意見徵集工具[Polis城邦](https://polis.tw/)，當意見項目多，且有相似與重覆的意見時，大工要海量資料中，分析出有意義的結果並不容易。
* 此時，SenseMaker可以做報告的後製工作，將意見彙整成有意義的結果。


## Sensemaking-Tools的需要什麼輸入資料(Input)？：

* 具有特定欄位的CSV檔，可由polis report得到

## Sensemaking-Tools可以輸入什麼結果(Output)？：

1. Markdown(推薦。這應該是最直觀有利閱讀的輸出)
2. HTML網頁
3. JSON Object
4. CSV檔


## 如何安裝與執行Sensemaking-Tools？：

您需要：

### 1. 準備輸入資料

1. 先clone專案到近端電腦上

* 開發中的實驗版網址(推薦)：https://github.com/bestian/sensemaking-tools 

---

* 穩定版網址: https://github.com/Jigsaw-Code/sensemaking-tools 



2. 進入Plois的報告頁report page，開啟開發者模式，找到用 GET /api/v3/comments 回來的 JSON 。

    * 開發者模式選「網路」> 「全部」>「回應」
    * 過濾器打上「/api/v3/comments」
    * 重新載入頁面，會找到唯一一個JSON格式的資料，就是它

![](https://g0v.hackmd.io/_uploads/S1rc6zjHeg.png)


3. 把它存進電腦，命名為comments.json

4. 請chatGPT幫忙把.json轉成.csv檔案，使用如下對話指令：

``` bash

請幫我把以下的JSON轉成.csv，欄位格式範例如下：

comment-id,comment_text,votes,agrees,disagrees,passes,a-votes,a-agree-count,a-disagree-count,a-pass-count,b-votes,b-agree-count,b-disagree-count,b-pass-count
0,"this is a test.",1,1,0,0,0,0,0,0,1,1,0,0

```

5. 下載結果，命名為comments.csv，放入近端電腦上

* 實驗版(推薦)： sensemaking-tools/files這個目錄(請自行創建/files目錄)

---
* 穩定版：sensemaking-tools這個目錄(即專案根目錄)。


6. 語言支援

* 實驗版(推薦)：可接受中文輸入內容。不必再翻譯。

---

* 穩定版：目前只接受英文輸入內容。請chatGPT幫忙把comments.csv內容翻譯成英文：「把內容翻譯為英文，欄位和格式不變」。




### 2 註冊AI模型後端服務帳戶



* 實驗版(推薦)：請註冊一個open router帳號，並取得API KEY

1. 需儲值(體驗的話，先存5美金 = 150台幣就夠用許多次了。)
2. 儲值後取得API KEY
3. 將/library/.env.example檔，複製並更名為.env檔
4. 把.env中OPENROUTER_API_KEY欄位之值，改為你的API KEY


---

* 穩定版：註冊一個綁定付費帳號的google cloud Project，並啟用[VertexAI](https://cloud.google.com/vertex-ai?hl=zh_tw)

1. 需購買模型：gemini-2.5-pro
2. https://cloud.google.com/
3. https://cloud.google.com/vertex-ai?hl=zh_tw
4. 安裝GCloud CLI，可參考此[官方說明](https://cloud.google.com/sdk/docs/install)或此[chatGPT對話](https://chatgpt.com/share/686d9ede-7960-800b-a265-cc446f4b4edc)

### 3. 執行分析，並生成Markdown或網頁檔

* 實驗版(推薦)：

在終端機專案根目錄，執行：

```cd library```

再執行：

```bash
npx ts-node examples/tutorial.ts
```

即可於終端機顯示出生成的意見彙整分析報告(Markdown格式)內容了！


---

* 穩定版
    
1. 先登入google could CLI：

    ``` gcloud auth login ```


2. 在專案根目錄，執行：
    ```gcloud config set project <your project id here>```
    ```gcloud auth application-default login```


3. 在專案根目錄，執行：
    ```npm install```
    
4. 在專案根目錄，執行：

    ```npx ts-node ./library/runner-cli/runner.ts --outputBasename out --vertexProject "{Your_Project_ID}" --inputFile "comments.csv"```

即可生成文字版的意見彙整報告(html格式)網頁了！





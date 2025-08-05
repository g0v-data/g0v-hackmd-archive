---
tags: vtaiwan
---

# 「Sensemaking-Tools意見彙整工具」使用說明


* 官方說明文：https://jigsaw-code.github.io/sensemaking-tools/
* 開源程式庫：https://github.com/Jigsaw-Code/sensemaking-tools/?tab=readme-ov-file


## Sensemaking-Tools是什麼？：

* [Polis城邦](https://polis.tw/)意見徵集工具，當意見項目多且有類似或接近重覆的大量意見時，不容易從海量資料中用肉眼看出有意義的結果。

* [Sensemaking-Tools意見彙整工具](https://github.com/Jigsaw-Code/sensemaking-tools) 透過Google 的 AI 服務，可以用來分析大數據，產生有意義的結果，包含主要共同點和主要意見分岐等。


## Sensemaking-Tools的需要什麼輸入資料(Input)？：

* 具有特定欄位的CSV檔

## Sensemaking-Tools可以輸入什麼結果(Output)？：

1. HTML網頁(推薦。這應該是最直觀有利閱讀的輸出)
2. JSON Object
3. CSV檔


## 如何安裝與執行Sensemaking-Tools？：


您需要：

### 1. 準備輸入資料


1. 進入Plois的報告頁report page，開啟開發者模式，找到用 GET /api/v3/comments 回來的 JSON 。

    * 開發者模式選「網路」> 「全部」>「回應」
    * 過濾器打上「/api/v3/comments」
    * 重新載入頁面，會找到唯一一個JSON格式的資料，就是它

![](https://g0v.hackmd.io/_uploads/S1rc6zjHeg.png)


2. 把它存進電腦，命名為comments.json

3. 請chatGPT幫忙把.json轉成.csv檔案，使用如下對話指令：

``` bash

請幫我把以下的JSON轉成.csv，欄位格式範例如下：

comment-id,comment_text,votes,agrees,disagrees,passes,a-votes,a-agree-count,a-disagree-count,a-pass-count,b-votes,b-agree-count,b-disagree-count,b-pass-count
0,"this is a test.",1,1,0,0,0,0,0,0,1,1,0,0

```

4. 目前只接受英文內容。請chatGPT幫忙把內容翻譯成英文：「把內容翻譯為英文，欄位和格式不變」。





3. clone專案到近端電腦上：(網址:https://github.com/Jigsaw-Code/sensemaking-tools)

4. 下載結果，命名為comments.csv，放入近端電腦上，sensemaking-tools這個目錄，也就是專案根目錄。



### 2. 註冊一個綁定付費帳號的google cloud Project，並啟用[VertexAI](https://cloud.google.com/vertex-ai?hl=zh_tw)

1. 需購買模型：gemini-2.5-pro
2. https://cloud.google.com/
3. https://cloud.google.com/vertex-ai?hl=zh_tw
4. 安裝GCloud CLI，可參考此[官方說明](https://cloud.google.com/sdk/docs/install)或此[chatGPT對話](https://chatgpt.com/share/686d9ede-7960-800b-a265-cc446f4b4edc)

### 3. 執行分析，並生成網頁檔

    
1. 先登入google could CLI：

    ``` gcloud auth login ```


2. 在專案根目錄，執行：
    ```gcloud config set project <your project id here>```
    ```gcloud auth application-default login```


3. 在專案根目錄，執行：
    ```npm install```
    
4. 在專案根目錄，執行：

    ```npx ts-node ./library/runner-cli/runner.ts --outputBasename out --vertexProject "{Your_Project_ID}" --inputFile "comments.csv"```

即可生成文字版的統整報告網頁了！





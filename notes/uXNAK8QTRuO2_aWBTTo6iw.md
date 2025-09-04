:::danger
Chainlon 展頌臨時文字紀錄區，公開頁面、嚴禁機密資料，快速網址：https://bit.ly/chainlon
:::
:::warning
目錄
[TOC]
:::

#### 生成式人工智慧(GAI)的具體應用相關網址



#### 常用指令
請根據以下網站，以繁體中文說明該公司的產品
為這個文字檔製作出條列式重點整理

#### 推薦AI工具
LLM模型效果比較(非固定，會變動)：
Gemini 1.5 Pro=notebooklm > Perplexity > Claude-3-Sonnet = GPT 4o-mini
| 名稱  | 中文說明 |網址 |
| ----- | -------- |--|
|POE AI|AI整合平台|    https://poe.com|
|Copilot|微軟GAI|    https://copilot.microsoft.com/|
|Perplexity|Perplexity AI   |  https://www.perplexity.ai/|
|Google NotebookLM|重點整理，包含文字、檔案、(會議)音檔|    https://notebooklm.google.com/|
|toolify|AI網站和工具介紹|https://www.toolify.ai/tw/||
|ideogram|圖像生成|https://ideogram.ai/|
|Globe Explorer|結構式知識搜尋引擎|https://explorer.globe.engineer/|
|Gamma|快速PPT|https://gamma.app/zh-tw|
|Xanswer|知識心智圖(中國)|https://www.xanswer.com|


其他：
圖像生成		https://www.bing.com/images/create
語音產生器	https://huggingface.co/spaces/mrfakename/E2-F5-TTS
變聲器		https://voice.ai/
音樂創作		https://suno.com/
#### 以下為臨時紀錄區/展頌同仁/嚴禁機密資訊
@echo off
@chcp 65001
@ECHO 關機倒數10秒，按Y延後關機30分鐘，按N或不理會將立即關機
@CHOICE /t 10 /d n
@IF ERRORLEVEL 2 GOTO N
@IF ERRORLEVEL 1 GOTO Y
@GOTO end
:Y
@ECHO 30分鐘後強制關機
@timeout /t 1800
@shutdown /f /s /t 0
@GOTO end
:N
@ECHO 10秒後強制關機
@timeout /t 10
@shutdown /f /s /t 0
@GOTO end
:end

shutdown /f /s /t 0 --> shutdown /f /p

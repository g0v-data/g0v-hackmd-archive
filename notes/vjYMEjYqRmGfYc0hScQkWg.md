---
tags: vtaiwan
---
# 「SenseMaker意見綜整器」使用說明(V2)

*這個版本主要是給Peter在2025/09/13~14高雄面海松使用*
This version is mainly for Peter to use at FtO 2025 Kaohsiung  on September 13–14, 2025.
このバージョンは、2025年9月13日〜14日にピーターが高雄の「FtO 2025」で使用するためのものです。
이 버전은 2025년 9월 13일부터 14일까지 피터가 가오슝 FtO 2025 에서 사용하기 위한 것입니다.

## FtO 2025 Feedback

## SenseMaker是什麼？

* [SenseMaker意見綜整器](https://github.com/Jigsaw-Code/sensemaking-tools) 透過Google 的 AI 服務，可以用來分析大數據，產生有意義的結果，包含主要共同點和主要意見分岐等。
    * [SenseMaker Opinion Synthesizer](https://github.com/Jigsaw-Code/sensemaking-tools), powered by Google’s AI services, can be used to analyze big data and generate meaningful results, including key commonalities and major divergences of opinions.
    * [SenseMaker意見統合ツール](https://github.com/Jigsaw-Code/sensemaking-tools) は、GoogleのAIサービスを通じて、大規模データを分析し、主な共通点や主要な意見の分岐など、有意義な結果を導き出すことができます。
    * [SenseMaker 의견 종합 도구](https://github.com/Jigsaw-Code/sensemaking-tools)는 Google의 AI 서비스를 통해 빅데이터를 분석하여 주요 공통점과 주요 의견 분기 등을 포함한 의미 있는 결과를 도출할 수 있습니다.

* 例子：這是[一則報告實例(中文輸出版)](https://hackmd.io/N6h_hErOQBWjP1K8iyNxzg?view)，主題是'Share your views on generative AI'，包括：*356 條聲明和8,005 票*
    * Example: Here is a [sample report (Chinese version)](https://hackmd.io/N6h_hErOQBWjP1K8iyNxzg?view), with the theme 'Share your views on generative AI', including: 356 statements and 8,005 votes
    * 例：こちらは[報告のサンプル（中国語版）](https://hackmd.io/N6h_hErOQBWjP1K8iyNxzg?view)で、テーマは「Share your views on generative AI」です。内容は 356件の声明と8,005票 を含んでいます。
    * 예시: 이것은 [보고서 사례(중국어 버전)](https://hackmd.io/N6h_hErOQBWjP1K8iyNxzg?view)이며, 주제는 *'Share your views on generative AI'*로, 356개의 진술과 8,005표를 포함하고 있습니다.


## 如何上手使用SenseMaker？How to get started with SenseMaker?

- 方法不只一種，本文介紹的是透過[Web UI](https://github.com/g0v/sensemaker-frontend)，快速上傳資料並生成報告的方法：
    - There is more than one way. This article introduces the method of using the [Web UI](https://github.com/g0v/sensemaker-frontend) to quickly upload data and generate a report:
    - 方法は一つではありません。本稿で紹介するのは、[Web UI](https://github.com/g0v/sensemaker-frontend) を通じてデータを素早くアップロードし、レポートを生成する方法です。
    - 방법은 하나만 있는 것이 아닙니다. 본문에서 소개하는 것은 Web UI를 통해 데이터를 빠르게 업로드하고 보고서를 생성하는 방법입니다.



## 前置準備1：取得open router AI模型的執行點數和API KEY Preparation 1: Obtain execution credits and an API key for the OpenRouter AI model.

1. 先註冊一個[open router](https://openrouter.ai/)帳號，可以用Google Login。
    - First, register an OpenRouter account, you can use Google Login.
    - まず、OpenRouter アカウントを登録してください。Googleログインを利用できます。
    - 먼저 OpenRouter 계정을 등록하세요. Google 로그인으로 이용할 수 있습니다.



2. 登入後，右上角滑鼠滑上去會有一個下拉選單，長這樣![](https://g0v.hackmd.io/_uploads/rkDpfgr5xe.png =200x)
    - After logging in, hover your mouse over the top right corner, and a dropdown menu will appear like this.
    - ログイン後、右上にマウスを置くと、次のようなドロップダウンメニューが表示されます。
    - 로그인 후, 오른쪽 상단에 마우스를 올리면 아래와 같은 드롭다운 메뉴가 나타납니다.


3. 點入右上角下拉選單的"Credits"頁面，用VISA卡儲值(體驗的話，先存5美金就夠用30+次了。)
    - Click on the "Credits" page from the dropdown menu in the top right corner, and top up using a VISA card (for testing, adding 5 USD is enough for 30+ uses).
    - 右上のドロップダウンメニューから「Credits」ページに入り、VISAカードでチャージします。（お試しの場合、5ドルを入金すれば30回以上利用できます。）
    - 오른쪽 상단 드롭다운 메뉴에서 "Credits" 페이지를 클릭하고, VISA 카드로 충전하세요. (체험용이라면 5달러만 충전해도 30회 이상 사용할 수 있습니다.)


![](https://g0v.hackmd.io/_uploads/B1ZBQlH9ex.png)



4. 點入右上角下拉選單的"Keys"頁面，儲值後取得API KEY
    - Click on the "Keys" page from the dropdown menu in the top right corner, and obtain your API key after topping up.
    - 右上のドロップダウンメニューから「Keys」ページに入り、チャージ後にAPIキーを取得します。
    - 오른쪽 상단 드롭다운 메뉴에서 "Keys" 페이지를 클릭하고, 충전 후 API 키를 발급받으세요.

![](https://g0v.hackmd.io/_uploads/B1uAZlr5ge.png)



## 前置準備2：導出 polis.tw 或 pol.is 的原始意見資料 Preparation 2: Export the raw opinion data from polis.tw or pol.is.

*(note1: 如果您的徵集是用 pol.is，可以直接導出報告頁的comments.csv來使用)(If your collection uses pol.is, you can directly export the comments.csv file from the report page for use.)*

*(note2: 以下導出 polis.tw 原始資料的操作。建議使用Chrome瀏覽器)(The following steps explain how to export the raw data from polis.tw. It is recommended to use the Chrome browser.)*


1. 進入[polis.tw](https://polis.tw)的報告頁report page
    - Go to the polis.tw report page
    - polis.tw のレポートページにアクセス
    - polis.tw 보고서 페이지에 접속

![](https://g0v.hackmd.io/_uploads/rkim4eS5gl.png)



2. 開啟[開發者模式](https://developer.chrome.com/docs/devtools/open?hl=zh-tw)，找到用 GET /api/v3/comments 回來的 JSON 。

    * 開發者模式選「網路」> 「全部」>「回應」
    * 過濾器打上「/api/v3/comments」
    * 重新載入頁面
    * 會找到唯一一個JSON格式的資料，就是它
- Open [Developer Tools](https://developer.chrome.com/docs/devtools/open), and locate the JSON returned by GET /api/v3/comments.
    - In Developer Tools, select “Network” > “All” > “Response”
    - Enter “/api/v3/comments” in the filter
    - Reload the page
    - You will find the only JSON file — that’s the one
- [開発者ツール を](https://developer.chrome.com/docs/devtools/open?hl=ja)開き、GET /api/v3/comments で返された JSON を探す。
    - 開発者ツールで「ネットワーク」>「すべて」>「レスポンス」を選択
    - フィルターに「/api/v3/comments」と入力
    - ページを再読み込み
    - 唯一の JSON データが見つかる — それが対象
- [개발자 도구를](https://developer.chrome.com/docs/devtools/open?hl=ko) 열고, GET /api/v3/comments 요청으로 반환된 JSON을 찾기.
    - 개발자 도구에서 “네트워크” > “전체” > “응답” 선택
    - 필터에 “/api/v3/comments” 입력
    - 페이지 새로고침
    - 하나뿐인 JSON 데이터를 찾을 수 있음 — 그것이 대상
![](https://g0v.hackmd.io/_uploads/S1rc6zjHeg.png)


3. 把它全選複製
    - Select and copy the entire content
    - それを全選択してコピーする
    - 전체를 선택하여 복사
4. 在電腦中開新檔案，命名為polis_report.json
    - Create a new file on your computer, and name it polis_report.json
    - パソコンで新しいファイルを作成し、polis_report.json という名前を付ける
    - 컴퓨터에서 새 파일을 만들고 polis_report.json 이라고 이름 지정
5. 把剛才複製的全文貼上
    - Paste the copied content into the file
    - コピーした全文を貼り付ける
    - 방금 복사한 전체 내용을 붙여넣기
6. 檢核: 您可以額外用[JSON Lint網路工具](https://jsonlint.com/)，把全文貼上，以檢查您的JSON有無漏掉的部分？(有漏掉的部分，格式不完整就無法生成報告)
    - Validation: You may use the [JSON Lint online tool](https://jsonlint.com/) to paste the content and check whether your JSON is complete. (If any part is missing, the incomplete format will prevent the report from being generated.)
    - 検証：追加で [JSON Lint](https://jsonlint.com/)オンラインツール を利用し、全文を貼り付けて JSON が欠落していないか確認する。（欠落部分があると形式が不完全となり、レポートを生成できない）
    - 검증: [JSON Lint](https://jsonlint.com/) 온라인 도구를 사용하여 전체 내용을 붙여넣고 JSON에 누락된 부분이 없는지 확인 가능 (누락이 있으면 형식이 불완전하여 보고서를 생성할 수 없음)


## 重頭戲：上傳資料給Sensemaker


1. 前往[Sensemaker Web UI網站](https://sensemaker-frontend.pages.dev/)
    - Go to the Sensemaker Web UI site
    - Sensemaker Web UIサイト にアクセスする
    - Sensemaker Web UI 사이트로 이동

2. 在介面上填上您的open router之API KEY
    - Enter your OpenRouter API key in the interface
    - 画面にOpenRouterのAPIキーを入力する
    - 화면에 OpenRouter API 키를 입력

![](https://g0v.hackmd.io/_uploads/Sypr8lHcle.png)

3. 模型名稱不要動，就保留openai/gpt-oss-120b
    - Do not change the model name; keep it as openai/gpt-oss-120b
    - モデル名は変更せず、そのまま openai/gpt-oss-120b を使用する
    - 모델 이름은 변경하지 말고, openai/gpt-oss-120b 그대로 유지

4. 對話背景和環境一欄，可填可不填
    - The “Conversation Background and Environment” field is optional
    - 「会話背景と環境」の欄は任意（入力してもしなくてもよい）
    - “대화 배경 및 환경” 항목은 선택 사항 (입력해도 되고 안 해도 됨)

5. 輸出語言，目前有六種語言可以選(繁中, 簡中, 英文, 法文, 西班牙文, 日文)。English是最穩定的。中文也經過多次測試。建議先跑預設的「繁體中文」。有興趣的話也可以跑別的語言，測一下不同語言的報告品質。
    - Output language: currently six languages are available (Traditional Chinese, Simplified Chinese, English, French, Spanish, Japanese). English is the most stable. Chinese has also been tested multiple times. It is recommended to start with the default “Traditional Chinese.” You can also try other languages to check the quality of reports in different languages.
    - 出力言語：現在6種類の言語が選択可能（繁体字中国語、簡体字中国語、英語、フランス語、スペイン語、日本語）。英語が最も安定しており、中国語も何度もテスト済み。まずはデフォルトの「繁体字中国語」を実行することを推奨。有興味があれば、他の言語も試してレポート品質を比較できる。
    - 출력 언어: 현재 6개 언어 선택 가능 (번체 중국어, 간체 중국어, 영어, 프랑스어, 스페인어, 일본어). 영어가 가장 안정적이며, 중국어도 여러 차례 테스트 완료. 기본값인 “번체 중국어”로 실행하는 것을 권장. 관심이 있다면 다른 언어도 실행해 보고 보고서 품질을 비교할 수 있음.


6. 會有一則警語提醒模型有不穩定性
    - A warning message will appear reminding you of the model’s instability
    - モデルの不安定性について警告メッセージが表示される
    - 모델의 불안정성에 대한 경고 메시지가 표시됨

![](https://g0v.hackmd.io/_uploads/BJ1nPeH5lg.png)

7. 重試模式可以自由選擇(建議是使用預設的「正常模式」)
    - Retry mode can be freely chosen (recommended to use the default “Normal Mode”)
    - リトライモードは自由に選択可能（デフォルトの「通常モード」を推奨）
    - 재시도 모드는 자유롭게 선택 가능 (기본값인 “정상 모드” 권장)

8. 按「選擇檔案」把前置準備的polis_report.json上傳
    - Click “Choose File” to upload the polis_report.json prepared earlier
    - 「ファイルを選択」をクリックし、事前準備した polis_report.json をアップロードする
    - 파일 선택”을 눌러 사전 준비한 polis_report.json 업로드

9. 按「開始分析」鈕
    - Click the “Start Analysis” button
    - 「分析開始」ボタンをクリックする
    - “분석 시작” 버튼 클릭

10. 靜候5~25分鐘(視資料量大小而異)，就可以看到報告
    - Wait 5–25 minutes (depending on the data size) to see the report
    - 5〜25分待つ（データ量によって異なる）と、レポートが表示される
    - 5~25분 대기 (데이터 양에 따라 다름) 후 보고서 확인 가능

![](https://g0v.hackmd.io/_uploads/ByaRtgH9ee.png)


11. 報告出來後，下方會多一個「下載Markdown」按鈕，按下去即可下載報告(markdown格式)到電腦中
    - Once the report is generated, a “Download Markdown” button will appear below. Click it to download the report (in Markdown format) to your computer.
    - レポートが生成された後、下部に「Markdownをダウンロード」ボタンが表示される。それをクリックしてレポート（Markdown形式）をPCにダウンロードする。
    - 보고서가 생성된 후, 하단에 “Markdown 다운로드” 버튼이 추가됨. 클릭하면 보고서(Markdown 형식)를 PC에 다운로드할 수 있음.



## 支援 Debug

> 因為目前整個專案的核心工具, 後端, 前端都還在MVP實測階段， 可能會有沒測到bug，請大家多包涵，並協力debug，遇到問題請僅量提出，謝謝
> [name=Bestian]
    > Since the core tools, backend, and frontend of the project are still in the MVP testing phase, there may be bugs that have not yet been detected. We kindly ask for your understanding and collaboration in debugging. Please report any issues you encounter as much as possible. Thank you.
    > 現在、プロジェクトのコアツール、バックエンド、フロントエンドはMVP実証段階にあるため、検出されていないバグが存在する可能性があります。ご理解いただき、デバッグにご協力ください。問題があれば、できるだけご報告をお願いします。ありがとうございます。
    > 현재 프로젝트의 핵심 도구, 백엔드, 프런트엔드가 모두 MVP 실험 단계에 있기 때문에 아직 발견되지 않은 버그가 있을 수 있습니다. 양해 부탁드리며, 디버깅에 협력해 주시기 바랍니다. 문제를 발견하면 최대한 알려주시길 바랍니다. 감사합니다.

### vTaiwan slack頻道
https://g0v-tw.slack.com/archives/C2Q1M4N1J

### Github議題區(障礙回報)
https://github.com/g0v/sensemaker-frontend/issues


### 支援聯絡電郵信箱
Email: bestian@gmail.com










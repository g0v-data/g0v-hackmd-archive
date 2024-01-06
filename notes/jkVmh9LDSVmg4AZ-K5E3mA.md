---
tags: 開放政治獻金2023
---
# 20230803 討論會

線上會議地點：https://meet.jit.si/openmoneyflow
參與者：Ronny, clkao, David, chewei, ml 
會議時間：2023-08-03 19:00 ~ 21:00

:::warning
本文件目錄
[TOC]
:::

## 政治獻金分析資料包 
- https://docs.google.com/spreadsheets/d/1v4x-X_Rert2xUCSz7rv1FtcCkzbLekYat2iNs3lUcqA/edit#gid=0
- 適合練習 OLAP 的開放資料集
    - https://g0v.hackmd.io/gGGUBDEXQOKGL_feUpPekg
- 中選會選舉資料打包檔	
    - cand.csv - 候選人資料
        - 9 萬多筆
        - 包含各種選舉的候選人，村里、國大代表 ..等
        - 欄位：所屬政黨、性別、生日、學歷、是否現任、當選註記
    - vote.csv - 投票資料
        - 400 多萬行
        - 只放 1000 行 Sample 資料
        - 欄位可以與 "cand.csv - 候選人資料" 串起來
- 2018 年之後的政治獻金收入資料
    - incomes.csv
    - 哪一場選舉、縣市、候選人
    - 申報序號
        - 辦公室支出
        - 四年內選舉使用
        - 捐給慈善或所屬政黨
    - 返還或已繳庫
        - 可能是不能收，就繳庫
    - 非金錢類
        - 例如礦泉水
- 2018 年之後的政治獻金支出資料
    - expenditures.csv
    - 科目
        - 有統一格式
    - 支出用途
        - 欄位可以自行修改用詞，沒有一定的統一格式

Kiang> 最近三次的財團統計，不過財團定義資料從 2016 之後就沒有更新了
- https://github.com/starsdog/openGroups

Power up your data science workflow with ChatGPT. 通過 Pandas 直接看 CSV 的 AI 
- pandas-gpt is a Python library for doing almost anything with a pandas DataFrame using ChatGPT prompts.
- https://github.com/rvanasa/pandas-gpt
- https://github.com/gventuri/pandas-ai
- （pandas-ai 可以用本地運行的 AI 但沒有顯卡超慢超痛苦⋯⋯ OpenAI API 真香）
:::spoiler 點選顯示更多 pandas-ai code
[Pandas-AI](https://github.com/gventuri/pandas-ai) is one of the cool LLM tools for CSV analysis.

1. It can be `pandas` + `ChatGPT`
```python
import pandas as pd
from pandasai import PandasAI

# Sample DataFrame
df = pd.DataFrame({
    "country": ["United States", "United Kingdom", "France", "Germany", "Italy", "Spain", "Canada", "Australia", "Japan", "China"],
    "gdp": [19294482071552, 2891615567872, 2411255037952, 3435817336832, 1745433788416, 1181205135360, 1607402389504, 1490967855104, 4380756541440, 14631844184064],
    "happiness_index": [6.94, 7.16, 6.66, 7.07, 6.38, 6.4, 7.23, 7.22, 5.87, 5.12]
})

# Instantiate a LLM
from pandasai.llm.openai import OpenAI
llm = OpenAI(api_token="YOUR_API_TOKEN")

pandas_ai = PandasAI(llm)
pandas_ai(df, prompt='Which are the 5 happiest countries?')
```

2. It can also run on local (need >8GB GPU RAM)
1) install dependencies
```bash
pip install pandasai[langchain] rwkv tokenizer
```
2) code
```python
import pandas as pd
from pandasai import PandasAI

# Sample DataFrame
df_cand = pd.read_csv('cand.csv')
df_vote = pd.read_csv('vote.csv')

# Instantiate a LLM
from pandasai.llm.openai import OpenAI
llm = OpenAI(api_token="YOUR_API_TOKEN")

pandas_ai = PandasAI(llm)
pandas_ai([df_cand, df_vote], prompt='哪個候選人籌措到最多錢？')
```
3) replace OpenAI LLM with local LLM
  a) download checkpoints
```bash
wget https://huggingface.co/BlinkDL/rwkv-4-raven/resolve/main/RWKV-4-Raven-3B-v12-Eng49%25-Chn49%25-Jpn1%25-Other1%25-20230527-ctx4096.pth
mv RWKV-4-Raven-*.pth RWKV-4-Raven-3B.pth
wget https://raw.githubusercontent.com/BlinkDL/ChatRWKV/main/20B_tokenizer.json
```

  b) change code
```python
## Instantiate a LLM
#from pandasai.llm.openai import OpenAI
#llm = OpenAI(api_token="YOUR_API_TOKEN")

from langchain.llms import RWKV

# Test the model
def generate_prompt(instruction, input=None):
    if input:
        return f"""Below is an instruction that describes a task, paired with an input that provides further context. Write a response that appropriately completes the request.

# Instruction:
{instruction}

# Input:
{input}

# Response:
"""
    else:
        return f"""Below is an instruction that describes a task. Write a response that appropriately completes the request.

# Instruction:
{instruction}

# Response:
"""


llm = RWKV(model="RWKV-4-Raven-3B.pth",
             strategy="cuda fp16i8",
             tokens_path="20B_tokenizer.json")

pandas_ai = PandasAI(llm)
pandas_ai([df_cand, df_vote], prompt=generate_prompt('哪個候選人籌措到最多錢？'))
```
> ⚠️ Less accuracy result with 3B model. Recommended to use 7B (>14 GPU RAM), 12B (>22 GPU RAM) or OpenAI API models.
:::



Join, Union 什麼的 SQL 好痛苦，不如提問提要求然後要 AI 來查詢資料庫和文件：  
- 可以幫忙寫 SQL 的 AI
- 可以直接回答問題
- https://github.com/eosphoros-ai/DB-GPT
- 但要在本地運行 LLM 而且要有顯卡不然超慢超痛苦

## 分析靈感

### 捐款來源產業別
- Ronny 有建立一個產業別清單
- 單一候選人，收到「營利事業」捐助的比例

### 一票花多少錢？
- 「總支出」與「得票數」
    - https://docs.google.com/spreadsheets/d/1peMSInCKhiG4JBgln1vf1gOyTtRrukTouugs-KccGIs/edit#gid=107283867
    - 註記：
        - googlesheet　裡面得票數是空白
            - (1) 多數是因為「補選」，中選會把得票資料另外提供檔案
            - (2) 真的後來沒參選
                - 案例：111年直轄市市長選舉 桃園市 羅智強 支出 14,434,646
                    - 初選沒過
                - 案例：[待貼數字] 109年立法委員選舉	屏東縣	莊瑞雄
                    - 讓出選舉名額
                - 案例：[待貼數字] 時代力量 議員 500 萬?
                    - 退選
- 現任優勢，支出費用減少
    - 新北市 市長選舉 侯友宜 
        - 107 1.5 億
        - 111 ? 千萬
    - 花蓮縣 縣長選舉


### 各層級選舉參選者有開戶比例、當選者有開戶比例、開戶後沒參選
- 是否有人，有當選但沒開戶？
    - 目前有查到立委層級有何志偉、傅崐萁
    - 縣市層級無查到
    - 議員非常多

### 從「收支科目或支出用途」歸類支出種類分佈
- 候選人花多少錢用於宣傳支出？ >>> 找相對應的「收支科目」
    - 選舉名稱	縣市	擬參選人／政黨	申報序號／年度	收支科目	捐贈者／支出對象 金額
- [收入完整相關統計](https://docs.google.com/spreadsheets/d/1v4x-X_Rert2xUCSz7rv1FtcCkzbLekYat2iNs3lUcqA/edit#gid=1160542376)
- [支出完整相關統計](https://docs.google.com/spreadsheets/d/1v4x-X_Rert2xUCSz7rv1FtcCkzbLekYat2iNs3lUcqA/edit#gid=1761213600)
    - 註記：「公共關係費用支出」這個項目
        - 花籃、書法社、聯誼費用、買飲料

### 看板
- 在支出用途欄位，包含 "看板" 關鍵字，上次查有 1 萬多筆
- 有看板，但無支出明細，來找出未申報的狀況
    - 需要 看板端的資料集，提供「候選人姓名」，才可以與政治獻金資料對應起來
- 已有各種看板追追追的專案團體、拍照上傳成果 
    - https://g0v.hackmd.io/Yn4uM3VQRdiJhH5D4ANXyw

### 餐飲美食店家
- 撈法
    - 從「收支科目」沒有對應項目
    - 所以要從「支出用途」累積關鍵字詞
        - 「餐」
            - 支出對象重複者整合
                - 不過仍有一些填寫方式，需要人工判斷是否為同一家
                    - 例如超商
                    - 例如飲料店名稱
            - 5 萬多筆資料
            - 用「餐」這個字來撈資料，也會撈出「餐會」
            - 資料集網址：https://docs.google.com/spreadsheets/d/1v4x-X_Rert2xUCSz7rv1FtcCkzbLekYat2iNs3lUcqA/edit#gid=127162616
        - 「飲」
            - 用「飲」這個字來撈資料，會撈到「飲料」?
        - 「食」
            - 用「食」這個字來撈資料，會撈到「食物」?
        - 「茶」
            - 用「茶」這個字來撈資料，會撈到「茶點」?
- 延伸
    - 跨黨派美食
    - 類似米其林三星台灣地圖
    - 韓國與台灣的國會美食 https://g0v.hackmd.io/y_O_IpKrRxm6pG5rlO4enw

### 幽靈支出單位？
- 成立沒有很久，選後就沒有
    - From [江明宗](https://www.facebook.com/k.olc.tw/posts/pfbid02Pg5tL7wxsHXzuU6scGvQ3Vzkrxqqnt8dcXqpoP9VsTNLXEfZ6euPSEd5PdiSuv9zl)
    - 大芮整合行銷，登記在悅世界 
    - 2022年3月成立，資本額 20 萬
    - 2022選舉收了 333 萬，2023年5月解散
- 初選但沒有競選市長，案例：羅智強與雪芃廣告

### 整體金流梳理構想
- 來源
    - [已有資料集] 監察院平台有紀錄的捐款
    - [應該沒資料？] 候選人自掏腰包
    - [應該沒資料？] 平台無紀錄的捐款
    - [應該沒資料？] 支持者自掏腰包
    - [應該沒資料？] 所屬政黨支援
- 支出
    - [已有資料集] 監察院平台有紀錄的支出
    - [應該沒資料？] 平台無紀錄的支出
- 示意圖簡報檔案
    - https://docs.google.com/presentation/d/1ElAKIXaSQ4ub8jA2XDbMr1QHLHjAiiDK0b1iTY2wt3I/edit#slide=id.g21f962ea493d7704_0

### 參考資料

選舉，不是你想的那樣！：人渣文本的48堂公民實戰課
- https://www.books.com.tw/products/0010697378













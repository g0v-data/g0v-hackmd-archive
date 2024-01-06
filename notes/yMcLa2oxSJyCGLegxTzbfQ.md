---
tags: 0archive, disinfo
---
# 0archive 資料分析教學

## PTT 政黑版使用者行為（使用 Python）

以下所寫的程式都放在 disinfoRG GitHub 的 [Tutorial repo](https://github.com/disinfoRG/Tutorial/tree/master/ptt-users)，可以直接 clone 下來跑看看。也可以直接看 [Jupyter notebook](https://github.com/disinfoRG/Tutorial/blob/master/ptt-users/hatepolitics.ipynb)。

### 設定專案架構、載入資料

1. 開一個專案使用的目錄。

    ```shell
    $ mkdir ptt-users
    $ cd ptt-users
    ```

2. 安裝需要的 Python 套件。建議先建一個專用的使用環境（可以用 [venv](https://docs.python.org/3/library/venv.html?highlight=venv#module-venv)、[pipenv](https://pipenv.pypa.io/en/latest/) 或 [conda](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#creating-an-environment-with-commands)）：

    ```shell
    $ python -m venv env
    $ source env/bin/activate
    $ pip install numpy pandas matplotlib
    ```

3. 到[公開資料集](https://drive.google.com/drive/folders/1ckDs03tdXhLdeF0N2St5OP0EeqxFC1bm)目錄裡下載資料。我們會用到的是 [Ptt 政黑版](https://drive.google.com/drive/folders/1sOsJWcWkAcPWsqUzFVC6PSuKs89cpg-O)，[2019 年 12 月](https://drive.google.com/open?id=11Rpvgrvq21Dc9Rjkq5s-e9pv22Y4Y6Fy)與[2020 年 1 月](https://drive.google.com/open?id=1sqi4phpVWvmFMPJJb-_QyK6-4aQTcN67)發文資料。把檔案抓下來，unzip 到專案目錄底下。

    ```shell
    $ unzip ~/Downloads/2019-12.zip
    $ unzip ~/Downloads/2020-01.zip
    ```

4. 在 `hatepolitics.py` Python script 裡載入剛才抓回來的資料：

    ```python
    import numpy as np, pandas as pd, matplotlib.pyplot as plt
    from pathlib import Path
    import itertools
    from datetime import *

    data_dir = Path(".")


    def load_data(*path_globs):
        df_all = pd.concat(
            [
                pd.read_json(json_file, lines=True, encoding="utf-8")
                for json_file in itertools.chain(
                    *[data_dir.glob(path_glob) for path_glob in path_globs]
                )
            ],
            ignore_index=True,
        )
        # take the lastest version of each publication in the dataset
        return (
            df_all.sort_values("version").groupby("id").last().sort_values("published_at")
        )


    hate_politics = load_data("2019-12-*.jsonl", "2020-01-*.jsonl")
    ```

    0archive 的發文資料集，每一筆資料都由一個 publication_id 與 version 唯一識別。一篇在網路上發表的文章，內容可能修改過許多次，有好幾個版本。0archive 會多次抓取同一個網址，如果文章內容修改過，就會存下一個新版本。每篇文章由唯一的 publictaion_id 識別，每個版本有不同的 version。
    
    因為接下來我們要分析的是發文數量，文章發表後的版本更新，不在我們的考慮之中。上面程式裡的這行
    
    ```python
    df_all.sort_values("version").groupby("id").last().sort_values("published_at")
    ```
    
    是資料集裡留下每篇文章最後抓到的版本，移除其它版本，並且以發表時間排序。

5. 修正欄位格式。0archive 資料集裡，"published_at"、"first_seen_at"、"last_updated_at" 都是 ISO 8601 格式的日期時間字串。我們把這些轉換成 Python 的 datetime，並增加一個發文日期 "published_date" 方便接下來的分析：

    ```python
    def convert(df):
        for f in ["published_at", "first_seen_at", "last_updated_at"]:
            df[f] = pd.to_datetime(df[f])
        df["published_date"] = df.published_at.map(lambda d: d.date())


    convert(hate_politics)
    ```

### 發文量、活躍使用者

1. 可以來簡單看一下資料長什麼樣子了。我們看一下這兩個月的發文量變化：

    ```python
    plt.figure(figsize=(12.8, 9.6))
    plt.plot(counts_by_day(df))
    plt.savefig("usage.png")
    ```
    
   執行下去，會看到一個 `usage.png` 檔案，畫出了發文量曲線。
   ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_585dd99db6d285755b7e5f2900df6f6b.png)
   可以看到大約在投票日（2020-01-11）前後，有一波發文高峰。我們比較一下選舉前後的發文量差異：
   
    ```python
    print(counts_by_day(df[df.published_date < date(2020, 1, 1)]).describe())
    print(counts_by_day(df[df.published_date > date(2020, 1, 13)]).describe())
    ```
    
   結果顯示 2020-01-13 之後到 1 月底的每日發文量平均，大約只有 2019 年 12 月的 6 成：
   
    ```txt
    count      31.000000
    mean     1069.838710
    std       229.658311
    min       611.000000
    25%       929.500000
    50%      1040.000000
    75%      1208.000000
    max      1622.000000
    dtype: float64
    count      18.000000
    mean      613.444444
    std       241.078514
    min       386.000000
    25%       451.500000
    50%       500.000000
    75%       715.250000
    max      1093.000000
    dtype: float64
    ```

2. 我們來看看個別作者在這段期間的發文數。

    ```python
    authors = df.author.value_counts()
    print(authors.describe())
    ```

   這段期間共有 6265 位使用者發文，平均每位發文約 10.6 篇。不意外地，超過一半的使用者發文數在 2 篇以下：
   
    ```txt
    count    6265.000000
    mean       10.632562
    std        25.478361
    min         1.000000
    25%         1.000000
    50%         2.000000
    75%         8.000000
    max       539.000000
    Name: author, dtype: float64
    ```

3. 假設我們想瞭解這段時間發文量最多的 1/4 的使用者們，有哪些不同的行為，我們可以看這些使用者的每日發文數的統計：

    ```python
    top_authors = authors[authors >= 8.0]
    top_author_stats = top_authors.to_frame().apply(
        lambda author: counts_by_day(df[df.author == author.name]).describe(), axis=1
    )
    print(top_author_stats)
    ```

   發文數最多的一群人，平均每日發文大約在 5 篇上下，中位數大部份是 5 篇，但標準差不一，表示他們不一定每天都固定發表這麼多文章。
   
    ```txt
                  count      mean       std  min  25%  50%   75%   max
    kero2377       61.0  8.836066  6.738398  2.0  5.0  7.0  10.0  38.0
    songgood       62.0  5.080645  1.662493  2.0  5.0  5.0   5.0  15.0
    tagso          59.0  4.830508  2.450563  1.0  4.0  5.0   5.0  20.0
    nicholas0406   55.0  5.127273  2.160714  1.0  5.0  5.0   5.0  18.0
    thouloveme     57.0  4.526316  1.489310  1.0  4.0  5.0   5.0  10.0
    ...             ...       ...       ...  ...  ...  ...   ...   ...
    airiguodala     3.0  2.666667  2.886751  1.0  1.0  1.0   3.5   6.0
    ryanwen         5.0  1.600000  0.894427  1.0  1.0  1.0   2.0   3.0
    mike143677      3.0  2.666667  2.081666  1.0  1.5  2.0   3.5   5.0
    MoneyMonkey     5.0  1.600000  0.894427  1.0  1.0  1.0   2.0   3.0
    a9104324        5.0  1.600000  1.341641  1.0  1.0  1.0   1.0   4.0
    ```

4. 假設我們對於每日固定上政黑版、固定發某個數量的文章的使用者感興趣。我們可以抓個範圍，把他們篩選出來，例如在有發文的日子，每日發文中位數 5 篇以上、標準差 1.2 以下：

    ```python
    consistent_authors = top_author_stats[
        (top_author_stats["std"] < 1.2) & (top_author_stats["50%"] >= 5.0)
    ]
    print(consistent_authors)
    ```
    
   結果是這幾位使用者：

    ```txt
                 count      mean       std  min   25%  50%  75%  max
    macaron5566   54.0  4.333333  1.115922  1.0  4.00  5.0  5.0  5.0
    oftisa        44.0  4.431818  0.925045  2.0  4.00  5.0  5.0  5.0
    nawabonga     17.0  4.764706  1.032558  1.0  5.00  5.0  5.0  6.0
    qwe3457878    15.0  4.333333  0.975900  2.0  4.00  5.0  5.0  5.0
    buoyant0828    5.0  4.600000  1.140175  3.0  4.00  5.0  5.0  6.0
    erkunden       4.0  4.750000  0.500000  4.0  4.75  5.0  5.0  5.0
    ```

   這幾位使用者裡面可能有些有趣的行為。用他們的 ID 交叉查詢 Google News 等其它資料庫，也會有些發現。

### 使用者來源 IP 交叉分析

[i'Analyseur 鄉民的鍵盤分析師](https://www.ianalyseur.org/)是一套 PTT 使用者的行為分析工具。其中有個功能是，從一個使用者連線到 PTT 的來源 IP，比對出其它也使用過這個 IP 連線到 PTT 的使用者，藉此[關連](https://www.ianalyseur.org/user/realtw/)推測使用分身帳號的可能。

不過 i'Analyseur 的資料只[更新](https://www.ianalyseur.org/faq/)到 2018 年 11 月 8 日。2020 選舉前後的使用者行為，目前還看不到。

利用 0archive 的 PTT 資料集，我們可以用最新的資料做類似的分析。

1. 首先從資料集裡的發文者（author）與來源 IP（connect_from）欄位，整理一份樞紐分析表：

    ```python
    lookup_table = (
        df[["author", "connect_from"]]
        .groupby(["author", "connect_from"])
        .size()
        .to_frame("count")
        .reset_index()
        .pivot("author", "connect_from", "count")
    )
    ```
    
2. 我們可以從樞紐分析表中查詢出需要的資料：

    ```python
    def ianalyseur(table, username):
        """
        List the IP addresses ever used by user `username`, with all of the users that have ever used each of these IPs and the number of times they have used it.
        """
        connect_from_user = table.loc[username]
        data = {}
        for ip in connect_from_user[connect_from_user > 0].index:
            connect_from_ip = table[ip]
            for user in connect_from_ip[connect_from_ip > 0].index:
                data[(ip, user)] = int(connect_from_ip.loc[user])
        return pd.DataFrame(
            data.values(), index=pd.MultiIndex.from_tuples(data.keys()), columns=["count"]
        )
    ```

3. 以使用者 "nawabonga" 為例，查詢 `print(ianalyseur(lookup_table, "nawabonga"))` 可以得到

    ```txt
                                             count
    101.12.163.236 nawabonga                    15
                   nawabonga (vista不到三年就玩完)      6
    115.82.134.222 nawabonga                    13
                   nawabonga (vista不到三年就玩完)      3
    115.82.20.125  isaluku                      37
                   nawabonga                     8
                   nawabonga (vista不到三年就玩完)      2
    115.82.20.78   nawabonga                    10
                   nawabonga (vista不到三年就玩完)      2
    118.233.86.18  isaluku                      29
                   isaluku (山本君)                 2
                   kapasky                      14
                   kapasky (偽卡巴斯基)               3
                   nawabonga                    14
                   nawabonga (vista不到三年就玩完)      6
    163.20.242.34  isaluku                      21
                   isaluku (山本君)                 5
                   kapasky                       3
                   kapasky (偽卡巴斯基)               3
                   nawabonga                     8
                   nawabonga (vista不到三年就玩完)      1
    49.214.228.220 nawabonga                     8
                   nawabonga (vista不到三年就玩完)      2
    49.216.17.208  nawabonga                     2
    49.216.4.114   nawabonga                     3
    ```

   從結果看來，資料集裡有些欄位沒有清理乾淨（⋯⋯），發文者的 ID 和暱稱沒有區分開來。結果也可以看到，nawabonga、isaluku、kapasky 這 3 個 ID 經常共用來源 IP。例如 115.82.20.125 這個 IP，在 2019-12-01 到 2020-01-31 之間 nawabonga 用了 10 次、isaluku 用了 37 次。
   
   從 i'Analyseur 也可以得到[類似的結論](https://www.ianalyseur.org/user/nawabonga/)。用 0archive 的資料集，我們可以把這個分析模型套到不同的時間區段，配合這些使用者的發文資料，看看能不能找出更多洞見。0archive 也提供 [Ptt 八卦版資料](https://drive.google.com/drive/folders/1mQWXRD8NZoI0paZSFpBD713VijdoJ7c2)（目前還不完整），可以加進來做進一步分析。

## PTT 政黑版使用者行為（使用 R）

1. 到[公開資料集](https://drive.google.com/drive/folders/1ckDs03tdXhLdeF0N2St5OP0EeqxFC1bm)目錄裡下載資料。
2. 在資料目錄內建立 hatepolitics.r
3. 進入R並install.packages('jsonlite')
4. 在 hatepolitics.r 裡載入剛才抓回來的資料：
```R
library('jsonlite')
dir <- "."
file_list <- list.files(path=dir, pattern = "\\.jsonl$")
mat_all <- fromJSON(readLines(file_list[1], n=1)) #init matrix
for(filename in file_list)
{  
  jsonlines <- readLines(filename)
  for(data in jsonlines)
  {
    mat_tmp <- fromJSON(data)
    mat_all <- rbind(mat_all, mat_tmp)
  }
}
mat_all <- mat_all[-1,] #remove the data for init matrix
rownames(mat_all) <- NULL
df <- as.data.frame(mat_all) #we get the dataframe df

print(df[,4:5]) #author & ip
```
即可透過R語言操作dataframe去產生圖表分析

## 肺炎名稱使用（？）


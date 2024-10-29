**创建新的 Conda 环境**
```
conda create -n NLP python=3.9
conda install -c conda-forge transformers pandas matplotlib nltk
conda install -c pytorch torch
conda activate NLP
conda install ipykernel
python -m ipykernel install --user --name NLP --display-name “NLP py"

```
# 主體程式碼
```
import numpy as np
import pandas as pd
import sqlite3
from transformers import pipeline
import time

# 加载情感分析模型
sentiment_analyzer = pipeline("sentiment-analysis", model="uer/roberta-base-finetuned-chinanews-chinese")

# 设置数据库路径
db_path = 'D:/SQLlite/udn.db'

# 连接到数据库，设置超时时间
conn = sqlite3.connect(db_path, timeout=10)
cursor = conn.cursor()

# 确保 `climate_change` 表中有 `sentiment` 和 `score` 列
# 若没有这些列，可以取消注释下面的代码进行添加
# cursor.execute("ALTER TABLE climate_change ADD COLUMN sentiment TEXT")
# cursor.execute("ALTER TABLE climate_change ADD COLUMN score REAL")

# 从数据库中读取 `climate_change` 表的全部数据
climate_data = pd.read_sql_query("SELECT * FROM climate_change ", conn)

# 定义情感分析函数
def analyze_weighted_sentiment(text, max_length=512):
    chunks = [text[i:i+max_length] for i in range(0, len(text), max_length)]
    
    positive_scores = []
    negative_scores = []
    
    for chunk in chunks:
        result = sentiment_analyzer(chunk, max_length=max_length, truncation=True)[0]
        score = result['score']
        weight = score  # 使用置信度作为权重
        
        if result['label'] == 'POSITIVE':
            positive_scores.append(score * weight)
        else:
            negative_scores.append(score * weight)
    
    # 计算加权平均分数
    avg_positive_score = np.sum(positive_scores) / len(positive_scores) if positive_scores else 0
    avg_negative_score = np.sum(negative_scores) / len(negative_scores) if negative_scores else 0

    dominant_sentiment = 'POSITIVE' if avg_positive_score >= avg_negative_score else 'NEGATIVE'
    dominant_score = max(avg_positive_score, avg_negative_score)
    
    return dominant_sentiment, dominant_score

# 测量情感分析的执行时间
start_time = time.time()

# 对数据进行情感分析
climate_data[['sentiment', 'sentiment_score']] = climate_data['content'].apply(
    lambda x: analyze_weighted_sentiment(x)
).apply(pd.Series)

end_time = time.time()
execution_time = end_time - start_time
print(f"單次情緒分析執行時間: {execution_time:.4f} 秒")

# 更新数据库的 sentiment 和 score 列
for index, row in climate_data.iterrows():
    cursor.execute('''
        UPDATE climate_change
        SET sentiment = ?, score = ?
        WHERE rowid = ?
    ''', (row['sentiment'], row['sentiment_score'], index + 1))

# 提交更改并关闭连接
conn.commit()
conn.close()

print("情緒分析結果已更新。")


```

示例
假设有两个片段的情感分析结果：

片段 1：POSITIVE，score = 0.9。
片段 2：NEGATIVE，score = 0.4。
则计算如下：

正面得分：0.9 * 0.9 = 0.81
负面得分：0.4 * 0.4 = 0.16
加权平均分数：
avg_positive_score = 0.81 / 1 = 0.81
avg_negative_score = 0.16 / 1 = 0.16
主导情感：POSITIVE
主导情感得分：dominant_score = 0.81
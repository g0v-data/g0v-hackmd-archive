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
import pandas as pd
import numpy as np
from transformers import pipeline
import matplotlib.pyplot as plt
```
```
# 加载情感分析模型
#sentiment_analyzer = pipeline("sentiment-analysis", model="distilbert-base-uncased-finetuned-sst-2-english")
# 使用 RoBERTa 模型替换
#sentiment_analyzer = pipeline("sentiment-analysis", model="cardiffnlp/twitter-roberta-base-sentiment")
sentiment_analyzer = pipeline("sentiment-analysis", model="uer/roberta-base-finetuned-chinanews-chinese")
```
```
# 读取新闻数据的前两行
climate_data = pd.read_csv("climate_change.csv").head(20)  # 只取前两行数据
#climate_data = pd.read_csv("climate_change.csv")
#climate_data = climate_data.iloc[[50]] 
# 定义分析函数
def analyze_weighted_sentiment(text, max_length=512):
    chunks = [text[i:i+max_length] for i in range(0, len(text), max_length)]
    
    positive_scores = []
    negative_scores = []
    
    for chunk in chunks:
        result = sentiment_analyzer(chunk, max_length=max_length, truncation=True)[0]
        score = result['score']
        weight = score  # 以置信度作为权重
        
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





# 对指定行数据进行情感分析
climate_data[['sentiment', 'sentiment_score']] = climate_data['content'].apply(
    lambda x: analyze_weighted_sentiment(x)
).apply(pd.Series)

# 查看结果
print(climate_data[['content', 'sentiment', 'sentiment_score']])

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
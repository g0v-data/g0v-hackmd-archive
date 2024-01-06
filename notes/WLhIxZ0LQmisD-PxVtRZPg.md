# NLP自然語言處理
## 文字雲
```python=
wordcloud = WordCloud(width = 800, height = 800, 
                background_color ='white', 
                stopwords = stopwords, 
                min_font_size = 10).generate(text) 

plt.figure(figsize = (8, 8), facecolor = None) 
plt.imshow(wordcloud) 
plt.axis("off") 
plt.tight_layout(pad = 0) 
  
plt.show() 
```
## Wordnet 向量/相關詞
```python=
# 同義詞集合
from nltk.corpus import wordnet as wn
wn.synsets('trunk')
wn.synset('car.n.01').lemma_names()

# 查找 motorcar 所屬的 synset 定義
wn.synset('car.n.01').definition()

# 上下位詞
motorcar = wn.synset('car.n.01')
types_of_motorcar = motorcar.hypernyms()

motorcar = wn.synset('car.n.01')
types_of_motorcar = motorcar.hyponyms()

# 找到下位詞組後後，再從 synset 找出單詞（以詞為中心）
sorted(lemma.name() for synset in types_of_motorcar for lemma in synset.lemmas())

# 完整路徑（上位詞組再往上走）
motorcar = wn.synset('car.n.01')
motorcar.hypernym_paths()

# 直指頂端上位詞組
motorcar = wn.synset('car.n.01')
motorcar.root_hypernyms()

# 以鯨魚為例
right = wn.synset("right_whale.n.01") 
minke = wn.synset("minke_whale.n.01")
# 「露脊鯨」與「小鬚鯨」在上位詞組中最低位的詞組
right.lowest_common_hypernyms(minke)

# 露脊鯨 vs 虎鯨
right = wn.synset("right_whale.n.01") 
orca = wn.synset("orca.n.01")
right.lowest_common_hypernyms(orca)

# 計算由當前 synset 而上的階層數
print(wn.synset('baleen_whale.n.01').min_depth())
print(wn.synset('whale.n.02').min_depth())
print(wn.synset('vertebrate.n.01').min_depth())
print(wn.synset('entity.n.01').min_depth())

# 上下位詞組結構的相似程度 (數字接近1代表path越像)
print(right.path_similarity(right))     #露脊鯨和自己本身
print(right.path_similarity(minke))     #露脊鯨和小鬚鯨
print(right.path_similarity(tortoise))  #露脊鯨和陸龜
print(right.path_similarity(novel))     #露脊鯨和小說
```
## jieba 重要詞
```python=
import jieba
sentence = "足球運動需要大家一起來推廣，歡迎加入我們的行列！"
words = jieba.tokenize(sentence)
for tk in words:
    print("word {}\t\t start: {} \t\t end:{}".format(tk[0],tk[1],tk[2]))
    
# 權威詞(重要單詞)
import jieba.analyse

content = open('./dataset/news.txt', 'r').read()

tags = jieba.analyse.extract_tags(content, 10)

print(",".join(tags))
```
## 文字轉向量 
```python=
# Bag of Word
from sklearn.feature_extraction.text import CountVectorizer

bards_words =["The fool doth think he is wise,",
              "but the wise man knows himself to be a fool"]

# 建立模型
vect = CountVectorizer(stop_words="english")
vect.fit(bards_words)

print("Vocabulary size: {}".format(len(vect.vocabulary_)))
print("Vocabulary content:\n {}".format(vect.vocabulary_))

# 轉換成向量
bag_of_words = vect.transform(bards_words)
print("Features name:\n{}".format(vect.get_feature_names()))
print("Dense representation of bag_of_words:\n{}".format(bag_of_words.toarray()))


# N-Gram 幾個字為單位
vect1 = CountVectorizer(ngram_range=(1, 1)).fit(bards_words)
print("Vocabulary size: {}".format(len(vect1.vocabulary_)))
print("Vocabulary:\n{}".format(vect1.get_feature_names()))

vect2 = CountVectorizer(ngram_range=(2, 2)).fit(bards_words)
print("Vocabulary size: {}".format(len(vect2.vocabulary_)))
print("Vocabulary:\n{}".format(vect2.get_feature_names()))
print("Transformed data (dense):\n{}".format(vect2.transform(bards_words).toarray()))

# 詞性標註POS Tagging
import jieba.posseg as pseg
words = pseg.cut("今天天氣很好")
for w in words:
    print('{} {}'.format(w.word, w.flag))
```
## Gensim
```python=
import gensim
from gensim import corpora

# Tokenize(split) the sentences into words
texts = [[text for text in doc.split()] for doc in documents]

# Create dictionary
dictionary = corpora.Dictionary(texts)

# Get information about the dictionary
print(dictionary)
#> Dictionary(33 unique tokens: ['Saudis', 'The', 'a', 'acknowledge', 'are']...)
# 查看字典內單字
dictionary.token2id

dictionary.add_documents(texts_2)

# 詞向量CBOW & Skip-gram
import gzip
import gensim
import logging
logging.basicConfig(format='%(asctime)s : %(levelname)s : %(message)s', level=logging.INFO)

data_file="./dataset/reviews_data.txt.gz"

def read_input(input_file):
    """This method reads the input file which is in gzip format"""
    
    print("reading file {0}...this may take a while".format(input_file))
    
    with gzip.open (input_file, 'rb') as f:
        for i, line in enumerate (f): 

            if (i%10000==0):
                print("read {0} reviews".format (i))
            # do some pre-processing and return a list of words for each review text
            yield gensim.utils.simple_preprocess (line)

# read the tokenized reviews into a list
# each review item becomes a serries of words
# so this becomes a list of lists
documents = list (read_input (data_file))
print("Done reading data file")

# 向量
model = gensim.models.Word2Vec (documents, vector_size=150, window=10, min_count=2, workers=10, sg=0)
model.train(documents,total_examples=len(documents),epochs=10)

# 相似字
w1 = ["bed",'sheet','pillow']
w2 = ['couch']
model.wv.most_similar (positive=w1,negative=w2,topn=10)

# 相似度
model.wv.similarity(w1="dirty",w2="smelly")

# 找無關詞
model.wv.doesnt_match(["cat","dog","france"])

# 印出向量
model.wv['dirty']
```
## Gensim預訓練模型
```python=
import gensim.downloader
print(list(gensim.downloader.info()['models'].keys()))

import gensim.downloader as api
wv = api.load('word2vec-google-news-300')

vec_king = wv['king']

print(wv.most_similar(positive=['car', 'minivan'], topn=5))
```
## Spacy
```python=
import spacy 
nlp = spacy.load('en_core_web_sm')

doc = nlp("All human beings are born free and equal...")

# 斷句
for item in doc.sents:
    print(item.text)
    
sentences_as_list = list(doc.sents)

# 還原型態
for word in doc:
    print(word.text, word.lemma_)
    
# 詞性
for item in doc:
    print(item.text, item.pos_, item.tag_)
    
# 找動詞
verbs = []
for item in doc:
    if item.pos_ == 'VERB':
        verbs.append(item.text)
        
# 找特徵詞(固有名詞)
doc2 = nlp("John McCain and I visited the Apple Store in Manhattan.")
for item in doc2.ents:
    print(item.text, item.label_)
```
## 垃圾郵件分類
```python=
import pandas as pd
import numpy as np
df=pd.read_csv('./dataset/spam.csv')
df['target'] = df['label'].map( {'spam':1, 'ham':0 })

text_train = np.asarray(df['sms'])
y_train = np.asarray(df['target'])
print(text_train[:3])
print(y_train[:3])

# 文字轉向量
from sklearn.feature_extraction.text import CountVectorizer
vect = CountVectorizer(stop_words="english", min_df=5).fit(text_train)
X_train = vect.transform(text_train)
print(X_train.shape)
print(y_train.shape)

# 建模型
from tensorflow import keras
from tensorflow.keras import layers

model = keras.Sequential([
    layers.Dense(512, activation='relu', input_shape=(1602,)),
    layers.Dense(256, activation='relu'),
    layers.Dense(128, activation='relu'),
    layers.Dense(2, activation='softmax')
])

model.compile(optimizer=keras.optimizers.Adam(),
             loss=keras.losses.SparseCategoricalCrossentropy(),
             metrics=['accuracy'])
model.summary()

# 訓練模型
history = model.fit(X_train, y_train, batch_size=64, epochs=10, validation_split=0.3, verbose=2)

# 測試
sms_test = ['Hi Paul, would you come around tonight']

test_str  = vect.transform(sms_test)

model.predict_classes(test_str)
```
## Seq2Seq
```python=
model = Seq2Seq(
    data.num_word, data.num_word, emb_dim=16, units=32,
    max_pred_len=11, start_token=data.start_token, end_token=data.end_token)

# training
for t in range(1500):
    bx, by, decoder_len = data.sample(32)
    loss = model.step(bx, by, decoder_len)
    if t % 70 == 0:
        target = data.idx2str(by[0, 1:-1])
        pred = model.inference(bx[0:1])
        res = data.idx2str(pred[0])
        src = data.idx2str(bx[0])
        print(
            "t: ", t,
            "| loss: %.3f" % loss,
            "| input: ", src,
            "| target: ", target,
            "| inference: ", res,
        )

```
```python=
```
```python=
```

## 其他
NLTK = 提供文本及詞法定義
RNN網路 = 給網路記憶
attention層 => 在 encoder 和 decoder 上加權

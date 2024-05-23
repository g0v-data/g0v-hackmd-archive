#資料預處理

在本程式碼中，數據預處理的部分主要包括以下幾個步驟：
1. 文本清理（Cleaning Text）

移除 HTML 標籤和非字母字符，並將句子中的多餘空格替換為單個空格。


```
def clean_text(text):
    text = re.sub(r'<[^>]+>', '', text)  # 移除 HTML 標籤
    text = re.sub(r'[^a-zA-Z\s]', '', text)  # 移除非字母字符但保留空格
    text = re.sub(r'\s+', ' ', text)  # 用單個空格替換多個空格
    text = text.strip()  # 移除前後的空白字符
    return text
```

2. 合併和清理句子（Combining and Cleaning Sentences）

將句子合併成一個字符串並清理每個句子。


```
cleaned_sentences = [clean_text(' '.join(sentence)) for sentence in sentences]
```
3. 分割和編碼文本（Splitting and Encoding Text）

將清理後的句子合併成一個字符串，並將其分割成單詞列表，然後使用 Tokenizer 將單詞編碼為整數。

```
text = ' '.join(cleaned_sentences)
words = text.split()  # 用空格分割成單字列表
tokenizer = Tokenizer()
tokenizer.fit_on_texts(words)
encoded = tokenizer.texts_to_sequences(words)
```

4. 創建三元組（Generating Trigrams）

使用 NLTK 創建句子的三元組，並生成輸入序列。



def generate_trigrams(sentence):
    tokens = nltk.word_tokenize(sentence)
    trigrams = list(nltk.trigrams(tokens))
    return [' '.join(trigram) for trigram in trigrams]

all_trigrams = []
for sentence in cleaned_sentences:
    all_trigrams.extend(generate_trigrams(sentence))

5. 準備數據集（Preparing the Dataset）

將三元組轉換為整數序列，並填充序列使所有序列具有相同的長度。

```
input_sequences = []
for trigram in all_trigrams:
    token_list = tokenizer.texts_to_sequences([trigram])[0]
    for i in range(1, len(token_list)):
        n_gram_sequence = token_list[:i+1]
        input_sequences.append(n_gram_sequence)

max_sequence_len = max([len(x) for x in input_sequences])
input_sequences = np.array(pad_sequences(input_sequences, maxlen=max_sequence_len, padding='pre'))  # 轉換為 numpy 數組
```

6. 創建 X 和 Y（Creating X and Y）

分割輸入序列為 X 和 Y，其中 X 是輸入數據，Y 是標籤。

```
X, y = input_sequences[:,:-1], input_sequences[:,-1]
y = to_categorical(y, num_classes=vocab_size)
```
上述這些部分共同完成了數據預處理的任務，使得數據可以輸入到模型中進行訓練。


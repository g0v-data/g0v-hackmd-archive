---
tags: cofacts
---

# Cofacts multimedia support research

## Retrieving file data

https://developers.line.biz/en/reference/messaging-api/#get-content

## Search & indexing

- Research: all image retrieval methods https://g0v.hackmd.io/bhL6csQ8T1e81E2De7ZS5Q#Search-with-similarity
- Image hash bit length https://g0v.hackmd.io/LHhF_VQ1RdS12C0k0ESQ_Q
- Indexing in hamming space https://g0v.hackmd.io/xsDcMPySQM69vA0xHO8_dA#Indexing
- Large-Scale Video Retrieval Using Image Queries - 介紹 https://www.youtube.com/watch?v=tLqbdQR7kjM
    - 見下 vectors / documents 章節

### Hashed file names
[The OpenDream's approach](https://github.com/cofacts/rumors-line-bot/issues/7#issuecomment-890709756).

- Convert each reported image / video to perceptual hash (fingerprint) stores the file using the hash in its name.
  - hash: https://www.npmjs.com/package/image-hash
  - [image-hash research](https://g0v.hackmd.io/LHhF_VQ1RdS12C0k0ESQ_Q)
- During query, convert the query image / video in the same way and look up for the file with the same name in Google Drive directly.
    - Query is performed on client side (chatbot), did not take 3rd party applications into consideration.

Hash for other file formats

Videos
- ffmpeg extract 
    ```
    # skip_frame: https://superuser.com/questions/669716/how-to-extract-all-key-frames-from-a-video-clip
    # remove dup: https://stackoverflow.com/questions/37088517/remove-sequentially-duplicate-frames-when-using-ffmpeg
    ffmpeg -threads 1 -skip_frame nokey -lowres 3 -i [video-file] -vf mpdecimate  -vsync 0 -f image2 output/file-%04d.jpg
    ```
    - https://www.npmtrends.com/ffmpeg-vs-ffmpeg-static-vs-ffmpeg.js-vs-fluent-ffmpeg-vs-@ffmpeg/ffmpeg

Audios
- chromaprint (fpcalc)
    - 越長的檔案 fingerprint 就越長

### Vector / embedding based similarity

#### Systems supporting vector search

- OpenSearch KNN https://opensearch.org/docs/latest/search-plugins/knn/index/
- ElasticKNNs https://github.com/alexklibisz/elastiknn
- Elasticsearch 8.6
    - [`dense_vector` fields](https://www.elastic.co/guide/en/elasticsearch/reference/8.6/dense-vector.html)
        - Max dimension: 1024 for indexed vectors
        - Indexing are for Approximate kNN
    - Exact, brute-force knn w/ scripted score and `cosineSimilarity()` function
    - [Approximate kNN w/ HNSW algorithm](https://www.elastic.co/guide/en/elasticsearch/reference/8.6/knn-search.html#_combine_approximate_knn_with_other_features)
        - can [combine with ordinary query](https://www.elastic.co/guide/en/elasticsearch/reference/8.6/knn-search.html#_combine_approximate_knn_with_other_features) and calculate score together
    - Official guides
        - https://www.elastic.co/guide/en/elasticsearch/reference/8.6/knn-search.html
        - Blog post: https://www.elastic.co/blog/how-to-deploy-nlp-text-embeddings-and-vector-search#
        - Upload Python model on Huggingface to Elasticsearch https://www.elastic.co/guide/en/machine-learning/current/ml-nlp-text-emb-vector-search-example.html
            - Does not support image-related models ([reference](https://www.elastic.co/guide/en/machine-learning/current/ml-nlp-deploy-models.html#:~:text=Specify%20the%20type%20of%20NLP%20task.%20Supported%20values%20are%20fill_mask%2C%20ner%2C%20text_classification%2C%20text_embedding%2C%20and%20zero_shot_classification.))

#### Systems / software for near duplicate video search
- [Near Duplicate Video Retrieval](https://github.com/4ML-platform/ndvr)
    - Handles these: side morrored, color-filtered, and waterwashed. Middle row: horizontal screen changed to vertical screen with large black margins. Botton row: rotated
- [videohash](https://github.com/akamhy/videohash)
    - Python
    -  Near Duplicate Video Detection (Perceptual Video Hashing) - Get a 64-bit comparable hash-value for any video. 
    -  Have collisions on unrelated video https://www.reddit.com/r/DataHoarder/comments/q74hkz/videohash_python_package_for_near_duplicate_video/


#### Methodologies

Image / video vectors
- Large-Scale Image Retrieval with Elasticsearch http://nmis.isti.cnr.it/falchi/Draft/2018-SIGIR.pdf
    - 2018 SIGIR
    - 先把圖變成 R-MAC feature (multi-resolution, dimension=2048)
    - 然後想辦法變成可以 encode 成 word 的東西塞進 Elasticsearch
- The VISIONE Video Search System: Exploiting Off-the-Shelf Text Search Engines for Large-Scale Video Retrieval
https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8321359/
    - 影片轉 scene, object, color, CNN descriptors 轉成可以 encode 成 word 的東西
    - "Scalar Quantization-based Surrogate Text representation"
- Towards Practical Visual Search Engine Within Elasticsearch https://arxiv.org/pdf/1806.08896.pdf
   - 也是轉成 word
- [Fisher vectors](https://youtu.be/tLqbdQR7kjM?t=665)
    - compact local descriptor as fixed-length vector, 用在 retrieval 上可做 vector comparison
    - Asymmetric comparison of FV - 圖只佔一部分可找（think of image in LINE chat screenshots), 一種 bag of features
    - Introduced by Perronnin and Dance, CVPR '07
    -  [Analyzing Classifiers: Fisher Vectors and Deep Neural Networks](https://openaccess.thecvf.com/content_cvpr_2016/papers/Bach_Analyzing_Classifiers_Fisher_CVPR_2016_paper.pdf)
- IVWBAE2019 - Video indexing and retrieval based on content: a systematic literature review
    - [Spreadsheet](https://docs.google.com/spreadsheets/d/1JzuAMTjCmY6zUZLmo-CrVHdhZ9WtCH612pigwYjAg8U/edit#gid=1193420145)

Text embeddings
- [OpenAI text embedding](https://platform.openai.com/docs/guides/embeddings/limitations-risks)
    - Dimension = 1536
    - normalized to 1 (dot product for cosign similarity)
    - pgvector cosine similarity example https://github.com/mckaywrigley/wait-but-why-gpt
- [tf.js Multilingual Universal Sentense Encoder](https://tfhub.dev/google/universal-sentence-encoder-multilingual/3)
    - Input: Variable length text in Chinese, Chinese (Taiwan), English, etc
    - Output: 512 dimension vector
    - [Can compare similarity across languages](https://colab.research.google.com/drive/1aVM8RRxlGGN4YgjOafFl_yAQ4Ms_QNO4?authuser=0)

Multimodal embeddings (image / text embedding)
- Microsoft unilm https://twitter.com/alphasignalai/status/1630651280019292161
- https://arXiv.org/abs/2302.14045
- https://palm-e.github.io/
- Visual foundation models in https://github.com/microsoft/visual-chatgpt
- CLIP
    - https://huggingface.co/sentence-transformers/clip-ViT-B-32-multilingual-v1
    - Deploy -> Inference API -> JavaScript
    - Input layer - max_seq_length: 128
    - Output layer - out_features: 512
    - https://www.sbert.net/examples/applications/image-search/README.html (seems to support both image and text inputs)
- Facebook multimodal model ImageBind
    - https://github.com/facebookresearch/ImageBind
    - https://imagebind.metademolab.com/
    - Also includes audio & video!
    - HF: https://github.com/huggingface/transformers/issues/23240
    - Input layer: TBD


#### Analysis

- Benefits
    - 無論是 FV 還是 embedding 應都有 locality similarity，裁切或截圖後仍有機會找得到
    - 中文簡體繁體、英文原始訊息，有機會被 multilingual text embedding 放在很近的地方而檢索得到
    - ==AI 繪圖、無聲音無字幕的影片，透過 multimodal embedding 可能可以達成，輸入文字敘述來搜尋相符圖片的事情==
- Efforts to get these benefits
    - Upgrade to ES 8.6 to get access to vector search
    - Integrate tf.js or other vector generation methods
- 用在 Cofacts？
    - 絕大多數有影響力的圖文都是文字，OCR 會比 embedding 更有用
    - 文字搜尋上，embedding 是否有比 bm25 好或好多少，要看 Cofacts dataset 決定
    - 即使圖片影片中沒有文字可 OCR，有錯的通常是在圖說。這樣一來，[surrounding text](https://g0v.hackmd.io/@cofacts/rd/%2Ff_Ze19PhQuqx_fzOAOkohQ) 又比 vector search 重要。


## File storage & hosting

### Google drive
[The OpenDream's approach](https://github.com/cofacts/rumors-line-bot/issues/7#issuecomment-890709756).

### Google cloud storage

## Database model

Considerations:

- Store surrounding text?
- Store text content of the image / video / voice message for full-text search

:::success
Prefer "In separate `articles`" - [discussion](https://g0v.hackmd.io/1WADYBY0TH27ZqOaVMjqUg?both#Overall-discussion)
:::

### Use `articles`

[The OpenDream's approach](https://github.com/cofacts/rumors-line-bot/issues/7#issuecomment-890709756).

Article text does not contain anything but `$image__xxx`

No surrounding text & text content for full-text search.

### In `articles.attachments`

One article stores:
- `attachments`: attachment data and its trasncription text for full-text search
    - Therefore search queries should also look up this field
    - highlights should also consider this field in addition
- `text`: the surrounding text

### ✅ In separate `articles`

One article stores:
- `attachment`: the multimedia data
- `text`: its transcription for full-text search

Another article stores:
- `text`: the surrounding text

Connect related articles together in other ways
- Easier search (no extra field) but associations after search hit may be complex
    - Should seek replies in related article and display?


### Separate MediaEntry index

Article stores only
- text, which is the transcription for full-text search

New index `mediaentries` stores:
- _id: the `hash`
- `articleId`: maps to the article storing the transcription and replies
- `url`: the URL to the file on GCS
- Other feature vectors for similar image retrieval
- Other meta data like media type

Pros
- Each hash can only map to 1 media entry
    - Cannot have 2 articles having same hash
- Faster query time by hash
    - Super fast retrieval by hash (by ID, no index time)
    - faster time to retrieve by feature vector due to fewer documents to scan / index
- Can be separated from Cofacts article logic
    - Media manager can just feed an Elastic client to media manager
    - Media manager can manage the index by itself

Cons
- Still possible to have 2 articles created
    - Process: Search `mediaentries` index --> If no, create article --> write `mediaentries` index
    - It is still a non-atomic read-then-write, so article creation is still possible
    - If this occurs, there will be a empty article with no media entries pointing to it.
- Cannot mix image & text query together
- Increased complexity of managing a separate index

### Surrounding text (cooccurrence) model

#### Separate ArticleGroup index

- Create another index, `articlegroups`, to place co-occurrences of article groups.
- ID: sorted article IDs --> unique ID for the same composition
- Does *not* have dedicated reply-request and replies
- Just records a link
- Q: If a reply is used in multiple articles in the same group, when user gives feedback, whose article-reply-feedback is this?

Processing multiple messages on LINE bot

#### Article group as an `article`

- No `text` nor `attachment`, but has an `articleIds` field pointing to ID of individual articles
- Has its own reply requests & replies


#### Common problems
- How to count occurrences / popularity of a specific article group

## Processor model

### Handle in rumors-line-bot

OpenDream's approach: search logic, hashing is done on line bot

### ✅ Dedicated multimedia processor

:::success
Design doc: [Cofacts media manager implementation](/C8dW2cFiR1-N5Z0wcOefuA?both)
:::

- Add-on of current API server
    - API server can serve multiple clients
    - can limit access of related API using API kjeys
- Can be implemented stand-alone
    - Replace current google drive first
    - Article integration can come later

input:
- URL to fetch data
- should insert or just query

output:
list of deduped
- public file url
- identifier
- similarity (1 for exact match)

processing:
- The processor handles download, storage, resolving and search function.
- It stream uploads the file onto google cloud storage.
- [OPTIONAL] It caches file content of an URL for a short while, so that query --> create via same URL works smoothly

----

### Processor implementation

See [Cofacts media processor implementation](/C8dW2cFiR1-N5Z0wcOefuA)

## Other topics

### stream file convert

- Image: https://www.npmjs.com/package/sharp
- Video
    - https://github.com/fluent-ffmpeg/node-fluent-ffmpeg
    - https://github.com/phaux/node-ffmpeg-stream

### Transcriptions

Crowd-sourced transcription tools & developments 

https://crowdsourcingweek.com/blog/decade-in-crowdsourcing-transcription/

https://anjackson.github.io/zombse/062013%20Libraries%20&%20Information%20Science/static/questions/826.html

Amara API - https://apidocs.amara.org/#list-videos

The crowd-sourced project of Library of Congress - https://crowd.loc.gov/
Design principles: https://github.com/LibraryOfCongress/concordia/blob/main/docs/design-principles.md

Crowdsourcing the transcription of digitized archival records - https://ctasc.blog.yorku.ca/2020/04/14/crowdsourcing-the-transcription-of-digitized-archival-records/

Wikipedia rules
- vandalism https://zh.wikipedia.org/wiki/Wikipedia:%E7%A0%B4%E5%9D%8F
- revert https://zh.wikipedia.org/wiki/Help:%E5%9B%9E%E9%80%80


### OCR

[Originally on chatbot](https://github.com/cofacts/rumors-line-bot/blob/dd0a007e23f65d0fd8e1705baec290a1bf013361/README.md#process-image-messageusing-tesseract-ocr):
- tesseract-ocr binary in docker
- store file in file system and let the process read 

[tesseract.js](https://github.com/naptha/tesseract.js)
- Can work on nodejs and browser
- works slower than tesseract-ocr [name=nonumpa]

[MMOCR](https://github.com/open-mmlab/mmocr) - python based

[Google cloud vision API](https://cloud.google.com/vision/docs/ocr?hl=zh-tw)
- ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ba39a2e37de4637d36cec59ecbd1851d.png)


#### When to apply OCR
- when image search yields no hit?
- or everytime when image is provided? (chatbot original)
- On chatbot v.s. on API
- When user inputs OCR text, on website?

### Metadata extraction

Following up above info, we can extend OCR to other metadata, and further discuss when should we apply these extractions

#### What to extract
- metadata like duration in https://g0v.hackmd.io/@cofacts/rd/%2FC8dW2cFiR1-N5Z0wcOefuA
- OCR text for video and image
- [multimodal embeddings / feature vectors](#Vector--embedding-based-similarity)

#### When to extract
- After ID is extracted by media manager?
    - Pros:
        - We can cache ID <> extracted info; when cache hits, don't need to perform extraction again, which may cost money and resources
        - Not all multimedia content are store in`articles` in Elasticsearch. cache IDs can be more flexible and may have search hit on popular search queries
    - Cons:
        - Slow -- download media twice (1 for ID, another for actual extraction) if ID cache miss
        - Complicates the system by additional cache lookup mechanism
- Extract in media manager?
    - Introduce new concept, *processors*, that is called alongside with [hash generation](https://github.com/cofacts/media-manager/blob/4b3b9a87ca4241f6e34b9fe6d980f8a1065b3b21/src/MediaManager.ts#L93-L94)
        - Output of processors (extracted info or vectors) are attached to `queryInfo`
        - Media manager does not store the extracted info itself.
    - Pros:
        - Cleaner implementation that separates API and media logic work
    - Cons:
        - Cannot implement cache
            - Media manager only records media that should be saved
            - Implemeting one will have the same complication as the previous solution
        - Extraction is made again and again for even the same binary
            - Limits the methods we use in extraction in terms of cost; only choice for OCR may be tesseract.js

#### How to extract

[Google Video Intelligence API](https://cloud.google.com/video-intelligence/docs/annotate-video-command-line?hl=en)
- [Visualizer](https://github.com/ZackAkil/video-intelligence-api-visualiser)
- [Pricing](https://cloud.google.com/video-intelligence/pricing?hl=en) ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6a8efe71436885d9632f297491c64d1a.png)



### Video summarization for thumbnails

Video summarization / abstraction / skimming

- Directly from 25% - 75% length - https://blog.logrocket.com/generating-video-previews-with-node-js-and-ffmpeg/
- Youtube:
  - Home page (https://www.youtube.com/) - 150% speed from 0:00
  - Recommendation list: fade in from thumbnail, pick 4 seconds of the video,  150% speed, loop
- DSNet - https://github.com/li-plus/DSNet
    - Paper 裡有整理 related work
- Related work 整理 https://github.com/seriousran/awesome-video-sum
- ffprobe to get duration https://www.npmjs.com/package/ffprobe

### Videos on Youtube / links

#### [Youtube data API](https://developers.google.com/youtube/v3)

- has all metadata, including duration, title, description, etc
- cannot store data for more than 30 days
    - Policy #: III.E.4.a-g ([Refreshing, Storing, and Displaying API Data](https://developers.google.com/youtube/terms/developer-policies#e.-handling-youtube-data-and-content)) 
    - Previous mitigations and research: [Youtube scrapping alternatives](/6f87Zwo7QAOGx7rYK-QRfw)

#### oembed

- Sample:  https://youtube.com/oembed?url=http://www.youtube.com/watch?v=iwGFalTRHDA&format=json
- Has title, author (not stored)
- url-resolver saves Youtube description via `unfurl` and `<meta description>`

#### schema.org microdata

:::success
Should implement this!
- Store parsed schema.org metadata in hyperlinks as-is
- Find a way to properly display the metadata
- Drop oembed if all data is in Microdata?
:::

- Youtube implements [VideoObject](https://schema.org/VideoObject)
- [Contains property](https://validator.schema.org/#url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DlSKd3yyhzw0)
    - `url`, `name`, `description`, `thumbnailUrl`, `embedUrl`
    - `duration`
    - [`interactionCount`](https://schema.org/interactionCount) - slightly less than play count, not sure why
    - `datePublished`, `uploadDate`
    - `author.name`, `author.url`
- Example: `view-source:https://www.youtube.com/watch?v=lSKd3yyhzw0`
    -`<meta itemprop="duration" content="PT31M55S">`
    - Format: [ISO8601 duration](https://en.wikipedia.org/wiki/ISO_8601#Durations)
- `cofacts/url-resolver` uses `unfurl`, which [supports custom `fetch`](https://github.com/jacktuck/unfurl/blob/master/src/index.ts#L47) (`node-fetch` instance)
    - We can store fetched result outside `unfurl` and parse microdata outside of unfurl.
    - microdata parser: https://www.npmjs.com/package/microdata-node or [others](https://www.npmjs.com/search?q=keywords%3Amicrodata&ranking=optimal)
- Additional info: Rumble also implements `VideoObject` with the [following properties](https://validator.schema.org/#url=https%3A%2F%2Frumble.com%2Fvx2dga-55538074.html):
    - `url`, `name`, `thumbnailUrl`
    - `duration`
    - `uploadDate`
    - `interactionStatistics.userInteractionCount`
    - `interactionStatistics.interactionType`
- Additional info: tiktok?

#### Crowdsourced metadata
Maybe allow users to manually input things on `hyperlinks` doc?

### Visualizing audio

- Waveform in SVG in browser
  - https://www.npmjs.com/package/audio-waveform-svg-path
  - give a URL and it will download & draw


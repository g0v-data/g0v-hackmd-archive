---
tags: cofacts
---

# API & Database enhancements

## API

We collect enhancements to API server here.

### Better multimedia support
- Video & audio thumbnail generation https://github.com/cofacts/rumors-api/issues/326
- Video metadata https://g0v.hackmd.io/aJqHn8f5QGuBDLSMH_EinA#How-to-extract
- Reduce STT hallucination https://github.com/cofacts/rumors-api/issues/322
  - 遇到圖片、影片：請 gemini 多模態 model 描述圖片影片、產生關鍵字，有助於關鍵字搜尋 / 搜尋類似影片


### Adopting Typescript
> [Typescript adoption on API](https://g0v.hackmd.io/It97AgA4RU6EwlWc7Q2yLw#rumors-api)

- Use current schema DSL & type the resolvers?

### API access & client management
> [Cloudflare Zero Trust Service Tokens](https://g0v.hackmd.io/51wwLHgvSUqtBDaP-yAVnA#Alternative-Implement-using-Cloudflare-Zero-Trust) 

- Add service token first to LINE bot
- Add service token to rumors-site & community builder after their rewrite
- Make announcement that we are going to enforce service token & remove `api.cofacts.g0v.tw`
- Apply access policy that blocks requests without service tokens


### URL resolution

- Currently url-resolver mostly works on `unfurl`, puppeteer seldom runs
    - Stored HTML and  `gRPC` is redundant
    - Does not handle PDF files
- Should extract metadata from microdata https://g0v.hackmd.io/aJqHn8f5QGuBDLSMH_EinA#schemaorg-microdata
- Replace url-resolver with ArchiveBox? https://github.com/cofacts/rumors-api/issues/136#issuecomment-1813762578
    - Stores multiple format
    - Including screenshots, solves https://github.com/cofacts/url-resolver/issues/71#issue-1641410356


## DB

### Requirements

The current Elasticsearch v6 does not fulfill the future need of vector search.

We need a solution that does not perform worse than the current ElasticSearch on rumor text retrieval.

### Solutions and alternatives

#### Elasticsearch v9

> Previous research: https://g0v.hackmd.io/aJqHn8f5QGuBDLSMH_EinA#Systems-supporting-vector-search

- [Semantic search with Inference API](https://www.elastic.co/guide/en/elasticsearch/reference/8.12/semantic-search-inference.html) (with built-in `query_vector_builder`; can use raw query vector instead)
- [Dense vector](https://www.elastic.co/guide/en/elasticsearch/reference/8.12/dense-vector.html) and [kNN search](https://www.elastic.co/guide/en/elasticsearch/reference/8.12/search-search.html#search-api-knn)
- Can `highlight` anyways
- Use [reindex from remote cluster](https://www.elastic.co/guide/en/elasticsearch/reference/8.19/reindex-upgrade-remote.html)

#### PostgreSQL

- Built-in full text search does not support
- `pg_vector` is recommended in many places (g0v slack, in Google's workshops, etc)
- Vercel, Google has support
- Can use [Prisma](https://www.prisma.io/) as ORM, which handles typing fields and DB schema.

If we only use semantic search using embeddings:
- We can chunk long articles and index multiple embedding vectors
    - May need to design a score function that adds up the matched score of each embedding vector in the document.
- No highlighting; can use  https://github.com/kpdecker/jsdiff to calculate highlight between search hits and the query


##### Supporting full-text search

- PGroonga: https://blog.gslin.org/archives/2023/04/21/11151/%E6%B8%AC%E4%BA%86-pgroonga%EF%BC%8Cpostgresql-%E4%B8%8A%E7%9A%84-fulltext-search-engine/
    - Support CJK
    - But probably not BM25/TF-IDF based
- [ParadeDB with pg_bm25](https://news.ycombinator.com/item?id=37809126)
    - Supports TF-IDF
    - Supports highlighting
    
Both solution has no GCP support.

#### MongoDB Atlas

- Has `$vectorSearch` and `$search` aggregation operator.
- `$search` runs Lucene, thus supports Elasticsearch-like queries such as `more_like_this`.
- MongoDB Atlas only feature; not available on the community version and self-hosted MongoDB.

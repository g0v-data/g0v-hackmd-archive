---
tags: cofacts
---

# API & Database enhancements

## DB

### Requirements

The current Elasticsearch v6 does not fulfill the future need of vector search.

We need a solution that does not perform worse than the current ElasticSearch on rumor text retrieval.

### Solutions and alternatives

#### Elasticsearch v8

- [Semantic search with Inference API](https://www.elastic.co/guide/en/elasticsearch/reference/8.12/semantic-search-inference.html) (with built-in `query_vector_builder`; can use raw query vector instead)
- [Dense vector](https://www.elastic.co/guide/en/elasticsearch/reference/8.12/dense-vector.html) and [kNN search](https://www.elastic.co/guide/en/elasticsearch/reference/8.12/search-search.html#search-api-knn)
- Can `highlight` anyways

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
- MongoDB Atlas only featuyre; not available on the community version and self-hosted MongoDB.

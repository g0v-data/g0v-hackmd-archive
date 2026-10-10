---
tags: AI, 零時小學校, edu
---

# g0v源力大使 _ 課程引導者


## 緣起


> [挖坑] 65 堂開放式課程
> https://g0v.hackmd.io/@jothon/Sch001courses/
> 有沒有可能有一位 源力大使 (AI)，可以QA詢問 課程選讀指南、大哉問
> 幫助選課者，從對話中推薦相關課程
> [name=chewei 哲瑋]


### 可能的實作方向

> 可以先請AI做摘要，把資料規格化，然後以此作為RAG的資料庫。[name=bestian]

> 昨天 NotebookLM 剛好開放公開分享功能，要不要試試看？[name=mrorz]


## A方案：用Google NotebookLM 的公開分享功能

優點：不必自架後端與前端，可以把重心聚焦在內容上

說明文件：
https://blog.google/technology/google-labs/notebooklm-public-notebooks/


Beta版：

1. [g0v源力大使 _ 課程引導者_part1_新手必看](https://notebooklm.google.com/notebook/2d2153ef-e8d0-477f-b986-2acf134e774f?_gl=1*cfodt9*_ga*MTg0MjgzMDg1NS4xNzMyMjIwNjg5*_ga_W0LDH41ZCB*czE3NDkwMTkzODEkbzkkZzEkdDE3NDkwMTkzODEkajYwJGwwJGgw)

> 因為NotebookLM有50個來源的上限，加上每個part的主題不同，先做了一個"g0v源力大使 _ 課程引導者_part1_新手必看"，可以試用看看~ [name=bestian]


#### 志願者：



---


## B方案：自架實作工程與專案(草案待共筆修訂)

優點：可以自訂介面與微調AI的反應
缺點：要自架後端與前端，維護不易

### 後端：couldFlare worker + worker AI + D1 database

#### 志願者(請留Github ID)：





### 前端：

#### 志願者(請留Github ID)：

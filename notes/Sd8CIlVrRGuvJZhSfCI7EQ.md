---
title: "graphbase 設計概念"
tags: outdated,hackpad
---

# graphbase 設計概念

> [點此觀看原始內容](https://g0v.hackpad.tw/vWmMFlS7TVK)


### ==本內容已被標註為過時或未維護。如果三十日內沒有更新，將會被移除。原有內容仍可在== ==[https://github.com/g0v-data/hackpad-backup-g0v](https://github.com/g0v-data/hackpad-backup-g0v)== ==找到。==


### 基本概念

類似firebase服務
能夠簡單儲存graph data
後端本來想用neo4j
clkao有提議可以用pgrest

可能要事先declare reference或relation也就是需要schema
但是提供最簡單的node和edge形式應該可以不需要schema
未來當然也是需要提供幾種不同的network
1.  不同type的node
2.  不同attribute的edge
3.  hybrid 1 & 2

### Use Case



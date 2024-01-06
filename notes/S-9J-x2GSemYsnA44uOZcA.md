---
title: "csv2json.sh"
tags: hackpad
---

# csv2json.sh

> [點此觀看原始內容](https://g0v.hackpad.tw/AgTQYZbNdP0)

curl -d "csv=\`awk '{if (NR!=1) {print}}' data.csv\`" [http://keyangxiang.com/projects/csv2json/api](http://keyangxiang.com/projects/csv2json/api)


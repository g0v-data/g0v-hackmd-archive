---
title: "g0v issue tracker"
tags: hackpad
---

# g0v issue tracker

> [點此觀看原始內容](https://g0v.hackpad.tw/iZZmyUdY57c)



## 專案簡介


### 緣由

[第一次基礎松](https://g0v.hackpad.tw/%25E7%25AC%25AC%25E5%25A3%25B9%25E6%25AC%25A1%25E5%259F%25BA%25E7%25A4%258E%25E6%259D%25BE#-2016612)
[projecthub redux](https://g0v.hackpad.tw/9U6DLtdZc48)

### 要解決的問題

增進人坑介面，讓人輕易找到自己能貢獻的 issue

### 預定使用者

設計師，工程師，任何想幫忙的人

### 預定功能

可以根據 language or label 搜尋 github issues

### 現有類似專案

[https://github.com/youchenlee/g0v-issue-tracker](https://github.com/youchenlee/g0v-issue-tracker)
[g0v issue label ](https://g0v.hackpad.com/L23ntanWnv7)

### 授權方式

MIT

### 使用資料

github api

### 專案目前狀態

把 json files 轉換成 postgresql database


### 實作細節（非技術背景可跳填）

目前使用 python, 會根據給定的 repo url list, call github api
1.  Download repos + issues 的 json files
2.  將 json files 轉成 db tables (postgres)
3.  使用 PostgREST 作為 api server
4.  前端 js


### 協作工具

github repo：[https://github.com/g0v/issues2db](https://github.com/g0v/issues2db)
hackfoldr 工作資料夾網址：
google drive 共用資料夾網址：

### 進度與 to-do

ui / visual design


### 成果展示






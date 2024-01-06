---
title: 班表小幫手系統簡介
tags: 班表小幫手, g0v, 公民科技獎助金
---

# 班表小幫手系統簡介

班表小幫手分成兩部分：檢測系統跟前端介面

## 檢測系統

repo: https://github.com/g0v/tw-shift-schedule

* `create.js`：產生班表
* `lexer.js`：將工時切段成休息日與上班日
* `schedule`：班表的封裝
* `validate.js`：按照勞基法驗證班表
* `overwork.js`：檢查班表是否符合過勞條件

## 前端介面

repo: https://github.com/g0v/tw-shift-schedule-ui
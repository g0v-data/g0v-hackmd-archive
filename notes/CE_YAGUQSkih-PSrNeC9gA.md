---
title: "動民主 2.0 responsive plan（過期文件不用看 XD）"
tags: hackpad
---

# 動民主 2.0 responsive plan（過期文件不用看 XD）

> [點此觀看原始內容](https://g0v.hackpad.tw/qjpEp6sdmih)

> 純幻想，實做時請依臨床狀況調整 XD
> [name=ET B]



### 尺寸變化


plans for vertical rhythm
> 之前在綠盟呼叫立委跟動民主 1.0 用過的，應該是可以實做，至於 horizontal grid 就沒概念了... 因為我沒寫過水平多欄的網頁 XDDD
> [name=ET B]

- html body font size 預設 16px，使用 rem 當度量單位
- nav bar、menu bar... 等橫向長條區塊的垂直高度：3rem（符合 android ics design guideline 的 48 px）
- 橫向長條區塊包含多行時，行高：2 rem，區塊上下邊緣與文字的距離：1 rem
- level 1 大 icon：感應區 2 rem x 2 rem，視覺大小高 1.5 rem（符合 android ics design guideline 的 24 px 和 32 px）

~mobile (portrait) max-width: 480px~
mobile (landscape) max-width: 640px
- 一般字級 1 rem（16px）

~tablet (portrait) max-width: 768px~
tablet (landscape) max-width: 1024px
- 一般字級 1.125 rem（18px）（老花 friendly）

desktop medium max-width: 1440px
- html body font size：18px 之類的，所有元素整體放大（老花 friendly）

desktop large min-width: 1440px
- html body font size：20px 之類的，所有元素整體放大（老花 friendly）


### 形狀變化


level 1 nav bar 由寬變窄時的行為
- 第一次卡到時：水平選單變成垂直 spinner，網站名稱剩下 logo（類似標準 android ics main menu）
- 第二次卡到時：搜尋框剩下 icon，要按一下 icon 才出現搜尋框
- 第三次卡到時：使用者名稱隱藏，剩下頭像

「問答」level 2 nav bar 由寬變窄時的行為
- 第一次卡到時：水平選單變成垂直 spinner，網站名稱剩下 logo（類似標準 android ics main menu）
- 第二次卡到時：左右邊界和頁緣的距離變成 0（原本大概有 2 rem 左右）
- 理論上應該不會再卡到第三次才對... XD




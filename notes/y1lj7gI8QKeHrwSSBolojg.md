---
title: "勞基法討論"
tags: hackpad
---

# 勞基法討論

> [點此觀看原始內容](https://g0v.hackpad.tw/i0SaVNv0Z5k)

2016/08/06 g0v hackath20n

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fe34007af2ed22a1da1b8530e7a4e0d0)
[http://i.imgur.com/2yzv4io.jpg](http://i.imgur.com/2yzv4io.jpg)

- [時代力量勞基法修法提案：院總第 1121 號 委員提案第 19428 號](http://lci.ly.gov.tw/LyLCEW/agenda1/02/pdf/09/01/21/LCEWA01_090121_00019.pdf)
- [2015工時制度及工作彈性化措施手冊](http://www.mol.gov.tw/media/2688168/2015%E5%B7%A5%E6%99%82%E5%88%B6%E5%BA%A6%E5%8F%8A%E5%B7%A5%E4%BD%9C%E5%BD%88%E6%80%A7%E5%8C%96%E6%8E%AA%E6%96%BD%E6%89%8B%E5%86%8A.pdf)
- [2016 法規實務彙編](http://bola.gov.taipei/public/Data/6159545171.pdf)
- [高鐵工會抗爭談到的工時水庫問題](http://www.eventsinfocus.org/news/368)



## 變形工時

### 輸入

- 類型：雙週，四周，八週
- 每天工時：

### 輸出：

- 最低薪水
- 是否違法

### 會造成工時違法的條件

1.  每天最多工作12小時
2.  每七天最少要休一天
3.  每個月加班不可超過46小時（一般以月份計，跨月即重新計算加班時數）

## 測試案例

```
8  8 8 8 8 0 0
12 8 8 8 0 0 0

```
1.  每天有沒有超過 12 小時
2.  非 0 不能連續超過 12 天
3.  兩週內工時有沒有超過 80+ 46
4.  四週內工時不能超過 160 + 46 （如果加在行事曆才可以做這功能）
> 不過這條有爭議，因為四週內不見得是一個月，有可能是跨越兩個月
> [name=Yuren J]


```
8  8 8 8 8 0 0
10 8 8 8 0 0 0
85+10+8+8+8 = 74




```
## 實作細節

- 應該把在 Google Calendar 輸入每天的工時，然後在網站上面檢查數值


## 結論

- 收集班表與薪資條（去除個資）
- 使用 Google Calendar 或用一個月的三十格的欄位輸入一整個月的班表
- 第一版實作的時候，應該分別填寫正常工時跟加班工時做出基礎版本。
- 利用之前整理出來的條件用於檢查是否違法

附件
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ec6d1bdf30ce79c33a4195b45dd90f69)

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fb8c53fc49160f013356272deae8e206)


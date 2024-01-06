---
tags: edu,幸福存摺
---

# 幸福存摺 線上聚

日期：2020911
時間：台灣時間早上12點
地點：線上

:::info
Join Zoom Meeting
https://us04web.zoom.us/j/75024830054?pwd=L0w0NXMzSEJoTFdHUW0wRFpKdVZqUT09
Meeting ID: 750 2483 0054
Passcode: 1XeEkQ
:::

## 參與者簽到

- John
- Justin
- Cindy
- 賈彬

## 討論事項

#### Cindy的設計稿
https://xd.adobe.com/view/6a7ceef2-d3dc-4833-b632-01d9125444c1-3f2f/


#### 點數的用詞的部分, Cindy希望用積分嗎? 因為之前都用點數, 可能相關頁面都要改

> John: 我覺得可以暫緩，我想這個最後可能會需要能讓機構自己客製化，可以自訂 分/點數/錢 或其他單位？

> Cindy: 我也覺得可以先保留之前的用詞~

#### 提取按鈕我先保留John原本的icon設計, 可以再改

> 讓他看起來像按鈕

#### 目前色調是綠底, Cindy希望用藍底嗎?

> Cindy: 色調可以一樣用綠底~~

```
const primary = '#68b386';
const accent = '#f8aa5d';
const raised = '#f05a5a';
const focused = '#439463';
const error = 'red';
```
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2811ab64c4d43ef27a9d57cd763cfd25.png)


#### 右上角我目前是放使用者的編輯, 然後調整點數的部分還沒放, 這部分可以再討論一下怎麼放

> Justin: 第四個問題我覺得可以用popup menu放在右上角, 等等討論大家如果ok我就改一改

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_54c90be7d68f1229d6d7e12c2489b9f2.png)

> Cindy: popup加上backdrop, 或改用dialog放在中間
> 新增任務的按鍵中間是正白，要加陰影
> 新增積分(ex:+2)改成藍色 

#### 新增了 兌換用的獎品 (上次@Justin 實地走訪發現的需求)， 也要討論一下放哪比較好

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_60b06c09c3aabaceace50fcab2429b15.jpeg)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5b01075eca2d52d491458a49f2b5c81f.jpg)


#### 未來想顯示任務列表的話會在哪裡呢？要用tabs切換 或是讓積分紀錄可以collapse？

> Justin: 我猜積分紀錄右邊那個按鈕是filter的功能, 也許就夠用了?

> Cindy:
> 1.任務列表如果是：申請中任務或進行中任務，再放一個tab，和積分紀錄切換會更好
> 2.積分旁的是filter沒錯XD但我原本預想它的功能會是篩選：已提取／已新增／本周內／本月內

> Justin: 篩選 '新增/提取/調整' 感覺會有用, 但是原本介面上 '經手人' 的左邊有日期, 所以篩選 '某個時間內' 可能比較用不到


#### 選單設計

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_18254c6be421ce03f3da5a016f83d0a2.jpg)

> Cindy: 覺得還是留著下方的快捷圖示好了，我原本想法是留下最主要功能＞指派任務，其他功能藏起來。
> 但忘了還有遺漏任務審核和任務設計的功能，總之原本功能都攤開來的作法比較好ＸＤ 職員一覽的部分，我覺得就可以收進設定裡面，因為他除了瀏覽外沒有其他功能(或有?)~

> John: 審核想拿掉～

下方選單
- 學生
- 任務
- 審核 (未來的任務審核)
- 設定 (把目前的"職員"放進去)

暫時不用側面選單
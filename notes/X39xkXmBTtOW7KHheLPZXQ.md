# 部落格文章

這邊說明一下部落格文章編輯使用方式

## 一、如何建立新文章
### 1-1 新增文章

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a601b60bdd57e1d5e6e6bfaa9521c416.png)

點選最上方的新增文章按鈕


### 1-2 新增文章標題
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d45bbde74c059a95b8ec6fd0df0fe522.png)

編輯文章標題欄位

### 1-3 新增文章專屬連結
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_20df8e1e5d269a5401b8632902ca95ce.png)

新增專屬連結，完成後按下確定按鈕

### 1-4 新增文章內容
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0434d5d292f6af1f2b4ff386fa497471.png)

1. 先點選右上角**文字**按鈕
2. 再將文章內容貼至此處

> 通常文章內容我會先在[**VScode**](https://code.visualstudio.com/)編輯好再貼上，因為比較好更改程式碼，主要看個人習慣
> 

如下：編輯html程式碼，完成後再貼上文字區的內容區塊
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1021786530ded75f11ab65b36c95bec8.png)

### 1-4 儲存及瀏覽
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_32e72c29f8ccfda7f7db2468dd9a4ae2.png)

1. 更新完成後可以點選右上角的的預覽變更，查看當前頁面更改狀態
2. 確認完成在更新至頁面

## 二、如何更換圖片
### 1-1 更換精選圖片
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5de058d564a83cc12ed1d652249adef5.png)


更換圖片完成後按下更新，返回到文章列表即可看到更換的小圖如下:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7ea0e62fd24b36c1360d3cb1eb78501e.png)

### 1-2 媒體庫上傳新圖片
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b221d59c319f725fd9ebdf362785a1f1.png)

點選左邊媒體->媒體庫


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_18c0e82837ccfe1dff002ab676995910.png)

進入媒體庫後點選左上角新增媒體庫，選取檔案

### 1-2 如何新增部落格首頁輪播圖

範例：
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9c811a76e95318b62510264bb8667560.png)


---
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5d5aa668106217a2be6fe0c6940ed184.png)

點選左邊頁面->部落格靜態首頁

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8328e1f2024bac5f278d0d6de999085b.png)

點選中間編輯的畫筆

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6df40f23094355b73c337ab1718a6200.png)

點擊左下角新增slide 按鈕

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fcd29c85eca5fe348e0344c7a3e5d635.png)

1. 更新上傳圖片
2. 新增Banner 連結
3. 按下save 保存


## 三、如何新增聯絡表單
### 1-1 新增聯絡表單
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_49e25c0aca2d991e5431323834ecaa0f.png)

1. 點選左邊的聯絡表單
2. 新增聯絡表單

---
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7e089a86e91d976499892b34d88145ff.png)

1. 設定表單標題
2. 更換表單系統參數
3. 保存

### 1-2 聯絡表單串接到部落格頁面
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_597821823a254c20310c255bb7b63a7d.png)

返回表單列表，複製剛新增表單的**短代碼**


---

```
[contact-form-7 id="2677" title="設計沒有絕對的答案 只有不斷地突破限制與框架" html_class="form-distribution"]
```

```
[contact-form-7 id="2677" title="設計沒有絕對的答案 只有不斷地突破限制與框架" html_class="form-distribution"]


  <!-- /wp:table -->[fusion_builder_row][fusion_builder_column type="1_1"
  layout="1_1" background_position="left top" background_color="" border_size=""
  border_color="" border_style="solid" border_position="all" spacing="yes"
  background_image="" background_repeat="no-repeat" padding_top=""
  padding_right="" padding_bottom="" padding_left="" margin_top="0px"
  margin_bottom="0px" class="" id="" animation_type="" animation_speed="0.3"
  animation_direction="left"
  hide_on_mobile="small-visibility,medium-visibility,large-visibility"
  center_content="no" last="no" min_height="" hover_type="none"
  link=""][fusion_text]
```

貼在文章內頁的最下方替換
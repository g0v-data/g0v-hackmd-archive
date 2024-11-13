#    Database, 2024 Autumn
**Final Project, Group 32**

##   Discussion board


##   Meeting record
[2024.10.23](https://raw.githubusercontent.com/kannny931110/Database_final_project_Group_32/main/%E6%9C%83%E8%AD%B0%E8%A8%98%E9%8C%84-24.10.23.pdf)


## 進度
2024/11/11 張祐廷
先用python連接到sql然後生出一個html

2024/11/13 張祐廷
因為政府提供的.xlsx資料會同時包含 全體國民 男性 女性 三個
只用一個表的的話會有看起來像重複三次
所以進sql前會先寫個小code把他們拆開
結構會是 db-> tables*3 -> 內容
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8c63819f88218159d170129b5dfc21c0.png =50%x)

簡單查詢
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c805e79cfa5ff9b9943cc182a7c0d0e7.png =30%x)

接下來要利用已有的表格生成standard ultimate life table協助後續的價格估算

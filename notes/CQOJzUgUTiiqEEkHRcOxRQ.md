#    Database, 2024 Autumn
**Final Project, Group 32**

##   Discussion board


##   Meeting record
[2024.10.23](https://raw.githubusercontent.com/kannny931110/Database_final_project_Group_32/main/%E6%9C%83%E8%AD%B0%E8%A8%98%E9%8C%84-24.10.23.pdf)


## 進度
11/11 張祐廷
先用python連接到sql然後生出一個html
非常的樸實 哈哈哈
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6012c600653b5cabd5480fee024d874e.png)


11/13 張祐廷
因為政府提供的.xlsx資料會同時包含 全體國民 男性 女性 三個
只用一個表的的話會有看起來像重複三次
所以進sql前會先寫個小code把他們拆開
結構會是 db-> tables*3 -> 內容
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8c63819f88218159d170129b5dfc21c0.png =50%x)

簡單查詢
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c805e79cfa5ff9b9943cc182a7c0d0e7.png =30%x)

接下來要利用已有的表格生成standard ultimate life table協助後續的價格估算
下圖是會用到的基本符號
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_378188414c7fec6d79bc16b49289ce56.jpg =40%x)

11/14 張祐廷
嘗試了Ax理論上應該隨x增加趨近1
但卻在A66之後開始變小
測試後發現是最後一年85+因為那個+導致讀取不到
增加條件後就可以了
然後這邊利率假設是2%(一般假設是5%但這不太符合台灣實際的利率)

<center class="half">
    <img src="https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_19bdf35b33578a582c89346c7069c1f5.png" width="150" />
    <img src="https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cb43c47fcdf02b468b1e9bef733a3ecb.png" width="148.5" />
</center>


接下來來弄10Ex
從20歲開始到75歲（不是85歲）因為10Ex最少需要能活10年
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2b7be81b123d804bf337a4d782d7d792.png =30%x)

有了這兩個基本的10年期的所有東西都能生成了
所以這邊來把最重要的ax生出
因為覺得丟一整張太佔版面剩下的基本上只會放部分截圖
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8373f27b6c28ea2ec6243fc471d7e86b.png =30%x)


有了這三個變數已經可以生成終生的生命險了
公式也很簡單 每年保費P = Ax/ax
到這裡我打算先把介面完善一下
如果能把這個結果展示出來後續也就是資料庫的擴增和公式的增加而已

雛形大概是這樣
輸入完年齡後按下計算保費就會跳出計算的結果
(網站我是用flask還不太熟 要我電腦當伺服器開著才能運作 我之後可能用桌機當伺服器吧（學校的電不用錢哈哈）)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_dacdb3d87205316cc449a9ef2202e7bf.png)

11/16 張祐廷
繼續弄常數
Ax:10最左邊那排實作下來如果利率跟標準表一樣5%的話數值會非常接近代表數值是沒問題的
<center class="half">
    <img src="https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7e804f4fd6dd54cf1b7ee3fe22fe5afa.png" width="200"/>
    <img src="https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_05f893394357b1fcff1ff95a612ee4d4.png" width="250"/>
</center>

<center class="half">
    <img src="https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a56676b5b139a1e56cfc724df42fe528.png" width="200">
    <img src="https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e9d769c9570fc0430966b0747d1b8ed6.png" width="250">
</center>

但台灣的利率通常是2%以下所以計算完會比原本超過30%
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5dc525b0a78f7b508b151974ec27fe1b.png =40%x)

該有的常數都新增了
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a941e11638914dafa21e164efafc0236.png)

這只是一個年度全體的生命表
之後會有其他年度以及男性女性的差別
近一步可能會有一些複合式的保險
或是考量成本的部分這些
不過等基礎功能完善再說
接下來先把利用現有的資料製作
5年10年20年期以及一輩子的生命險
付款可以一次付或分5年10年20年
（或許未來可以嵌入公式讓年限更彈性）

大概是這樣
<center>
    <img src="https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_14b76077312a89932572d542c7951120.png" width="230"/>
    <img src="https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6a074a07e988c060faf86e37dfefaf76.png" width="230"/>
</center>

12/19 更新
太久沒碰先熟悉一下內容
然後把功能整理一下
![](https://g0v.hackmd.io/_uploads/ryI_vr-B1e.png =30%x)

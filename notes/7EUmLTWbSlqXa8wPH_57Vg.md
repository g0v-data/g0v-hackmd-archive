## 3/25 MVC


Catch請假沒上


# 引用northwind資料庫建立引用流程


*_Layout

這放在頁首 調整Styles

    @await RenderSectionAsync("Styles", required: false)
    
這放在頁尾 調整Scripts

        @await RenderSectionAsync("Scripts", required: false)
        
        
#  partial 資料引用調整
    
 Model與partial相同名稱的檔案
 不能使用同一種class
 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_96a8aebeb5b48cf87c975e69f66207eb.png)

 不要在這邊作業
 
 
 
 要建立一個新的
 使用
   [ModelMetadataType(typeof(ProductMatadata))]
 後找他的燈泡新增一個新的ProductMatadata檔
 
 在ProductMatadata中進行操作
 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ec5435cd8a4f87b3153fe53386d4b08d.png)

 
 
 [Required(ErrorMessage ="商品名稱不能為空白")]

 [Display(Name ="商品名稱")] 

 [StringLength(40)] 
 長度限制
 
 public string ProductName { get; set; } = null!;


 [DisplayFormat(DataFormatString ="{0:C0}")] - 
 {0:C0} 0 = 取第一位數值 , C0 為取小數點後第0位 , 可以打C就給系統自己判斷 
 
 [Display(Name ="商品價格")]
 public decimal? UnitPrice { get; set; }
 
 
 

 
#  多語系網站
 影片講解
 自己摸講解檔


#  分頁篩選、排序、篩選


* 這是套件
為查詢資料庫的結果加入分頁
 -ASP.NET MVC = PagedList.Mvc
 -ASP.NET Core MVC = x.PagedList.Mvc.Core



async非同步
要限制xx在Task裡面


---

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_af6961ce9e32ad6cdfc2631103ff1fd2.png)

* 要讀取JSON檔
可先使用async Task<JsonResult>
return  Json 來轉換目標內容


在index裡面讀取json檔內容顯示
寫在script裡面


---

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b978d03a629d6311646380e0b72f1567.png)

* ajax
type使用GET讀取
URL 找到Products裡面的IndexJson
使用function處理資料取得
*function裡面用的是jQuery
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_10fe25a32f3d542e97a678a57ffead83.png)



* columns
讀取欄位,名稱要一樣
因為是讀取內容,所以是陣列




---


# 顯示圖形資料庫

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_edd279e64c85a9d74148b1a5e85a69be.png)
* 導入一個資料庫
先加入控制器

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_aa18b10c6cfbf3a185758dc1e5efada7.png)
有資料庫就第二個

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_083ad33594e9d11d57d6ff8dc955e22a.png)
選擇自己要建立的資料庫


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3d0c15121823a33ad4927bc4cf4b5f2e.png)

到CategoriesController
做一個
把Categories物件轉成圖片的
物件

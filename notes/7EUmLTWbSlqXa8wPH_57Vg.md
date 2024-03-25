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


為查詢資料庫的結果加入分頁
 ASP.NET MVC = PagedList.Mvc
 ASP.NET Core MVC = x.PagedList.Mvc.Core

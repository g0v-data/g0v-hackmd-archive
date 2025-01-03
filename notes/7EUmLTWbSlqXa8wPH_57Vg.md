# MVC


---

# 3/25

早上講Catch請假沒上




---

開始講Partial
----
 引用northwind資料庫建立引用流程
----


---

*_Layout

這放在頁首 調整Styles

    @await RenderSectionAsync("Styles", required: false)
    
這放在頁尾 調整Scripts

        @await RenderSectionAsync("Scripts", required: false)
        
        
 partial 資料引用調整
---- 
 Model與partial相同名稱的檔案
 不能使用同一種class
 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_96a8aebeb5b48cf87c975e69f66207eb.png)

 不要在這邊作業
 *productName要刪掉,這邊要空的
 
 
 要建立一個新的
 使用
   [ModelMetadataType(typeof(ProductMatadata))]
 後找他的燈泡新增一個新的ProductMatadata檔
 新的ProductMatadata檔會在同一個資料夾
 
 在ProductMatadata中進行操作
 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ec5435cd8a4f87b3153fe53386d4b08d.png)

 
 
 [Required(ErrorMessage ="商品名稱不能為空白")]

 [Display(Name ="商品名稱")] 

 [StringLength(40)] 
 長度限制
 
 public string ProductName { get; set; } = null!;


 [DisplayFormat(DataFormatString ="{0:C0}")] - 
 {0:C0} - 0 = 取第一位數值 , C0 為取小數點後第0位 , 可以打C就給系統自己判斷 
 
 *CN 為取小數點後第N位
 
 [Display(Name ="商品價格")]
 public decimal? UnitPrice { get; set; }
 
 
 

 
多語系網站
 ----
 影片講解
 自己摸講解檔


分頁篩選、排序、篩選
----

* 這是 x.PagedList 套件
為查詢資料庫的結果加入分頁
 -ASP.NET MVC = PagedList.Mvc
 -ASP.NET Core MVC = x.PagedList.Mvc.Core




---

async非同步 and Task
----

講解網址
1. https://www.develop-note.com/blog/2022/02/14/asp-net-core-asynchronous/
1. https://learn.microsoft.com/zh-tw/dotnet/csharp/asynchronous-programming/

這邊有一些async非同步的GPT回應
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b37ee3ac522d2b4d0d2e942caf33bac9.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9e8b6faee63821f0590a3f85d3760e0b.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_83e899b783ef8ee4cf2d756bb6101339.png)


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


 顯示圖形資料庫
----

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


# 3/26


---
做局部顯示
----

示範先從detail引用圖片
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_54dbfd3ca259d2799bde139dd7327fdd.png)

修改照片欄位
 改一個img格子
  <img src="@Url.Action("GetPicture","Categories",new {id=Model.CategoryId})" title="@Model.CategoryName" style="height:240px;width:320px"/>
  

  
  ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_60b033e78eb0772712c8b9729d360a76.png)


---

  
  
  ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e99a09c38e88a003f9e57d029246c37f.png)


要使用局部檢視
選這個
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1c624da017c8ca87b6ebafdb0a03fc54.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_97d52889fc99250c326044ab2acafc87.png)

要做局部顯示
這不是完整的檢視
名稱前面加"_"做標記
局部檢視要打勾

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_94143676e6977312e40e8d8c06262bbc.png)



* 自己加入模型
@model Category

* 貼上剛剛測試的img格子
    <img src="@Url.Action("GetPicture","Categories",new {id=Model.CategoryId})" title="@Model.CategoryName" style="height:240px;width:320px" />
    
    

* 再做一個沒有圖片的顯示
    先在wwwroot裡面做一個資料夾叫做images
    找一張 noimage 圖片顯示
    在這個檢視做引用
    <img src="@Url.Content("~/images/NoImage.jpg")" title="NoImage" style="height:240px;width:320px" />
    
* 路徑要注意修改
    ~/images/NoImage.jpg
    
    ~是根目錄
    再從根目錄(就是wwwroot)往下找

    大小顯示基本上要調整跟原本顯示一樣
---


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6c6541468ffd95aa518b361f85912178.png)    

    
再回detail做引用這個_ShowPicturePartial


---


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_aa0b7dafee83c2e5933962812b287881.png)
這樣是引用成功




---


修改Index的Picture欄位
----

修改前
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d96e1623194d5def9ca361b1051587fa.png)

修改後
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c0e5019a4c07fd938a63c1b1fcca686c.png)

* 要顯示多個圖片要跑foreach
所以要在<partial name="_ShowPicturePartial" />
多加一個 model="@item"
變這樣
 <partial name="_ShowPicturePartial" model="@item" />
 不然他不知道要foreach
 
 
 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2fa6e1ca0a9100fb3aa677cc235b3358.png)
* 有多張圖片顯示
測試NoImage有沒有執行

*圖片大小要注意

檔案上傳-圖片顯示
----

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e6234effeb7b13d7a1ab1fbefc276f0a.png)
要改這兩個


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_18187587420720d39cd9145e9b5ceec4.png)
要給人家上傳
*一定要有 enctype="multipart/form-data"  !!!


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0ee3825d01cfaf3a3f3b24ab09bb4e4f.png)
要有input給人放 
給人上傳要設定name屬性
不然上傳不會成功
東西找不到地方放


檔案上傳有兩種
一種轉byte陣列,儲存
一種在form裡面上傳,直接存放在wwwroot裡面的資料夾

要預防有人沒上傳圖片
沒上傳就保留原本的圖片



 先做更改
----

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6f170fc23a7b8be4c29b3c6aebd2106d.png)


判斷上傳有沒有上傳檔案
Request.Form.Files["Picture"] != null

有上傳就跑
*  using (BinaryReader br = new 
     BinaryReader(Request.Form.Files["Picture"].OpenReadStream())) //BinaryReader一次性
 {
     category.Picture = br.ReadBytes((int)Request.Form.Files["Picture"].Length);
 }
 
 解釋在這
 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_59ad7224b8942761c014d10a7cc57c0f.png)

 


* 兩個追蹤中的物件不能有相同的Frign Key
確認可以更改




現在要限制大小
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_14b3dced6de5c46c02ccdd231f67a259.png)

    [RequestFormLimits(MultipartBodyLengthLimit =2048000)]
    [RequestSizeLimit(2048000)]
限制大小為4MB
*單位要用位元組

 -ASP.NET MVC = .NET平台
 預設上傳檔案大小限制 4MB
 
 -ASP.NET Core MVC =  .NET Core平台 與 Kestral平台
 預設上傳檔案大小限制 約30MB
 
 

---

去做Creat
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_abf2f3a8c9f3ef94691fbf15f1015750.png)
enctype跟input加上


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9a35b563daf37fed7ea2e67049e13cad.png)
上面是edit的
下面是Creat的

也要修改
複製過去再刪減
變數c有關的值
因為沒有原本的圖片

3/26-早上11:35分左右有除錯講解



---

creat檔案上傳
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_930c7ebd9a864b6042ba40faf7ef2abf.png)

對檔案做判斷
檔案不對就不給按按鈕


再做即時顯示
on就是觸發事件

reader.onload = function (e)登記觸發事件
有讀取才會跑

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_12f9540486f504577d91a5f08b6d612e.png)
根據使用者\使用選擇不同讀取出來的值

*readAsArrayBuffer讀檔案取得byte陣列
*readAsDataURL讀檔案取得url


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4504185ec96e04e745ee4bec71621f50.png)



$("#imgPreview").attr("src", e.target.result);
更改id = imgPreview的地方
把src改成目標的url

$("#imgPreview").attr("title", inputFile.files[0].name);
更改id = imgPreview的地方
把title改成目標的name



改edit的圖片顯示
----

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_24e01e89fb9b1c2a6c2c5b9d8528ccf3.png)
先從creat貼過來

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fa09b6b417ca0f308d28685da9b74748.png)

                        $("#imgPreview").attr("src", e.target.result);
                        $("#imgPreview").attr("title", inputFile.files[0].name);
                        

改成

                        $("#Picture").prev().attr("src", e.target.result);
                        $("#Picture").prev().attr("title", inputFile.files[0].name);
                        
就差不多了



---

    <label asp-for="Picture" class="control-label"></label>
    =這兩個一樣,因為TagHelper=
    <label for="Picture" class="control-label"></label>


    <input type="file" asp-for="Picture"/>
    =這兩個一樣,因為TagHelper=
    <input type="file" id="Picture" name="Picture"/>
    
    

---


對照兩個地方
重構function


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4a49bc41b898622efe280e670fc40ed2.png)


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e2f3f55e1974890d4acc9f1db8348058.png)


調整與精簡一下
轉放到js檔裡面
再引用到 Creat 與 Edit 裡面
*基礎精簡程式





---

重構這段
          using (BinaryReader br = new
              BinaryReader(Request.Form.Files["Picture"].OpenReadStream())) //BinaryReader一次性
          {
              category.Picture = br.ReadBytes((int)Request.Form.Files["Picture"].Length);
          }


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_31c7b9b2818be8b748aae908f531e057.png)


重構出來
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ff145420b1ad25c1026d7f59cf035960.png)

設定名稱SetPicture
會新增一個方法
讓原本的地方引用

再到
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8a414b901e81829ebdcec697cde558c8.png)

替換成SetPicture




---


ASP .NET Core MVC身分認證
----

*  Entity Framework (ORM)
1. Database First
資料庫-->Scaffold-DbContxt-->模型

1. Model First 
Entity Framework Core不支援

1. Code First 
(版本管理)
類別-->Add Migration-->資料庫
-----( ↑ Update Database)---

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_074ee22f7ca22ea0a2c9b768b66d8b88.png)
這是身分認證用的連接




---

Microsoft支援的身分驗證
----------------
第一代)ASP .NET Membership(2002~2015)之間
第二代)ASP .NET Identity(2013~now)
第三代)ASP .NET Core Identity(.NET Core適用)




---

# 3/28
CodeFirst
-----
Core MVC實作
-----

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5b2aeda9cd132eecfd93a6640209924f.png)


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d705e5baa22b9290716df49b4f51483e.png)
在Program這邊改掉

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f803154819e0e0a30f2e57f6eb918d8b.png)
換成ApplicationUser


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_27d8604e08484af0297c99bb4ea77332.png)
_LoginPartial裡面找出IdentityUser要改ApplicationUser


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ab6da8fc96c67c020508fd6bc21232a3.png)
處理紅字部分


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ddf50f14dd4dcab9dd37cfc1f1a0bdf4.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f023a4b440f2af4296ecd2db6d25d831.png)
找燈泡處理辨識
生成@using CategoryProducts.Data


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bfa62696ee084acfe6289749f19e8a29.png)
再放到_ViewImports出處理所有辨識


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a407afb9053129314eeab5706865b777.png)
方案建置scaddold項目


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ed47bf0673479ab2ca26ba1863b9074a.png)
上面是VIEW
裡面是Controllers

InputModel

生成畫面處理是OnGetAsync
接submit的是OnPostAsync



在Register中加入國別碼設定
-----
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b49d8b45271abeaf1daf7f3ecbdeea14.png)

Register.cshtml.cs中
找到input加入

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_837e61e7a43e7067326eb4bdbbd40c46.png)
        
CountryCode 跟 加入設定


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7750b11a81e8f52c825cbf62c94f95e7.png)
在Register.cshtml中
加入input欄位

再到Program調整
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8ff79254c381d0ab8636cd0386442f2f.png)
做輸入項的相關設定




---

發送驗證信
-----

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2f245d03abba0b941b1d912562fd3597.png)

client.port = 587通常都是






---

登入更改帳號欄位
---



![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7fdd13e57e1bca3662aae479abdb2f42.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_aa76df0da7d2c37ad6e74e7af582c1e5.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_64d2932d5e0f6435bda52589fc19faf4.png)

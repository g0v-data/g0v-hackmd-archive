# MVC整理 --- 建立模型 QAQ


---


### 建立模型
 
基本設定有四項固定流程

##### 1.建立資料庫連線
* 用指令
* 用EF Core Tool套件
自己翻書,懶得打

---


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fe02f2209889440c35bcc864fc3d603f.png)

##### 2.定義連線

找到appsettings.json檔案修改
    
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8b72d4c1f019ca62749336d0093fc733.png)

紅色是要新增的連線字串
"Northwind": "Data Source=(localdb)\\ProjectModels;Initial Catalog=Northwind;TrustServerCertificate=True;Integrated Security=true"

前面"Northwind"這邊可以自己命名
後面"Data Source=(localdb)\\ProjectModels;Initial Catalog=Northwind;TrustServerCertificate=True;Integrated Security=true"

1. Data Source=(localdb)\\ProjectModels;
    設定伺服器路徑
    這邊路徑是(localdb)\\ProjectModels
    
2. Initial Catalog=Northwind;
    設定資料庫
    這邊資料庫是Northwind
3. TrustServerCertificate=True;
    信任憑證=true
    使用 Windows 身份驗證（Windows Authentication）進行身份驗證。
4. Integrated Security=true;
    應用程式信任 SQL Server 的 SSL/TLS 憑證

這邊有3.4.的資料庫解釋
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0f94cc6ffb34363d1319139148a92983.png)

    

##### 3.修改連線資訊

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8edeccc1d0fd2ccf8e6b5119a4ed58ba.png)
自己新增一個Partial資料夾

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_405025c827d3b74ca8f9afab08d57574.png)


在裡面加入一個新的空白類別
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3f86f5cd7c8c87430fdf27f83fe3a3be.png)
Model裡面會有自己原本的資料庫連線的檔案(紅色)
把他的名字複製過來給新建的空白類別(橘色)


***
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0f06a51ea6af871059303493ce42796d.png)
Model裡面原本的檔案裡面會有OnConfiguring這個東西
把它註解掉
不然會有錯誤

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0490cf9a4c8095f27bfe1bb93afa16d4.png)
Model裡面原本的檔案裡面複製這些
放到新的空白類別中
*小心括號要接上

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_30ef22553b68649c256a617c7b50478c.png)
做一個新的OnConfiguring

##### 4.註冊資料到DI容器
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_63cf3b1a08d5d87c2cf8543a44f43995.png)

找到Program文件新增一些東西
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_12565f1bca29a876d69e31c327d38d47.png)
為自己的資料庫新增這些
builder.Services.AddDbContext<NorthwindContext>(options =>
{
options.UseSqlServer(builder.Configuration.GetConnectionString("Northwind"));
});


GPT的備註
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d09772b0fbc4f22d93e39160a4871c2f.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9c716ee09a2129c1f1cb1a45fafe04a5.png)



---

### 建立控制器
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1d9617bae1ac09eb1923ef92fe2f31f7.png)

都好就針對自己要處理的資料建立控制器

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_75c89d43edc675ddd9d89b3a6083ef63.png)
基本上會三選一
1. 空白
1. 都做好
1. 讀取/寫入

懶就選 2 自己改

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7950afdbfd6369e0fe8607e3a6bcb2d2.png)

紅色是資料表
橘色是資料庫

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4042ca20dc312a60438c020538b6f213.png)
好了就會有屬於資料表的Controllers跟View

後面就自己在個別操作

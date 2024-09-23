# Dorm

## 建立資料庫
1. 從NuGet管理員中新增
* MySql.EntityFrameworkCore
* Microsoft.EntityFrameworkCore.Tools
2. 在套件管理主控台輸入
```
Scaffold-DbContext "Server=127.0.0.1;Database=Web;User ID=Web;Password=123456;" MySql.EntityFrameworkCore -OutputDir Models -NoOnConfiguring -UseDatabaseNames -NoPluralize -Force
```
3. 成功的話Model即會生成出所有資料表及一個context
4. 將appsettings.json加入
```
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*",
  "ConnectionStrings": {
    "testDatabase": "Server=127.0.0.1;Database=test;User ID=root;Password=root;TrustServerCertificate=true"
  }
}
```
5. 在Program.cs新增
```
builder.Services.AddDbContext<testContext>(options =>
options.UseMySQL(builder.Configuration.GetConnectionString("testDatabase")));
```
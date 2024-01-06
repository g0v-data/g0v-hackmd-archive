# Blazor Server Application with LDAP authentication on Linux

Get one project needs to access the LDAP server doing auth with Blazor Server App. I search the Blazor resources online but all of them are with System.DirectoryServices but it can't work in Linux (get PlatformNotSupportedException)

Found one solution that he Novell LDAP nuget package can run under Linux. So this repo is an example to do LDAP authentication in Blazor Server.

## Environment
- VS 2022
- Blazor Server App
- .net 6
- [Novell.Directory.Ldap.NETStandard](https://github.com/dsbenghe/Novell.Directory.Ldap.NETStandard)

## Code

1. AddControllers and AddAuthentication

Program.cs
```csharp
builder.Services.AddControllers();
builder.Services                    
    .AddAuthentication(CookieAuthenticationDefaults.AuthenticationScheme)
    .AddCookie(); 
```

```csharp
app.MapControllers();
```

2. Login Page (Login.razor)
3. Add CascadingAuthenticationState, AuthorizeRouteView in App.razor
```csharp
<CascadingAuthenticationState>
    <Router AppAssembly="@typeof(App).Assembly">
        <Found Context="routeData">
            <AuthorizeRouteView RouteData="@routeData" D
```
4. Modify the MainLayout.razor to show User authentication status and Logout link.
5. Modify index.razor for auth content
6. Add LDAP auth in LoginController.cs
Claim will be username as ClaimTypes.Name and Attribute"gidNumber" as ClaimTypes.Role
```csharp
var claims = new[]
{
    new Claim(ClaimTypes.Name, User.username),
    new Claim(ClaimTypes.Role, $"{resultEntity.GetAttribute("gidNumber").StringValue}")
};
```

## Online LDAP Test Server

Thanks forumsys for the [Online LDAP Test Server](https://www.forumsys.com/2022/05/10/online-ldap-test-server/)

LDAP Server Information (read-only access): 

Server: ldap.forumsys.com  
Port: 389

Bind DN: cn=read-only-admin,dc=example,dc=com
Bind Password: password

All user passwords are password.

You may also bind to individual Users (uid) or the two Groups (ou) that include:

ou=mathematicians,dc=example,dc=com

- riemann
- gauss
- euler
- euclid

ou=scientists,dc=example,dc=com

- einstein
- newton
- galieleo
- tesla

## Screenshot
### Login (Username="tesla", Password="password")



## Reference

- [Blazor Server LDAP Authentication](https://www.youtube.com/watch?v=sFNBOeYTAQ4&t=1069s)
- [在 Dotnet Core 中使用第三方套件處理 LDAP 驗證](https://blog.poychang.net/use-thired-party-package-to-implement-ldap-authenticate-in-dotnet-core/)


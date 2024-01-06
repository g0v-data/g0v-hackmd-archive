# 移除 IIS header 版本資訊
1. Server
    Web.config 中加上：
```
    <system.webServer>
        <security>
          <requestFiltering removeServerHeader="true" />
        </security>
    </system.webServer>
```
    
2. X-Powered-By
    Web.config 中加上：
```
    <system.webServer>
        <httpProtocol>
          <customHeaders>
            <remove name="X-Powered-By"/>
          </customHeaders>
        </httpProtocol>
    </system.webServer>
```

3. X-Aspnet-Version
    Web.config 中加上：
    
    `<httpRuntime targetFramework="4.6.1" enableVersionHeader="false" />`
    

4. X-AspNetMvc-Version
    Global.aspx.cs 中加上：
    ```
    protected void Application_Start(){
        MvcHandler.DisableMvcResponseHeader = true;
    }
    ```  

* 若加在 Global.aspx.cs 中(如下)，代表網頁執行時會移除標頭，**但靜態網頁及錯誤頁則不會**
```
    protected void Application_PreSendRequestHeaders(object sender, EventArgs e)
    {
        Response.Headers.Remove("Server");
        Response.Headers.Remove("X-AspNetMvc-Version");
    }
```


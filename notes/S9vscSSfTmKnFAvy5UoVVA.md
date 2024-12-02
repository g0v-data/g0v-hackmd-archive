### **MVC模型綁定的特性**

<aside>
💡

**在ASP.NET MVC** ，`Content-Type` 是後端用來判斷請求數據格式的**核心依據**。

</aside>

**Query String** 讀取數據是內建的模型綁定行為，並且**與 `Content-Type` 無關**。`Content-Type` 的作用僅影響 **Body** 的數據解析方式，而不影響 **Query String**。
> 

故若要多來源傳送請求並成功綁定，可透過**Query String及`Content-Type` 來完成多來源綁定**



### **核心結論**

- Query String **獨立解析**，與 Body 或 `Content-Type` 無關。
- Body 必須依賴正確的 `Content-Type` 進行解析。
- 簡單型別來自 Query String，複雜類型來自 Body 或 Form Data。

## 如何成功資料綁定

傳送資料須區分為Json跟非Json

先講非Json，資料若為簡單型別，例如`int`、`bool`，
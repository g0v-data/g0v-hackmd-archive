### 步驟 1: 資料庫準備

資料庫中的 `Images` 表格包含圖片的相對路徑。例如：

| Id | ImagePath         |
|----|-------------------|
| 1  | images/photo1.jpg |
| 2  | images/photo2.jpg |

### 步驟 2: VB.NET 程式碼

以下是 VB.NET 程式碼，用於從資料庫讀取相對路徑並解析為完整路徑：

```vb.net
Imports System.Data.SqlClient
Imports System.IO
Imports System.Drawing

Module Module1
    Sub Main()
        ' SQL 連接字串
        Dim connectionString As String = "您的連接字串"
        ' SQL 查詢語句
        Dim query As String = "SELECT ImagePath FROM Images WHERE Id = 1" ' 假設您要加載 Id 為 1 的圖片

        Dim relativeImagePath As String = ""

        Using conn As New SqlConnection(connectionString)
            Dim cmd As New SqlCommand(query, conn)

            conn.Open()

            Using reader As SqlDataReader = cmd.ExecuteReader()
                If reader.Read() Then
                    relativeImagePath = reader("ImagePath").ToString()
                End If
            End Using

            conn.Close()
        End Using

        ' 解析相對路徑為完整路徑
        Dim basePath As String = AppDomain.CurrentDomain.BaseDirectory ' 或者您的特定根目錄
        Dim fullPath As String = Path.Combine(basePath, relativeImagePath)

        If File.Exists(fullPath) Then
            ' 從路徑加載圖片
            Dim image As Image = Image.FromFile(fullPath)

            ' 在此處處理圖片（例如，顯示在界面上或進行其他處理）
            ' ...

            Console.WriteLine("圖片已成功加載。")
        Else
            Console.WriteLine("圖片路徑無效或檔案不存在。")
        End If
    End Sub
End Module
```

在這個範例中，`AppDomain.CurrentDomain.BaseDirectory` 用於獲取應用程式的基礎路徑。然後，我們使用 `Path.Combine` 方法來將基礎路徑和從資料庫獲取的相對路徑結合起來，形成圖片的完整路徑。

這種方法的好處是它使您的應用程式更具可移植性和靈活性，因為您只需要更改基礎路徑就可以遷移應用程式和其資源。
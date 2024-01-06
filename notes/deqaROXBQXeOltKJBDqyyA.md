### 1.請問什麼是乾淨的程式碼（Clean Code）？
簡短 可讀性 不重複  賦義 標準化 相依性

簡短:
動詞名詞配合使用簡短的方式命名，最好能做到不使用註解也能做到高可讀性

不重複:
可以提高維護效率，但不能為了降低重複率而過度合併程式碼，不同用途就必須分開，遵守單一職責原則

高易讀性:
團隊協作間可降低交流上的誤會與時間，維護上也可提升效率

標準化:
統一寫法，例:function/method有固定的編排方式與間距標準，提高可讀性

低相依性:
避免修A壞B 修B又壞C
 
賦義:
變數名稱賦予段落意義

<br><br><br><br>

### 2.在 Safari 10 不再支援 user-scalable 後，該如何禁止使用者縮放？
使用者有兩種方式互動畫面縮放
Pinch(兩指) 與 Double-tap (雙擊)
本來可以使用 user-scalable=no 關閉這兩個功能 但 Safari 10 不再支援 user-scalable 功能預設為開啟

使用 JavaScript 來監聽使用者行為
```
//Pinch
window.onload = () => {
  document.addEventListener('touchstart', (event) => {
    if (event.touches.length > 1) {
       event.preventDefault();
    }
  }, { passive: false }); // Pinch的 touch start 在 true 時會導致preventDefault失效


//Double-tap  
        var lastTouchEnd=0;  
        document.addEventListener('touchend',function (event) {  
            var now=(new Date()).getTime();  
            if(now-lastTouchEnd<=300){   //預設300ms來判斷是否為單次點擊行為
                event.preventDefault();  
            }  
            lastTouchEnd=now;  //當前為最後一次觸控
        },false)  
    }
```

<br><br><br><br>

### 3.計算 g(N) 從 1 到 N 所有的數字，任一位數包含有 7 的個數。
##### TestCase

| 編號 | 背景 | 步驟 | 資料 | 預期結果 | 實測結果 | 狀態 |
|:---:|:---:|:---:|:---:|:---:|:-------:|:-----:|
| TC1 | 輸入數字 | 帶入數字參數 | 20 | 2 | 2 | 通過|
| TC2 | 輸入非數字 | 帶入非數字參數 | "20" | 請輸入數字 | 請輸入數字 | 通過 |


##### Program by Ruby
```
def g(n)
  sum = 0
  return puts "請輸入數字" unless n.is_a?(Numeric)
  for i in 0..n
    if i.to_s.count("7") != 0
      sum += 1
    end
  end
  puts sum
end


g(1000) #答案 271
```

<br><br><br><br>

### 4.請寫一個 SQL query 去尋找每個部門最高薪的前三位員工。

Employee
| Id | Name  | Salary | DepartmentId |
|:---:|:---:|:---:|:---:|
| 1  | Joe   | 85000  | 1            |
| 2  | Min   | 80000  | 2            |
| 3  | David | 60000  | 2            |
| 4  | Max   | 90000  | 1            |
| 5  | Harry | 69000  | 1            |
| 6  | Xavier| 85000  | 1            |
| 7  | Andrew| 70000  | 1            |

<br>

Department 
| Id | Name     |
|:---:|:---:|
| 1  | Marketing|
| 2  | Research |

<br>

```
SELECT * FROM "Employee" WHERE "DepartmentId" = 1 ORDER BY "Salary" DESC LIMIT 3 OR WHERE "DepartmentId" = 2 ORDER BY "Salary" DESC LIMIT 3
```

<br><br><br><br>

### 5.What are the features/advantages of GraphQL?

1.一次即可拿回全部資料，可減少request次數
2.強型別 (Strongly Typed)
3.可選擇要撈取的欄位，減少資源浪費
4.API只需要一套，可以減少現在多API串接的工作量
5.

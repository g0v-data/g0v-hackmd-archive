其他爬蟲資訊還在嘗試，如之前爬不出來的富邦、台新
(1)嘗試轉換成JSON檔
```python=
from bs4 import BeautifulSoup
import urllib.request as request
import json

src="https://data.taipei/opendata/datalist/apiAccess?scope=resourceAquire&rid=296acfa2-5d93-4706-ad58-e83cc951863c"
with request.urlopen(src) as response:
    data=json.load(response)
    print(data)
  ```
  
(2) 嘗試將轉換出來的JSON轉換成.txt檔案
```python=
import urllib.request as request
import json

src="https://data.taipei/opendata/datalist/apiAccess?scope=resourceAquire&rid=296acfa2-5d93-4706-ad58-e83cc951863c"
with request.urlopen(src) as response:
    data=json.load(response)
#印出公司名稱
clist=data["result"]["results"]
#with open("data.txt", "w", "encoding="utf-8") as file
#若要建立成data.txt檔案
for company in clist:
    print(company["公司名稱"])
    
#file.write(company["公司名稱"]+"\n")
```

(3)嘗試央爬蟲內容回傳LINEBOT
```python=
if event.message.text == "最新電影":
        a=movie()
        line_bot_api.reply_message(event.reply_token,TextSendMessage(text=a))

```
        
(4)嘗試央爬蟲內容回傳LINEBOT(圖文兼備的資訊)
```python=
 news_group=[]    #創一個List
    #將剛剛的三個List加進來
    news_group.append(news_title)
    news_group.append(news_link)
    news_group.append(news_photo)
    #要做為key值的List
    x=['title','link','link2']
    #把兩個做成dictionary
    dictionary = dict(zip(x,news_group))
```
之前台新富邦爬不出來，於是重新將所有方法重新看過筆記紀錄下來，目前台新、富邦還在嘗試，順帶學習了JSON檔的轉換提取和LINEBOT的回傳方式
Find方法
```pyhhon=
import requests
from bs4 import BeautifulSoup
headers = {‘User-Agent’: “Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.1 (KHTML, like Gecko) Chrome/22.0.1207.1 Safari/537.1”}
html = requests.get(url, headers=headers)
soup = BeautifulSoup(html.text, ‘lxml’)  #以上是網路獲取html
soup=BeautifulSoup(open(‘index.html’)) # 讀取本地的html，加個open函式即可
print（soup.prettify()）  # 用標準html 顯示方法列印html
#soup.find_all()方法介紹 ，soup.find()與之基本類似，只是返回的是第一個值
find_all( name , attrs , recursive , text , **kwargs )

soup.find_all(‘b’)  #查詢所有的b標籤，返回列表

soup.find_all(re.compile(“^b”)) # 正規表示式

soup.find_all([“a”, “b”])  #傳入列表引數，找到所有的a標籤和b標籤

soup.find_all(id=’link2′)  #傳入id是link2的引數,Beautiful Soup會搜尋每個tag的”id”屬性

soup.find_all(href=re.compile(“elsie”)) #傳入正規表示式，查詢所有的href標籤內容中含有 elsie 的內容

soup.find_all(href=re.compile(“elsie”), id=’link1’) # 多層過濾，除了href進行限定之外，對id標籤的內容也做了限定

soup.find_all(“div”, class_=”sister”) #最常用的查詢技巧，這裡之所以加‘_=’是因為‘class’不僅是html中的tag，也是python語法的關鍵詞，其他的不用加下劃線

data_soup.find_all(attrs={“data-foo”: “value”}) # 針對html5裡面的data- 進行的專項查詢

soup.find_all(text=”Elsie”) # 對text內容進行查詢

soup.find_all(text=[“Tillie”, “Elsie”, “Lacie”]) # 列表形式進行查詢，與上面name類似

soup.find_all(text=re.compile(“Dormouse”)) # 正規表示式形式，與上面類似

soup.find_all(“a”, limit=2) #找到前兩個a標籤，limit用來限定次數
```
Select方法

# 我們在寫 CSS 時，標籤名不加任何修飾，類名前加點，id名前加 #，在這裡我們也可以利用類似的方法來篩選元素，用到的方法是soup.select()，返回型別是list
（1）通過標籤名查詢
soup.select(‘title’)
（2）通過類名查詢
soup.select(‘.sister’)
（3）通過 id 名查詢
soup.select(‘#link1’)
（4）組合查詢
組合查詢即和寫 class 檔案時，標籤名與類名、id名進行的組合原理是一樣的，例如查詢 p 標籤中，id 等於 link1的內容，二者需要用空格分開
soup.select(‘p #link1’)
（5）屬性查詢
查詢時還可以加入屬性元素，屬性需要用中括號括起來，注意屬性和標籤屬於同一節點，所以中間不能加空格，否則會無法匹配到。
soup.select(‘a[class=”sister”]’)
soup.select(‘a[href=”http://example.com/elsie”]’)
get_text()方法可以用來獲取內容，請看下面程式碼：
soup = BeautifulSoup(html.text, ‘lxml’)
print (type(soup.select(‘title’)))
print (soup.select(‘title’)[0].get_text())  # 獲取第一個title標籤的對應內容
for title in soup.select(‘title’):
           print (title.get_text()) # 獲取列表中的title對應內容

```
 
LINE BOT:
(文字關鍵字回傳網址和標題)
 
(可以回傳圖文資訊)
 
 
(JSON轉檔圖片)
 
(嘗試性轉換JSON檔案)
 

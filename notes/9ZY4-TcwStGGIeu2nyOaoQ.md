## 問題分類
#### 1.一般做法:
>讀取網址後，利用class.id.xpath等方法鎖定元素，提取內容
>ex.國泰
``` python=
#鎖定目標網站
driver.get('https://www.cathaybk.com.tw/cathaybk/personal/deposit/deposit/service/rate/#first-tab-01')
#鎖定目標(<table class='exchange-table'>)
element=driver.find_element_by_class_name('exchange-table')
#鎖定表格中的列
tr_content=element.find_elements_by_tag_name('tr')
list=[]
for tr in tr_content:
    list.append(tr.text)
print(list)
```
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7792c636e1d8e9b21f28bbb8aa978cff)


---

#### 2.畫面轉換網址不變
(1) 找到真正的連結
> 藉由觀察網頁原始碼找到連結
> ex.富邦
```python=
driver.get("https://ebank.taipeifubon.com.tw/B2C/cfhqu/cfhqu012/CFHQU012_Home.faces?menuId=CFH0301&")
element3=driver.find_elements_by_class_name('tb1')
list3=[]
for tr in element3:
    list3.append(tr.text)
print(list3)
```
| ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3e44caef02026bd0b9146b48f9ecc361)  | ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f93e7bc34c7744667fa6fa55e64e31f7) | 
| -------- | -------- | -------- |
(2)利用selenium的功能進行換頁
>先鎖定超連結的元素，再利用selenium的.click()進行換頁
>ex.花旗
```python=
driver.get('https://www.citibank.com.tw/TWGCB/apba/inrts/InitializeSubApp.do?currencyType=L')
target=driver.find_element_by_css_selector('form')
#鎖定超連結的元素
page=target.find_element_by_tag_name('a')
#模擬瀏覽器點擊
page.click()
#進入下一頁後再開始抓取爬取的資料
table=driver.find_element_by_xpath('//*[@id="f1"]/table[2]')
element5=table.find_elements_by_class_name('sortbg')
list5=[]
for tr in element5:
    list5.append(tr.text)
print(list5)
```
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_409d803385f24bd6a8a443b09eaee063)
#### 3.進入網頁時必須達成某種條件(按鈕.登入等)
>利用selenium定位元素執行動作
>ex.郵局:>進入網頁時會跳出確認畫面，沒按按鈕無法定位其他元素

>
| ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_3069911100213f33338c212b9bd21d7d) |  
| -------- | -------- | -------- |
| <center>進入畫面時須按按鈕 </center>    | 

```python=
driver.get('https://ipost.post.gov.tw/pst/home.html')
#利用selenium找到按鈕
buttons=driver.find_elements_by_class_name('css_btn_class')
#找到目標按鈕按下
for button in buttons:
    if button.text=='不再提醒':
        button.click()
        break
#按下後就可繼續尋找目標元素抓需要的資料
page=driver.find_element_by_xpath('//*[@id="noticeall"]/div[5]/div/div[1]/div[2]/ul/li[1]/a')
page.click()
time.sleep(5)
driver.save_screenshot('shott.png')
divtable=driver.find_element_by_id('table1_overflow')
element6=divtable.find_elements_by_class_name('css_tr')
list6=[]
for tr in element6:
    list6.append(tr.text)
print(list6)
```
 
#### 4.連線失敗
>偽裝成一般網頁瀏覽者
>尚在嘗試結合request模組更改headers
>ex.中信
```python=
driver.get("https://www.ctbcbank.com/twrbo/zh_tw/index.html")
driver.page_source
```
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9cb9d9065726ee18b079431fdbe4dec0)







 





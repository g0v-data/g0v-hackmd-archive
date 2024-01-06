# PTT

```python=
import time
import os
import requests
from bs4 import BeautifulSoup

# 建資料夾
resource_path = r'./res_gossiping'
if not os.path.exists(resource_path):
    os.mkdir(resource_path)

# 建session
headers = {'User-Agent' : 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/75.0.3770.142 Safari/537.36'}
ss = requests.session()
ss.cookies['over18'] = '1'

url = 'https://www.ptt.cc/bbs/Gossiping/index.html'

n = 20
for i in range(0,n):
    # 抓標題
    res = ss.get(url, headers = headers)
    soup = BeautifulSoup(res.text, 'html.parser')
    article_title_html = soup.select('div[class="title"]')

    for each_article in article_title_html:
        try:
            # 印標題和網址
            print(each_article.a.text)
            print('https://www.ptt.cc' + each_article.a['href'])
            # 抓內文
            article_url = 'https://www.ptt.cc' + each_article.a['href']
            article_text = each_article.a.text
            article_res = ss.get(article_url, headers=headers)
            article_soup = BeautifulSoup(article_res.text, 'html.parser')
            # 紀錄資料
            push_up = 0
            push_down = 0
            score = 0
            author = ''
            title = ''
            datetime = ''
            article_content = article_soup.select('div#main-content')[0].text.split('--')[0]
            push_info_list = article_soup.select('div[class="push"] span')
            for info in push_info_list:
                if '推' in info.text:
                    push_up += 1
                if '噓' in info.text:
                    push_down += 1
            article_info_list = article_soup.select('div[class="article-metaline"] span')
            for n, info in enumerate(article_info_list):
                if (n+1)%6 == 2:
                    author = info.text
                if (n+1)%6 == 4:
                    title = info.text
                if (n+1)%6 == 0:
                    datetime = info.text
            score = push_up - push_down
            article_content += '\n---split---\n'
            article_content += '推: %s\n'%(push_up)
            article_content += '噓: %s\n' % (push_down)
            article_content += '分數: %s\n'%(score)
            article_content += '作者: %s\n'%(author)
            article_content += '標題: %s\n'%(title)
            article_content += '時間: %s\n'%(datetime)
            try:
                with open(r'%s/%s.txt' % (resource_path, article_text), 'w', encoding='utf-8') as w:
                    w.write(article_content)
                print()
            except FileNotFoundError as e:
                print('==========')
                print(article_url)
                print(e.args)
                print('==========')
            except OSError as e:
                print('==========')
                print(article_url)
                print(e.args)
                print('==========')

        except AttributeError as e:
            print('==========')
            print(each_article)
            print(e.args)
            print('==========')

    # 上一頁網址
    url = 'https://www.ptt.cc' + soup.select('div[class="btn-group btn-group-paging"]')[0].select('a')[1]['href']

```
```python=
import jieba
# 將所有文章存成一個字串
all_article_string = ''
for each_article in file_list:
    article_path = source_file_path + '/' + each_article
    with open(article_path, 'r', encoding = 'utf-8') as f:
        tmp_article_string = f.read().split('---split---')[0].split('\n')[1:]
    for article_line in tmp_article_string:
        all_article_string += article_line + '\n'
```
```python=
jieba.load_userdict('./mydict.txt') # 使用者字典

# 使用預設模式進行分詞
s_list = jieba.cut(all_article_string)
word_count = {}
for i in s_list:
    if i in word_count:
        word_count[i] += 1
    else:
        word_count[i] = 1
word_count
```
```python=
# 做進一步篩選 將冗餘字串去除
# 將停用字放在list裡面
stopword_path = r'./stopword.txt'
stopword_list = []
with open(stopword_path, 'r', encoding = 'utf-8') as f:
    for each_line in f.readlines():
        stopword_list.append(each_line.replace('\n', ''))
stopword_list

# 只保留長度大於1的詞 len(k) > 1
# 以及不在停用字list裡面的詞 k not in stopword_list
word_list = [(k, word_count[k]) for k in word_count if len(k) > 1 and k not in stopword_list]

# 排序
word_list.sort(key = lambda x : x[1], reverse=True)
word_list
```
# CSV
```python=
# DataFrame
import pandas as pd
import os
columns = ['推數', '噓數', '文章分數', '文章作者', '文章名稱','發表時間']
# 讀取每一篇文章，並將需要的部分取出，轉成我們需要的格式
article_info_row_data = []
for each_article in file_list:
    article_path = source_file_path + '/' + each_article
    with open(article_path, 'r', encoding = 'utf-8') as f:
        tmp_article_string = f.read()
    tmp_row_data = tmp_article_string.split('---split---')[1].split('\n')[1:-1]
    article_info_row_data.append(tmp_row_data)

article_info_row_data

# 製作 DataFrame
df = pd.DataFrame(data=article_info_row_data, columns=columns)

# 過濾器
df2 = df.copy()
df2['推數'].apply(lambda x: x.split(':')[-1].strip())

for c in df2:
    df2[c] = df2[c].apply(lambda x: x.split(': ')[-1].strip())
df2

# 儲存csv檔
df.to_csv(r'./pttGossiping.csv', index=0, encoding = 'utf-8-sig')

# 讀取
df_load = pd.read_csv(r'./pttGossiping.csv')
```
# selenium
```python=
import sys
from selenium import webdriver
from bs4 import BeautifulSoup
import time

sys.path.insert(0,'/usr/lib/chromium-browser/chromedriver')

chrome_options = webdriver.ChromeOptions()
chrome_options.add_argument('--headless')
chrome_options.add_argument('--no-sandbox')
chrome_options.add_argument('--disable-dev-shm-usage')

# 關通知
prefs = {'profile.default_content_setting_values':{'notifications': 2}}
chrome_options.add_experimental_option('prefs', prefs)

driver = webdriver.Chrome('chromedriver',options=chrome_options)
driver.get("https://www.facebook.com/emuse.com.tw")

time.sleep(3)

# 登入
from selenium.webdriver.common.by import By
!gdown --id 1jVnhx4MAttjzKT-p5wje1PhTInsXWOmO --output FBLogin.txt

with open('./FBLogin.txt', 'r', encoding = 'utf-8') as f:
  acc_string = f.read()
email = acc_string.split('\n')[0]
pas = acc_string.split('\n')[1]

driver.find_elements(By.ID, 'email')[0].send_keys(email)
driver.find_elements(By.ID, 'pass')[0].send_keys(pas)
driver.find_elements(By.ID, 'loginbutton')[0].click()

from bs4 import BeautifulSoup

# 下滑
for x in range(3):
    driver.execute_script("window.scrollTo(0,document.body.scrollHeight)")
    print("scroll")
    time.sleep(5)

# 定位文章標題
res = driver.page_source
soup = BeautifulSoup(res, 'html.parser')
titles = soup.find_all('div', class_="xdj266r x11i5rnm xat24cr x1mh8g0r x1vvkbs x126k92a")
print(soup.prettify())

for title in titles:
    # 定位每一行
    posts = title.find_all("div", dir="auto")
    if len(posts):
        for post in posts:
            print(post.text)

    print("-" * 30)

driver.close()
```

# 物件導向
```python=
class Animals():
    """Animals類別, 這是基底類別 """
    def __init__(self, animal_name, animal_age ):
        self.name = animal_name # 紀錄動物名稱
        self.age = animal_age   # 紀錄動物年齡

    def run(self):              # 輸出動物 is running
        print(self.name, " is running")

class Dogs(Animals):
    """Dogs類別, 這是Animal的衍生類別 """
    def __init__(self, dog_name, dog_age):
        super().__init__('My pet ' + dog_name, dog_age)
    def sleeping(self):
        print("My pet", "is sleeping")

mycat = Animals('lucy', 5)      # 建立Animals物件以及測試
print(mycat.name, ' is ', mycat.age, " years old.")
mycat.run()

mydog = Dogs('lily', 6)         # 建立Dogs物件以及測試
print(mydog.name, ' is ', mydog.age, " years old.")
mydog.run()
mydog.sleeping()
```
# MySQLdb
```python=
import MySQLdb

db = MySQLdb.connect("localhost","root","Ro.root","mydatabase")

cursor = db.cursor()

## 1.將如果STUDENTS資料表存在，將STUDENTS資料表丟棄
cursor.execute("DROP TABLE IF EXISTS STUDENTS")


## 2.創建STUDENTS資料表，資料表欄位如下
'''
| ID INT(11) | NAME CHAR(20) | GENDER CHAR(20) | CHINESE CHAR(20) | ENGLISH CHAR(20) | MATH CHAR(20) | SOCIAL_SCIENCE CHAR(20) | SCIENCE  CHAR(20) |

PRIMARY KEY = ID
CHARSET = utf8

'''
sql = """CREATE TABLE STUDENTS (
         ID INT(11) NOT NULL AUTO_INCREMENT,
         NAME  CHAR(20) NOT NULL,
         GENDER CHAR(20) NOT NULL,
         CHINESE CHAR(20) NOT NULL,
         ENGLISH CHAR(20) NOT NULL,
         MATH CHAR(20) NOT NULL, 
         SOCIAL_SCIENCE CHAR(20) NOT NULL,
         SCIENCE CHAR(20) NOT NULL,
         INCOME FLOAT,
         PRIMARY KEY  (ID)
         )DEFAULT CHARSET=utf8"""
cursor.execute(sql)


db.close()
```
```python=
db = MySQLdb.connect("localhost","root","Ro.root","mydatabase" )

cursor = db.cursor()

print("enter students score")
while True:

    student_name = input("enter name: ")
    student_gender = input("enter gender: ")
    student_chinese = input("enter chinese score: ")
    student_english = input("enter english score: ")
    student_math = input("enter math score: ")
    student_social_science = input("enter social science score: ")
    student_science = input("enter science score: ")
    
    ## 3.將student_name, student_gender, student_chinese, ......插入到資料庫
    x = (student_name, student_gender, student_chinese, student_english, student_math, student_social_science, student_science)
    sql = """INSERT INTO STUDENTS(NAME,
         GENDER, CHINESE, ENGLISH, MATH, SOCIAL_SCIENCE)
         VALUES ( %s, %s, %s, %s, %s, %s, %s)"""
    try:
        cursor.execute(sql, x)
        db.commit()
    except:
        db.rollback()
    
    
    again = input("continue(y/n)? ")
    if again[0].lower() == "n":
        break

db.close()
```
```python=
db = MySQLdb.connect("localhost","root","Ro.root","mydatabase" )


cursor = db.cursor()

sql = "SELECT * FROM STUDENTS"

## 4.查詢目前資料庫所有內容
try:
    cursor.execute(sql)
    results = cursor.fetchall()
    for row in results:
        student_id = row[0]
        student_name = row[1]
        student_gender = row[2]
        student_chinese = row[3]
        student_english = row[4]
        student_math = row[5]
        student_social_science = row[6]
        student_science = row[7]
        
      # Now print fetched result
        print("name={},gender={},chinese={},english={},math={},social science={},science={}"
              .format(student_name, student_gender, student_chinese, student_english, student_math, student_social_science, student_science))

except:
    print("Error: unable to fecth data")

    
db.close()
```
```python=
db = MySQLdb.connect("localhost","root","Ro.root","mydatabase" )


cursor = db.cursor()

## 5.將exam_score.csv所有學生成績插入資料庫
with open("exam_score.csv","r",encoding="utf-8") as f:
    for index,i in enumerate (f.readlines()):
        if index == 0:
            continue
        x = tuple(i.strip().split(','))
        print('insert {} data......'.format(x[0]))
        
        sql = """INSERT INTO STUDENTS(NAME,
             GENDER, CHINESE, ENGLISH, MATH, SOCIAL_SCIENCE)
             VALUES ( %s, %s, %s, %s, %s, %s, %s)"""
        try:
            cursor.execute(sql, x)
            db.commit()
        except:
            db.rollback()

db.close()
```
```python=
db = MySQLdb.connect("localhost","root","Ro.root","mydatabase" )

cursor = db.cursor()

## 6.將sophia英文成績改成99
sql = """UPDATE STUDENTS
       SET ENGLISH = 99
       WHERE NAME = 'sophia'"""
try: 
    cursor.execute(sql)
    db.commit()
except:
    db.rollback()

db.close()
```
```python=
db = MySQLdb.connect("db4free.net","isaac60103","isaac60103test","isaac60103", port = 3306 )

cursor = db.cursor()


sql = "SELECT * FROM STUDENTS"
#學生總成績
chinese_avg = 0
english_avg = 0
math_avg = 0
social_science_avg = 0
science_avg = 0

try:
    
    cursor.execute(sql)

    results = cursor.fetchall()
    num_students = len(results)
    ## 7.計算各個科目平均成績
    for row in results:
        student_id = row[0]
        student_name = row[1]
        student_gender = row[2]
        
        student_chinese = row[3]
        chinese_avg += float(row[3])                
        
        student_english = row[4]
        english_avg += float(row[4])        
        
        student_math = row[5]
        math_avg += float(row[5])        
        
        student_social_science = row[6]
        social_science_avg += float(row[6])   
        
        student_science = row[7]
        science_avg += float(row[7])           
        
        
        print('name: {}, gender: {}, chinese: {}, english: {}, math: {}, social_science: {}, science: {}' 
               .format(student_name, student_gender, student_chinese, student_english, student_math, student_social_science, student_science))

except:
    print("Error: unable to fecth data")

print('chinese_avg: {}'.format(chinese_avg/num_students))
print('english_avg: {}'.format(english_avg/num_students))
print('math_avg: {}'.format(math_avg/num_students))
print('social_science_avg: {}'.format(social_science_avg/num_students))
print('science_avg: {}'.format(science_avg/num_students))

db.close()
```
# 其他
```python=
list[]
tuple()
set{}
dict{key:value}

for i in range(1,10,2):

re.search()

# 存圖
for i in img_tags:
        print(i['src'])
        urlretrieve(URL, save_path+'/'+i['title']+'.jpg')

# 接多個輸入
def varnumArg(*meals):
# 接字典
def dinner(**kwargs):

# 轉換每個元素
list = list(map(lambda x: x ** 2, my_list))
# 多個元素合併
list = list(reduce(lambda x,y: x+y, my_list))

# 製作警告
if pwdlen<4:
    raise Exception('pass is too short.')
    
assert pwdlen < 4,'pass is too short.'

# 存讀檔
content = f.read() # 指定字數
print(content)
f.close()

# 常用
time.time()
sys.argv[]
with Zipfile(file_name, 'r')as zip:

# 除錯訊息
logging.debug()
logging.info()
logging.warning()
logging.error()
logging.critical()

# 子執行緒
import threading, time

def job():

t = threading.Thread(target = job)
t.start()
# 等待結束
t.join()
```

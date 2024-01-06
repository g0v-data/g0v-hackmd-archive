Quickstart

# A minimal application
```
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return "Hello, world!"
```

# Routing
綁定一個程式到一個URL。
```
@app.route('/')
def index():
    return 'Index page.'
```

```
@app.route('/user/<username>')
def show_user_profile(username):
    return 'User: %s' % username
```
## Unique URLs & Redirect Behavior
The following two rules differ in their use of a trailing slash.
```
@app.route('/projects/')
def projects():
    return 'The project page'
#結尾有/，就好像檔案系統中的資料夾，若在URL中沒有打/，會自動重導向到/
```
```
@app.route('/about')
def about():
    return 'The about page'
#結尾沒有/，就好像檔案中的路徑名稱，確保URL單一性、不會被搜尋引擎找兩次
```
## Render template_渲染模板



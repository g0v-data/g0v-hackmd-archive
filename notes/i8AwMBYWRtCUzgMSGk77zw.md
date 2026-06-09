# 1. 先測試在實體機器執行
## python 後端程式
儲存為 app.py (名稱可自訂)
```
from flask import Flask, render_template, request
from werkzeug.security import check_password_hash
import csv
import datetime

app = Flask(__name__)

# 讀取使用者資料的函數
def get_users():
    users = {}
    with open('users.csv', mode='r', encoding='utf-8') as file:
        reader = csv.DictReader(file)
        for row in reader:
            users[row['student_id']] = {
                'hash': row['password_hash'],
                'name': row['name']
            }
    return users

# 記錄登入時間的函數
def log_login(student_id):
    with open('login_records.csv', mode='a', encoding='utf-8', newline='') as file:
        writer = csv.writer(file)
        writer.writerow([student_id, datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")])

@app.route('/', methods=['GET', 'POST'])
def login():
    if request.method == 'POST':
        student_id = request.form.get('student_id')
        password = request.form.get('password')
        
        users = get_users()
        
        # 檢查帳號是否存在，以及密碼 Hash 是否吻合
        if student_id in users and check_password_hash(users[student_id]['hash'], password):
            log_login(student_id)
            return render_template('success.html', name=users[student_id]['name'])
        else:
            return "登入失敗：帳號或密碼錯誤"
            
    return render_template('login.html')

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
```
## html 前端網頁
統一儲存在python後端程式目錄下的templates目錄下
```
<!DOCTYPE html>
<html>
<head>
    <title>系統登入</title>
</head>
<body>
    <h2>系統登入</h2>
    <form method="POST" action="/">
        <label>學號:</label>
        <input type="text" name="student_id" required><br><br>
        <label>密碼:</label>
        <input type="password" name="password" required><br><br>
        <button type="submit">登入</button>
    </form>
</body>
</html>
```
```
<!DOCTYPE html>
<html>
<head>
    <title>登入成功</title>
</head>
<body>
    <h2>歡迎，{{ name }}！</h2>
    <p>您的登入紀錄已安全儲存。</p>
</body>
</html>
```
## 資料檔案 (以CSV格式處理)
使用者認證資料
```
student_id,password_hash,name
11208013a,scrypt:32768:8:1$ZmwEkGUcwcASGmkS$ccb93fd16d7409dde58d3fa151211373dc8d02a67d4ca63424ebb2f7affd7ea2ebf3145747364eb2b8b44e56e2759d5136c010bdd7b7a81a332c786028ec4903,邱彥勛
```
使用者資料
```
log_id,username,login_time
1,11208013A,2026-06-09 11:15:30
2,11208013A,2026-06-09 11:20:45
帳號:11208013A
密碼:INT30120
```
# 2. 建立 Dockerfile
在和應用程式同一層的目錄中，新增檔名為 Dockerfile 的檔案
需將所需檔案複製到 工作目錄
考慮檔案內容是否須和主機互通
Dockerfile內容

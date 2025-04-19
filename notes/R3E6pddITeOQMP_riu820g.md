---
tags: edu,
---

# React 網站建置
[toc]
### 建立 React 專案
```bash
npx create-react-app react-apache-demo
```

```
cd react-apache-demo
```
### 修改首頁內容
- 打開 src/App.js
- 啟用一個 React 的開發伺服器（localhost:3000），支援熱更新（Hot Reloading）
- 開發階段（即時更新）
```
npm start
```

### 打包網站
- 這會產生 build/ 資料夾，裡面是靜態網站檔案。
```
npm run build
```
- 建立 Dockerfile（Apache + React），在專案根目錄建立 Dockerfile
```
# 使用 Apache 官方映像檔
FROM httpd:2.4

# 複製 React 打包後的靜態網站進 Apache 的根目錄
COPY build/ /usr/local/apache2/htdocs/

EXPOSE 80

```

### 建置與啟動 Docker 容器
- 在 react-apache-demo/ 目錄下執行：
```
docker build -t react-apache .
```
```
docker run -d -p 8080:80 react-apache
```
- 這樣網站就會在：👉 http://localhost:8080 出現 🎉

### 部署階段（build 後不會即時更新）
- 解法：重新 build & 重建 Docker image
```
# 1. 重新打包 React 專案
npm run build

# 2. 重新 build Docker image
docker build -t react-apache .

# 3. 停掉舊的 container（可用 docker ps 看 container ID）
docker stop <container-id>

# 4. 啟動新的 container
docker run -d -p 8080:80 react-apache

```
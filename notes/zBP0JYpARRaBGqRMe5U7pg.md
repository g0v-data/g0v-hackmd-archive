# ccd轉址
## 來源判定
router.js 進行來源網域判定與控制，如果是從`proxy.icantech.org.tw`近來，加上前綴`/icantech`如下
```
const isProxyDomain = window.location.hostname === 'proxy.icantech.org.tw';
const basePath = isProxyDomain ? '/icantech' : '';
const routes = [
    { path: `${basePath}/maintain/`, element: <Home /> }}
];
```

問題:靜態檔案讀去異常
解法:嘗試使用web server而非react的開發伺服器
## 使用代理伺服器Nginx -在ubuntu中安裝
1. 在react資料夾執行 `npm run build`,同資料夾會產生一個build資料夾


3. 安裝nginx
4. 在sites-available/放Nginx 站點配置
5. sites-enabled/ 符號連結(指令:`ln -s /etc/nginx/sites-available/maintain-web /etc/nginx/sites-enabled/`)
6. 在 package.json 裡，homepage
7. nginx 有專用的docker 部屬環境 改直接部屬


## 使用代理伺服器Nginx -直接使用docker的Nginx環境
1. homepage 與 pathURL皆為管理server靜態文件的位置
2. Dockerfile，主要是將build文件夾內的資料複製到`/usr/share/nginx/html`，並更新`/etc/nginx/nginx.conf`
```
# 使用官方 Nginx 映像檔
FROM nginx:latest

# 設定工作目錄
WORKDIR /usr/share/nginx/html

# 清除預設 Nginx HTML 檔案
RUN rm -rf ./*

# 設定環境變量，防止在安裝時被詢問區域設置的問題
ENV DEBIAN_FRONTEND=noninteractive
# 更新軟件庫並安裝必要的軟件
#新增nginx
RUN apt-get update && apt-get install -y \
    curl \
    git \
    gnupg \
    build-essential \      
    && rm -rf /var/lib/apt/lists/*

# 複製 React Build 資料夾內容到 Nginx 伺服器目錄
COPY build /usr/share/nginx/html
# COPY .env /usr/share/nginx/html/.env

# 複製自訂 Nginx 設定檔
COPY nginx.conf /etc/nginx/nginx.conf

# 暴露 3000 port
EXPOSE 3000

# 啟動 Nginx
CMD ["nginx", "-g", "daemon off;"]
```

微調deploy-maintain-web (sh檔)
```
#!/bin/bash

NAME="maintain-web"
PORT="3000"
DOCKER_NETWORK="puhui-test"

echo "removing folder build."
rm -rf build

echo "Unzip maintain-web-build.tar."
tar -xvf maintain-web-build.tar

if [[ -n $(docker ps -a -q -f "name=^$NAME$") ]]; then
    docker stop $NAME
    docker rm $NAME
    docker rmi $NAME
else
    echo "container not exist."
fi

docker build -t $NAME . --no-cache

echo "docker image build finished."

docker run -d --network $DOCKER_NETWORK --ip 172.20.1.10 --name $NAME --restart always -p ${PORT}:${PORT} $NAME
echo "docker run finished."

REGISTRY_PATH="asia-east1-docker.pkg.dev/ida-puhui/puhui-docker-registry"
docker tag $NAME:latest $REGISTRY_PATH/$NAME:latest
docker push $REGISTRY_PATH/$NAME:latest
echo "docker image push finished."

docker system prune -a -f

```

# 核對0615test與maintain only 兩邊有部分檔案不同步(已完成)

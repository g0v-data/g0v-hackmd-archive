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
## 使用代理伺服器Nginx
1. 在react資料夾執行 `npm run build`,同資料夾會產生一個build資料夾


3. 安裝nginx
4. 在sites-available/放Nginx 站點配置
5. sites-enabled/ 符號連結(指令:`ln -s /etc/nginx/sites-available/maintain-web /etc/nginx/sites-enabled/`)
6. 在 package.json 裡，homepage
7. 



# 核對0615test與maintain only 兩邊有部分檔案不同步

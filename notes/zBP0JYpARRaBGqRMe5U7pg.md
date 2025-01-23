# ccd轉址
## 來源判定
router.js 進行來源網域判定與控制，如果是從`proxy.icantech.org.tw`近來，加上前墜`/icantech`如下
```
const isProxyDomain = window.location.hostname === 'proxy.icantech.org.tw';
const basePath = isProxyDomain ? '/icantech' : '';
const routes = [
    { path: `${basePath}/maintain/`, element: <Home /> }}
];
```
## 使用代理伺服器Nginx
1. 在react資料夾執行 `npm run build`,同資料夾會產生一個build資料夾
2. 

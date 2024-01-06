# Day 28 - 準備好要上線了嗎？(六)

## SSL

昨天完善了自動部署，今天要來補上 SSL 的設定，讓 Traefik 幫我把憑證處理完

第一步先來處理憑證申請

```yaml
  traefik:
    image: traefik:v2.10
    container_name: reverse-proxy
    networks:
      - traefik-public
    ports:
      - "80:80"
      - "443:443"
    volumes:
      ...
      - traefik-public-certificate:/certificates
    command:
	  # le 是指 Let's Encrypt
      - --certificatesresolvers.le=true
      - --certificatesresolvers.le.acme.dnschallenge=true 
	  # 剛好 API 清單有 godaddy ， 域名也是同一個地方買的就直接使用
      - --certificatesresolvers.le.acme.dnschallenge.provider=godaddy 
	  # 申請要附上個人信箱
      - --certificatesresolvers.le.acme.email=dantecherng@gmail.com
	  # 憑證存放的位置，這裡使用 volumes 存放重複使用
      - --certificatesresolvers.le.acme.storage=/certificates/acme.json
```


微調細節，將申請憑證的站點改成測試站

否則跟我一樣忘記改，結果部署的過程中 Volumes 跟原本 Action 部署的方式沒有配合好，憑證一直沒放到 Volumes，直接消失
搞了大半天才看到憑證已經申請過多，要等到隔天才能繼續申請 XD

另外補上 Godaddy API 的 Key 跟 Secret ，就能申請憑證啦

```yaml
  traefik:
    ...
    command:
      ...
	  # 預設是正式站，這裡先用測試站申請，確認好再改回來
      - --certificatesresolvers.le.acme.caserver=https://acme-staging-v02.api.letsencrypt.org/directory
    environment:
      GODADDY_API_KEY: ${GODADDY_API_KEY}
      GODADDY_API_SECRET: ${GODADDY_API_SECRET}
```

補一個進入點的設定，之後會拿來做 app 的進入點設定
這裡 `entrypoints` 後面的 `http` / `https` 只是暱稱的概念，小心搞混（對 自己查資料的時候也搞混  lol

```yaml
 traefik:
    ...
    command:
      ...
      - --entrypoints.http.address=:80
      - --entrypoints.https.address=:443
```

接著來做 app 的設定，將 Http 導回 Https
記得還要去 AWS 將 InboundRule 加入 443 的設定

```yaml
  app:
    ...
    labels:
      - traefik.enable=true
      - traefik.docker.network=traefik-public
	  # 等號後面的 http 就是前面提到的暱稱
      - traefik.http.routers.app_http.entrypoints=http
      - traefik.http.routers.app_http.rule=Host(`ironman2023.traefik.dantecheng.me`)
      - traefik.http.routers.app_http.middlewares=https-redirect
      - traefik.http.routers.app_https.entrypoints=https
      - traefik.http.routers.app_https.rule=Host(`ironman2023.traefik.dantecheng.me`)
	  # 憑證設定，會將整個域名申請下來，就不用單獨域名申請
      - traefik.http.routers.app_https.tls=true
      - traefik.http.routers.app_https.tls.certresolver=le
      - traefik.http.routers.app_https.tls.domains[0].main=traefik.dantecheng.me
      - traefik.http.routers.app_https.tls.domains[0].sans=*.traefik.dantecheng.me

```


以上設定完成，原則上就能夠視為一個正常的網站ㄌ！

盡善盡美，順便試了一下怎麼設定把 traefik 內部監控用的 API 連到另一個 domain 上

原則上大同小異，只有一些小坑

像是 `redirectscheme.permanent` 這個設定，強制給你轉成 http 308（看人家寫，以為是必要的放的

結果導致藍星 API 那邊要 200 不成，交易失敗（哭 誰叫你不看文件

本日最坑：Ｄ （我自己


```yaml

  traefik:
    ...
    labels:
      - traefik.enable=true
      - traefik.docker.network=traefik-public
	  # API 連接 8080 所以要強制指定導向
      - traefik.http.services.traefik.loadbalancer.server.port=8080
      - traefik.http.services.traefiks.loadbalancer.server.port=8080
	  # 指定導入的 Service ，這個在本地調適或是官方文件都能看到
      - traefik.http.routers.traefik_http.service=api@internal
      - traefik.http.routers.traefik_http.entrypoints=http
      - traefik.http.routers.traefik_http.rule=Host(`traefik.dantecheng.me`)
      - traefik.http.routers.traefik_http.middlewares=https-redirect
      - traefik.http.routers.traefik_https.service=api@internal
      - traefik.http.routers.traefik_https.entrypoints=https
      - traefik.http.routers.traefik_https.rule=Host(`traefik.dantecheng.me`)
      - traefik.http.routers.traefik_https.tls=true
      - traefik.http.routers.traefik_https.tls.certresolver=le
      - traefik.http.routers.traefik_https.tls.domains[0].main=dantecheng.me
      - traefik.http.routers.traefik_https.tls.domains[0].sans=*.dantecheng.me
      - traefik.http.middlewares.https-redirect.redirectscheme.scheme=https
      # - traefik.http.middlewares.https-redirect.redirectscheme.permanent=true
```

如此這般就完成今天 SSL 設定，準備迎來大結局ㄌ！

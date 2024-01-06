# Day 25 - 準備好要上線了嗎？(三)

## Dockerfile
前期的安裝就不贅述了，這裡會專注 `Dockerfile` 上

而這邊要推薦~~偷懶~~用一下 [Boxing](https://github.com/elct9620/boxing) ，可以快速幫忙生成一個簡單且輕量化的 `Dockerfile`

因為本次沒有特殊的設定，甚至連設定檔都不太需要更動

```
bundle exec boxing generate
```

就能生成 `Dockerfile` ， 之後建立映像檔 上一個 tag 方便使用

```
docker build -t ironman2023 .
```

run 起來，確認有沒有走到 server 啟動

```
docker run -p 3000:3000 ironman2023
```

配上 -p(port) 讓容器內與本機的 port 對應到，即可在本機連入容器內

確認有啟動且沒有發生錯誤的話，這步姑且就算過關

（感覺這段很容易，但其實花最多時間都在解這個[問題](https://nokogiri.org/tutorials/installing_nokogiri.html#cannot-load-such-file-nokogirinokogiri-loaderror)，

## Docker compose
因為前一步僅僅只是建立 Application 的映像檔，Database 及其他的服務並沒有啟用連接

所以連入後並沒辦法使用整個應用，這時候就需要借助 compose ，透過 Yaml 調整設定來為相依的服務建立容器，並使之與 Application 連接

所以先建立最基本常見的 Application / Database / Redis ，透過 networks 來連接起來

```
services:
  redis:
    image: redis:6.0-alpine
    command: redis-server
    networks:
      - net
    volumes:
      - shared_data:/var/shared/redis
 
  postgres:
    image: postgres:14-alpine
    container_name: postgres
    volumes:
      - database_data:/var/lib/postgresql/data
    networks:
      - net
    environment:
      - POSTGRES_DB=postgres
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=password

  app:
    build:
      context: .
      dockerfile: Dockerfile
    container_name: app
    volumes:
      - .:/var/app
      - shared_data:/var/shared
      - gem_cache:/usr/local/bundle/gems
    networks:
      - net
    environment:
      - DATABASE_URL=postgres://postgres:password@postgres/postgres
    depends_on:
      - postgres
    ports:
      - 3000:3000
```

設定完之後，透過 app 設定 ports 讓本機 3000 能夠連進去容器的 3000

```
docker compose build
docker compose up
```

此時還不能用

因為只是把 Server 開起來

需要進到容器內去做 migrate 跟 seed 塞入資料

查詢現在使用 app 的容器 ID

```
docker exec -it [container_id] sh

bundle exec rails db:migrate
bundle exec rails db:seed
```

這裡還要手動操作，之後再來慢慢調整到自動化一點，所以現在先求可以動就好

然後，本地開 `localhost:3000` 就能看到畫面並登入囉！

至此算是先處理好容器了，下一步就是 `Traefik`!

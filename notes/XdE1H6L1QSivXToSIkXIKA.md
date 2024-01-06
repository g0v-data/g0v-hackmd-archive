---
title: "tisa.g0v.tw development"
tags: hackpad
---

# tisa.g0v.tw development

> [點此觀看原始內容](https://g0v.hackpad.tw/7g0bP9SJVgl_YQ7IlR4jniZ)

This board contains sensitive information and was shared to "invitees only".
Insensitive information should be going to [服貿協議相關 g0v 專案](https://g0v.hackpad.com/-g0v--SUkMbG4IV6v)
## Production

### SSH access

Transfer your `~/.ssh/id_rsa.pub` to authorized owners for ssh access without password.
```
$ ssh tisa@<ip>
```
If you don't have \`id_rsa.pub\`, run
```
$ ssh-keygen
```
Then you will have it in `~/.ssh/`
### Machine List

For your conveniences to access rapidly, put this machines into your `~/.ssh/config` as following format.
```
Host tisa
    HostName  162.243.145.68
    User      tisa
    Port      22
```
- tisa
    - Function: Reverse Proxy by Nginx
    - IP: \`162.243.145.68\`
- tisa-app1
    - Function: App
    - IP: \`107.170.210.212\`
- tisa-app2
    - Function: App
    - IP: \`107.170.209.101\`
- tisa-app3
    - Function: App
    - IP: \`107\`
- tisa-db1
    - Function: Database by Postgresql 9.3 (Postgis Extension)
    - IP: \`107.170.209.102\`
### Deployment

All `/tisa-app\\d+/` machines have a clone of codebase at `~/tisa-map`. Currently we have no capistrano script. Just run
```
$ git pull
```
And restart unicorn server in \`screen\` session.
### Database

#### setup

```
$ createuser tisa --superuser --encrypted --pwprompt
$ createdb tisa
$ sequel config/database.yml -m migrations
```
#### connection

To run Sequel console, put following content in \`config/database.yml\`
```
production:
    :adapter:    postgres
    :host:       162.243.145.68
    :database:   tisa
    :username:   tisa
    :password:   tisamap
    :encoding:   utf8
    :pool:       5
```
And run
```
$ sequel config/database.yml
```
#### backup

```
$ pg_dump --blobs --verbose --format tar --encoding utf8 --file tisa-yyyy-mm-dd.tar tisa
```
Some recent backups from the production environment
- [http://1](http://140.112.20.144/tisa-2014-04-06.tar)[4](http://140.112.20.144/tisa-2014-04-06.tar)[0](http://140.112.20.144/tisa-2014-04-06.tar)[.1](http://140.112.20.144/tisa-2014-04-06.tar)[1](http://140.112.20.144/tisa-2014-04-06.tar)[2](http://140.112.20.144/tisa-2014-04-06.tar)[.2](http://140.112.20.144/tisa-2014-04-06.tar)[0](http://140.112.20.144/tisa-2014-04-06.tar)[.1](http://140.112.20.144/tisa-2014-04-06.tar)[4](http://140.112.20.144/tisa-2014-04-06.tar)[4](http://140.112.20.144/tisa-2014-04-06.tar)[/](http://140.112.20.144/tisa-2014-04-06.tar)[t](http://140.112.20.144/tisa-2014-04-06.tar)[i](http://140.112.20.144/tisa-2014-04-06.tar)[s](http://140.112.20.144/tisa-2014-04-06.tar)[a](http://140.112.20.144/tisa-2014-04-06.tar)[-](http://140.112.20.144/tisa-2014-04-06.tar)[2](http://140.112.20.144/tisa-2014-04-06.tar)[0](http://140.112.20.144/tisa-2014-04-06.tar)[1](http://140.112.20.144/tisa-2014-04-06.tar)[4](http://140.112.20.144/tisa-2014-04-06.tar)[-](http://140.112.20.144/tisa-2014-04-06.tar)[0](http://140.112.20.144/tisa-2014-04-06.tar)[4](http://140.112.20.144/tisa-2014-04-06.tar)[-](http://140.112.20.144/tisa-2014-04-06.tar)[0](http://140.112.20.144/tisa-2014-04-06.tar)[6](http://140.112.20.144/tisa-2014-04-06.tar)[.t](http://140.112.20.144/tisa-2014-04-06.tar)[a](http://140.112.20.144/tisa-2014-04-06.tar)[r](http://140.112.20.144/tisa-2014-04-06.tar)
- [http://1](http://140.112.20.144/tisa-2014-04-10.tar)[4](http://140.112.20.144/tisa-2014-04-10.tar)[0](http://140.112.20.144/tisa-2014-04-10.tar)[.1](http://140.112.20.144/tisa-2014-04-10.tar)[1](http://140.112.20.144/tisa-2014-04-10.tar)[2](http://140.112.20.144/tisa-2014-04-10.tar)[.2](http://140.112.20.144/tisa-2014-04-10.tar)[0](http://140.112.20.144/tisa-2014-04-10.tar)[.1](http://140.112.20.144/tisa-2014-04-10.tar)[4](http://140.112.20.144/tisa-2014-04-10.tar)[4](http://140.112.20.144/tisa-2014-04-10.tar)[/](http://140.112.20.144/tisa-2014-04-10.tar)[t](http://140.112.20.144/tisa-2014-04-10.tar)[i](http://140.112.20.144/tisa-2014-04-10.tar)[s](http://140.112.20.144/tisa-2014-04-10.tar)[a](http://140.112.20.144/tisa-2014-04-10.tar)[-](http://140.112.20.144/tisa-2014-04-10.tar)[2](http://140.112.20.144/tisa-2014-04-10.tar)[0](http://140.112.20.144/tisa-2014-04-10.tar)[1](http://140.112.20.144/tisa-2014-04-10.tar)[4](http://140.112.20.144/tisa-2014-04-10.tar)[-](http://140.112.20.144/tisa-2014-04-10.tar)[0](http://140.112.20.144/tisa-2014-04-10.tar)[4](http://140.112.20.144/tisa-2014-04-10.tar)[-](http://140.112.20.144/tisa-2014-04-10.tar)[1](http://140.112.20.144/tisa-2014-04-10.tar)[0](http://140.112.20.144/tisa-2014-04-10.tar)[.t](http://140.112.20.144/tisa-2014-04-10.tar)[a](http://140.112.20.144/tisa-2014-04-10.tar)[r](http://140.112.20.144/tisa-2014-04-10.tar)
- [http://140.112.20.144/tisa-2014-04-19.tar](http://140.112.20.144/tisa-2014-04-19.tar)
#### restore

```
$ pg_restore --verbose --clean --no-acl --no-owner -h localhost -U tisa -d tisa --format tar tisa-yyyy-mm-dd.tar
```
## Development

### postgresql array column

[http://sequel.jeremyevans.net/rdoc-plugins/files/lib/sequel/extensions/pg\_array\_rb.html](http://sequel.jeremyevans.net/rdoc-plugins/files/lib/sequel/extensions/pg_array_rb.html)
[http://www.postgresql.org/docs/9.3/static/functions-array.html](http://www.postgresql.org/docs/9.3/static/functions-array.html)
### postgresql json column

[http://sequel.jeremyevans.net/rdoc-plugins/files/lib/sequel/extensions/pg\_json\_rb.html](http://sequel.jeremyevans.net/rdoc-plugins/files/lib/sequel/extensions/pg_json_rb.html)
[http://www.postgresql.org/docs/9.3/static/functions-json.html](http://www.postgresql.org/docs/9.3/static/functions-json.html)
### 代碼對照表 與 服務貿易特定承諾表 對照數字(紅字, 57 個)

[https://www.dropbox.com/sh/xh488y46hgxjy6b/LFIfMNhQ_M](https://www.dropbox.com/sh/xh488y46hgxjy6b/LFIfMNhQ_M)
## Schema

### Company

| id | integer |
| --- | --- |
| location | geometry(Point,4326) |
| taxid | character(8) |
| name | character varying(128) |
| address | text |
| categories | text\[\] |
| status | character varying(128) |
| owner | character varying(128) |
### Tisa

| id | integer |
| --- | --- |
| articles | json |
### CPC

| id | integer |
| --- | --- |
| tisa_id | integer |
| key | text |
| name | text |
### Group

| id | integer |
| --- | --- |
| tisa_id | integer |
### Category

### Standard

| id | integer |
| --- | --- |
| type | integer |
| ip | text |
| created_at | timestamp without time zone |
| updated_at | timestamp without time zone |
## Contributors

[nchild](https://g0v.hackpad.tw/ep/profile/tXyPGAkvFX9) xchild@gmail.com
[Shelling Ford](https://g0v.hackpad.tw/ep/profile/nl9nKXU6Z1L) navyblueshellingford@gmail.com
[howard chi](https://g0v.hackpad.tw/ep/profile/uldM12vxAYG) chilijung@gmail.com
[Johnson Liang](https://g0v.hackpad.tw/ep/profile/z4JarLrJBea) johnsonliang7@gmail.com
[Shenk Wang](https://g0v.hackpad.tw/ep/profile/BBGX8lqNMr7) shenkyw@gmail.com
[ipa chiu](https://g0v.hackpad.tw/ep/profile/od9zls3wnWG) ipawei@gmail.com
[Lucien Lee](https://g0v.hackpad.tw/ep/profile/qaqB0AtENES) lkiral7903@gmail.com
 洪偉 wayne930242@gmail.com
 凜希 luanyoung@gmail.com



# 養狗的艾斯 
# [參考文件](https://www.isc.org/docs/BIND_RPZ.pdf) 
> 沒看到改了什麼
# /etc/named.conf
```
options {
        listen-on port 53 { any;};
        directory       "/var/named";
        allow-query     { 10.0.0.0/8;127.0.0.1; };
        recursion yes;
        dnssec-enable no;
        dnssec-validation no;
        pid-file "/run/named/named.pid";
        session-keyfile "/run/named/session.key";
        querylog yes;
        response-policy {
            zone "aceaceace.com";
        };
        allow-transfer { none;};
};


zone "aceaceace.com" {
    type master;
    allow-update { 127.0.0.1;};
    file "aceaceace.com.rpz";
};
zone "." IN {
        type hint;
        file "named.ca";
};
// End of named.conf
```


# /var/named/aceaceace.com.rpz
```
$TTL 30
@       IN SOA  @ rname.invalid. (
                                        1       ; serial
                                        1D      ; refresh
                                        1H      ; retry
                                        1W      ; expire
                                        3H )    ; minimum
        NS      localhost.

deteque.com     CNAME   rpz-passthru.
*.deteque.com   CNAME   rpz-passthru.
spamhaus.org    CNAME   rpz-passthru.
*.spamhaus.org  CNAME   rpz-passthru.
32.25.195.194.32.rpz-ip CNAME   rpz-passthru.
32.71.219.156.35.rpz-ip CNAME   rpz-passthru.
8.0.0.0.142.rpz-ip      CNAME   .
example.com     CNAME   .       ;       local   block   against example.com
*.example.com   CNAME   .
aaa.com         CNAME   .
aab.com         CNAME   .
aac.com         CNAME   .
*.3322.org      CNAME   .
*.a123.net      CNAME   .
456.info        CNAME   .

; End of RPZ file
```


[root@dns01 named]# systemctl restart named

# 正常解析
```
[root@dns01 named]# dig aaa.com

; <<>> DiG 9.11.4-P2-RedHat-9.11.4-26.P2.el7_9.5 <<>> aaa.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 50376
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;aaa.com.                       IN      A

;; ANSWER SECTION:
aaa.com.                108     IN      A       45.60.107.121
aaa.com.                108     IN      A       45.60.62.121
```
# NXDOMAIN 代表被 RPZ 攔截了
```
[root@dns01 named]# dig aaa.com  @localhost

; <<>> DiG 9.11.4-P2-RedHat-9.11.4-26.P2.el7_9.5 <<>> aaa.com @localhost
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: **NXDOMAIN**, id: 55073
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 2

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;aaa.com.                       IN      A

;; ADDITIONAL SECTION:
aceaceace.com.          30      IN      SOA     aceaceace.com. rname.invalid. 2 86400 3600 604800 10800
```

# 正常解 google (IP=142.250.185.164)
```
[[root@dns01 named]# dig www.google.com

; <<>> DiG 9.11.4-P2-RedHat-9.11.4-26.P2.el7_9.5 <<>> www.google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 51309
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;www.google.com.                        IN      A

;; ANSWER SECTION:
www.google.com.         300     IN      A       142.250.185.164

;; Query time: 345 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Sat Sep 04 08:05:15 UTC 2021
;; MSG SIZE  rcvd: 59


```
# 經過 RPZ 處理 ( IP 在黑名單, 因為 8.0.0.0.142.rpz-ip, 這行代表 142.0.0.0/8)
)
```
[root@dns01 named]# dig www.google.com @localhost

; <<>> DiG 9.11.4-P2-RedHat-9.11.4-26.P2.el7_9.5 <<>> www.google.com @localhost
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 27819
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 2

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;www.google.com.                        IN      A

;; ADDITIONAL SECTION:
aceaceace.com.          30      IN      SOA     aceaceace.com. rname.invalid. 1 86400 3600 604800 10800

;; Query time: 347 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sat Sep 04 08:07:57 UTC 2021
;; MSG SIZE  rcvd: 102
```
# 其他例子 (aaa.com 黑名單)
```
[root@dns01 named]# dig aaa.com +short
45.60.62.121
45.60.107.121
[root@dns01 named]# dig aaa.com +short @localhost
```

# 其他例子 (wildcard 影響)
```
[root@dns01 named]# dig a123.net +short @localhost
208.74.69.235
[root@dns01 named]# dig www.a123.net +short @localhost
```

# 其他例子 (隨機檢驗一些例子, 142.0.0.0/8 已經黑名單)
```
[root@dns01 named]# dig -x 142.1.1.1 +short
utmuser1-1.wireless.utoronto.ca.
[root@dns01 named]# dig utmuser1-1.wireless.utoronto.ca. +short
142.1.1.1
[root@dns01 named]# dig utmuser1-1.wireless.utoronto.ca. @localhost +short
```
`

# EXCEL copy & paste,再貼到 aceaceace.com 檔案底部
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_98b9923cc159fa2cc55852f76e88a1ea.png)

```







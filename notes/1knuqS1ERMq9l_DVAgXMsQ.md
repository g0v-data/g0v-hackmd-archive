電腦網路C3 - Transport Layer
=====

多工 解多工 是必要的

提供nton的最後一層(端對端)(process to process)

核心網路最多看到第三層

segments:第四層的封包
接收端把收到的segment 轉成 message 再送到第四層

AP層不管送的東西有沒有到=>交給第四層

transport layer protocol
第四層: 人送到人(process to process)
第三層: 郵政送信把信送到家(host to host)
- TCP:
    - congestion control:碰到塞車(路上狀況)(核心網路壅塞)

    - flow control: (端點壅塞) 車庫不夠用(收端告訴送端你能送多少東西過來)

    - congestion control & flow control 得處理方法 都是 叫送端不要再送

    - connection setup:收端在送端 送資料前 告訴送端你能送多少東西過來
    
----
- UDP:
    - best-effort 盡力送 但不能夠給保證
    - IP+port number

- 不提供時限內送達(下層沒有) (下層部提供的服務 上層做不到)
- 可靠傳送: 下層做不到 但上層做得到

---------------
multiplexing demultiplexing
=====
同一個機器的多個應用程式可以透過同一個連線出去

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8c3ea7cc67991c6812dad057c51371e4.png)

透過port number 傳到正確的process (IP 送到一個機器)

source port: 送件人
dest port: 收件人

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9753e46002897252c22e5ab1518c7d8c.png)

TCP socket : 4 
soure IP 
source port number
dest IP 
dest port number
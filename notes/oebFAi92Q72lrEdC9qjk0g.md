# RabbitMQ

**AMQP (Advanced Message Queuing Protocol)**
```
核心概念: 
1. Server (Broker)
2. Connection
3. Channel
4. Message
5. Virtual host
6. Exchange
7. Binding
8. Routing Key
9. Queue
```

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4ad9c7867febb88dfeae02a054a54473)


**Docker Container安裝**
```
docker run -d -p 5672:5672 -p 15672:15672 --name rabbitmq rabbitmq:management
```
* 5672:AMQP
* 15672:Http
* 25672:Cluster




**Exchange 類型**
```
1. Fanout :發送到所有綁定該exchange的queue (忽略Routing Key)
2. Direct :發送到Routing Key=Binding Key的queue
3. Topic : 發送到Routing Key匹配Binding Key的queue
    * #匹配一個或多個 *匹配一個
    * 例: user.# 可接收到 user.a、user.a.a1之訊息; user.*則只能收到 user.a之訊息
4. Header :不常用
```

**Queue 參數**
```
1. Durable:是否持久化
2. Exclusive: 是否獨佔
3. AutoDelete: 是否刪除 (若為yes，則當最後一個監聽被移除後，該Queue會自動刪除)
```
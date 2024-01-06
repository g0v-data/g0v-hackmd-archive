# Lily 交接文件

### 交接專案
1. 冠天下爬蟲
2. 看板盤口歷程
3. 九州賽果程式
4. 九州備用帳號登入
5. game center 架構
6. redis機器
7. 目前流程圖


- - -  
### 冠天下爬蟲

git: http://git.sp168.cc/lily/newCtx
線上版本：master
game center版本： rod_Test
說明文件： git readme
值班資料：https://www.evernote.com/shard/s477/nl/141085642/30abcfef-82e1-4af3-93de-0708eaaee079/
帳密：
- 泰金站(無法使用)：http://www.tga8889.net/newapp/
                 http://www1.tga8889.net/newapp/
  密碼：a123
    
    帳號|使用說明
    --|:-------
    c76121 |
    c76122 |
    c76123 |
    c76124 |
 

- 冠天下:http://www1.as8889.com/newapp/
  密碼：a123
    
  帳號|使用說明
  --|:-------
  872706| 機器 147 (full)| 
  872768| 機器 147 (live)|
  873008| 機器 50 (full)|
  873009| 機器 50 (live)|
  872568| 巨力測試live
  870887| 巨力測試full
  87914|
  872570|
  872765 |
  872566| apple用
  87925 | hank
  873011| apple用
  872767|
  872572|
  872763|
  87916|
  872764|
  872766 |
  872769 | SY使用
  873010 | 測試live
  872770 | 測試full
  872569|
  872571|
  872705|

 
## 看板盤口歷程
git: http://git.sp168.cc/lily/logData
線上版本：master
game center版本：http://git.sp168.cc/lily/game_center_log （branch:sy@handover）
說明文件： git readme
注意：
新交換機須先接到對應的.fanout交換機
例如 CTX訊號源有新交換機 CTX_HR 
則需要將 CTX.fanout(交換機) 接上 CTX_HR 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_da0cb21e7308434fb8b2acca92165fb7.png)


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6e188a9c1d89b3f773d7a6437904921d.png)


## 九州賽果程式
git: http://git.sp168.cc/lily/gameResult
線上版本：master
game center版本：branch:rod@change_jsontype
game center規格文件：https://g0v.hackmd.io/O1mGF95cRdumydw-LcaYEA?view
說明文件： git readme
值班資料：https://www.evernote.com/shard/s477/nl/141085642/b7c345f4-e66a-41a7-88a2-e49cf7f8378b/

## 九州備用帳號登入
git: http://git.sp168.cc/lily/auto_logIn_TX
線上版本：master
說明文件： git readme


## game center 架構
DB文件：nas/JS-JavaPython資料區/規格文件/gameDB說明書_日期
代辦事項：
1. slow log太多，需加入index 。
   greyLog查看:
   http://graylogtc.justdoit.im:9000/streams 
   帳密：sprd / gp6fu61l41o
   ```
   SELECT  u.UP_id AS event, u.sportType_id AS sportType, l.name_c AS league, p.name_c AS homeTeam, a.name_c AS awayTeam, s.short_name  AS source, u.gameTime, h.game_id AS gameId, h.gameType_id AS gameType, h.eventType_id AS eventType, h.gameTitle_id AS gameTitle, h.hdcpType_id AS hdcpType, h.oddType_id AS oddType, e.league AS leagues, h.strong, h.pointSpread AS line, h.odd_1 AS home, h.odd_2 AS away, h.odd_3 AS draw, h.system_close AS scloce, r.live_time AS liveTime FROM  UP_event AS u  
    INNER JOIN event AS e ON u.UP_id = e.UP_id 
    LEFT JOIN participant AS p ON u.homeTeam_id = p.p_id  
    LEFT JOIN participant AS a ON u.awayTeam_id = a.p_id  
    LEFT JOIN league AS l ON u.lg_id = l.lg_id  
    LEFT JOIN source AS s ON s.source_id = e.source_id  
    INNER JOIN hdcp AS h  ON e.event_id = h.event_id AND e.source_id = h.source_id 
    LEFT JOIN result AS r ON r.event_id = h.event_id AND r.game_id = h.game_id AND r.source_id = h.source_id 
    WHERE u.gameTime LIKE '2020-06-16%' AND e.sportType_id = 3 AND h.gameType_id = 1 AND h.gameTitle_id = '0' AND h.hdcpType_id  IN( '1','2','3' ) AND  h.eventType_id = 0 AND h.oddType_id = 1;
    ＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝
    UPDATE result SET source_updatetime='2020-06-16 18:57:11.002' WHERE game_id = '6084321' AND event_id = '26f3920e693de5a7c8f1c0c8322f4c47' AND gameType_id = '1' AND gameTitle_id = '0' AND resultType_id = '4' AND status_id = '2' AND source_updatetime < '2020-06-16 18:57:11.002' AND source_id = '1';
    ＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝
    UPDATE result SET live_time='上 30',source_updatetime='2020-06-16 19:00:33.895' WHERE game_id = '34118844' AND event_id = '61652de882a8ebbbb382343314aca2a9' AND gameType_id = '2' AND gameTitle_id = '0' AND resultType_id = '5' AND status_id = '2' AND source_updatetime < '2020-06-16 19:00:33.895' AND source_id = '1';


   ```
2. 新賽果流程尚未測試：
   傳送MQ規格文件https://g0v.hackmd.io/O1mGF95cRdumydw-LcaYEA?view

3. 設定gameDB刪除log排程。 

## 機器：
### redis 
- 158 台灣正式redis
    - 192.168.4.158
    - 密碼：bb3235681253211daed5bd068e51ce15
    - Port : 6379
    - 啟動 redis-server /home/pyuser/redis-5.0.7/redis.conf

- 221 香港正式redis
    - 10.0.1.221
    - 密碼：bb3235681253211daed5bd068e51ce15
    - Port : 6379
    - 啟動 redis-server /etc/redis.conf


- Redis 6樓辦公室測試機
    - 192.168.21.220
    - 密碼：1qazxsw2 
    - Port : 6379
    - 啟動 redis-server /home/pyuser/redis-5.0.7/redis.conf

- python 159 測試機
    - 192.168.4.159
    - 密碼：1qazxsw2
    - Port : 6379
    - 啟動 src/redis-server /home/pyuser/redis-5.0.7/redis.conf

## 目前流程圖：
看板開賽：
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7278d8eba3090da646d6aadd645fc8fb.png)

---  
  
後端跟盤流程：
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d620a74ad9c9931c2136954e4781828f.png)

---  
  
一般跟盤同步：
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7b32489279e4db02da58add09013fabb.png)


---

半全場跟盤同步
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fc59bb26b19f69caf4a80e8887c8f65b.png)


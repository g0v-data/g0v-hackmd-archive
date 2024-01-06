jitsi 流水帳
===========

這邊是 Ronny 隨手亂記一些 Jitsi 的筆記

* LAST_N_ENDPOINT 是用來指定最多只會顯示幾個人的影像，-1 表示無限
* 如果使用者因網路問題造成影像無法傳來，可透過 JitsiMeetJS.events.conference.PARTICIPANT_CONN_STATUS_CHANGED 抓他是否有變 inactive ，有時可以透過 detach > attach 的方式修復
* sendEndpointMessage 和 broadcastEndpointMessage 要在 JitsiMeetJS.events.conference.DATA_CHANNEL_OPENED 事件後才能呼叫，在 JitsiMeetJS.events.conference.CONFERENCE_JOINED 之後呼叫可能會失敗
    * 房間內成員至少要有兩人 data channel 才會是 opened 的，只有一人的話 sendEndpointMessage, broadcastEndpointMessage 都會失敗
* 使用官方 jitsi 時，options.bosh 後面必須要加 ?room={房間名} ，因為他有 load balancer ，不加的話可能會進到不同伺服器造成看不到別人
* 需要 websocket 支援的話，prosody 要在 0.10 版以上，並且需要設定 nginx
* 一個 JitsiMeetJS.JitsiConnection 只能連一個房間，需要同時連不同房間要建立多個 JitsiConnection
* 在瀏覽者未做任何點擊動作前，瀏覽器不允許 js 在 audio tag 做 play 動作，因此需要提示使用者要點一下螢幕任何地方
* room.participantConnectionStatus.connectionStatusMap 可以抓到目前其他參與者的連線狀態，如果是 inactive 的話，可以用 selectParticipant(id) 把他再啟動
* room.selectParticipants 可以一次指定多人高畫質
* JitsiMeetJS.events.conference.PARTICIPANT_PROPERTY_CHANGED
* 有時會有頻道一直吐  Bridge Channel send: no opened channel 的問題，這是 prosody 單一頻道問題
    * 還不知道怎麼解決，只能換個房間名?
    * 重開 videobridge
    * 把 openBridgeChannel: 'websocket' 改成 openBridgeChannel: true
* 如果遇到螢幕分享分享音訊時聲音會斷斷續續，可以試試看把 LogLevel 設成 INFO (很奇怪的解法 QQ)
* broadcastEndpointMessage 和 sendEndpointMessage 若送內容過大的資料，會造成 Bridge Channel send: no opened channel 並且接下來不會再收到任何更新（user_joined, user_left ... )，所以要避免送過大的資料
* 如果發現畫質持續很差不會更新，請檢查看看是否有「Bridge Channel send: no opened channel」的錯誤訊息，如果發生 js error 可能導致之後 selectParticipant 函式失效。
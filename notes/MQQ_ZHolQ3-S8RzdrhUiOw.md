# IDystopia API Server

API: https://pingtung-hao-305236.middle2.me/api

* POST /register
    * 回傳 {"token": "foo"} ，client 端需要記下 token 重覆使用，所有動作都需要加上 &token={token} 才是有效動作
* GET /check_token?token={token}
    * 回傳 {"ok": true / false}
* POST /inc?key=[key]
    * 回傳 {"value": 123} ，將 key 的 counter 累加並會傳值
* GET /getc?key=[key]
    * 回傳 {"value": 123} ，回傳 key 的 counter 值
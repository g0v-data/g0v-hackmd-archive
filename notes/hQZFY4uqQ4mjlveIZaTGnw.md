# 鄉民看電視 API

* /api/list 列出所有的新聞片段（每小時），以及有輸入過的內容
* /api/section/{channel}/{time} 回傳該小時內經過影像辨識後切割的結果
* /index/result/{channel}/{time}/{input_id} 某個輸入結果的 JSON 格式
* /index/result/{channel}/{time}/{input_id}?format=csv 某個輸入結果的 CSV 格式

* 回報
    * POST /api/input/{channel}/{time}
        * input:
            * from: 
            * score: 分數
            * csv: CSV 成果
            * data: 自己的過程 data
        * example: {"from":"v2","score":90,"csv":"start,end,duration,type,title\n1,12,12,新聞,商辦大樓當掩護！　洗錢集團4個月獲利「破千萬」(fWGHJBQnU18)","data":{"foo":"bar"}}
        * curl -XPOST -d '{"from":"v2","score":90,"csv":"start,end,duration,type,title\n1,12,12,新聞,商辦大樓當掩護！　洗錢集團4個月獲利「破千萬」(fWGHJBQnU18)","data":{"foo":"bar"}}'  https://tvlogger.g0v.ronny.tw/api/input/ctitv/2019050612
"}
        * output:
            * input_id
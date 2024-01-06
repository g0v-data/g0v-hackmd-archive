### Ascare 關懷回報Bot



### 選單（RichMenu）功能
* web
  - 取得選單：GetPersonRichMenuFromWeb(w http.ResponseWriter, r *http.Request)


### WebSocket 設計
* Web - Client 間傳遞訊息格式
```
// HTTP log message
type HTTPMessagePackage struct {
   RemoteAddr   string          `json:"remoteAddr,omitempty"`
   Status       string          `json:"status,omitempty"`
   Proto        string          `json:"proto,omitempty"`
   Url          string          `json:"url,omitempty"`
}

type MessagePackage struct {
   Action       string                  `json:"action"`
   TimeStamp    string                  `json:"timestamp"`
   Message      string                  `json:"message"`
   PersonInfo   *Person                 `json:"person,omitempty"`
   Http         HTTPMessagePackage      `json:"http,omitempty"`
}
```

* Action
```
log
cronjob
notify
```
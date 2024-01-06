# SZ admin api

## Action 53
- subAction 1 ※ 取得所有的語言
    - *Request*
        ```json
        {
          "action": "53",
          "subAction": "1"
        }
        ```
    - *Response*
        ```json
        {
          "status": "0000",
          "LanguageList": [
            {
              "id": 1,
              "code": "zh"
            },
            {
              "id": 2,
              "code": "en"
            }
          ]
        }
        ```

- subAction 2 ※ 新增語言
    - *Request*
        ```json
        {
          "action": "53",
          "subAction": "2",
          "languageCode": "ja"
        }
        ```
        >languageCode ※ 語言代碼 ISO 639-1 ※英語：en 日文：ja
        https://zh.wikipedia.org/zh-tw/ISO_639-1
    - *Response*
        ```json
        {
          "status": "0000",
          "LanguageList": [
            {
              "id": 1,
              "code": "zh"
            },
            {
              "id": 2,
              "code": "en"
            },
            {
              "id": 3,
              "code": "ja"
            }
          ]
        }
        ```
- subAction 3 ※ 修改語言
    - *Request*
        ```json
        {
          "action": "53",
          "subAction": "3",
          "languageId": "3"
          "languageCode": "aa"
        }
        ```
        >languageId ※ DB 自動產出的 Id
    - *Response*
        ```json
        {
          "status": "0000",
          "LanguageList": [
            {
              "id": 1,
              "code": "zh"
            },
            {
              "id": 2,
              "code": "en"
            },
            {
              "id": 3,
              "code": "aa"
            }            
          ]
        }
        ```
- subAction 4 ※ 刪除語言
    - *Request*
        ```json
        {
          "action": "53",
          "subAction": "4",
          "languageId": "3"
        }
        ```
        >languageId ※ DB 自動產出的 Id
    - *Response*
        ```json
        {
          "status": "0000",
          "LanguageList": [
            {
              "id": 1,
              "code": "zh"
            },
            {
              "id": 2,
              "code": "en"
            }        
          ]
        }
        ```
        
## Action 54
- subAction 1 ※ 取得所有遊戲設定支援的語言
    - *Request*
        ```json
        {
          "action": "54",
          "subAction": "1"
        }
        ```
    - *Response*
        ```json
        {
          "status": "0000",
          "GameLanguageSetting": [
            {
              "gameId": 1001,
              "languageId": 1
            },
            {
              "gameId": 1001,
              "languageId": 2
            },
            {
              "gameId": 1002,
              "languageId": 1
            },
                    .
                    .
                    .
            {
              "gameId": 4001,
              "languageId": 1
            },
            {
              "gameId": 4001,
              "languageId": 2
            }
          ]
        }    
        ```
- subAction 2 ※ (無)
- subAction 3 ※ 修改遊戲支援語言
    - *Request*
        ```json
        {
          "action": "54",
          "subAction": "3",
          "gameIdListObj": [1001, 4001]
          "languageIdListObj": [2,3]
        }
        ```
    - *Response*
        ```json
         {
          "status": "0000",
          "GameLanguageSetting": [
            {
              "gameId": 1001,
              "languageId": 2
            },
            {
              "gameId": 1001,
              "languageId": 3
            },
            {
              "gameId": 1002,
              "languageId": 1
            },
                    .
                    .
                    .
            {
              "gameId": 4001,
              "languageId": 2
            },
            {
              "gameId": 4001,
              "languageId": 3
            }
          ]
        }
        ```
        
## Action 55

# line chatbox
- 使用gemini取得api key 
![](https://g0v.hackmd.io/_uploads/r1fFSsS-xe.png)

![](https://g0v.hackmd.io/_uploads/HJlyFBjrblx.png)

- 使用gemini進行對話
![](https://g0v.hackmd.io/_uploads/rJK2rsrWle.png)
![](https://g0v.hackmd.io/_uploads/BJs2rjS-ex.png)
![](https://g0v.hackmd.io/_uploads/S1p2BiS-ll.png)
```
#!/bin/bash
set -e -E

GEMINI_API_KEY="$GEMINI_API_KEY"
MODEL_ID="gemini-2.0-flash"
GENERATE_CONTENT_API="streamGenerateContent"

cat << EOF > request.json
{
    "contents": [
      {
        "role": "user",
        "parts": [
          {
            "text": "請推薦我台南美食"
          },
        ]
      },
      {
        "role": "model",
        "parts": [
          {
            "text": "台南美食真的太多了！為了讓你更好選擇，我會先依據你的需求推薦，請告訴我：\n\n1.  **你想吃什麼類型的美食？** 例如：小吃、甜點、海鮮、特色餐廳等等。\n2.  **你的預算大概是多少？**\n3.  **你喜歡排隊嗎？** 有些名店需要排隊，我可以推薦不用排隊或排隊時間較短的店家。\n4.  **你偏好古早味、文青風，還是其他風格？**\n5.  **你想要在哪個區域吃？** (例如：中西區、安平區、等等)\n\n如果以上問題你一時沒有答案，沒關係，我先推薦一些經典且廣受歡迎的台南美食給你參考：\n\n**小吃類：**\n\n*   **牛肉湯:**\n    *   文章牛肉湯：老字號，湯頭濃郁，肉質鮮嫩。\n    *   六千牛肉湯：凌晨排隊名店，湯頭清甜。\n    *   旗哥牛肉湯：24小時營業，隨時都能吃到。\n*   **滷肉飯:**\n    *   小南碗粿：滷肉飯搭配碗粿，絕佳組合。\n    *   大菜市包仔祿：老店，口味傳統。\n    *   矮仔成蝦仁飯：滷汁香濃，蝦仁飯也值得一試。\n*   **蝦捲/虱目魚:**\n    *   周氏蝦捲：觀光客必吃，口味穩定。\n    *   王氏魚皮：虱目魚料理專賣店，魚皮湯鮮美。\n    *   阿堂鹹粥：料多實在，早餐首選。\n*   **碗粿/米糕:**\n    *   小南碗粿：碗粿口感Q彈，搭配滷肉飯更棒。\n    *   富盛號碗粿：歷史悠久，口味傳統。\n    *   米糕城：米糕香氣十足，料也豐富。\n*   **麵類:**\n    *   度小月擔仔麵：百年老店，湯頭鮮甜。\n    *   阿龍意麵：在地人推薦，意麵Q彈。\n\n**甜點類：**\n\n*   **豆花:**\n    *   同記安平豆花：傳統豆花，配料豐富。\n    *   茂記黑豆花大王：黑豆花香氣濃郁。\n*   **冰品:**\n    *   莉莉水果店：新鮮水果冰，消暑聖品。\n    *   泰成水果店：哈密瓜冰是招牌。\n*   **布丁:**\n    *   依蕾特布丁：口感滑順，口味多樣。\n    *   紅磚布丁：焦糖香氣濃郁。\n\n**其他：**\n\n*   **棺材板:** 赤崁棺材板：酥炸吐司搭配濃稠內餡，獨特風味。\n*   **鱔魚意麵:** 阿江鱔魚意麵：鑊氣十足，酸甜夠味。\n*   **鹹粥:** 阿堂鹹粥：料多實在，早餐首選。\n\n**提醒：**\n\n*   台南美食口味偏甜，不習慣的人可以事先告知店家調整。\n*   建議可以多安排幾天行程，才能品嚐到更多台南美食。\n*   善用Google Maps，搜尋附近的美食，並參考網友評價。\n\n等你告訴我更詳細的需求，我就可以給你更精準的推薦喔！  祝你旅途愉快，吃得開心！\n"
          },
        ]
      },
      {
        "role": "user",
        "parts": [
          {
            "text": "INSERT_INPUT_HERE"
          },
        ]
      },
    ],
    "generationConfig": {
      "responseMimeType": "text/plain",
    },
}
EOF

curl \
-X POST \
-H "Content-Type: application/json" \
"https://generativelanguage.googleapis.com/v1beta/models/${MODEL_ID}:${GENERATE_CONTENT_API}?key=${GEMINI_API_KEY}" -d '@request.json'

```
- 丟到[hoppscotch](https://hoppscotch.io/)
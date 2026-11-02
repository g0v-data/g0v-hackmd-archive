curl -v -X POST 'https://api.line.me/v2/bot/message/push' \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer {channel access token}' \
  -d '{
    "to": "{user ID}",
    "messages": [
      {
        "type": "text",
        "text": "您的餐點已完成，請前來取餐！"
      }
    ]
  }'
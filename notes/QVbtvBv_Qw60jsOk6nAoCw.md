Order 中文說明

正在修正中...不是final version

我晚上繼續打 結構有變

order state:

0. arrearage
1. unpaid
2. paid
3. intransit
4. cancel


結構如下:
```
[
  {
    "order_id": "538f777f-33e6-4284-8de8-8e8899065354",
    "created_at": "2021-05-13T21:02:00.713285+08:00",
    "updated_at": "2021-05-13T21:02:00.713285+08:00",
    "order_number": "202105130001",
    "owner_id": "dff59203-b7f7-4e3b-ba01-378204bc53b0",
    "delivery_location": "台灣",
    "delivery_method": {
      "id": 0,
      "price": "0"
    },
    "products": [
      {
        "product_info": {
          "ID": "718fa555-b4ec-4b15-9a43-30de0e7b8890",
          "product_number": "XXXXXXXXX",
          "name": "product name2",
          "description": "test",
          "images": [
            "2278ed87-8552-47ab-a942-0c427f26e4d1"
          ],
          "specifications": [
            {
              "id": 9,
              "name": "product1",
              "description": "des1"
            }
          ]
        },
        "id": "",
        "product_specifications": [
          {
            "id": 9,
            "amount": 20,
            "price": "4000"
          }
        ]
      }
    ],
    "payment_way": "atm",
    "payment_detail": {
      "atm": {
        "bank": "中國信託銀行(822)",
        "branch": "中正分行",
        "name": "王曉明",
        "account": "1234567890123456"
      },
      "credit_card": {
        "name": "",
        "number": "",
        "ExpiryDate": "",
        "ccv": ""
      }
    },
    "orderer": {
      "name": "王曉明",
      "phone_number": "0900123456",
      "address": "台北市中山區西路43巷5弄10樓之7"
    },
    "receiver": {
      "name": "王曉明",
      "phone_number": "0900123456",
      "address": "台北市中山區西路43巷5弄10樓之7"
    },
    "total_price": "4100",
    "state": 0
  }
]
```
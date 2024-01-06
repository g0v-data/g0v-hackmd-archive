# juancash 客戶端 API

## flow - 會員註冊/登入

### 會員註冊/登入

https://api.juanwallet.net:443/v1/version/getVersion?versionCode=20230901&type=0


https://api.juanwallet.net:443/v1/user/loginSms

#### Request

```
{
	"deviceId":"d3f8435b-7d77-4708-a186-9989f6c9b4a4",
	"deviceName":"V2204",
	"mobile":"639121231231548"
}
```

#### Response

```

{
	"code":0,
	"desc":null,
	"customize":null,
	"dialogBoxType":"COMMON",
	"dialogBox":null,
	"data":null,
	"success":true
}
```
https://api.juanwallet.net:443/v1/user/loginOrRegister

#### Request

```
{
	"code":"789789",
	"deviceId":"d3f8435b-7d77-4708-a186-9989f6c9b4a4",
	"deviceName":"V2204",
	"mobile":"639121231231548",
	"mobilePrefix":"63",
	"userType":1,
	"version":"20230901"
}
```

#### Response

```
{
"code":0,
	"desc":null,
	"customize":null,
	"dialogBoxType":"COMMON",
	"dialogBox":null,
	"data":{
		"userVO":{
			"id":8132,
			"name":"",
			"state":0,
			"mobile":"639121231231548",
			"quickPwd":"",
			"firstName":"",
			"middleName":"",
			"lastName":"",
			"suffix":"",
			"fullName":"",
			"email":"",
			"sex":0,
			"country":"",
			"birthDay":null,
			"permanentAddress":null,
			"token":"2b053acfa0c8ae5664997b54365d14f5",
			"regTime":1702298877000,
			"finalLoginTime":1702306620618,
			"ip":"58.97.163.42",
			"photoUrl":null,
			"photoState":0,
			"validPhotoUrl":null,
			"uploadPhotoTime":null,
			"uploadCount":null,
			"regSource":"EMI",
			"riskLevel":0,
			"customerDueDiligence":0,
			"agent":false,
			"agentNeedMoney":1000.0,
			"invideCode":null,
			"inideCodeUrl":null,
			"userType":1,
			"hasShop":false,
			"certificationStatus":1,
			"countryVersion":null,
			"mobilePrefix":"63",
			"vMobile":"9121231231548",
			"preRegisterInviteCode":null,
			"accountCertifiedShopId":0,
			"accountCertifiedShopApplyTime":null,
			"accountCertifiedShopRefuseMark":null,
			"accountCertifiedShopHandleTime":null,
			"regTimeFormat":1702298877000,
			"phipippines":false,
			"birthDayFormat":null,
			"finalLoginTimeFormat":1702306620618
		},
		"accountVO":{
			"uid":8132,
			"level":1,
			"savePayPwd":false,
			"money":0.0,
			"errorTimes":5,
			"banPay":false,
			"banTime":null,
			"pubKey":"MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCEYTMR8h0tqjYEVv11/7qwBJBpBQn828bDuOwPELSpBikvygOYnSY+W2pXfpA6vy7hXLkTVjP4ipnZtoLQ+B04W6fyMDNgwFpzNeHuS8P1+Hexsla5Zhi0Bgl6hoRZKjb4xOUtG4Ws/IOZ69yT/4iKU2tMjbGrNIXcPThaEEFW0wIDAQAB",
			"salt":"907B2E898C0557F0",
			"receiptCodeUrl":"http://pay.juanwallet.net/merchant?ac=scheme&paycode=anVhbmNhc2g6Ly9xcmNvZGUvZGVhMTM5NTYzMTMzM2NjYWY1Yjk0OWE4NTAzMjMwMGI=",
			"freeWithdrawAmount":0.0
		}
	},
	"success":true
}
```

---

## flow - 初始化會員註冊設置


### 取得用戶資訊

https://api.juanwallet.net:443/v1/user/info


#### request
```
{
	"birthDay":"2005-12-11",
	"country":"Philippines",
	"email":"121111113@gmail.com",
	"firstName":"1",
	"lastName":"3",
	"middleName":"2",
	"permanentAddress":"helloworld",
	"sex":0,
	"suffix":"4",
	"token":"2b053acfa0c8ae5664997b54365d14f5"
}
```


### 初始化付款密碼

> 客戶端加密有金鑰洩漏的風險

https://api.juanwallet.net:443/v1/user/initPayPwd?d=AkU8M49n7oPlJf5dvhfCfTy%2B3w2pQS6txZg1YS1gBZpMRns%2Bs2DqkKy0y8R1UWQXCzTn9ytgOOQ4yJA8shllwvAW3i65KAkfV1CPhyFhRHYGl9ppPuCxDm2mg5bHbk505qBHWqemdr6cUC0WuQ8zOUaKbiRPGxiXUmgdK6I8Tg0%3D


### 取得版本?

https://api.juanwallet.net:443/v1/version/getVersion?versionCode=20230901&type=0

### 快速設置密碼

> 有加密的風險

#### request

https://api.juanwallet.net:443/v1/user/quickPwd
```
{
	"qpwd":"1de25345cad15d1c0ee50fd7ef9f87b1"
}
```
https://api.juanwallet.net:443/v1/version/getVersion?versionCode=20230901&type=0

### 取得頁面訊息?

https://api.juanwallet.net:443/v1/message/pageMessageRecord?pageNum=0&pageSize=20

### 取得廣告
https://api.juanwallet.net:443/v1/advertising/getAdvertisingPageListNew?pageNum=1&pageSize=20&strKey=HOMERECOMMEND

https://api.juanwallet.net:443/v1/advertising/getAdvertisingPageListNew?pageNum=1&pageSize=20&strKey=e8dfc465-c2f4-40a1-a963-c4c0a4969d12

https://api.juanwallet.net:443/v1/advertising/getAdvertisingPageListNew?pageNum=1&pageSize=2&strKey=HOMEDISCOUNT

### 取得用戶資訊
https://api.juanwallet.net:443/v1/user/info?version=20230901

### 取得文章列表
https://api.juanwallet.net:443/v1/client/findArticleInfoList

#### request
```
{
	"pageNumber":1,
	"pageSize":3,
	"strKey":"LifeGuide",
	"userId":8132
}
```

### 取得電話資料?
https://api.juanwallet.net:443/v2/applicationCenter/getNewProjectPhoneDataALL?proItem=ALL

### ???
https://api.juanwallet.net:443/v1/applicationCenter/getProjectItemListAndParamsByKeyStr?keyStr=ALL

### 取得廣告
https://api.juanwallet.net:443/v1/advertising/getAdvertisingPag

https://api.juanwallet.net:443/v1/advertising/getAdvertisingPag

https://api.juanwallet.net:443/v1/advertising/getAdvertisingPag

https://api.juanwallet.net:443/v3/page/getPageByType?pageType=HOME&area=PHILIPPINES&versionCode=2.1

---


## flow - 充值(地下充值)


### 查詢充值列表

[POST] https://api.juanwallet.net:443/v3/trade/getCashInPageVO


#### request

```
{
	"area":"PHILIPPINES",
	"pageNum":1,
	"pageSize":10,
	"payType":0,
	"uid":0,
	"versionCode":"2.1"
}
```




### 取得最小存取款金額

[POST] https://api.juanwallet.net:443/v1/juancash/withdraw/getMinWithdrawAmountNew

### 取得所有充值銀行卡

[POST] https://api.juanwallet.net:443/v1/remittance/listAllCard


### 提交充值申請

[POST] https://api.juanwallet.net:443/v1/remittance/commitApply


# 程式 alpaca
## 登入變數
```
api_key = "PKR70V2JWLC0USZNGQX7"
secret_key = "CbIa4NCgAExbkl5LbKNMzHxnxU8F0yu0ASPHQ9K8"
end_point = "https://paper-api.alpaca.markets/v2"

#### We use paper environment for this example ####
paper = True # Please do not modify this. This example is for paper trading only.
####

# Below are the variables for development this documents
# Please do not change these variables
trade_api_url = None
trade_api_wss = None
data_api_url = None
stream_data_wss = None
```

## 需要的庫
```
import json
from datetime import datetime, timedelta
from zoneinfo import ZoneInfo

import alpaca
from alpaca.data.live.stock import *
from alpaca.data.historical.stock import *
from alpaca.data.requests import *
from alpaca.data.timeframe import *
from alpaca.trading.client import *
from alpaca.trading.stream import *
from alpaca.trading.requests import *
from alpaca.trading.enums import *
from alpaca.common.exceptions import APIError

# to run async code in jupyter notebook
import nest_asyncio
nest_asyncio.apply()

#確認版本
alpaca.__version__
```

## 交易帳號
```
trade_client = TradingClient(api_key=api_key, secret_key=secret_key, paper=paper, url_override=trade_api_url)

#確認帳號內容
acct = trade_client.get_account()

#確認帳號配置
acct_config = trade_client.get_account_configurations()

# set account configuration
# ref. https://docs.alpaca.markets/reference/patchaccountconfig-1
req = acct_config
req.fractional_trading = not req.fractional_trading # toggle fractional trading
acct_config_new = trade_client.set_account_configurations(req)
display(acct_config_new)

# revert changes
req = acct_config_new
req.fractional_trading = not req.fractional_trading # toggle fractional trading
acct_config_reverted = trade_client.set_account_configurations(req)
display(acct_config_reverted)

# get list of assets which are us_equity (default), active, and in NASDAQ
# ref. https://docs.alpaca.markets/reference/get-v2-assets-1
req = GetAssetsRequest(
  # asset_class=AssetClass.US_EQUITY,  # default asset_class is us_equity
  status=AssetStatus.ACTIVE,
  exchange=AssetExchange.NASDAQ,
)
assets = trade_client.get_all_assets(req)
assets[:2]
```
# 程式 alpaca
## 參考網址
https://github.com/alpacahq/alpaca-backtrader-api/tree/master/sample
https://github.com/alpacahq/alpaca-py/tree/master/examples
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

#輸出範例與解釋
{   'account_blocked': False, 帳戶是否被封鎖
    'account_number': 'PA30PGR9YG8Q', 您的Alpaca帳戶號碼
    'accrued_fees': '0', 累計的費用
    'buying_power': '200000', 可用於買入的資金總額
    'cash': '100000', 現金餘額
    'created_at': datetime.datetime(2023, 8, 26, 1, 24, 11, 658202, tzinfo=TzInfo(UTC)), 帳戶創建時間
    'crypto_status': <AccountStatus.ACTIVE: 'ACTIVE'>, 加密貨幣交易狀態
    'currency': 'USD', 帳戶使用的貨幣
    'daytrade_count': 0, 當日交易次數
    'daytrading_buying_power': '0', 日內交易可用資金
    'equity': '100000', 帳戶總權益
    'id': UUID('b312a20a-dc20-4121-a8e6-2bfafe25b3d1'), 帳戶的唯一識別碼
    'initial_margin': '0', 初始保證金
    'last_equity': '100000', 上一個交易日結束時的權益
    'last_maintenance_margin': '0', 上一個交易日的維持保證金
    'long_market_value': '0', 多頭倉位的市值
    'maintenance_margin': '0', 維持保證金
    'multiplier': '2', 槓桿倍數
    'non_marginable_buying_power': '100000', 不可用於保證金交易的買入力
    'options_approved_level': 2, 期權交易批准級別
    'options_buying_power': '100000', 期權交易可用資金
    'options_trading_level': 2, 期權交易級別
    'pattern_day_trader': False, 是否被標記為模式日交易者
    'pending_transfer_in': None, 待入帳的轉入金額
    'pending_transfer_out': None, 待出帳的轉出金額
    'portfolio_value': '100000', 投資組合總價值
    'regt_buying_power': '200000', 根據Regulation T計算的可用買入力
    'short_market_value': '0', 空頭倉位的市值
    'shorting_enabled': True, 是否啟用做空功能
    'sma': '100000', 特別備忘錄帳戶餘額
    'status': <AccountStatus.ACTIVE: 'ACTIVE'>, 帳戶狀態
    'trade_suspended_by_user': False, 用戶是否暫停了交易
    'trading_blocked': False, 交易是否被阻止
    'transfers_blocked': False} 轉帳是否被阻止

```
```
#確認帳號配置
acct_config = trade_client.get_account_configurations()

#範例輸出
{   'dtbp_check': <DTBPCheck.ENTRY: 'entry'>,
    'fractional_trading': True, 是否允許零股交易
    'max_margin_multiplier': '4', 最大保證金乘數
    'max_options_trading_level': None, 最高期權交易級別
    'no_shorting': False, 是否禁止做空
    'pdt_check': <PDTCheck.ENTRY: 'entry'>,
    'ptp_no_exception_entry': False, 是否禁止例外入場
    'suspend_trade': False, 是否暫停交易
    'trade_confirm_email': <TradeConfirmationEmail.ALL: 'all'>} 交易確認郵件設置

#更改帳號配置
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
```

```
# get list of assets which are us_equity (default), active, and in NASDAQ
# ref. https://docs.alpaca.markets/reference/get-v2-assets-1
req = GetAssetsRequest(
  # asset_class=AssetClass.US_EQUITY,  # default asset_class is us_equity
  status=AssetStatus.ACTIVE,
  exchange=AssetExchange.NASDAQ,
)
assets = trade_client.get_all_assets(req)
assets[:2]

#範例輸出
[{   'asset_class': <AssetClass.US_EQUITY: 'us_equity'>, 資產類別
     'attributes': [], 
     'easy_to_borrow': False, 是否容易借入
     'exchange': <AssetExchange.NASDAQ: 'NASDAQ'>, 交易所
     'fractionable': False, 是否可進行零股交易
     'id': UUID('77af178f-0368-4585-b342-acf8e29a11ea'),
     'maintenance_margin_requirement': 100.0, 維持保證金要求
     'marginable': False, 是否可用於保證金交易
     'min_order_size': None, 最小訂單大小
     'min_trade_increment': None, 最小交易增量
     'name': 'Shuttle Pharmaceuticals Holdings, Inc. Common Stock', 資產名稱
     'price_increment': None, 價格增量
     'shortable': False, 是否可做空
     'status': <AssetStatus.ACTIVE: 'active'>, 資產狀態
     'symbol': 'SHPH', 股票代碼
     'tradable': False},是否可交易
     
 {   'asset_class': <AssetClass.US_EQUITY: 'us_equity'>,
     'attributes': [],
     'easy_to_borrow': False,
     'exchange': <AssetExchange.NASDAQ: 'NASDAQ'>,
     'fractionable': False,
     'id': UUID('21696e64-2e84-41de-8c88-dbf542d72cef'),
     'maintenance_margin_requirement': 100.0,
     'marginable': False,
     'min_order_size': None,
     'min_trade_increment': None,
     'name': 'ICZOOM Group Inc. Class A Ordinary Shares',
     'price_increment': None,
     'shortable': False,
     'status': <AssetStatus.ACTIVE: 'active'>,
     'symbol': 'IZM',
     'tradable': False}]
```

## 下單
```
symbol = "SPY"

#簡易下單
req = MarketOrderRequest(
    symbol = symbol, #購買標的
    # 則一
    # qty = 5.5, #購買多少單位
    # notional = 1.11, #購買多少金額
    limit_price = 550.25, #限價單
    side = OrderSide.BUY, #買單
    type = OrderType.MARKET, #型態(市價單)
    time_in_force = TimeInForce.DAY, #訂單有效期限
    stop_price = 600 #結單點位
    take_profit = TakeProfitRequest(limit_price=600),#設置止盈位置
    stop_loss = StopLossRequest(stop_price=300)#設置止損位置
)
res = trade_client.submit_order(req)



```

## 交易策略
https://medium.com/@ioi75UT/cta%E9%A1%9E%E6%8C%87%E6%A8%99%E5%B0%8F%E7%A0%94%E7%A9%B6-%E5%8D%8A%E7%A5%9E%E5%8D%8A%E7%9B%AE%E5%A4%8F%E7%AD%96%E7%95%A5-95-%E5%8B%9D%E7%8E%87-879676d80a56


## Basic
1. Package: backtrader
- !pip install backtrader backtrader_plotting: 主要安裝包
```python
    import backtrader as bt
    from datetime import datetime
    import matplotlib
    # 互動圖表
    from backtrader_plotting import Bokeh
    # Tradimo 或 Blackly
    from backtrader_plotting.schemes import Blackly 
```

```python
    %matplotlib inline 
    cerebro = bt.Cerebro() # 這是運行環境
    cerebro.broker.setcash(1e5)# 平台手續費
```


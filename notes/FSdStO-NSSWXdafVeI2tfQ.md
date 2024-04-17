# Tourmap重構事項

## Addition

### AdditionIntervalPrice

![image](https://files.furthersoftware.com.tw/assets/Tourmap/重構/additionIntervalPrice.png)

#### manager
```c#
AdditionIntervalPriceManager //目前沒有新增任何額外方法，但須補上check和set方法
```

#### repository
```c#
IAdditionIntervalPriceRepository //目前沒有新增任何額外方法，不用調整
```

#### provider
```c#
//計算該附加服務今天是多少錢，非同步版本多做的是get的事情
public interface IAdditionIntervalPriceCalculateProvider{
    
    Task<decimal> CalculatePriceAsync(Guid additionId, DateTime date);

    decimal CalculatePrice(List<AdditionIntervalPrice> additionIntervalPrices, DateTime date);
}
```

### AdditionOrder

![image](https://files.furthersoftware.com.tw/assets/Tourmap/重構/additionOrder.png)

#### manager
```c#
AdditionOrderManager //目前沒有新增任何額外方法，但須補上check和set
```

#### repository
```c#
IAdditionOrderRepository //目前沒有新增任何額外方法，不用調整
```

#### Aggregates
```c#
//改用設定小表的方式做調整
public class AdditionOrderForBrowse
{
    public AdditionOrder AdditionOrder { get; set; } = null!;
    public List<AdditionOrderLine> AdditionOrderLines { get; set; } = new();
}
```
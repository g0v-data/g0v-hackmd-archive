# Tourmap重構事項

## Addition

### AdditionIntervalPrice

![image](https://files.furthersoftware.com.tw/assets/Tourmap/重構/additionIntervalPrice.png)

#### Manager
```c#
AdditionIntervalPriceManager //目前沒有新增任何額外方法，但須補上check和set方法
```

#### Repository
```c#
IAdditionIntervalPriceRepository //目前沒有新增任何額外方法，不用調整
```

#### Provider
```c#
//計算該附加服務今天是多少錢，非同步版本多做的是get的事情
public interface IAdditionIntervalPriceCalculateProvider{
    
    Task<decimal> CalculatePriceAsync(Guid additionId, DateTime date);

    decimal CalculatePrice(List<AdditionIntervalPrice> additionIntervalPrices, DateTime date);
}
```

### AdditionOrder

![image](https://files.furthersoftware.com.tw/assets/Tourmap/重構/additionOrder.png)

#### Manager
```c#
AdditionOrderManager //目前沒有新增任何額外方法，但須補上check和set

//基本方法補上check和set
public class AdditionOrderLineManager{
    //這是把所有綠色類別屬性打平的create方法，目前沒有使用後續刪除
    Task<AdditionOrderLine> CreateAsync(Guid additionOrderId,
    Addition.Additions.Addition addition, DateTime usedDate, string primaryCategoryName,
    string secondaryCategoryName, string productSkuName, string primarySpecValue,
    string? secondarySpecValue, string primaryTimeSpecValue, string primaryDateSpecValue,
    string? secondaryTimeSpecValue, string? secondaryDateSpecValue, AdditionOrderLineAmount amount,
    string customerRemarkValue, Guid? tenantId)
}
```

#### Repository
```c#
IAdditionOrderRepository //目前沒有新增任何額外方法，不用調整

IAdditionOrderLineRepository //目前沒有新增任何額外方法，不用調整
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

### Addition

![image](https://files.furthersoftware.com.tw/assets/Tourmap/重構/addition-01.png)

![image](https://files.furthersoftware.com.tw/assets/Tourmap/重構/addition-02.png)

#### Manager

```c#
//基本方法補上check和set
public class AdditionManager{

    //為了對參數做檢查新增的create方法，改用原本的create
    Task<Addition> CreateAsync(
           Guid? coverImageId,
           int index,
           string type,
           decimal handlingFeeRatio,
           string displayName,
           Guid additionCategoryId,
           AdditionSpec primarySpec,
           AdditionSpec secondarySpec,
           AdditionTimeSpec primaryTimeSpec,
           AdditionTimeSpec secondaryTimeSpec,
           AdditionSchedule schedule,
           AdditionAmount amount,
           AdditionCustomerRemark cutomerRemark,
           AdditionIntroductions introductions);
           
    //上傳封面圖片，如果不帶檔案則刪除
    Task<Addition> UploadImgAsync(Addition addition, IRemoteStreamContent? inputStream = null)
    
    //上傳輪播圖
    Task<Addition> AddBannerAsync(Addition addition, IRemoteStreamContent? inputStream = null);
    
    //刪除輪播圖
    Task<Addition> DeleteBannerAsync(Addition addition, Guid mediaId);
    
    //組出樹，目前沒有使用，待刪除
    Task<Aggregates.AdditionTree> GetAdditionTreeAsync(DateTime useDate, Guid productGuid);
}
```
#### Repository

```c#
IAdditionRepository //目前沒有新增任何額外方法，不用調整
```

#### Aggregates

```c#
//目前沒有使用待刪除
public class AdditionTree
{
	public string Date { get; set; }
	public List<object> AvailableAddition { get; set; } = new();
}
```

### AdditionSales

#### R
```c#
//破棄泛行版本
public partial interface IAdditionSaleDefinitionRepository<T,U>:IAdditionRepository<T,Guid>
    where T : AdditionSaleDefinitionBase
    where U : Entity<Guid>
{
    //搬到原本的Repository
    Task<T> FindByOwnerIdAsync(Guid ownerId, CancellationToken cancellationToken = default);
    //搬到原本的Repository
    Task<T> GetByOwnerIdAsync(Guid ownerId, CancellationToken cancellationToken = default);
    //破棄
    Task<Aggregates.AdditionSaleDefinitionForBrowse<T, U>> GetForViewAsync(Guid id, CancellationToken cancellationToken = default);
    //破棄
    Task<Aggregates.AdditionSaleDefinitionForBrowse<T, U>> FindByOwnerIdForViewAsync(Guid ownerId, CancellationToken cancellationToken = default);
    //破棄
    Task<Aggregates.AdditionSaleDefinitionForBrowse<T, U>> GetByOwnerIdForViewAsync(Guid ownerId, CancellationToken cancellationToken = default);
    //破棄
    Task<List<Aggregates.AdditionSaleDefinitionForBrowse<T, U>>> GetListForViewAsync(
    ISpecification<Aggregates.AdditionSaleDefinitionForBrowse<T, U>>? specification = null,
    string? sorting = null,
    int maxResultCount = int.MaxValue,
    int skipCount = 0,
    CancellationToken cancellationToken = default);
    //破棄
    Task<long> GetCountForViewAsync(
    ISpecification<Aggregates.AdditionSaleDefinitionForBrowse<T, U>> specification,
    CancellationToken cancellationToken = default);

    /// <summary>
    /// AdditionParameters是否有任何資料 (不分類型)
    /// </summary>
    /// <returns></returns>
    //破棄
    Task<bool> ExistsAnyParameterDataAsync();
}
```



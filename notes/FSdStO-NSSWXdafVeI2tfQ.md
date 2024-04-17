# Tourmap重構事項

## Addition

### AdditionCategory

#### Manager

```c#
//基本方法補上check和set
public class AdditionCategoryManager{
    /// <summary>
    /// 上傳圖片
    /// </summary>
    /// <param name="additionCategory"></param>
    /// <param name="inputStream">如果為null代表刪除</param>
    /// <returns></returns>
    Task UploadCoverImageAsync(AdditionCategory additionCategory, IRemoteStreamContent? inputStream = null);
    
    //待破棄
    List<Aggregates.AdditionCategoryTree> BuildTreeAdditionCategory(List<Aggregates.AdditionCategoryWithTree> nodes);
    
    //待破棄
    List<AdditionCategory> FindAdditionUseCategoryRecursive(List<AdditionCategory> allCategory, List<Guid> additionByCategoryIds);
}
```


#### Repository

```c#
public interface IAdditionCategoryRepository{
    //待破棄
    Task<long> GetCountWithTreeAsync(ISpecification<Aggregates.AdditionCategoryWithTree> specification, CancellationToken cancellationToken = default);
    //待破棄
    Task<List<Aggregates.AdditionCategoryWithTree>> GetListWithtWithTreeAsync(ISpecification<Aggregates.AdditionCategoryWithTree> specification = null, string sorting = null, int maxResultCount = int.MaxValue, int skipCount = 0, CancellationToken cancellationToken = default);
    //待破棄
    Task<Aggregates.AdditionCategoryWithTree> GetWithTreeAsync(Guid categoryId, CancellationToken cancellationToken = default);
}
```

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

![image](https://files.furthersoftware.com.tw/assets/Tourmap/重構/additionSales.png)

#### Manager

```c#
//TODO待破棄泛型方法
public class AdditionSaleDefinitionManager<T, U>{
    //改用原本Create
    Task<T> CreateAsync(Guid ownerId, int pripority, Guid? tenantId = null);
    
    //改用原本Update
    Task<T> UpdatePriporityAsync(Guid ownerId, int pripority, bool autoSave = false);
    
    //應該不用此方法，待刪除
    Task DeleteAsync(Guid ownerId, bool autoSave = false);
    
    //需搬到產生方法內
    Task<T> AddAdditionSaleParameterAsync(Guid ownerId, Guid additionId, bool? isRequired = null, int? freeAmount = null, WeekDayUsable? weekDayUsable = null, bool? disabled = null, Guid? tenantId = null, bool autoSave = false);
    
    //需搬到產生方法內
    Task<T> UpdateAdditionSaleParameterAsync(Guid ownerId, Guid additionSaleParameterId, Guid additionId, bool? isRequired = null, int? freeAmount = null, WeekDayUsable? weekDayUsable = null, bool? disabled = null, Guid? tenantId = null, bool autoSave = false);
    
    //需搬到產生方法內
    Task<T> RemoveAdditionSaleParameterAsync(Guid ownerId, Guid additionSaleParameterId, bool autoSave = false);
    
    //需搬到產生方法內
    Task<T> RemoveManyAdditionSaleParameterAsync(Guid ownerId, List<Guid> additionSaleParameterIds, bool autoSave = false);
    
    //需搬到產生方法內
    Task<T> RemoveAllAdditionSaleParameterAsync(Guid ownerId, bool autoSave = false);
}
```

#### Repository
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

#### Provider

```c#
public class AvailableSaleParameterModel
{
    public List<ParameterCalculateResult> ParameterCalculateResults { get; set; } = new();
}

public interface IAdditionSaleParameterCalculateProvider
{
    /// <summary>
    /// 根據帶入的ownerId做Parameter組合
    /// </summary>
    /// <param name="ownerIds">要組合的ownerId</param>
    /// <param name="additionIds">想組合的附加服務</param>
    /// <returns>回傳附加服務組合結果的陣列</returns>
    Task<AvailableSaleParameterModel> ParameterCalculateAsync(List<Guid> ownerIds, List<Guid>? additionIds = null);

    /// <summary>
    /// 帶入組合好的Parameter做過濾，會根據時間過濾出可用的Parameter
    /// </summary>
    /// <param name="parameters"></param>
    /// <param name="dateTime"></param>
    /// <returns></returns>
    AvailableSaleParameterModel FilterAvailableParameter(List<ParameterCalculateResult> parameters, DateTime? dateTime = null);
}
```

### EntityAdditionParameter(破棄)

![image](https://files.furthersoftware.com.tw/assets/Tourmap/重構/entityAdditionParameter.png)

該整個實體刪除，如有用到的地方都該拿掉

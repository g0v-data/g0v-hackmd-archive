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

目前考慮把繼承關係拆除

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


## Camping

### CampingArea

![image](https://files.furthersoftware.com.tw/assets/Tourmap/重構/campingArea.png)

#### Manager

```c#
//基本方法補上check和set
public class CampingAreaManager{
    //改用原本方法
    Task<CampingArea> CreateAsync(string displayName, int deafultAddPeopleLimit, int defaultAddPeoplePrice, int index);
    
    /// <summary>
    /// 上傳圖片
    /// </summary>
    /// <param name="campingArea"></param>
    /// <param name="inputStream">如果為null代表刪除</param>
    /// <returns></returns>
    //調整名字
    Task<CampingArea> UploadImgAsync(CampingArea campingArea, Volo.Abp.Content.IRemoteStreamContent? inputStream = null);
    
    /// <summary>
    /// 移動CampingArea並做排序，將prevIndex移動到nextIndex
    /// </summary>
    /// <param name="input">要做排序的CampingArea</param>
    /// <param name="prevIndex">原先位置</param>
    /// <param name="nextIndex">新位置</param>
    /// <returns></returns>
    //調整名字
    List<CampingArea> SortCampingAreasIndex(List<CampingArea> input, int prevIndex, int nextIndex);
    
    //將campingArea做重新排序，目前是刪除為了保持整齊重新排序用，可能有更好的做法
    List<CampingArea> ResetCampingAreaIndex(List<CampingArea> input);
    
    /// <summary>
    /// 獲取家人加價總價
    /// </summary>
    /// <param name="campingAreaId">營區Id</param>
    /// <param name="campingId">營位Id</param>
    /// <param name="quantity">加人加價人數</param>
    /// <returns></returns>
    //簡易計算家人加價參數的方法，應該另開provider，並且改善回傳
    //目前只回傳錢也沒回傳人數
    public async Task<decimal> GetAddPeoplePriceAsync(Guid campingAreaId, Guid campingId, int quantity)
}
```

#### Repository

```c#
public interface ICampingAreaRepository{
    //為了檢查名稱是否存在建立的方法，待破棄
    Task<bool> ExistAsync(string displayName);
    
    //待破棄
    Task<Aggregates.CampingAreaFullCamping> GetFullCampingAsync(Guid id, CancellationToken cancellationToken = default);

    //待破棄
    Task<List<Aggregates.CampingAreaFullCamping>> GetListFullCampingAsync(
ISpecification<Aggregates.CampingAreaFullCamping>? specification = null,
string? sorting = null,
int maxResultCount = int.MaxValue,
int skipCount = 0,
CancellationToken cancellationToken = default);

    //待破棄
    Task<long> GetCountFullCampingAsync(
    ISpecification<Aggregates.CampingAreaFullCamping> specification,
    CancellationToken cancellationToken = default);
}
```

#### Aggregates

```c#
//目前沒用到待破棄
public class CampingAreaFullCamping
{
    /// <summary>
    /// 營區
    /// </summary>
    public CampingArea CampingArea { get; set; } = null!;

    /// <summary>
    /// 營區封面圖
    /// </summary>
    public MediaDescriptor? CampingAreaCoverImageUrl { get; set; }

    /// <summary>
    /// 各個Camping的Sku資料
    /// </summary>
    public List<CampingDetail> CampingSkuDetails { get; set; } = new();

}
```

### CampingOrder

![image](https://files.furthersoftware.com.tw/assets/Tourmap/重構/campingOrder.png)

#### Manager

```c#
CampingOrderManager //基本方法補上check和set

CampingOrderLineManager //基本方法補上check和set
```

#### Repository

```c#
ICampingOrderRepository //目前沒有新增任何額外方法，不用調整

ICampingOrderLineRepository //目前沒有新增任何額外方法，不用調整
```

### Camping

![image](https://files.furthersoftware.com.tw/assets/Tourmap/重構/camping.png)


#### Manager

```c#
//基本方法補上check和set
public class CampingManager{
    //TODO 內部改用原本方法，但Assert不變
    Task<Camping> CreateCampingAndAssetAsync(
            Guid campingAreaId,
            string assetName,
            EasyAbp.BookingService.AssetSchedules.PeriodUsable defaultUsable,
            string description,
            int? addPeopleLimit = null,
            int? addPeoplePrice = null,
            int? index = null
            );
            
    //TODO 改用原本方法，Asset用event同步名稱
    Task<Camping> UpdateCampingAndAssetAsync(Guid id,
                                             Guid campingAreaId,
                                             string displayName,
                                             int? addPeopleLimit,
                                             int? addPeoplePrice,
                                             EasyAbp.BookingService.AssetSchedules.PeriodUsable defaultUsable,
                                             string description,
                                             int index);
    //不變                                             
    Task DeleteCampingAndAssetAsync(Guid id);
    
    //目前沒用到，待破棄
    Task<List<EasyAbp.BookingService.Assets.Asset>> ListAssetCategoryChildrenAssetsAsync(
            string productGroupName);
            
    //目前沒用到，待破棄
    Task<bool> SearchCampingIsAvailableBookingPeriodAsync(
            Guid assetId, Guid? periodSchemeId, DateTime currentDateTime, DateTime targetDate)
            
    /// <summary>
    /// 對camping做排序
    /// </summary>
    /// <param name="input">要做排序的Camping</param>
    /// <param name="prevIndex">原先位置</param>
    /// <param name="nextIndex">新位置</param>
    /// <returns></returns>
    List<Camping> SortCampingsIndex(List<Camping> input, int prevIndex, int nextIndex);
    
    //將camping做重新排序，目前是刪除為了保持整齊重新排序用，可能有更好的做法
    List<Camping> ResetCampingIndex(List<Camping> input);
    
    //TODO 調整名字成AttachmentImage
    Task<Camping> UploadImgAsync(Camping camping, Volo.Abp.Content.IRemoteStreamContent inputStream);
    
    //TODO 調整名字成AttachmentImage
    Task<Camping> DeleteImgAsync(Camping camping, Guid mediaId);
    
    //TODO 調整名字成AttachmentImage
    Task<Camping> DeleteAllImgAsync(Camping camping);
    
    //目前沒用到，待破棄
    Task<bool> CampingCanOccupyAsync(EasyAbp.BookingService.AssetCategories.AssetCategory assetCategory, Guid? periodSchemeId,
            DateTime targetTime, int volumn)
}
```

#### Repository

```c#
public interface ICampingRepository{
    //TODO待破棄，改用原先方法
    Task<Aggregates.CampingAggregate> GetFixWithNavigationPropertiesAsync(Guid id, CancellationToken cancellationToken = default);
    
    //TODO待破棄，改用原先方法
    Task<List<Aggregates.CampingAggregate>> GetFixListWithNavigationPropertiesAsync(
    ISpecification<Aggregates.CampingAggregate>? specification = null,
    string? sorting = null,
    int maxResultCount = int.MaxValue,
    int skipCount = 0,
    CancellationToken cancellationToken = default);
    
    //TODO待破棄，改用原先方法
    Task<long> GetFixCountWithNavigationPropertiesAsync(
    ISpecification<Aggregates.CampingAggregate> specification,
    CancellationToken cancellationToken = default);
    
    //Query之後會變擴充方法，待破棄
    Task<System.Linq.IQueryable<Aggregates.CampingAggregate>> GetQueryFixForNavigationPropertiesAsync();
    
    //TODO 目前沒有用到，待破棄
    Task<Aggregates.CampingDetail> GetSkuDetailAsync(Guid id, CancellationToken cancellationToken = default);
    
    //TODO 目前沒有用到，待破棄
    Task<List<Aggregates.CampingDetail>> GetListSkuDetailAsync(
    ISpecification<Aggregates.CampingDetail>? specification = null,
    string? sorting = null,
    int maxResultCount = int.MaxValue,
    int skipCount = 0,
    CancellationToken cancellationToken = default);

    //TODO 目前沒有用到，待破棄
    Task<long> GetCountSkuDetailAsync(
    ISpecification<Aggregates.CampingDetail> specification,
    CancellationToken cancellationToken = default);
}
```

#### Event

```c#
//目前會當CampingArea刪除時Camping會跟著刪除
ILocalEventHandler<EntityDeletedEventData<CampingArea>>
```

#### Aggregates

```c#
//TODO目前沒用到，待破棄
public class CampingDetail
{
    /// <summary>
    /// 營位
    /// </summary>
    public Campings.Camping Camping { get; set; } = null!;

    /// <summary>
    /// 圖片
    /// </summary>
    public List<MediaDescriptor> CampingImages { get; set; } = new();
}

//TODO目前沒用到，待破棄
public class CampingIsAvalible
{
    public bool IsAvalible { get; set; }
    public Camping Camping { get; set; } = null!;
}
```

### IntervalPeriodSchemes(破棄)

刪除遺留的綠色類別

### Schedule

![image](https://files.furthersoftware.com.tw/assets/Tourmap/重構/schedule.png)
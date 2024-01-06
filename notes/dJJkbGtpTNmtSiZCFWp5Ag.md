---
tags: DD技術讀書會
---
> DD技術讀書會 
>
> # DiskCacheStrategy of Glide  
>
> Glide is a fast and efficient open source media management and image loading framework for Android that wraps media decoding, memory and disk caching, and resource pooling into a simple and easy to use interface.
>
> [name=Kelly] [time=Fri, Mar 29, 2019] [color=#907bf7]

這次要從 Glide 的硬體快取決策去看決策模式的應用。

下面是抽象類別 DiskCacheStrategy 的介面 
跟他提供了五種不同的決策 (為了方便閱讀我把實作細節都拿掉了)

- ALL : 全部圖像包含尺寸變換都儲存快取

- NONE : 不作儲存快取

- DATA : 在解碼前儲存（只存遠端資料）

- RESOURCE : 在解碼後儲存 （包含本地端跟遠端）

- AUTOMATIC : 自動判斷是否該儲存快取 (預設值)

   

```java
public abstract class DiskCacheStrategy {
  
  public static final DiskCacheStrategy ALL = new DiskCacheStrategy() {
    public boolean isDataCacheable(DataSource dataSource) {}
    public boolean isResourceCacheable(boolean isFromAlternateCacheKey, 	                 DataSource dataSource,EncodeStrategy encodeStrategy) {}
    public boolean decodeCachedResource() {}
    public boolean decodeCachedData() {}
  };

  public static final DiskCacheStrategy NONE = new DiskCacheStrategy() {
    public boolean isDataCacheable(DataSource dataSource) {}
    public boolean isResourceCacheable(boolean isFromAlternateCacheKey, 	               DataSource dataSource,EncodeStrategy encodeStrategy) {}
    public boolean decodeCachedResource() {}
    public boolean decodeCachedData() {}
  };

  public static final DiskCacheStrategy DATA = new DiskCacheStrategy() {
    public boolean isDataCacheable(DataSource dataSource) {}
    public boolean isResourceCacheable(boolean isFromAlternateCacheKey, 	               DataSource dataSource,EncodeStrategy encodeStrategy) {}
    public boolean decodeCachedResource() {}
    public boolean decodeCachedData() {}
  };

  public static final DiskCacheStrategy RESOURCE = new DiskCacheStrategy() {
    public boolean isDataCacheable(DataSource dataSource) {}
    public boolean isResourceCacheable(boolean isFromAlternateCacheKey, 	               DataSource dataSource,EncodeStrategy encodeStrategy) {}
    public boolean decodeCachedResource() {}
    public boolean decodeCachedData() {}
  };

  public static final DiskCacheStrategy AUTOMATIC = new DiskCacheStrategy() {
    public boolean isDataCacheable(DataSource dataSource) {}
    public boolean isResourceCacheable(boolean isFromAlternateCacheKey, 	               DataSource dataSource,EncodeStrategy encodeStrategy) {}
    public boolean decodeCachedResource() {}
    public boolean decodeCachedData() {}
  };

 
  public abstract boolean isDataCacheable(DataSource dataSource);
  public abstract boolean isResourceCacheable(boolean isFromAlternateCacheKey,
      DataSource dataSource, EncodeStrategy encodeStrategy);
  public abstract boolean decodeCachedResource();
  public abstract boolean decodeCachedData();
}
```



藉由封裝進 RequestOptions 讓使用者可以自由改變想要的策略

在資源解碼時使用 DecodeJob

```java
// Decide the stage
private Stage getNextStage(Stage current) {
    switch (current) {
      case INITIALIZE:
        return diskCacheStrategy.decodeCachedResource()
            ? Stage.RESOURCE_CACHE : getNextStage(Stage.RESOURCE_CACHE);
      case RESOURCE_CACHE:
        return diskCacheStrategy.decodeCachedData()
            ? Stage.DATA_CACHE : getNextStage(Stage.DATA_CACHE);
      case DATA_CACHE:
        // Skip loading from source if the user opted to only retrieve the resource from cache.
        return onlyRetrieveFromCache ? Stage.FINISHED : Stage.SOURCE;
      case SOURCE:
      case FINISHED:
        return Stage.FINISHED;
      default:
        throw new IllegalArgumentException("Unrecognized stage: " + current);
    }
  }

@Synthetic
@NonNull
<Z> Resource<Z> onResourceDecoded(DataSource dataSource, @NonNull Resource<Z> decoded) {
    ...

    Resource<Z> result = transformed;
    boolean isFromAlternateCacheKey = !decodeHelper.isSourceKey(currentSourceKey);
    if (diskCacheStrategy.isResourceCacheable(isFromAlternateCacheKey, dataSource,
        encodeStrategy)) {
         ...
      }
      LockedResource<Z> lockedResult = LockedResource.obtain(transformed);
      deferredEncodeManager.init(key, encoder, lockedResult);
      result = lockedResult;
    }
    return result;
}
```
### 簡易架構圖
![](https://i.imgur.com/5JHRlbg.jpg)

```kotlin=

    Glide.with(context)
         .load(imageUrl)
         .apply(RequestOptions()
            .diskCacheStrategy(DiskCacheStrategy.RESOURCE))
         .into(imageView)
```
### 基本使用 Glide 流程圖（Create）
![](https://i.imgur.com/bWrW2e9.jpg)

### 針對創建 Target 部分的流程圖（Start）
![](https://i.imgur.com/nJxZ5xp.jpg)


### 更加詳細版
*下方類別圖只畫了部分相關的類別
![](https://i.imgur.com/c8Ilw7A.jpg)

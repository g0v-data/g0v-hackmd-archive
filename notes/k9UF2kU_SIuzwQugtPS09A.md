# Cache Memory 
## 特點
- Location 位置
- Capacity 容量
- Unit of transfer 轉讓單位
- Access method 訪問方式
- Performance 性能
- Physical type 物理類型
- Physical characteristics 物理特性
- Organisation 組織

### Location
- CPU
- Internal 內部
- External 外部

### Capacity
- Word size
    - The natural unit of organisation
- Number of words or byte

### Unit of Transfer
- Internal memory
    - Usually governed by data bus width 通常由數據總線寬度決定
- External memory
    - Usually a block which is much larger than a word
- Addressable unit 可尋址單元
    - Smallest location which can be uniquely addressed
    - Word mostly, some in byte-level

### Access Methods
- Sequential
    - Start at the beginning and read through in order
    - Access time depends on location of data and previous location
    - e.g. tape
- Direct
    - Individual blocks have unique address
    - ==Access is by jumping to vicinity plus sequential search
      訪問方法是跳到附近再進行順序搜索==
    - Access time depends on location and previous location
    - e.g. disk
- Random
    - Individual addresses identify locations exactly
      各個地址可準確識別位置
    - ==Access time is independent of location or previous access==
    - e.g. RAM
- Associative
    - Data is located by a comparison with contents of a portion of the store
      通過與內容的比較來定位數據商店的一部分
    - Access time is independent of location or previous access
    - e.g. cache

### Memory Hierarchy 記憶層級
- Registers In CPU
- Internal or Main memory 
    - May include one or more levels of cache
    - “RAM”
- External memory
    - Backing store

### Performance
- Access time
    - Time between presenting the address and getting the valid data 
      從提供地址到獲取有效數據的時間
- Memory Cycle time
    - Time may be required for the memory to “recover” before next access
        - ==Cycle time is access + recovery==
- Transfer Rate
    - Rate at which data can be moved

### Cache
- 少量快速記憶
- 坐落於記憶體與CPU之間
- 可能位於CPU晶片或模組上

- CPU請求內存位置的內容
- 檢查緩存中的此數據
- 如果存在，從緩存中獲取（快速）
- 如果不存在，則從主存儲器讀取所需的塊以緩存
- 然後從緩存傳遞到CPU
- 緩存包括標籤，用於標識每個緩存插槽中的主內存塊


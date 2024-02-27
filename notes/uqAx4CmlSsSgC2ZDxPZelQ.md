# 2024-02-27 Recap
###### tags: `School`, `recap`

## Recap

- week 0 part 3 要注意下拉刷新須重 call API
- collection view 要注意 estimate 改為 none
    - 嘗試搜尋關鍵字 「UIcollection view Delegate flowlayout work」
    - 或是查 Error message
- button 有 image view 和 label
    - 如果無法調整 button color (set title color)，可嘗試調整 title label .textcolor 
- Tint color 類似預設顏色，影響範圍最大 
- network link conditioner 可測網速
    

## Discussion Topics

1. 一個合法的 JSON 長什麼樣子？
    1. 大括號
    2. key: value
    3. 用 , 分隔不同資料
    4. 後端常用 snake case，swift 可用 coding key 轉為 camelcase
        - 也可參考 JSONDecoder.keyDecodingStrategy = .convertFromSnakeCase
3. Pod 是否該 git ignore？
    - pod 該上傳：如果第三方套件有客製化，才會讓開發者檔案一致
    - pod 不該上傳：podfile 檔案太大
5. Kingfisher 的功用
    - 顯示 loading indicater
    - 圖片快取

補充：
- 可以參考 Almofire 的 code 精進 coding 功力
- 可更改第三方套件（例如 copy 特定片段 code）作為自己的東西
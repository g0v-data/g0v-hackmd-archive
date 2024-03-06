# 2024-03-06 Recap
###### tags: `School`, `recap`
## Recap

- 可善用 enum 群組化的特性，優化男女裝配件
- git 小工具：sourceTree 
    
    

## Discussion Topics
1. 什麼是 Main thread？
    1. 負責更新 UI
    2. thread 線程：執行事情
    3. queue 佇列：類似隧道
    4. DispatchQueue.main.async
    5. [GCD 多執行緒的說明與應用. GCD(Grand Central Dispatch) 是 Apple… | by 法蘭克的 iOS 世界 | Medium](https://franksios.medium.com/ios-gcd%E5%A4%9A%E5%9F%B7%E8%A1%8C%E7%B7%92%E7%9A%84%E8%AA%AA%E6%98%8E%E8%88%87%E6%87%89%E7%94%A8-c69a68d01da1)
3. 怎麼確定 Auto Layout 拉得正確？
    1. 確認 interface builder 的屬性
      2. 確認紅色、黃色警告標記
      3. 用模擬器看
      4. 用 View hierarchy 確認
          如果是下 break point，沒有更動 code，可以不用重 run 模擬器
    5. Bounds Rectangles 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0076c96bb59c183959a4ebb0a439659d.png)
    6. 如果用 code 寫 autolayout，可以在下方 po 某物件.frame，這樣會輸出 x, y 軸

5. UIScrollView 的特性

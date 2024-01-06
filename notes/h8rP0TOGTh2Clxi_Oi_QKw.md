---
tags: cofacts
---

Cofacts list page refactor
=====

## 相關 spec
- [[Spec] 可疑轉傳訊息](/ahtI6xsFRQyxktrIlc1VcQ)
- [[Spec] 最新查核訊息(需複查列表)](/ZZWHWi2BTuyhkSWzAvKLAw)
- [[Spec] 等你來答](/N8I2-zkJTaS35BP8VH8ZQA)
- [[Spec] 搜尋結果](/oWSar1t0SzWo150Dsbepxw)

## 相關 bugs
- Search page 應該 sort by relevance
- Replied by me filter 目前是壞的
- Latest reply 頁面卻有沒回應過的訊息

## Input components

目標：最終結果複製貼上到各個 page component 能輕鬆客製化行為，但又最小化 code duplication。

每個 input component 都設計成可以讀寫 URL query。URL 設定的 key 是一致的，但每一個不同列表頁，又都能自己的傳 option 進去給 input component，修改要顯示的選項等等。

- `Filters` (wrapper)
  - 基礎 `Filter` 改名 `BaseFilter`
    - 加入 storybook
    - 刪掉 `selected` state，直接做成 controlled input
  - 新增各自 sub-filters 作為 `<Filters>` 的 children
    - `ArticleStatusFilter`
    - `ReplyTypeFilter`
    - `CategoryFilter`
      - Loads categories via `LIST_CATEGORIES`
  - 以上 subfilter 都會直接讀寫 URL
    - 直接從 `useQuery` 讀 filter 決定 highlight 項目，輸入 `BaseFilter`
    - `BaseFilter` 發生 `onChange` 時呼叫 `goToUrlQueryAndResetPagination` 修改自身 URL param
  - 包含 Filter FAB 與 Filter modal (故 children 會被 render 2 次，
一次在桌面版，一次在手機版)
  - 刪除 `FilterGroup` 封裝
- `SortInput`
  - 原本 input 版本(與 URL 無關)改名為 `BaseSortInput` 放入 storybook
  - default export 會直接讀 URL、onChange 也寫 URL
    - 直接從 `useQuery` 讀 `orderBy (與 GTE, LTE 等 query 邏輯脫鉤)
    - `BaseSortInput` 發生 `onChange` 時，呼叫 `goToUrlQueryAndResetPagination`
- `TimeRange`
  - 原本 input 版本(與 URL 無關)改名為 `BaseTimeRange` 放入 storybook
  - default export 會直接讀 URL、onChange 也寫 URL
    - 直接從 `useQuery` 讀 `start` / `end` (與 GTE, LTE 等 query 邏輯脫鉤)
    - `BaseTimeRange` 發生 `onChange` 時呼叫 `goToUrlQueryAndResetPagination` 寫 `start`, `end`
    - 如何從 URL 讀值轉成 query 是 page component 的邏輯，與此 component 無關。
      - 例如說 `/replies` 頁面的 `TimeRange` 要依照 `SortInput` 選「最後回應」還是「文章回報」來改變 time range 的 range key，但 component 本身不管此邏輯，是由 page component 處理。
    - 保留 `options` props 讓 page component 自訂要顯示的 option 與 option value

- `LoadMore`
  - expose `onClick` as a prop (然後輸入 variables)；或輸入 `fetchMore` 與 `getDataFetchMoreResult` 當 prop 之類的
  - 直接輸入 `edges` 與 `pageInfo` 作為 input prop，自動抽取 cursor 判斷是否要顯示

## Layout components

- `Header`: expose `title`、`feedUrl` props
- `HeaderControls`: 手機上上下擺放 children、桌機上左右擺放 children、設好 margin。預計在 children 擺放 `<TimeRange>` 與 `<SortInput>` 用。

## 規劃

分成 3 個 PR：
1. Packaging input components
    - filter, sort, pagination 抽成 component
    - 處理 URL <> value change 之間的關係
    - 設計各個 input component 的 props & callbacks
    - 加入 loading progress bar
2. Packaging display components: Header, layouts, list items 抽成 component，檢視其 props 設計
3. Extract logic to page
    - 上述 component 從 `ArticlePageLayout` 中抽出到 page component
    - URL --> GraphQL query param 的邏輯 (`getQueryVars`, `urlQuery2Filter`, `urlQuery2OrderBy`) 抽到 utility function 去，在各個 page components 重用
    - data loading 邏輯放去各自的 page component
      - `getQueryVars` 拿回來的 GraphQL filter / sort 物件，在送去 `useQuery` 前還有針對該 page 特性來修改的機會，例如說 hoax-for-you 可在 page component 裡呼叫 `getQueryVars` 之後，先在 `filter` 裏頭加料再傳給 `useQuery`，確保列出的東西都是「等使用者來答」的。
      - `/articles`, `/replies`, `/hoax-for-you` 的 `LIST_ARTICLES`, `LIST_STATS` 若有重複（其實應該都會有微妙不同，因為 display item 需求欄位不同⋯⋯）
    - 移除 `ArticlePageLayout`。

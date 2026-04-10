# HW3 - Testing

## 1) 程式碼片段

檔案：`backend/test/todo.spec.ts`

```ts
test('Given a valid ID and status, When receive a PUT /api/v1/todos/:id request, Then it should response the updated todo object', async () => {
  // arrange: mock the repo function to return an updated todo object
  const updatedTodo: Todo = {
    id: '1',
    name: 'todo 1',
    description: 'description 1',
    status: true
  }
  vi.spyOn(TodoRepo, 'updateTodoById').mockImplementation(async () => updatedTodo)

  // act: receive a PUT /api/v1/todos/:id request
  const response = await server.inject({
    method: 'PUT',
    url: '/api/v1/todos/1',
    payload: {
      status: true
    }
  })

  // assert: response should be the updated todo object
  expect(response.statusCode).toBe(200)
  const todo = JSON.parse(response.body)['todo']
  expect(todo).toStrictEqual(updatedTodo)
})

test('Given an invalid ID, When receive a PUT /api/v1/todos/:id request, Then it should response with status code 404', async () => {
  // arrange: mock the repo function to return null
  vi.spyOn(TodoRepo, 'updateTodoById').mockImplementation(async () => null)

  // act: receive a PUT /api/v1/todos/:id request
  const response = await server.inject({
    method: 'PUT',
    url: '/api/v1/todos/invalid-id',
    payload: {
      status: true
    }
  })

  // assert: response should with status code 404
  expect(response.statusCode).toBe(404)
  const result = JSON.parse(response.body)
  expect(result.msg).toBe('Not Found Todo:invalid-id')
})
```

---

## 2) 測試報告
![](https://g0v.hackmd.io/_uploads/B1x-emmLnbl.png)

---

## 3) 說明

### A. 測試描述（後端）

本次測試聚焦在 Todo API 的更新路由：
- `PUT /api/v1/todos/:id` 成功更新的情境
- `PUT /api/v1/todos/:id` 查無資料的情境

這兩個案例分別驗證：
1. 路由在成功更新時，是否回傳正確 HTTP 狀態碼 `200` 與正確資料。
2. 路由在找不到對應 Todo 時，是否回傳 `404` 與預期錯誤訊息。

### B. 使用的測試工具

- **Vitest**：測試框架，提供 `test`, `expect`, `describe`。
- **Fastify inject**：不需要真的開 HTTP port，就能模擬 API 請求。
- **vi.spyOn**：mock repository 層 (`updateTodoById`) 回傳值，隔離資料庫依賴。

### C. 測試策略

#### Test Case 1：有效 ID 更新成功
- 測試場景：使用有效 ID + 合法 `status`。
- 測試主體：`PUT /api/v1/todos/:id` route handler。
- Mock 設定：`updateTodoById` 回傳一筆更新後的 Todo。
- 預期結果：
  - HTTP status = `200`
  - response body 的 `todo` 與 mock 物件完全一致。
- 想驗證的重點：路由在 service/repo 回傳正常資料時，是否正確轉換為成功 API 回應。

#### Test Case 2：無效 ID 回傳 404
- 測試場景：使用不存在的 Todo ID。
- 測試主體：`PUT /api/v1/todos/:id` route handler。
- Mock 設定：`updateTodoById` 回傳 `null`。
- 預期結果：
  - HTTP status = `404`
  - response body 的 `msg` = `Not Found Todo:invalid-id`
- 想驗證的重點：路由在查無資料時，是否走到錯誤分支並回傳正確訊息。

### D. 為什麼這樣設計

這份測試採用「路由整合測試 + repo mock」：
- 保留 HTTP request/response 行為（比純函式測試更接近真實使用情境）。
- 用 mock 控制資料回傳，避免依賴 MongoDB，讓測試快速且穩定。

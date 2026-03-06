## 萌典翻新社群協作指南（非同步參與）

這個專案目前採取 **非同步協作（asynchronous collaboration）** 的方式進行。  
也就是說，不需要固定會議或同步討論，任何人都可以在自己方便的時間參與。

最需要的協助主要有三種：

1. **實際測試功能**
2. **整理與搬移既有 Issue**
3. **提交 Pull Request 修正問題**

這些工作都可以分散進行，非常適合開源社群協作。

---

## 1️⃣ 實測與回報問題（最需要）

目前最需要的協助是幫忙實測、發現 bug、提出 issue。  
字典牽涉四種語系與多種複雜功能，很多問題必須靠實際操作流程才會發現。

所以想參與協作，不一定要先建立完整開發環境；  
只要像「啄木鳥」一樣持續測試、發現問題並回報，就非常有幫助。

- 線上實測頁面：https://dev.moedict.tw/  
- 錯誤回報頁面：https://github.com/g0v/cf-moedict-webkit-neo/issues  

### 回報問題建議格式

請先確認是否已有相同 issue。

Issue 描述建議包含：

- 重現步驟（Steps to reproduce）
- 預期結果（Expected result）
- 實際結果（Actual result）
- 截圖（可選）
- 瀏覽器與作業系統版本

如果是資料相關問題（例如部首、詞條、分類），  
請盡量附上對應詞條與 URL。

---

## 2️⃣ 搬移舊 Issue（很需要）

原始萌典專案多年來累積了許多 Issue，其中不少仍然有價值。

我們希望社群協助把有用的 Issue **整理並搬移到新的 repo**。

原始 Issue：

https://github.com/g0v/moedict-webkit/issues/

新的 Issue Repo：

https://github.com/g0v/cf-moedict-webkit-neo/issues/

### 搬移方式

1. 在舊 repo 找到仍然 relevant 的 Issue  
2. 在新 repo 建立一個 Issue  
3. 附上原始 Issue 連結  
4. 簡單說明目前狀態或需要的修復

例如：

```

Duplicate from:
[https://github.com/g0v/moedict-webkit/issues/XXXX](https://github.com/g0v/moedict-webkit/issues/XXXX)

```

---

## 3️⃣ 用 AI 協助修正字典資料

字典資料位於：

```

data/dictionary/pack/

```

每個 `.txt` 為 **JSON Lines 格式**，包含多個詞條。

如果發現：

- 詞條錯字
- 錯誤翻譯
- 符號錯誤（例如易經卦象 ☱ ☶ 對調）
- 引用典籍筆誤

都可以透過 PR 修正。

### 建議流程

1️⃣ **指出詞條與錯誤**

在 Cursor 或支援 `@` 的編輯器中，可：

```

@pack

```

或直接開啟：

```

data/dictionary/pack/

```

例如：

> 「咸」條目寫成  
> 艮（☱）下兌（☶）上  
> 應改為  
> 艮（☶）下兌（☱）上

---

2️⃣ **搜尋詞條位置**

詞條可能以 Unicode escape 方式儲存，  
可用 repo 搜尋詞條名稱或錯誤字串找到位置。

---

3️⃣ **只修改資料並提交 PR**

修正時：

- 只修改  
```

data/dictionary/pack/*.txt

```

- 不需要修改程式碼

完成後：

1. Fork repo  
2. 修改資料  
3. 提交 Pull Request  

PR 合併後，如果專案有部署 R2，需要重新上傳字典資料：

```

commands/upload_dictionary.sh

```

線上站才會反映變更。

---

## 適合 AI 協助的修正類型

AI 特別適合協助處理：

- 釋義錯字
- 多語翻譯錯誤
- 專有名詞錯誤
- 符號或卦象錯誤
- 引用典籍筆誤

若涉及：

- 版權問題
- 大規模改寫
- 結構性修改

建議先在 Issue 討論。

---

## 協作方式

整個專案採用典型的 g0v 協作模式：

- Issue 討論
- Fork → PR
- 非同步協作

任何人都可以從 **實測、整理 Issue、或提交小修正** 開始參與。

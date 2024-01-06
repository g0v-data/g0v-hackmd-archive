---
tags: 
---

> 跳回[gather.town 使用說明](https://g0v.hackmd.io/@SeanGau/S19eA4cK_)

# gather.town地圖編輯資料收集
以下部分翻譯至官方地圖編輯指引

## 基礎
### gather.town地圖基礎知識
Gather Space 是一個由 1 個或多個 Room 組成的虛擬世界，由其 url 引用。Gather Room 是 一個空間內的 2D 地圖，可以連接到該空間中的其他房間（甚至其他空間）。一個聚集室必須至少有一個背景和一個出生點瓷磚效果，但可以包括一個背景、一個前景、多個瓷磚效果以及多個高級和基本對象。

### 自訂地圖創建過程概述
創建自訂地圖共四個步驟：
1. 創造空間：轉到gather.town/app 並創建或編輯空間。您可以從我們的任何模板開始，也可以從頭開始（空白地圖）。您還可以向現有空間添加房間。
2. 創造背景（和前景，可選）：為您正在處理的房間創建佈局和样式。
3. 添加磁貼效果：指示 GatherTown 應允許人物行走或不行走的位置（即牆壁）以及當化身進入某些瓷磚位置時應發生的任何其他特殊效果。
4. 最後，添加物件：這包括椅子、桌子和可交互的電視、遊戲、白板等。

### 創建背景
在gather.town，背景是人物走在其「上面」的圖像 - 它們顯示在人物下方，並且可以對它們擺放磁磚效果。每個 Gather Room 將只有一個背景，也可以選擇有一個前景（人物走在其「下面」的圖像）。

#### 可以通過以下三種方式之一創建背景：

1. 使用預先構建的模板
    - 在 Gather 中創建背景的最簡單方法是使用我們預先構建的模板之一。當您創建新房間並使用模板時 - 您可以滾動瀏覽數十個不同的預建區域。
    - 這些模板還包括預先放置的瓷磚效果，因此您的空間幾乎完全配置好，可以立即使用或繼續修改。
    - 您可以為不同的房間使用不同的模板，並將它們與門（門戶）連接在一起。

2. 上傳在 Gather 之外創建的自定義圖像
    - Gather 背景（或前景）是平面圖像，因此您也可以在 Gather 之外創建背景，然後將其上傳到“空白”房間。
    - 此圖像應為 PNG 文件，並應縮放以適合 32x32 像素平鋪系統（因此高度和寬度均應為 32 的倍數）。
    - [Tiled](https://www.mapeditor.org/)是一個第三方軟體，我們建議將其作為構建自定義地圖的絕佳選擇。我們無法為它提供支持，因為它不是我們發布的軟體，但是網上有很多很棒的資源。
        - 我們的公共地圖集：https : //github.com/gathertown/mapmaking
            - 單擊綠色的“代碼”按鈕並選擇“下載 zip”
        - 關於如何使用 Tiled 的教程，由我們的內部地圖製作者指導 https://drive.google.com/file/d/1lYhaaZIUE0p0gsaDzOgiXZHZ5T8JpWWc/view?usp=sharing
        - https://opengameart.org/content/tilesets-and-backgrounds-pixelart
        - https://itch.io/game-assets/tag-pixel-art
    - 我們還看到了用 Photoshop、GIMP、Illustrator 製作的精美地圖，甚至是掃描照片和手繪藝術！只要將其縮放以匹配我們的 32x32 網格並採用 PNG 或 JPEG 格式，您就可以將其作為背景或前景上傳。
    - 注意：上傳自定義地圖時需要考慮的一些重要技術事項
        - 前景和背景文件必須具有相同的尺寸/分辨率。
        - PNG 支持透明度，這對於前景很重要，但如果背景中有透明空間，則會在地圖上留下黑色空間。
        - 當人們在您的 Gather Space 中時，您可以熱交換背景圖像。我們已經看到它被創造性地用來“打開”房間裡的燈！

3. 在 Map Maker 中使用背景畫家（BETA）
    - Background Painter 仍處於 BETA 測試模式，因此您可能會遇到不直觀的錯誤或交互。我們很想听聽您對此產品的反饋，以便我們不斷改進它 - 請通過feedback@gather.town 與我們聯繫，讓我們知道您對背景畫家的體驗。
    - 目前，我們建議您觀看我們關於背景畫家的 Youtube 教程，並遵循以下一些準則
    - Background Painter 不應用於之前上傳過自定義背景的房間，或應用了模板的房間。
    - 背景畫家只能在全新的房間中單獨使用。

## 文字資料
- [官方基礎教學與地圖編輯指引](https://docs.google.com/document/d/e/2PACX-1vQrz8JSQv83CfoOXWm4Ja03BITBlV9GDdTbcPQ1uZUXrkd-34FWxnD4vHdFgxAAoNZrmCQEtBV7XP8Q/pub)

## 推薦地圖編輯器

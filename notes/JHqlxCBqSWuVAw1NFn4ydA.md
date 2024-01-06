# **flex box**

:::warning
・運用 display: flex 啟動 flexbox 系統，宣告 container 和 item
・瞭解 flexbox 系統裡 main axis 和 cross axis 的區別，並使用 flex-direction 切換主軸線
・使用 flex-wrap 屬性控制子元素 overflows
・使用 align-items 和 justify-content 屬性調整對齊和間距
:::

Flex 基本結構：Container & Item
在進入語法前，先了解 Flex 的基本元素，以下是 Flex 的示意圖：


你需要先透過 display: flex 將某個元件宣告成 flex container，然後這個容器內所有的子元素就會變成 flex item，你可以運用 flex 相關屬性來操作它們的對齊、方向、順序和尺寸，只需要更改 flex 屬性，不需要更改任何 HTML 結構，佈局就可以會靈活變化。

接下來我們要解釋 Flexbox 語法，為了避免「見樹不見林」，建議你先到 Flexbox Playground 網頁玩玩看，這個網頁讓你可以實驗不同的語法組合，灰色的空間就是 container，中間四個彩色長條框是 flex items，你可以透過上方的面板來控制 items 的排列與對齊。


先玩玩看，會對之後要教的語法比較有概念。

宣告 Flex Container
使用 flexbox 的第一步是建立 flex container，如下圖所示，我們可以透過把 flex-container 的 display 屬性設定為 flex來達成這個目的。

.flex-container {
  display: flex;
}
設定完以後，flex container 以下所有的緊鄰子元素會成為 flex items 並且啟動 flexbox 排版模式。

先直接動手試試看吧，請你用這個 CodePen 例子來練習設定 flexbox 屬性，在這裡我們建立了簡單的 HTML 架構，內含有一個 container 和四個 items，並做好 CSS 樣式以方便你觀察。目前我們沒有設定任何的 display 屬性，因此 <div> 的預設值會是 block。


現在，請你為 .flex-container 加入 display: flex 屬性，並觀察畫面的改變：


在你宣告 flex container 的瞬間，item 會自動代入預設屬性，並發生變化：

使用水平維度，全部排在同一行 (row)
套用已定義的大小 (width & height)，如果還未定義就用該元素中內容的大小
縮小以適應 flex container 的寬度
Flex Container 的屬性

現在讓我們透過 flex container 的屬性來操作 item 的排列。Flexbox 的一個重要特點是單一維度。也就是說，item 的排列方向有水平或垂直兩個維度，也就是欄 (column) 或是列 (row)，你可以切換它們要使用哪一個維度，但一次只能選一個。


flex-direction

flex-direction 可以改變 item 的排列方向，請你在剛才的 CodePen 專案的 .flex-container 實驗切換以下屬性，觀察 flex item 的排列變化：

flex-direction: row
flex-direction: column
flex-direction: row-reverse
flex-direction: column-reverse
flex-wrap

當你不希望 flex items 溢出 container 時，你可以使用 flex-wrap 來「包裝」內容，也就是讓他們遇到邊界就「自動換行」。這在設計 RWD 時會非常地有用。

這裡有一個新的 CodePen，加入了比較多的 items，讓你可以觀察 items 的流動。

請你在 .flex-container 裡切換以下屬性：

flex-wrap: nowrap
flex-wrap: wrap
flex-wrap: wrap-reverse
flex-wrap 的預設值是 nowrap，這表示 flex items 會縮小尺寸來適應 flex container的邊界。要特別注意的是，如果 flex items 設定了 min-width，items 不會縮小反而會溢出 flex container。你可在 CodePen 試試並透過在 flex container 內加入更多 flex items 來測試效果。

試試看把 flex items 的 width 屬性改成 min-width ，會發生什麼事呢？


flex-flow
flex-direction 和 flex-wrap 這兩個屬性可以合併成 flex-flow 屬性。flex-flow 接受兩個值，第一個是給 flex-direction 第二個是給 flex-wrap。例如：

.flex-container {
    flex-flow: row wrap;
}
對齊 Flex Items

接下來我們看看怎麼控制 flex items 之間的對齊與間距，由於 flex 是單一維度的，你可以用 flex-direction 來切換主軸 (main axis)與交叉軸 (cross axis)，然後再用以下兩個屬性控制對齊：

justify-content - 用於 main axis
align-items - 用於 cross axis
由於 flex-direction: row 是預設值，下文的圖例都屬於「main axis 是水平軸」的情境。

justify-content

讓我們先從控制主軸的 justify-content 開始，它一共可接受六個值，在理解上可以分成兩組，請你一邊參見上圖，一邊對照下表的說明：

Value	Note
flex-start (default)
flex-end
center
這組設定著重對齊，也就是置左、置右、置中，而 item 的間距則完全由 margin or padding 來控制。
space-between
space-around
space-evenly
這組設定著重間距，也就是在 container 的空間裡，item 要怎麼分佈。只要選用了 space-* 就會是平均分散，細部差別是：
space-between - 最兩側的 item 會緊貼 container 邊界，再分配剩餘空間。
space-around - 每個 item 左右兩側都分配到等量的空格，但最兩側的空格會只剩一半
space-evenly - 也是 item 左右兩側都有空格，但會讓所有的空格大小相同
請你在之前的 CodePen 中繼續加上屬性，看看會發生什麼事。

align-items
相對於 justify-content 控制主軸的空間配置，align-items 則處理在交叉軸上 flex items 的排版。它接受以下五個值：

flex-start
flex-end
center
baseline
stretch (預設)
若要區分這五個值，版面需要設計一下，這裡準備了一組 Codepen，請你消化一下裡面的內容，並找到 container 上設定 align-items 的位置，試著切換屬性，一邊觀察圖像的改變、並閱讀下方的文字說明：


flex-start - item 會貼齊交叉軸的起點
flex-end - item 會貼齊交叉軸的終點
center - item 會對齊交叉軸的中間
baseline - 先把內容對齊 baseline，item 隨著跑 (通常文字下緣對齊的地方稱為 baseline）
stretch - item 會延展填滿容器空間，但會尊重特別指定的 width or height (如方塊 3)
在這單元，我們只講了跟 flex container 有關的 flexbox 屬性。其實 flex items 也有許多屬性，例如可以控制排列順序，或者搭配 RWD 的設計，控制 viewport 尺寸變化時的縮放比例。這些細緻的微調我們留待下學期討論，綜合目前學過的招式，你已經可以完成一定水準的排版了，例如剛剛完成的「我的履歷」專案，我們來回顧一下吧！
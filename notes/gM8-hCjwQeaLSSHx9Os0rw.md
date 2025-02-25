# HTML
以下是 HTML 教學中所涉及的技法整理成的表格：

| 技法分類 | 技法名稱 | 說明 | 範例 |
|----------|---------|------|------|
| **結構與內容** | 標題 (Heading) | 定義標題層級 | `<h1>標題</h1>` |
|  | 段落 (Paragraph) | 定義一個段落 | `<p>這是一個段落</p>` |
|  | 區塊引用 (Blockquote) | 用於引用段落 | `<blockquote>這是一個引用</blockquote>` |
|  | 預格式化文字 (Preformatted Text) | 保持原始格式的文字 | `<pre>這是一段格式化文字</pre>` |
|  | 跳行 (Line Break) | 強制換行 | `<br>` |
| **語意標籤** | 強調 (Strong/Em) | 使文字加強語氣 | `<strong>重要</strong>` `<em>強調</em>` |
|  | 縮寫 (Abbr) | 定義縮寫 | `<abbr title="World Health Organization">WHO</abbr>` |
|  | 代碼 (Code) | 表示程式碼 | `<code>print("Hello")</code>` |
| **多媒體** | 圖片 (Image) | 顯示圖片 | `<img src="image.jpg" alt="圖片描述">` |
|  | 音訊 (Audio) | 嵌入音樂 | `<audio src="music.mp3" controls></audio>` |
|  | 視訊 (Video) | 嵌入影片 | `<video src="video.mp4" controls></video>` |
| **列表** | 有序列表 (Ordered List) | 編號列表 | `<ol><li>項目1</li><li>項目2</li></ol>` |
|  | 無序列表 (Unordered List) | 圖標列表 | `<ul><li>項目1</li><li>項目2</li></ul>` |
|  | 定義列表 (Definition List) | 解釋性列表 | `<dl><dt>術語</dt><dd>定義</dd></dl>` |
| **連結與導航** | 超連結 (Anchor) | 網頁內跳轉 | `<a href="https://example.com">點我</a>` |
|  | 書籤連結 (Bookmark) | 網頁內定位 | `<a href="#section">跳到段落</a><p id="section">目標段落</p>` |
|  | 電子郵件連結 (Email Link) | 點擊發送郵件 | `<a href="mailto:example@email.com">寄信</a>` |
| **表單** | 表單 (Form) | 讓使用者輸入資料 | `<form action="submit.php" method="post"></form>` |
|  | 輸入欄位 (Input) | 讓使用者輸入文字 | `<input type="text" placeholder="輸入文字">` |
|  | 選項按鈕 (Radio) | 單選選項 | `<input type="radio" name="gender" value="男"> 男` |
|  | 核取方塊 (Checkbox) | 多選選項 | `<input type="checkbox" name="hobby" value="閱讀"> 閱讀` |
|  | 按鈕 (Button) | 提交或重置 | `<button type="submit">送出</button>` |
| **表格** | 表格 (Table) | 顯示表格 | `<table><tr><td>數據</td></tr></table>` |
|  | 表頭 (Table Header) | 定義表格標題 | `<th>標題</th>` |
|  | 合併儲存格 (Merge Cells) | 合併列或欄 | `<td colspan="2">合併欄位</td>` |
| **佈局** | div 容器 (Div) | 區塊級元素容器 | `<div>這是區塊</div>` |
|  | span 容器 (Span) | 行內元素容器 | `<span>這是行內</span>` |
|  | iframe (Inline Frame) | 插入其他網頁 | `<iframe src="page.html"></iframe>` |
| **HTML5 新技術** | Semantic Elements | 更語意化的標籤 | `<article>文章內容</article>` `<section>區塊</section>` |
|  | 圖片標註 (Figure) | 圖片帶有標題 | `<figure><img src="image.jpg"><figcaption>說明</figcaption></figure>` |
|  | 萬國碼| 中文字浮 | <meta charset="UTF-8"> |


<pre>
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>個人檔案</title>
    <style>
        img {
            border-radius: 10%;
            width: 150px;
            height: 150px;
            /*object-fit: cover;*/
        }

    </style>

    <!-- style>/*css*/
        body {
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
            text-align: center;
        }
        header {
            background-color: #4CAF50;
            color: white;
            padding: 20px;
            font-size: 24px;
        }
        main {
            max-width: 600px;
            margin: 20px auto;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        ul {
            list-style-type: none;
            padding: 0;
        }
        li {
            background: #e0e0e0;
            margin: 5px 0;
            padding: 10px;
            border-radius: 5px;
        }
        figure {
            margin-top: 20px;
        }
        img {
            border-radius: 50%;
            width: 150px;
            height: 150px;
            object-fit: cover;
        }
        figcaption {
            font-style: italic;
            color: #555;
        }
    </style-->
</head>
<body>
    <header>
        <figure>
            <img src="cars.jpg" alt="個人照片">
            <figcaption>profile pic</figcaption>
        </figure>

        <h1>Ella Tso</h1>
    </header>
    
    <main>
        <section>
            <h3>Basic INFO</h3>
            <ul>
                <li><strong>職業：</strong> 學生</li>
                <li><strong>興趣：</strong> 旅行、編程、閱讀</li>
                <li><strong>聯絡方式：</strong> ella@email.com</li>
            </ul>
        </section>
        
        <article>
            <a href="https://www.google.com/search?gs_ssp=eJzj4tVP1zc0TEmriK8wSDcxYPQSz0stSy1SSM_Py0tUSM8sS1WozC9VKC0AAANTDVU&q=never+gonna+give+you+up&rlz=1C1YTUH_zh-TWTW1023TW1023&oq=never+&gs_lcrp=EgZjaHJvbWUqBwgCEC4YgAQyBggAEEUYOTIPCAEQABgKGIMBGLEDGIAEMgcIAhAuGIAEMgcIAxAAGIAEMgwIBBAuGEMYgAQYigUyBwgFEC4YgAQyBwgGEC4YgAQyBggHEAUYQNIBCDQ2NzNqMGo3qAIAsAIA&sourceid=chrome&ie=UTF-8">🔗ABOUT ME</a>

            <p>click the link to learn more...</p>
        </article>
        
        
    </main>
</body>
</html>


</pre>
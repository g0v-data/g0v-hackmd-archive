## 開発ノート
`文字入力、プロンプト入力->ストーリーを入力することに絞る`
> 6/25
* マルチモーダルAI 
GPT-4V
tsuzumi
**LLaVAに決定**

* graphRAG
LlamaIndex

---
>Llama(ラマ) 3.1 8B ins 

* 文字数（Maxtext）:128k(約10万〜15万文字,一般的な小説や新書で約1〜1.5冊分)

* 変圧器と一緒に使用してください
以降ではtransformers >= 4.43.0、Transformers のpipeline抽象化を使用するか、関数を使用して Auto クラスを活用することで、会話推論を実行できますgenerate()。

----

> RAG技術(要約する、外部記憶として使う)

トランスフォーマーのインストールを必ず更新してくださいpip install --upgrade transformers。

> ~~~~数式エディタの搭載
>* MathJax(JavaScriptプログラム)~~~~

> ベンゼン環の描画
>* RDKit

> AIによる仮漫画化　（orネーム案の考案）
>* (Stable Diffusion XL(画像))　もしくは　Pony Diffusion V6(アニメや漫画風に特化) + LoRA(キャラの固定)

> タグ付けの自動化
>* Mistral 7B, (LIama 3.1 8B)

> 漫画を本投稿
>人間がやる

--------------------------
文章を受け入れられる画像生成AI探す
->文章とイラストをまとめる

Qwen(2b/7b)
対話の場合はInstructがいい
react->ユーザーインタフェースを簡単にJavaScriptでつくれる
RAGをつかうときにLangChain, Llamaindex

### AIメモ
- 画像生成AIの別候補について
* Anything v5（ベース：SD 1.5）パソコンのスペックを抑えつつ、手軽に綺麗な日本の「アニメ・マンガ風」イラストを生成したい場合の定番モデルです。メリット: 動作が非常に軽く、VRAMが少ないパソコン（8GB以下）でもサクサク動きます。一般的なプロンプトで、最初から綺麗な「アニメ塗り」のキャラクターが出力されます。デメリット: Ponyに比べると、複雑なポーズの指定や「持ち物」などの細かい指示が通りにくい傾向があります。

- RAGを、タスクに特化した、オープンモデルAIを用いてgoogle colabで使うには？
-----
>git hubにあげるときのコミット・プッシュ

`git add`
`git commit`
`git push`

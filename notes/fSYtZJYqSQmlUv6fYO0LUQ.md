# 開発ノート
・文字入力、プロンプト入力->ストーリーを入力することに絞る
->Llama(ラマ) 3.1 8B, <=文字数Maxtext,RAG技術（要約する、外部記憶として使う）

・数式エディタの搭載
->MathJax(JavaScriptプログラム)

・ベンゼン環の描画
->RDKit

・AIによる仮漫画化　（orネーム案の考案）
->(Stable Diffusion XL(画像))　もしくは　Pony Diffusion V6(アニメや漫画風に特化) + LoRA(キャラの固定)

・タグ付けの自動化
->Mistral 7B, (LIama 3.1 8B)

・漫画を本投稿
->人間がやる

--------------------------
**文章を受け入れられる画像生成AI探す
->文章とイラストをまとめる

・Qwen(2b/7b)
**対話の場合はInstructがいい**
react->ユーザーインタフェースを簡単にJavaScriptでつくれる
RAGをつかうときにLangChain, Llamaindex
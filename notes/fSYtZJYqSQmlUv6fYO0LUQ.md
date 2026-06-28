## 開発ノート
`文字入力、プロンプト入力->ストーリーを入力することに絞る`

> 6/28
LLaVAの導入

新しく Python 3.10 を入れ直すよりも、「現在の Python 3.12 のままで、LLaVA 側の要求（Python 3.10用である PyTorch 2.1.2）を無視して最新の PyTorch を強制的に使う」方式
----
* 仮想環境（venv）を作る
````
# 仮想環境を作成
python3 -m venv l_env

# 仮想環境を有効化（画面左端に (l_env) と出ます）
source l_env/bin/activate

# pipを最新にする
pip install --upgrade pip
````
* LLaVA が求めている 2.1.2 は諦めて、現在の Python 3.12 で動く最新の PyTorch（2.4以上など）を先に手動でインストール

````
# Python 3.12 に対応した PyTorch をインストール
pip install torch torchvision torchaudio

````

* 通常通り pip install -e . を実行すると、LLaVA が「やっぱり 2.1.2 じゃないとダメ！」とエラーを出してしまいます。そのため、--no-deps（依存関係のチェックを無視する） というオプションを使って、LLaVA 本体だけを強制インストールします。

````
# LLaVAフォルダに移動
cd /workspace/LLaVA

# バージョンチェックを無視して LLaVA を強制インストール
pip install --no-deps -e .

````
* 足りない他のパッケージを補う

````
pip install -r requirements.txt

````
*上記でエラーが出たので、足りていないパッケージを別の方法で補う
````
pip install bitsandbytes fastapi markdown2[all] pydantic shortuuid uvicorn peft gradio==4.16.0 gradio_client==0.8.1 timm==0.6.13 einops-exts==0.0.4 scikit-learn==1.2.2

````
* 7Bモデルを4bitで軽く動かすコマンド
````
python -m llava.eval.run_llava \
    --model-path liuhaotian/llava-v1.5-7b \
    --image images/llava_logo.png \
    --query "What is unusual about this image?" \
    --load-4bit
````
* 次回コンテナを開いたときの注意点
もし一度コンテナを閉じたり、パソコンを再起動したりして、新しくターミナルを開き直したときは、環境を思い出すために以下のコマンドだけ毎回実行してください。


````
# 作成した仮想環境を起動する（これをやらないとLLaVAが動かない）
source l_env/bin/activate

# LLaVAのフォルダに移動する
cd /workspace/LLaVA
````
* 標準的な7Bモデルの実行コマンド
````
python -m llava.eval.run_llava \
    --model-path liuhaotian/llava-v1.5-7b \
    --image images/llava_logo.png \
    --query "What is unusual about this image?"
````

----
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
